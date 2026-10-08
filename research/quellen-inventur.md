# Quellen-Inventur: TPD und Regelheft 2025/2026

Recherche zu Issue #3 („Inhaltsinventur von TPD und Regelheft“). Stand: 2026-10-08.

**Quellen (lokal, nicht im Repo):**

- **TPD**: DFB, *Trainingsphilosophie Deutschland – Entwicklung individueller Qualität*. `original_TPD.pdf`, 70 Seiten A4, QuarkXPress-Export vom 14.10.2024, 14,2 MB. Gedruckte Seitenzahl = PDF-Seite.
- **RH**: DFB, *Fußball-Regeln 2025/2026* (DFB-Ausgabe der IFAB-Spielregeln mit „Zusätzlichen Erläuterungen des DFB“). `original_Regelheft_2025_2026.pdf`, 164 Seiten (A5-ähnlich), InDesign/PDF-X-3 vom 08./09.07.2025, 7,1 MB. **Achtung: gedruckte Seitenzahl = PDF-Seite − 2.** Unten steht deshalb immer „PDF-S. x / gedr. S. y“.

**Werkzeuge:** `pdfinfo`, `pdftotext` (Poppler, mit `-enc UTF-8`), `pdfimages -list`, `pdftoppm` (300 dpi), Python `pypdf` 6.19 (Lesezeichen, Link-Annotationen), `zxing-cpp` (QR-Dekodierung). Visuelle Prüfung über gerenderte Seiten (u. a. TPD S. 4, 5, 10, 19, 24, 54; RH PDF-S. 41, 105). Die QR-Ziele wurden per YouTube-oEmbed und durch Auflösen der qrcc.me-Weiterleitungen verifiziert.

---

## 1. Gliederung TPD (mit Seiten)

Die Gliederung stammt aus den PDF-Lesezeichen und deckt sich mit dem Inhaltsverzeichnis auf S. 3.

| Seite | Abschnitt | Inhaltsart |
|---|---|---|
| 1 | Titel | Cover (Foto) |
| 2 | Einführung „Eine Trainingsphilosophie für alle“ | Fließtext, Porträts Kompetenzteam |
| 3 | Inhalt | Inhaltsverzeichnis mit internen Links |
| 4–13 | **01 Trainingsphilosophie Deutschland** | Fließtext, Infografik, Zitatkästen, Steckbriefe, Tabellen, QR-Codes |
| 4–5 | Infografik „Freude / Intensität / Wiederholung – Basistrainingsformen 1 vs 1 bis 4 vs 4“ | Grafik mit 3 QR-Codes |
| 6–7 | „Das Warum“ (U21-Einsatzzeiten, Dropout), Kompetenzteam, „Der Spieler im Mittelpunkt“ | Fließtext, Liniendiagramm U23-Einsätze (S. 6) |
| 8–9 | Freude, Intensität, Wiederholung; Mindest-Nettospielzeiten | Fließtext; Tabelle „Anzahl der Aktionen 3v3 vs. 7v7“ (S. 9) |
| 10 | „Die beste Trainingseinheit“: Struktur 15/30/15/30 | Tabelle, Balkendiagramm (Trainerumfrage) |
| 11 | Altersgrenzen der Spielformen, Feldeinteilung nach Entwicklungsstand | Fließtext |
| 12 | Übergreifende Konzepte, Verweis auf „Mein.Fußball“ auf FUSSBALL.DE | Fließtext, 1 QR-Code |
| 13 | Videos im Schnellzugriff | 8 QR-Codes |
| 14–51 | **02 Spielformen** | Kategorie-Intros und Spielform-Steckbriefe mit Feldskizzen |
| 14–15 | Überblick über die 4 Kategorien | Kurztexte |
| 16–29 | Gleichzahlspiele | Intro S. 16–18, Spielformen S. 19–29 |
| 30–37 | Gleichzahlspiele mit Anspielern | Intro S. 30–31, Spielformen S. 32–37 |
| 38–45 | Eine Linie verteidigen und bespielen | Intro S. 38–39, Spielformen S. 40–45 |
| 46–51 | Über-/Unterzahlspiele | Intro S. 46–47, Spielformen S. 48–51 |
| 52–61 | **03 Trainingseinheiten für den Kinder- und Jugendfußball** | Strukturtabelle (S. 53), Einheiten mit Skizzen |
| 54–55 | Bambini-Spielstunde | |
| 56–57 | Trainingseinheit F-/E-Junioren | |
| 58–59 | Trainingseinheit D- bis A-Junioren | |
| 60–61 | D-Junioren-Einheit mit Antonio Di Salvo | |
| 62–65 | **04 Der Spieltag der Zukunft** | Fließtext, 1 QR-Code (S. 63) |
| 66–68 | **05 Die Schule des Kleinfeldfußballs** | Fließtext, Aufbau-Skizze, 1 QR-Code (S. 67) |
| 69–70 | Impressum, Rückseite | |

