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

**Schwerpunkt**:
Das Lern- bzw. Trainingsziel, das eine Trainingsform „pointiert“ (z. B. Umschalten nach Ballgewinn, Torabschluss).
_Avoid_: Trainingsziel, Thema, Fokus

**Spielsituation**:
Ein im Wettkampf beobachtetes Verhalten oder Problem einer Mannschaft (z. B. „Ballverluste im Aufbau“); wird in einen Schwerpunkt übersetzt.
_Avoid_: Spielszene, Problem

### Trainingsformen

**Trainingsform**:
Oberbegriff für alles, was in einer Trainingseinheit gespielt oder geübt wird; entweder Übungsform oder Spielform.
_Avoid_: Übung, Drill

**Übungsform**:
Eine Trainingsform aus Start-Stop-Situationen (Aktion endet, neue beginnt). Ausprägungen: reine Übungsform (ohne Gegner, eine vorgegebene Lösung), wettkampfnahe Übungsform (Gegner vereinfacht, mehrere Lösungen), spielgemäße Übungsform (positionsabhängig, Gegner spielgemäß, realistischer Spielausschnitt).
_Avoid_: Übung, Drill

**Spielform**:
Eine Trainingsform als Endlosschleife mit zwei oder mehr Mannschaften und regelgemäßer Spielfortsetzung. Ausprägungen: reine Spielform (keine Spielrichtung), wettkampfgemäße Spielform (Spielrichtung, Tore, positionsunabhängig), spielnahe Spielform (Spielrichtung, Räume wie im 11 gegen 11).
_Avoid_: Spiel, Übung

**TPD-Spielform**:
Eine der 28 in der TPD beschriebenen kleinen Spielformen (Gleichzahl, Gleichzahl mit Anspielern, Linie verteidigen/bespielen, Über-/Unterzahl), jeweils mit Organisation, Ablauf und Variationen.

**Provokationsregel**:
Eine Zusatzregel einer Spielform, die ein bestimmtes Verhalten gezielt herausfordert (z. B. Shotclock, Rückpassregel, „nur nach vorne passen“); laut TPD neben Feldgröße und -form das Mittel, um Schwerpunkte zu setzen.
_Avoid_: Coachingregel, Sonderregel

**Basistrainingsform**:
Spielformen von 1 gegen 1 bis 4 gegen 4, der Kern jeder Trainingseinheit nach TPD.

### Weitere TPD-Begriffe

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

- Eine **Trainingseinheit** besteht aus mehreren **Trainingsformen**; nach TPD überwiegend **Spielformen**, im Zwischenblock auch **Übungsformen**
- Jede **TPD-Spielform** ist eine **Spielform**, nicht jede **Spielform** ist eine **TPD-Spielform**
- Eine **Spielsituation** wird in einen **Schwerpunkt** übersetzt; eine **Trainingsform** pointiert einen oder mehrere **Schwerpunkte**
- Ein **Skill** stützt seine Aussagen auf eine oder mehrere **Quellen** und verweist auf sie
- Die **TPD** ist die führende **Quelle**; das **Regelheft** ergänzt sie bei Regelfragen

## Flagged ambiguities

- „Spiele vorbereiten“ meint Vorbereitung im Sinne des Kinder- und Jugendfußballs (Spieltag, Einsatzzeiten), nicht taktische Gegneranalyse – Erwachsenenfußball ist außerhalb des Fokus.
