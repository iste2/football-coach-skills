# Aufbau eines Claude-Code-Plugin-Marketplace und Portabilität von Agent Skills

Research zu Issue #2. Stand der Quellen: abgerufen am 2026-10-08. Getestet mit Claude Code 2.1.294.
Die Claude-Code-Doku nennt viele Details mit Versionsangabe (z. B. „requires v2.1.2xx“). Bei Abweichungen gilt die aktuelle Doku.

## Kurzfassung

1. **Zwei Schichten.** Der plattformneutrale Teil ist der *Agent-Skills-Standard*: ein Ordner `<skill-name>/SKILL.md` mit YAML-Frontmatter (`name`, `description`, optional `license`, `compatibility`, `metadata`, `allowed-tools`) und optional `scripts/`, `references/` und `assets/`. Alles andere ist Claude-Code-spezifische Verpackung: `.claude-plugin/marketplace.json`, `.claude-plugin/plugin.json`, Namespacing `/plugin:skill`, `${CLAUDE_PLUGIN_ROOT}`, Zusatz-Frontmatter wie `disable-model-invocation`, `argument-hint` und `when_to_use`.
2. **Gemeinsame Dateien.** In Claude Code geht das *innerhalb einer Plugin-Wurzel*. Dateien außerhalb der Plugin-Wurzel (`../shared`) werden nicht in den Cache kopiert. Symlinks innerhalb desselben Marketplace werden beim Kopieren aufgelöst. Für claude.ai-ZIP, Skills-API und andere Tools muss **jeder Skill eigenständig** sein. Anthropic dupliziert dafür selbst gemeinsame Dateien: `docx`, `pptx` und `xlsx` haben jeweils eine eigene `scripts/office/`-Kopie.
3. **Skill nutzt Skill.** Einen harten Aufrufmechanismus gibt es nicht. In Claude Code ruft das Modell über das Skill-Tool einen weiteren Skill auf, wenn die Anweisung das nahelegt. claude.ai sagt ausdrücklich: „skills can't explicitly reference other skills“. Empfehlung: `tpd-training-vorbereiten` funktioniert eigenständig und nennt `finde-spielform` nur als optionale Ergänzung.
4. **Slash-Commands.** Jeder Skill wird automatisch zum Command. Im Plugin heißt er `/<plugin>:<skill>`, z. B. `/tpd:frage-tpd`. Den Kurzaufruf `/frage-tpd` gibt es zusätzlich, solange kein anderer Command so heißt. Namen bestehen aus Kleinbuchstaben, Ziffern und Bindestrichen, höchstens 64 Zeichen. **Keine Umlaute** (transliterieren: ae/oe/ue/ss). Die `description` hat höchstens 1024 Zeichen. Die Kernaussage gehört in die ersten ~200 Zeichen.
5. **Große Quellen (Buch).** Das Buch kommt in Kapiteldateien unter `references/`, mit Inhaltsverzeichnis pro Datei und einem Index samt grep-Hinweisen in `SKILL.md`. `SKILL.md` bleibt unter 500 Zeilen bzw. unter ~5k Tokens. Gebündelte Dateien kosten keinen Kontext, solange sie nicht gelesen werden. Upload-Limit der Skills-API: 30 MB unkomprimiert.

---

## 1. Aufbau eines Claude-Code-Plugin-Marketplace

### 1.1 Begriffe und Dateien

- **Marketplace**: ein Verzeichnis oder Repo mit `.claude-plugin/marketplace.json`. Pflichtfelder sind `name`, `owner` und `plugins`. Jeder Eintrag in `plugins` braucht `name` und `source`. [create-marketplace], [marketplace-reference]
- **Marketplace-Wurzel**: das Verzeichnis, das `.claude-plugin/` enthält. Relative `source`-Pfade beginnen mit `./` und werden von dort aufgelöst. `..` ist verboten. [create-marketplace]
- **Plugin**: ein Verzeichnis mit optionalem Manifest `.claude-plugin/plugin.json`. Pflicht ist dort nur `name` (kebab-case). Ohne Manifest lädt Claude Code die Standard-Layout-Ordner, und der Name kommt aus dem Marketplace-Eintrag. [manifest-reference]
- **Standard-Layout im Plugin**: `skills/<name>/SKILL.md`, `commands/`, `agents/`, `hooks/hooks.json`, `.mcp.json`, `bin/` usw. Alles liegt in der Plugin-Wurzel, nicht in `.claude-plugin/`. Eine `CLAUDE.md` in der Plugin-Wurzel wird **nicht** als Kontext geladen. [manifest-reference]
- **Plugin-Quellen** (`source`): ein relativer Pfad, `github`, `git-subdir`, `url`, `npm`, `archive` oder `command`. [marketplace-reference]