Seiten ohne nennenswerten Text, also reine Foto- oder Kapitelaufmacher: 1, 16, 38, 46, 70 (pdftotext liefert dort jeweils unter 130 Zeichen).

### Zentrale Querschnittsinhalte (für spätere Skills wichtig)

- **Kernbotschaften:** mindestens 2 Einheiten pro Woche in kleinen Spielformen auf mehreren Feldern; „Freude, Intensität, Wiederholung“ (S. 2, 8–10).
- **Mindest-Nettospielzeit pro Spieler und Woche:** U8–U16 mindestens 48 Minuten, ab U17 mindestens 32 Minuten (S. 8).
- **„Beste Trainingseinheit“:** 15 Min. Aktivierung, 30 Min. Spielblock 1 (mehrmals 3–4 Min. netto, 1–2 Min. Pause), 15 Min. Zwischenblock, 30 Min. Spielblock 2 (S. 10, wiederholt auf S. 53).
- **Altersgrenzen der Spielformgröße** (S. 11):
  - Bambini höchstens 2v2;
  - F-Junioren höchstens 3+TW v 3+TW;
  - E-Junioren höchstens 4+TW v 4+TW;
  - D- bis A-Junioren 1v1 bis 4v4, bei 4+TW-Formen zusätzlich bis zu 2 Anspieler pro Team.
- **Spielfeldbegleiter** (S. 11): Bambini 1 pro 4 Kinder, F-Junioren 1 pro 6 Spieler.
- **Feldeinteilung** nach Entwicklungsstand bzw. biologischem Alter, mit Niveaus Gold/Silber/Bronze (S. 11, 63). Positionsspezifik erst ab der C-Jugend (S. 8, 11).

## 2. Spielform-Steckbriefe in der TPD

### Aufbau eines Steckbriefs

Beispiele: S. 19, 20, 24, 51. Typischerweise steht links oder oben eine Feldskizze, rechts der Text.

| Feld | Vorhanden? | Bemerkung |
|---|---|---|
| **Titel** | immer | Enthält die Spielerzahl bzw. das Format, z. B. „4 PLUS TW PLUS 2 GEGEN 4 PLUS TW PLUS 2 MIT DIAGONALEN ANSPIELERN“ (S. 32) |
| **ORGANISATION** | immer | Feldgröße in Metern (z. B. „25 x 25 Meter“, S. 19) oder nur „doppelter Strafraum“ ohne Meterangabe (S. 20, 29, 35, 40, 48). Außerdem Tore/Torhüter, Teamgröße, Position des Trainers und Balldepots. Teils als „ORGANISATION UND ABLAUF“ zusammengefasst (S. 35) |
| **ABLAUF** | fast immer | Die eigentlichen Spielregeln: Eröffnung, Zählweise, Shotclock, Angriffsrecht, Abseits |
| **VARIATION(EN)** | meist | Provokationsregeln, Feldveränderungen |
| **HINWEIS(E)** | gelegentlich | z. B. Belastungssteuerung oder Rotation der Startspieler (S. 20, 21), Sekunden laut herunterzählen (S. 22) |
| **KOMMENTAR von …** | 1–4 pro Seite | Zitate aus dem Kompetenzteam (Wolf, Gerland, Wagner, Di Salvo u. a.). Hier stecken die impliziten Coaching-Hinweise, z. B. „Coaching einfach halten“ (Balitsch, S. 23) |
| **Feldskizze** | immer | Spielerpositionen (Teamfarben Blau/Rot/Gelb), Pass-, Lauf- und Dribbelpfeile, Tore, Hütchen, Trainerposition, Balldepots |
| Alter / Altersklasse | **fehlt** | Muss aus den globalen Grenzen auf S. 11 abgeleitet werden. Einzelhinweise stehen nur in Kommentaren, z. B. „Bei Kindern … 10 (12) Sekunden“ (S. 22) |
| Dauer / Belastung | **fehlt als Feld** | Nur vereinzelt im Ablauf, z. B. „15 (20) Sekunden“ (S. 21) |
| Coaching-Punkte | **fehlt als Feld** | „COACHINGTIPPS“ gibt es nur in der Di-Salvo-Einheit (S. 60–61) |
| Ziel / Schwerpunkt | nur pro Kategorie | Steht in den Kategorie-Intros (S. 14–15, 18, 30–31, 39, 47), nicht je Spielform |

