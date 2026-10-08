# plane-trainingseinheit ruft finde-trainingsform auf, statt Inhalte selbst zu bestimmen

`plane-trainingseinheit` baut nur das Gerüst einer Trainingseinheit nach den TPD-Vorlagen (Ablauf, Zeiten, Felder) und lässt jede Trainingsform von `finde-trainingsform` bestimmen; auch die Übersetzung einer Spielsituation in einen Schwerpunkt geschieht nur dort. Wir weichen damit bewusst von der Empfehlung aus der Marketplace-Recherche (#2) ab, Skills vollständig eigenständig zu halten: Auswahl, Abwandlung und Konstruktion von Trainingsformen sollen an genau einer Stelle leben, damit sie nicht auseinanderlaufen und nur einmal gegen die TPD-Prinzipien geprüft werden müssen.

## Consequences

- Claude Code ist die Hauptplattform: Dort ruft das Modell `finde-trainingsform` über das Skill-Tool auf. `finde-trainingsform` darf deshalb nie `disable-model-invocation: true` setzen.
- Auf claude.ai und anderen Agent-Skills-Tools gibt es keinen garantierten Aufruf zwischen Skills. Ist `finde-trainingsform` nicht verfügbar, sagt `plane-trainingseinheit` das dem Trainer und nennt den fehlenden Skill, statt selbst Trainingsformen zu wählen.
- Die beiden Skills werden immer gemeinsam ausgeliefert.