Minimalbeispiel aus der Doku:

```json
{
  "name": "my-marketplace",
  "owner": { "name": "Your Name" },
  "plugins": [
    { "name": "my-first-plugin", "source": "./plugins/my-first-plugin", "description": "..." }
  ]
}
```

### 1.2 Installation

- In der Session: `/plugin marketplace add iste2/football-coach-skills` und danach `/plugin install <plugin>@<marketplace-name>`. In der Shell: `claude plugin marketplace add …` und `claude plugin install …`. [create-marketplace], [host-marketplace]
- Die Install-ID ist `<Eintragsname>@<marketplace.json name>`. Maßgeblich ist der `name` im JSON, nicht der Repo-Name. [host-marketplace]
- Der Eintragsname in `marketplace.json` und der `name` in `plugin.json` sollten übereinstimmen. Der Eintragsname dient zur Installation, der Manifest-Name ist das Präfix der Skills. [create-marketplace]
- Prüfen: `claude plugin validate ./` (mit `--strict` für CI). [create-marketplace]

### 1.3 Muster aus `anthropics/skills`, passend für Portabilität

Anthropics eigenes Skills-Repo hält alle Skills flach unter `skills/<name>/` in der Repo-Wurzel. Plugins werden nur im Marketplace gruppiert, über `source: "./"`, `strict: false` und eine explizite `skills`-Liste ([anthropics/skills marketplace.json]):

```json
{
  "name": "document-skills",
  "source": "./",
  "strict": false,
  "skills": ["./skills/xlsx", "./skills/docx", "./skills/pptx", "./skills/pdf"]
}
```

Hat ein Eintrag als `source` die Marketplace-Wurzel und listet er bestimmte `skills`-Unterordner, dann werden nur diese geladen. [manifest-reference]
Vorteil: Die Skill-Ordner bleiben reine Agent-Skills-Ordner, die sich ohne Umbau als ZIP hochladen oder in `.agents/skills/` bzw. `.claude/skills/` anderer Tools kopieren lassen.

### 1.4 Versionierung und Updates

- Ist `version` gesetzt (in `plugin.json` oder im Eintrag), bleiben Nutzer bis zur nächsten Änderung dieses Strings auf der gecachten Kopie. Ohne `version` gilt der Commit-SHA, Nutzer folgen also jedem Commit. `version` nicht an beiden Stellen setzen, weil dann `plugin.json` gewinnt. [host-marketplace], [loading]
- Auto-Update ist für Drittanbieter-Marketplaces **standardmäßig aus**. Nutzer schalten es in `/plugin` → Marketplaces ein oder aktualisieren mit `/plugin marketplace update <name>`. [host-marketplace], [loading]

### 1.5 Namensregeln für Plugin und Marketplace

- `name` in `marketplace.json` und `plugins[].name`: Buchstaben a–z/A–Z, Ziffern, `.`, `_` und `-`, Beginn mit Buchstabe oder Ziffer. Nicht-ASCII-Zeichen im Marketplace-Namen gelten als Imitation und werden abgelehnt. [marketplace-reference]
- Reserviert: Plugin-Namen, die mit `claude-`, `anthropic-` oder `cc-plugin-` beginnen. Marketplace-Namen wie `agent-skills`, `claude-plugins-official` u. a. [manifest-reference], [marketplace-reference]
- Kein `bin/` auf oberster Ebene im Plugin, wenn es auch über claude.ai/Cowork verteilt werden soll. Ausführbare Dateien kommen nach `scripts/`. [manifest-reference], [host-marketplace]
- Keine Dateien in Git LFS, weil der Clone nur Pointer-Dateien liefert. [host-marketplace]