### Anzahl der Spielformen je Kategorie

Gezählt wird nach Kapitelbereich (Lesezeichen). Eine Spielform zählt, wenn sie einen eigenen Titel und einen ORGANISATION-Block hat. Die Formen auf S. 26–29 enthalten bereits Anspieler, stehen aber im Kapitel „Gleichzahlspiele“.

| Kategorie (Seiten) | Anzahl | Spielformen (Seite) |
|---|---|---|
| Gleichzahlspiele (16–29) | **11** | 4 gegen 4 (19) · 1 gegen 1 bis 4 gegen 4 (20) · Vom 2 gegen 2 zum 4 gegen 4 (21) · 2 gegen 2 in 8 Sekunden (22) · Funino im 3 gegen 3 (23) · 3 gegen 3 mit drehendem Angriffsrecht (24) · 4 gegen 4 mit drehendem Angriffsrecht (25) · 3 gegen 3 mit drehendem Angriffsrecht mit Anspieler (26) · dito auf zwei 22 x 25 m-Feldern (27) · Funino im 2 gegen 2 mit Anspieler und drehendem Angriffsrecht (28) · 4 plus TW gegen 4 plus Anspieler (29) |
| Gleichzahlspiele mit Anspielern (30–37) | **7** | 4+TW+2 gegen 4+TW+2 mit diagonalen Anspielern (32) · 3+TW+2 gegen 3+TW+2 mit Anspielern neben dem Tor (33) · 4+TW+2 gegen 4+TW+2 mit Anspielern zum Flanken (34) · 4+TW gegen 4+TW plus Flankengeber (35) · Funino im 3 gegen 3 mit Anspieler (36) · 3 plus 2 diagonale Anspieler gegen 3+TW+1 Anspieler (37) · 3 gegen 3 mit drehendem Angriffsrecht plus 2 diagonale Anspieler (37) |
| Eine Linie verteidigen/bespielen (38–45) | **6** | 4 gegen 4 auf Linie verteidigen (40) · dito breit, 30 x 45 m-Sechseck (41) · 3 gegen 3 plus TW auf Linie verteidigen (42) · 5+TW gegen 5+TW auf Linie verteidigen (43, überschreitet das 4v4-Maximum aus S. 11) · 3-gegen-3-Liniendribbling I (44) · 3-gegen-3-Liniendribbling II (45) |
| Über-/Unterzahlspiele (46–51) | **4** | 4+TW gegen 4+TW plus 1 (48) · 4+TW gegen 4 plus 1 – Tore nur direkt (49) · 4 gegen 3 mit „fliegendem“ Torhüter (50) · Funino im 3 gegen 3 plus 1 – Tore nur direkt/Stürmer neutral (51) |
| **Summe** | **28** | |

Hinzu kommen 4 Funino-Varianten, verteilt auf die Kategorien (S. 23, 28, 36, 51). Funino ist laut Hannes Wolf „ein pures Gleichzahlspiel“ (S. 18).

### Trainingseinheiten-Vorlagen (Kapitel 03, S. 52–61)

