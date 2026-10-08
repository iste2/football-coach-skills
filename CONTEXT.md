# Football Coach Skills

Ein Marketplace von Agent Skills, die Trainerinnen und Trainer im Kinder- und Jugendfußball bei Trainingsplanung, Spielvorbereitung und Fragen zur Trainingsphilosophie unterstützen – grundiert auf den offiziellen DFB-Quellen.

## Language

### Quellen

**Trainingsphilosophie Deutschland (TPD)**:
Die DFB-Publikation „Trainingsphilosophie Deutschland – Entwicklung individueller Qualität“; die fachliche Grundlage aller Skills.
_Avoid_: DFB-Philosophie, Ausbildungskonzept

**Regelheft**:
Die offiziellen DFB-Fußballregeln einer Saison (aktuell 2025/2026); ergänzende Quelle für Regelfragen.
_Avoid_: Regelwerk, Satzung

**Quelle**:
Ein Dokument, auf das sich Skill-Aussagen stützen und auf das sie verweisen (TPD, Regelheft).

### Nutzer

**Trainer**:
Jede Person, die eine Kinder- oder Jugendmannschaft (Bambini bis A-Junioren) trainiert – unabhängig von Lizenz oder Erfahrung, vom Elternteil bis zum NLZ-Trainer.
_Avoid_: Coach, Übungsleiter

### Fußball (aus der TPD)

**Trainingseinheit**:
Ein einzelnes Training; nach TPD gegliedert in Aktivierung/Erwärmung, Spielen, Zwischenblock, Spielen.
_Avoid_: Session, Übungseinheit

**Spielform**:
Eine kleine Spielform mit Regeln, Feldgröße und Spielerzahl, wie sie die TPD beschreibt (Gleichzahl, Gleichzahl mit Anspielern, Linie verteidigen/bespielen, Über-/Unterzahl).
_Avoid_: Übung, Drill

**Basistrainingsform**:
Spielformen von 1 gegen 1 bis 4 gegen 4, der Kern jeder Trainingseinheit nach TPD.

**Netto-Spielzeit**:
Die Zeit, in der ein einzelner Spieler tatsächlich am Ball- und Spielgeschehen beteiligt ist; nach TPD möglichst hoch.

**Spieltag der Zukunft**:
Die von der TPD beschriebene Wettkampfform für den Kinderfußball (kleine Teams, mehrere Felder).

### Produkt

**Skill**:
Ein eigenständiges Paket im Agent-Skills-Standard (SKILL.md), das eine Aufgabe des Trainers übernimmt, z. B. eine Trainingseinheit vorbereiten.

**Marketplace**:
Dieses Repo als Verteilquelle der Skills, zunächst für Claude Code, perspektivisch für weitere Plattformen.

## Relationships

- Eine **Trainingseinheit** besteht aus mehreren **Spielformen**
- Ein **Skill** stützt seine Aussagen auf eine oder mehrere **Quellen** und verweist auf sie
- Die **TPD** ist die führende **Quelle**; das **Regelheft** ergänzt sie bei Regelfragen

## Flagged ambiguities

- „Spiele vorbereiten“ meint Vorbereitung im Sinne des Kinder- und Jugendfußballs (Spieltag, Einsatzzeiten), nicht taktische Gegneranalyse – Erwachsenenfußball ist außerhalb des Fokus.