---

## 2. Was ist plattformneutraler Agent-Skills-Standard?

Quelle: Spezifikation auf agentskills.io [spec].

```
skill-name/
├── SKILL.md          # Pflicht: Frontmatter + Anweisungen
├── scripts/          # optional: ausführbarer Code
├── references/       # optional: Doku, die bei Bedarf gelesen wird
└── assets/           # optional: Templates, Daten, Bilder
```

| Feld | Pflicht | Regel laut Spezifikation |
|---|---|---|
| `name` | ja | 1–64 Zeichen, Kleinbuchstaben/Ziffern/Bindestrich, kein `-` am Anfang oder Ende, kein `--`, **muss dem Ordnernamen entsprechen** |
| `description` | ja | 1–1024 Zeichen, sagt *was* und *wann* |
| `license` | nein | kurz |
| `compatibility` | nein | ≤ 500 Zeichen |
| `metadata` | nein | String→String-Map |
| `allowed-tools` | nein | experimentell |

Dateiverweise sind relativ zur Skill-Wurzel und gehen nur eine Ebene tief (z. B. `references/REFERENCE.md`). [spec]

**Claude-Code-Erweiterungen, die nicht portabel sind:** `when_to_use`, `argument-hint`, `arguments`, `disable-model-invocation`, `user-invocable`, `disallowed-tools`, `model`, `effort`, `context: fork`, `agent`, `hooks`, `paths`, `shell` sowie die Substitutionen `$ARGUMENTS`, `${CLAUDE_SKILL_DIR}`, `${CLAUDE_PLUGIN_ROOT}` und `` !`cmd` ``. [skills]
Wichtig: „Outside Claude Code (claude.ai uploads, the Skills API), only `name`, `description`, `license`, `compatibility`, `metadata`, and `allowed-tools` are allowed. Other keys cause a hard error.“ [skills]
→ Entweder enthält `SKILL.md` nur die sechs Spec-Felder, oder ein Export-Skript entfernt die Claude-Code-Felder vor dem ZIP-Upload.

---

## 3. Gemeinsame Dateien (z. B. eine Quellen-Wissensbasis)

### Claude Code

- Marketplace-Plugins werden nach `~/.claude/plugins/cache/<marketplace>/<plugin>/<version>/` kopiert. „Files outside the plugin directory aren't copied, so when a script inside a copied plugin reads a path above the plugin root, such as `../shared`, it doesn't find them.“ [loading]
- Komponentenpfade, die die Plugin-Wurzel verlassen, werden abgelehnt („path escapes plugin directory“). [loading], [manifest-reference]
- **Innerhalb einer Plugin-Wurzel** dürfen sich Skills Dateien teilen. Beim Muster aus 1.3 (`source: "./"`) ist die ganze Repo-Wurzel die Plugin-Wurzel, ein Ordner wie `wissen/` wird also mitkopiert. Skills verweisen darauf über `${CLAUDE_PLUGIN_ROOT}/wissen/...` oder `${CLAUDE_SKILL_DIR}/../../wissen/...`. Beides funktioniert **nur in Claude Code**.
- **Symlinks:** Ein Symlink zu einem Ziel innerhalb desselben Marketplace wird beim Kopieren in den Cache *aufgelöst*, der Inhalt wird also kopiert. Ziele außerhalb des Marketplace werden übersprungen. Bei lokal hinzugefügten Marketplaces bleiben nur Symlinks innerhalb des eigenen Plugins erhalten. [host-marketplace]
  Unter Windows brauchen Git-Symlinks den Developer Mode bzw. `core.symlinks`. Das ist für dieses Repo (Windows-Entwicklung) fehleranfällig.

### claude.ai, Skills-API und andere Tools

- Ein ZIP enthält genau einen Skill-Ordner. Die API erwartet `SKILL.md` „at the upload root (or at the top of a single enclosing folder)“. Dateien außerhalb des Skill-Ordners gibt es dort nicht. [help-create], [skills-guide]
- Die Spezifikation definiert nur den Inhalt *eines* Skill-Ordners. Ein Konzept für geteilte Dateien zwischen Skills gibt es nicht. [spec], [client-impl]
- Belege aus der Praxis: In `anthropics/skills` hat jeder der Skills `docx`, `pptx` und `xlsx` einen eigenen Ordner `scripts/office/`. Anthropic dupliziert also, statt zu teilen. [anthropics/skills]