Jede Einheit beginnt mit einem Organisationsblock („So ist der Aufbau“, „Das Material benötigst du“) und einer Gesamtskizze. Danach folgen die Phasen Aktivierung, Spielphase 1, Zwischenblock und Spielphase 2, jeweils mit Skizze und dem Schema ORGANISATION (UND ABLAUF), VARIATIONEN und HINWEISE.

| Einheit | Seiten | Aufbau | Inhalte (Minuten) |
|---|---|---|---|
| Bambini-Spielstunde | 54–55 | 3 Minifußballfelder ca. 20 x 16 m (Minitore, Dribbeltore, Stangentore); 18 Bälle | Fangspiel „Weißer Hai“ (10) · 1-gegen-1-Turnier (20) · „Ballraub“ (10) · 2-gegen-2-Turnier (20), zusammen ca. 60 Min. Mit Geschichten bzw. Bewegungsaufgaben |
| F-/E-Junioren | 56–57 | 3 Felder ca. 25 x 20 m (Hybridfeld, Minifußballfeld, Kleinfeld); 18 Bälle | „Schatzjäger“ (15) · 3-gegen-3-Variationen (30) · 2 gegen 2 und 1 gegen 1 (15) · 3-gegen-3-Turnier (30), zusammen 90 Min. |
| D- bis A-Junioren | 58–59 | 2 Hybridfelder ca. 33 x 25 m (Jugendtor + 2 Minitore); 20 Bälle | Ballgeschicklichkeit (15) · Sechseckspiel/Drehrecht (30) · 3-Farben-Spiel/2 gegen 2 (15) · 4 gegen 4 Linie verteidigen (30), zusammen 90 Min. |
| D-Junioren mit A. Di Salvo | 60–61 | Verschiedene Felder | Fintieren und Abkappen · 3 gegen 3 mit wechselndem Angriffsrecht · Flankenwettbewerb · 4 plus 2 gegen 4 plus 2. Ohne Minutenangaben, dafür mit **COACHINGTIPPS** und Kommentaren |

### „Der Spieltag der Zukunft“ (S. 62–65)

Das Kapitel ist Fließtext und enthält keine Steckbriefe. Kernaussagen:

- **„Alle spielen immer“:** höchstens 1 Rotationsspieler pro Feld. Sobald ein weiteres 2 gegen 2 möglich ist, wird ein weiteres Feld aufgebaut. Gemischte Formate sind erlaubt, z. B. bei E-Junioren 1x 5v5 inkl. TW und 2x 3v3. Beispiel: Spielzeit 6 x 7 Min., jedes Kind spielt alle 42 Min. (S. 62–63).
- Mindestens 3 Bälle pro Feld; Spielfeldbegleiter bzw. Eltern holen die Bälle (S. 63).
- Teams nach Niveau Gold/Silber/Bronze einteilen; ab den F-Junioren ist der Champions-League-Modus möglich (S. 63).
- Rolle der Erwachsenen; Festivals, Freundschaftsspiele und Turniere (S. 64).
- **Vision:** 7v7 als „Zwillingsspiel“ auf zwei Feldern für die D-Jugend (S. 64). „Spielformate-Buffet“, z. B. C-Junioren mit 7v7 auf zwei Feldern oder 9v9 bzw. 11v11 (S. 65). Mindestens 75 % Spielzeit für alle (Wolf, S. 65).
- Spielformate und Spielzeiten der Wettspielreform werden *nicht* tabellarisch aufgeführt. Es gibt nur den Verweis auf den „neuen Kinderfußball“ und das Video auf S. 63.

### „Die Schule des Kleinfeldfußballs“ (S. 66–68)

- Zielgruppe sind die Klassen 1–6 im Ganztag. 3v3 als Kernform, mindestens 30 Kinder täglich, polysportiv nutzbar (S. 66).
- Konkretes Setting: Bolzplatz geviertelt in 4 Minifußballfelder à ca. 15 x 20 m. Material: 16 Mini-, Hütchen- oder Stangentore, 12 Leibchen, 16 Bälle (S. 68).
- Aufgabenliste der Spielfeldbegleiter in der Schule (S. 68).