### Empfehlung

Jeder Skill ist **eigenständig** und hat sein eigenes `references/`. Die gemeinsame Wissensbasis (TPD-Quellen) liegt einmal als Single Source of Truth im Repo, z. B. unter `wissen/`, und ein **Sync- bzw. Build-Skript** kopiert die benötigten Ausschnitte in `skills/<name>/references/`. Kopie statt Symlink, wegen Windows und Portabilität. Optional prüft CI, dass die Kopien aktuell sind.

---

## 4. Wie ein Skill einen anderen nutzt

- **Claude Code:** Das Modell lädt Skills über das **Skill-Tool**. Jeder Skill ohne `disable-model-invocation: true` ist für das Modell aufrufbar, auch während ein anderer Skill aktiv ist. Steht in `tpd-training-vorbereiten` etwa „Für die Auswahl der Spielformen den Skill `finde-spielform` verwenden“, ruft Claude ihn in der Regel auf. Garantiert ist das nicht, es ist eine Modellentscheidung. Ist am Ziel `disable-model-invocation: true` gesetzt, blockiert Claude Code den Aufruf. [skills]
  Weitere Mechanismen: Ein Nutzer kann mehrere Skills stapeln (`/a /b …`, höchstens 6). Ein Subagent kann Skills über sein `skills`-Feld vorladen. Ein Plugin kann über `dependencies` andere Plugins voraussetzen. [skills], [manifest-reference]
- **claude.ai:** „While skills can't explicitly reference other skills, Claude can use multiple skills together automatically.“ [help-create]
- **Andere Clients:** Die Aktivierung ist laut Implementierungsleitfaden modellgesteuert (Katalog → Modell entscheidet). Querverweise sind nicht spezifiziert. [client-impl]

### Empfehlung

`tpd-training-vorbereiten` muss **ohne** `finde-spielform` funktionieren. Was es zwingend braucht, z. B. ein Kriterienraster für Spielformen, liegt als eigene Kopie in seinem `references/`. Der Verweis auf `finde-spielform` ist ein optionaler Hinweis mit Namen („falls verfügbar …“), kein Pfadverweis in einen anderen Skill-Ordner.

---

## 5. Slash-Commands und Namenskonventionen

- Jeder Skill ist automatisch ein Slash-Command. Der Name kommt aus dem `name`-Frontmatter oder, falls der fehlt, aus dem Ordnernamen. [skills]
- Plugin-Skills sind namespaced: `my-plugin/skills/review/SKILL.md` → `/my-plugin:review`. „bare `/fancy` also works unless another command uses that name.“ [skills]
  → Bei einem Plugin namens `tpd` ist `frage-tpd` als `/tpd:frage-tpd` und meist auch als `/frage-tpd` aufrufbar.
- Steuerung: `disable-model-invocation: true` macht den Skill nur manuell aufrufbar. `user-invocable: false` blendet ihn im `/`-Menü aus. Beide Felder gibt es nur in Claude Code. [skills]

### Längen und Zeichen: die Quellen widersprechen sich

| Quelle | `name` | `description` |
|---|---|---|
| agentskills.io-Spezifikation [spec] | 1–64, „unicode lowercase alphanumeric characters (`a-z`, `0-9`) and hyphens“ | 1–1024 |
| Referenz-Validator `skills-ref` [skills-ref] | `isalnum()` nach NFKC, akzeptiert also z. B. `ü` („Skill names support i18n characters“) | ≤ 1024 |
| Anthropic Platform-Doku [overview], [best-practices] | max. 64, „only lowercase letters, numbers, and hyphens“, keine XML-Tags, nicht „anthropic“/„claude“ | max. 1024, keine XML-Tags |
| Claude Code [skills] | keine Zeichenregel dokumentiert | `description` + `when_to_use` werden im Listing bei 1536 Zeichen abgeschnitten |
| claude.ai Help Center [help-create] | „64 characters maximum“ | „**200 characters maximum**“ |

Eigener Test: `claude plugin validate` (v2.1.294) akzeptiert einen Plugin-Skill `skills/übung-test/` mit `name: übung-test` ohne Warnung.

**Empfehlung:**
- Nur `[a-z0-9-]`. Umlaute transliterieren: `uebung`, `groesse`, `fuer`. Gründe: Die Platform-Doku erlaubt nur ASCII, der Ordnername muss gleich `name` sein, und Nicht-ASCII-Pfade sind zwischen Git, Windows und macOS (Unicode-Normalisierung) fehleranfällig.
- Keine Präfixe `claude-`/`anthropic-`.
- `description` auf Deutsch, in der dritten Person, mit Was und Wann. Die wichtigsten Trigger-Wörter stehen in den ersten ~200 Zeichen, insgesamt höchstens 1024 Zeichen.
- Das Skill-Listing in Claude Code hat ein Budget von ~1 % des Kontextfensters. Bei vielen Skills werden Beschreibungen der selten genutzten gekürzt. Deshalb lieber wenige, gut abgegrenzte Skills. [skills]

---

## 6. claude.ai (ZIP-Upload), API und andere Agent-Skills-Tools

| Plattform | Verteilung | Besonderheiten |
|---|---|---|
| Claude Code | Plugin-Marketplace, `~/.claude/skills/`, `.claude/skills/` | volle Frontmatter-Erweiterungen, Substitutionen, Netzwerkzugriff [skills], [overview] |
| claude.ai | ZIP-Upload unter Settings, pro Nutzer | ZIP enthält den Skill-Ordner als Wurzel, Ordnername = Skill-Name. Code-Ausführung muss aktiv sein. Nur Spec-Frontmatter-Felder. Netzwerk je nach Einstellung [help-create], [overview], [skills] |
| Claude API (Skills-API) | Upload über `/v1/skills`, workspace-weit | < 30 MB unkomprimiert, max. 20 Skills pro Request, kein Netzwerk, keine Paketinstallation zur Laufzeit [skills-guide], [overview] |
| Andere Clients (Cursor, VS Code/Copilot, Gemini CLI, Codex, OpenCode, Goose, Junie, Kiro u. v. m.) | Kopie nach `.agents/skills/` oder in das client-eigene Verzeichnis | Konvention `.agents/skills/` und `~/.agents/skills/`. Manche scannen auch `.claude/skills/`. Validierung oft tolerant [clients], [client-impl] |

- Custom Skills **synchronisieren nicht** zwischen claude.ai, API und Claude Code. [overview]
- Ergänzung: Auf Team- und Enterprise-Plänen können Organisationen ganze Plugin-Marketplaces über die claude.ai-Organisationseinstellungen synchronisieren (privates Repo, kein `bin/`). Diese Plugins laden in Claude Code als `<name>@synced`. [host-marketplace], [loading]
- Abweichungen in der Help-Center-Seite: Sie schreibt die Datei als `skill.md` und nennt ein Frontmatter-Feld `dependencies`. Laut Claude-Code-Doku führt jedes Nicht-Spec-Feld beim Upload zu einem Fehler. Empfehlung: `SKILL.md` (Großschreibung wie in Spec und Anthropic-Repo) und **kein** `dependencies`-Feld. Abhängigkeiten stattdessen im Text oder über `compatibility` angeben. [help-create], [skills]

### Was portabel bleibt

- Ordner `<name>/SKILL.md` mit `name` und `description`, optional `license`, `compatibility`, `metadata`
- relative Verweise `references/…`, `scripts/…` und `assets/…`, eine Ebene tief, mit Vorwärts-Slashes
- reine Markdown-Anweisungen. Skripte nur, wenn sie ohne Netzwerk und ohne Paketinstallation laufen (API).

### Was nicht portabel ist

- `marketplace.json`, `plugin.json`, Namespacing `/plugin:skill`, Hooks, MCP, Agents
- Frontmatter-Erweiterungen von Claude Code (siehe Abschnitt 2), `$ARGUMENTS`, `${CLAUDE_*}`
- Verweise aus dem Skill-Ordner hinaus (`../`), Symlinks

---

## 7. Größenlimits und Progressive Disclosure für große Referenzdateien

Ladestufen ([overview], [spec], [client-impl]):