## 3. Extrahierbarkeit

**Beide PDFs haben einen vollständigen Textlayer**, OCR ist nicht nötig. Keine Seite ist als reines Bild gesetzt.

- TPD: 232 KB Text; Inhaltsseiten liefern pro Seite 500–3.500 Zeichen.
- RH: 243 KB Text.
- Beide sind nicht getaggt („Tagged: no“), es gibt also keine logische Lesereihenfolge.

### Was bei der Textextraktion verloren geht oder verfälscht wird

1. **Feldskizzen (TPD):** Sie sind als eingebettete JPEG-Bilder enthalten (CMYK, 150 ppi, z. B. S. 19: 711 x 607 px). Mit `pdfimages` lassen sie sich als Dateien extrahieren, ihr Inhalt ist aber nicht als Text verfügbar: Positionen, Laufwege, Passpfeile, Torarten. Textstellen wie „(hier: Blau)“, „gemäß Abbildung“ oder „siehe Abbildung 2“ (S. 51, 56–58) sind ohne Skizze nur halb verständlich.
2. **Infografiken und Tabellen:** Die Infografik S. 4–5 und die Tabellen S. 9, 10 und 53 werden zu Wortketten bzw. Zahlenkolonnen ohne Zeilenbezug zerlegt. Ein Beispiel ist die Wiederholungszahlen-Tabelle auf S. 9.
3. **Lesereihenfolge:** KOMMENTAR-Kästen, Pull-Quotes und Bildnachweise („Foto: …“) werden mitten in Steckbriefe und Fließtext geschoben. Fließtext läuft teils über Seiten weiter, z. B. „verlore-“ auf S. 8 → „nen Spielen“ auf S. 9. Auch das Inhaltsverzeichnis auf S. 3 wird durcheinandergewürfelt.
4. **Typografie-Artefakte:**
   - 53 ﬁ/ﬂ-Ligaturen in der TPD (per Unicode-NFKC normalisieren);
   - gesperrte Kolumnentitel („T R A I N I N G S P H I L O S O P H I E“);
   - zusammengezogene Trennstriche („Kinderund Jugendfußball“, S. 5);
   - im RH abgetrennte Initialen („W enn“, „D ie“).
5. **Encoding:** Ohne `-enc UTF-8` erzeugt pdftotext unter Windows Latin-1-Mojibake.
6. **QR-Codes:** Sie sind als Vektorgrafik gesetzt und erscheinen im Text gar nicht. Die Ziele lassen sich aber zuverlässig aus den Link-Annotationen auslesen (pypdf) oder nach dem Rendern dekodieren (zxing-cpp; OpenCV scheiterte an den abgerundeten Modulen).
7. **Verstümmelte URL (RH):** Die Anzeige auf PDF-S. 105 / gedr. S. 103 zeigt im Bild „dfb.de/mehr-fussball/kinderfussball“. Extrahiert wird daraus „dfb.de/mkinehdre-rfussball/kinderfussball“.
8. **RH-Schiedsrichterzeichen** (z. B. PDF-S. 41) und die Spielfeldmaße in Regel 1 sind Vektorgrafiken mit Beschriftung. Erhalten bleiben nur die Beschriftungen („Vorteil (1)“, „9,15 m“), die Grafik selbst nicht. Rasterbilder hat das RH nur auf PDF-S. 1, 2, 6, 13, 53, 63, 105 und 163.

**Konsequenz für die Skill-Erstellung:** Die Steckbrieftexte (ORGANISATION, ABLAUF, VARIATIONEN, HINWEIS) lassen sich gut seitenweise extrahieren, müssen aber manuell bzw. halbautomatisch von Kommentaren und Bildnachweisen getrennt werden. Die Skizzen müssen entweder als Bild mitgeführt oder als strukturierte Beschreibung neu verfasst werden, z. B. Feldmaße, Tore, Teams und Startpositionen.

## 4. QR-Codes und Link-Ziele (TPD)