| Stufe | Wann | Kosten |
|---|---|---|
| Metadaten (`name` + `description`) | immer, beim Start | ~50–100 Tokens pro Skill |
| `SKILL.md`-Body | bei Aktivierung | Empfehlung < 5.000 Tokens bzw. < 500 Zeilen |
| `references/`, `scripts/`, `assets/` | nur bei Bedarf | 0, bis sie gelesen werden. Bei Skripten zählt nur die Ausgabe |

- „No practical limit on bundled content: Files don't consume context until accessed.“ [overview]
- Harte Grenzen: Skills-API < 30 MB unkomprimiert [skills-guide]. Für Archive-Quellen eines Marketplace gelten 256 MiB Download, 512 MiB je Datei, 1 GiB entpackt [host-marketplace]. Für claude.ai-ZIPs nennt das Help Center kein Limit [help-create].
- Claude Code: Ein aktivierter Skill bleibt im Gespräch. Nach einer Kompaktierung werden pro Skill nur die ersten 5.000 Tokens wieder angehängt, insgesamt höchstens 25.000. Kritische Regeln gehören deshalb an den **Anfang** von `SKILL.md`. [skills]

Empfehlungen aus den Best Practices [best-practices]:
- Verweise nur eine Ebene tief ab `SKILL.md`. Bei verschachtelten Verweisen liest Claude oft nur teilweise (z. B. `head -100`).
- Referenzdateien über 100 Zeilen bekommen oben ein Inhaltsverzeichnis.
- Gliederung nach Domänen (`reference/finance.md`, `reference/sales.md` …) mit grep-Hinweisen in `SKILL.md`.
- Sprechende Dateinamen, Vorwärts-Slashes.

### Für ein ganzes Buch als Markdown

```
frage-tpd/
├── SKILL.md                     # Ablauf, Zitierregeln, Index aller Kapitel mit 1-Zeilen-Inhalt, grep-Beispiele
└── references/
    ├── 01-spielidee.md          # je Kapitel eine Datei, jeweils mit eigenem Inhaltsverzeichnis
    ├── 02-ausbildungsstufen.md
    ├── ...
    └── glossar.md
```

Also keine einzelne Riesendatei. Kapitel- bzw. Themendateien, die direkt aus `SKILL.md` verlinkt sind, und dort Anweisungen wie „Suche zuerst mit `grep -n -i "<Begriff>" references/*.md`, lies dann nur den relevanten Abschnitt“.

---

## Quellen

- [create-marketplace] Claude Code Docs, Create a marketplace: https://code.claude.com/docs/en/plugin-marketplaces
- [host-marketplace] Claude Code Docs, Host and maintain a marketplace: https://code.claude.com/docs/en/plugins/host-marketplace
- [marketplace-reference] Claude Code Docs, Marketplace reference: https://code.claude.com/docs/en/plugins/marketplace-reference
- [manifest-reference] Claude Code Docs, Plugin manifest reference: https://code.claude.com/docs/en/plugins-reference
- [loading] Claude Code Docs, Plugin loading reference: https://code.claude.com/docs/en/plugins/loading
- [skills] Claude Code Docs, Skills: https://code.claude.com/docs/en/skills
- [spec] Agent Skills Specification: https://agentskills.io/specification
- [client-impl] agentskills.io, How to add skills support to your agent: https://agentskills.io/client-implementation/adding-skills-support
- [clients] agentskills.io, Client Showcase: https://agentskills.io/clients
- [skills-ref] Referenz-Validator: https://github.com/agentskills/agentskills/blob/main/skills-ref/src/skills_ref/validator.py
- [overview] Anthropic Platform Docs, Agent Skills overview: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
- [best-practices] Anthropic Platform Docs, Skill authoring best practices: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices
- [skills-guide] Anthropic Platform Docs, Using Agent Skills with the API: https://platform.claude.com/docs/en/build-with-claude/skills-guide
- [help-create] Claude Help Center, How to create custom Skills: https://support.claude.com/en/articles/12512198-creating-custom-skills
- [anthropics/skills] https://github.com/anthropics/skills (`.claude-plugin/marketplace.json`, `skills/docx|pptx|xlsx/scripts/office/`)