Gefunden wurden **14 QR-Codes** in der TPD (S. 4: 1, S. 5: 2, S. 12: 1, S. 13: 8, S. 63: 1, S. 67: 1). Alle ließen sich dekodieren, und jeder ist zusätzlich mit einer anklickbaren Link-Annotation hinterlegt. **Das Regelheft enthält keine QR-Codes**; der Scan aller 164 Seiten blieb ohne Treffer.

| Seite | Kontext | QR-Inhalt | Endziel | Titel / Kanal |
|---|---|---|---|---|
| 4 | Infografik „Die beste Trainingseinheit“ | `qrcc.me/sc1gc2z83uob` | dfb-akademie.de/beste-trainingseinheit/-/id-11011533/ | DFB-Akademie (Webseite) |
| 5 | Infografik „Basistrainingsformen“ (großer QR) | `qrcc.me/say98654b0ln` | dfb-akademie.de/trainingsphilosophie-deutschland/-/id-11011532/ | DFB-Akademie (Webseite) |
| 5 | Infografik „Viele Fußballaktionen durch Spielen auf mehreren Feldern“ | `qrcc.me/sc1geaffyem3` | youtube.com/watch?v=f9chzjNaPhA in der Playlist PLe9XQeUG6KlJg6l8ejn1YgOJHktx-2p5Y | „Nachwuchstraining – Mehrere Felder“ (DFB). Kurzvideos von mehreren Feldern, z. B. „4 vs 4 Linie bespielen und 4 vs 4 + 1 nur direkte Tore zählen“, „4 + 2 vs 4 + 2 im Sechseck …“ |
| 12 | Mein.Fußball auf FUSSBALL.DE | `qrcc.me/skmextih4v7z` | fussball.de/newsdetail/das-ist-die-trainingsphilosophie-deutschland/-/article-id/253111 | FUSSBALL.DE-Artikel |
| 13 | Teil 1 | youtube.com/watch?v=YWGZXHKSO-I | – | „Vom Wohnzimmer auf den Trainingsplatz“ (DFB) |
| 13 | Teil 2 | youtube.com/watch?v=_kzw9ODTvP4 | – | „Vom Trainerzimmer auf den Trainingsplatz“ (DFB) |
| 13 | Teil 3 | youtube.com/watch?v=J3OewZoxBHU&t=510s | – | „Von der Umkleidekabine … (1) mit Sandro Wagner“ (DFB) |
| 13 | Teil 4 | youtube.com/watch?v=fGQy051_ma0 | – | „… (2) mit Lars Bender“ (DFB) |
| 13 | Teil 5 | youtube.com/watch?v=efI8YSdYS3o&t=5s | – | „… (3) mit Sven Bender“ (DFB) |
| 13 | Teil 6 | youtube.com/watch?v=-6ewyr9Bihc | – | „… (4) mit Hanno Balitsch“ (DFB) |
| 13 | Sky Matchplan Spezial Teil 1 | youtube.com/watch?v=KW3uWkcZBJI&t=2343s | – | „MATCHPLAN Spezial \| Trainingsphilosophie Deutschland – Teil 1“ (Kanal **MATCHPLAN Portal**, nicht DFB) |
| 13 | Sky Matchplan Spezial Teil 2 | youtube.com/watch?v=3NC9Ltw8tP4&t=1987s | – | „… Teil 2“ (MATCHPLAN Portal) |
| 63 | Spieltag der Zukunft | youtube.com/watch?v=ClyPbkLNcjk&t=809s | – | „Unsere Vision für Spielformate …“ (DFB) |
| 67 | Schule des Kleinfeldfußballs | youtube.com/watch?v=7WVdFsQw924 | – | „Die Schule des Kleinfeldfußballs …“ (DFB) |

Anmerkungen:

- Vier QR-Codes laufen über den Drittanbieter-Kurzlinkdienst **qrcc.me** (dynamische QR-Codes). Diese Weiterleitungen können ausfallen, die Link-Annotationen zeigen dagegen direkt auf das Ziel.
- Kleine Abweichungen zwischen QR und Annotation: Bei KW3uWkcZBJI hat nur der QR `&t=2343s`, bei YWGZXHKSO-I hat nur die Annotation `&t=0s`, und auf S. 5 verlinkt die Annotation `youtu.be/f9chzjNaPhA` ohne Playlist.
- Die Ziele sind **ergänzende DFB-Quellen**: DFB-Akademie-Seiten, FUSSBALL.DE und der YouTube-Kanal des DFB. Die beiden Matchplan-Folgen stammen von einem Fremdkanal. Die Videos sind Gespräche bzw. Demonstrationen, aber keine zusätzlichen Spielform-Steckbriefe. Die Playlist „Mehrere Felder“ zeigt Spielformen in Aktion.
- Die Tabelle auf S. 10 und S. 53 nennt im Spielblock „Videos“. Das ist nur kursiver Text, weder Link noch QR.
- Weitere Textlinks: fussball.de (S. 12), dfb.de (S. 70).

## 5. Regelheft 2025/2026

### Gliederung

Die Gliederung folgt dem Inhaltsverzeichnis auf PDF-S. 5. Das PDF hat keine Lesezeichen, aber interne Links im Inhaltsverzeichnis.

| Abschnitt | gedr. S. | PDF-S. |
|---|---|---|
| Umschlag, Schiri-Werbung | – | 1–3 |
| Anmerkungen zu den Spielregeln | 2 | 4 |
| Inhaltsverzeichnis | 3 | 5 |
| Regel 1 Spielfeld | 5 | 7 |
| Regel 2 Ball | 15 | 17 |
| Regel 3 Spieler | 17 | 19 |
| Regel 4 Ausrüstung der Spieler | 26 | 28 |
| Regel 5 Schiedsrichter (inkl. Schiedsrichterzeichen) | 32 | 34 |
| Regel 6 Weitere Spieloffizielle | 44 | 46 |
| Regel 7 Dauer des Spiels | 53 | 55 |
| Regel 8 Beginn und Fortsetzung des Spiels | 56 | 58 |
| Regel 9 Ball im und aus dem Spiel | 59 | 61 |
| Regel 10 Bestimmung des Spielausgangs | 60 | 62 |
| Regel 11 Abseits | 65 | 67 |
| Regel 12 Fouls und sonstiges Fehlverhalten | 70 | 72 |
| Regel 13 Freistöße | 87 | 89 |
| Regel 14 Strafstoß | 91 | 93 |
| Regel 15 Einwurf | 97 | 99 |
| Regel 16 Abstoß | 99 | 101 |
| Regel 17 Eckstoß | 101 | 103 |
| (Anzeige „Neuer Kinderfußball“) | 103 | 105 |
| VAR-Protokoll | 104 | 106 |
| Glossar | 113 | 115 |
| Spieloffizielle | 124 | 126 |
| Leitlinien für Zeitstrafen | 126 | 128 |
| Praktischer Leitfaden für Spieloffizielle | 129 | 131 |
| Notizen, Anzeige, Rückseite | 160–162 | 162–164 |

Inhaltsart: Fließtext in nummerierten Abschnitten. Nach den meisten Regeln folgen „Zusätzliche Erläuterungen des DFB“ (u. a. PDF-S. 16, 18, 56–57, 66, 88, 92, 100). Dazu kommen Vektorgrafiken (Spielfeldmaße, Schiedsrichterzeichen, Positionierungsdiagramme im Leitfaden). Die wichtigsten Regeländerungen sind gelb unterstrichen (PDF-S. 4), was bei der Textextraktion verloren geht.

### Relevanz für Kinder- und Jugendfußball

**Das Regelheft ist im Kern die IFAB-Regelausgabe für den 11-gegen-11-Spielbetrieb.** Es enthält **keine** Jugendbestimmungen im Sinne einer Jugendordnung oder Jugendspielordnung, **keine** Spielformate des Kinderfußballs (2v2/3v3/Funino, 5v5, 7v7, 9v9), **keine** Feld-, Tor- oder Ballgrößen für Junioren und nichts zum „Spieltag der Zukunft“. „Funino“ kommt null Mal vor; geprüft wurde auch mit einer Suche, die Leerzeichen-Artefakte toleriert. Ball und Spielfeld sind nur für den Standardfall definiert: Ballumfang 68–70 cm (PDF-S. 17 ff.), übliche Feldgröße 105 x 68–70 m (DFB-Erläuterung, PDF-S. 16 / gedr. S. 14).

Jugendrelevante Stellen:

| Stelle | PDF-S. / gedr. S. | Inhalt |
|---|---|---|
| Anmerkungen zu den Spielregeln | 4 / 2 | Für den **Jugendbereich** dürfen die Verbände Spielfeldgröße, Ball (Größe, Gewicht, Material), Torgröße, Dauer der Halbzeiten, Rückwechsel und Zeitstrafen anpassen |
| Regel 3, Rückwechsel | 20 / 18 | Rückwechsel nur im Junioren-, Senioren-, Behinderten- und Breitenfußball mit Erlaubnis des Verbands |
| Regel 7 + DFB-Erläuterungen Nr. 7–8 | 56–57 / 54–55 | Verlängerung: A-Junioren höchstens 2x15, B-Junioren 2x10, alle anderen Junioren 2x5. **Spieldauer-Tabelle:** A (U19/U18) 2x45 · B (U17/U16) 2x40 · C (U15/U14) 2x35 · D (U13/U12) 2x30 · E (U11/U10) 2x25 · F (U9/U8) 2x20 · G/Bambini (U7) max. 2x20 Minuten |
| Leitlinien für Zeitstrafen | 128–130 / 126–128 | Zeitstrafen u. a. im Juniorenfußball zulässig, wenn der Verband zustimmt. Dauer, Ablauf und Vergehenskatalog. Abweichende Modelle sind seit 01.07.2025 unzulässig |
| Anzeige „Neuer Kinderfußball“ | 105 / 103 | Nur Werbung mit Verweis auf dfb.de/mehr-fussball/kinderfussball, ohne Regelinhalt |
| Regeln 1–17 allgemein | 7–105 | Gelten für den Großfeld-Spielbetrieb (relevant etwa ab den C-Junioren, je nach Format auch für D) bzw. als Grundlage, z. B. Abseits (Regel 11), Fouls (Regel 12), Spielfortsetzungen (Regeln 13–17) |
| Praktischer Leitfaden, Einführung | 131 / 129 | Gesunder Menschenverstand in unteren Spielklassen; anpfeifen trotz kleiner Mängel (fehlende Eckfahne u. Ä.) |

**Lücke für die Wayfinder-Map:** Für Spielformate und Regeln des Kinder- und Jugendfußballs (Funino, 3v3/5v5/7v7/9v9, Feld- und Torgrößen, Spielzeiten jenseits der Tabelle in Regel 7, Durchführungsbestimmungen zum „neuen Kinderfußball“) wird eine **weitere Quelle** gebraucht. Weder TPD noch Regelheft enthalten diese Angaben vollständig. Welche Quelle das sein soll, bleibt offen. Die Anzeige auf PDF-S. 105 und der Verweis auf den „neuen Kinderfußball“ (TPD S. 9, 62) zeigen nur, dass es solches DFB-Material gibt. Ihr Inhalt wurde hier nicht geprüft.

## 6. Kurzfazit für die Skill-Planung

- Die TPD ist die Hauptquelle. Sie enthält **28 Spielform-Steckbriefe in 4 Kategorien**, **4 Einheiten-Vorlagen**, die Leitplanken für Altersstufen, Nettospielzeit und Trainingsstruktur sowie zwei konzeptionelle Kapitel (Spieltag, Schule).
- Die Steckbriefe haben ein einheitliches Schema (Titel, ORGANISATION, ABLAUF, VARIATIONEN, ggf. HINWEIS, Kommentare). Für ein Skill-Datenmodell müssen **Alter, Kategorie, Schwerpunkt und Coaching-Punkte ergänzt oder abgeleitet** werden: Alter aus S. 11, Schwerpunkt aus den Kategorie-Intros, Coaching-Punkte aus den Kommentaren.
- Der Text ist gut extrahierbar; Skizzen, Tabellen und die Lesereihenfolge brauchen Handarbeit.
- Das Regelheft liefert für den Jugendbereich nur wenig: die Spieldauer-Tabelle, Verlängerung, Rückwechsel und Zeitstrafen. Kinderfußball-Formate fehlen.
