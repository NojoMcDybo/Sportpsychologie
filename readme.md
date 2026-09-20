# Sportpsychologie MAP 3 — Klausur-Trainer

Einseitige Lernwebsite für die MAP 3 Sportpsychologie (Uni Münster, SoSe 2026).
Alles steckt in einer Datei: **`index.html`** — öffnen, fertig. Kein Server, kein Build
zum Lernen, offline lauffähig. Die 7 MB sind überwiegend Hintergrundbilder und
Sprites als Data-URI.

> **Private Fassung.** Die Seite gibt Inhalte urheberrechtlich geschützter Foliensätze
> wieder und ist ausschließlich für den eigenen Gebrauch gedacht. Nicht ins offene Netz
> stellen, nicht weitergeben. Eine teilbare Version müsste alle Aussagen paraphrasieren
> und die Folienverweise durch Literaturverweise ersetzen.

---

## Stand

| | |
|---|---|
| Module | 16 Lernmodule + Start, Glossar, Trainer |
| Belegte Aussagen | 819 |
| Prüfungsfragen | 777 |
| Glossarbegriffe | 325 |
| Klausurformat | 96 Fragen, 120 Minuten, 48 zum Bestehen |

Jede Aussage, jede Frage und jeder Glossareintrag trägt einen Beleg auf die Folie,
aus der sie stammt. Wo das Material etwas nur benennt, ohne es zu erklären, steht das
ausdrücklich da, statt die Lücke plausibel zu füllen.

---

## Ordner

```
index.html            das Lernprogramm — das ist die Datei, die man öffnet
daten/                die Quelldaten, aus denen index.html gebaut wird
  module.json           die Modulseiten (fertiges HTML je Modul)
  quiz.json             777 Prüfungsfragen
  glossar.json          325 Begriffe
  cards.json            Karteikarten
  funken.json           die Fakten, die im Hintergrund aufleuchten
  bilder.json           Hintergrundbilder und Leuchtkarten (AVIF, Data-URI)
  akzent.json           Farbton je Modul
  meta.json             Titel, Klausurformat, Companion-Sprüche
  sprites.json          die Spritesheets des Companions
  fakten/               neuer Stoff in strukturierter Form
    m15.json              Modul Schlaf & Erholung
    m16.json              Modul Forschungsmethoden
    nachtrag-a/-b/-c.json Ergänzungen zu m01–m11
quellen/              Folientexte mit Foliennummern (Grundlage der Belegprüfung)
werkzeug/
  baue.js               baut index.html aus daten/
  pruefe_belege.py      prüft jede Zahl gegen die belegte Folie
  pruefe_bau.py         Browser-Regression über alle Module
  FORMAT.md             Datenformat für neue Modulinhalte
  kopf.html, rumpf.js   Rahmen und Renderer (unverändert aus der Erstfassung)
```

---

## Neu bauen

```bash
node werkzeug/baue.js          # schreibt index.html
python3 werkzeug/pruefe_belege.py   # jede Zahl gegen die belegte Folie
python3 werkzeug/pruefe_bau.py      # Browser-Regression (braucht Playwright)
```

Stoff ergänzen heißt: eine Datei unter `daten/fakten/` anlegen oder erweitern
(Format in `werkzeug/FORMAT.md`), dann neu bauen. `index.html` nie von Hand
bearbeiten — der nächste Build überschreibt es.

---

## Was am 20.09. dazugekommen ist

Eine Vollständigkeitsprüfung hat 537 Vorlesungsfolien und 10 Seminardateien Folie
für Folie gegen die 1358 Belege der damaligen Fassung gehalten. Ergebnis und Nachtrag:

**Zwei ganze Blöcke haben gefehlt.**

- **Modul 15 · Schlaf & Erholung.** Die Seminarsitzung «Sport und Schlaf» war beim
  ersten Bau komplett durchgerutscht — null Belege in der ganzen Seite. 35 Aussagen,
  14 Begriffe, 8 Studien, 34 Fragen.
- **Modul 16 · Forschungsmethoden.** Die Folien 65–81 der VL Emotion & Stress sind ein
  geschlossener Methodenlehrgang (Datenarten nach Cattell, Testdefinition nach Lienert,
  Itemformate, Likert, Antwortverzerrungen), und das offizielle Seminar-Glossar ist ein
  reines Methodenglossar. Beides fehlte fast vollständig, obwohl Folie 8 der Einführung
  „Forschungsmethoden" ausdrücklich als Prüfungsstoff nennt. 40 Aussagen, 22 Begriffe,
  36 Fragen.

**Das Klausurformat war falsch.** Die Seite rechnete mit 60 Fragen. Auf den Folien 7
und 8 steht mehrfach: *Multiple Choice Fragen (48 von 96), 120 Minuten*. Das sind
1,25 Minuten pro Frage statt 2. Korrigiert — aber vor der Klausur im Learnweb
gegenprüfen, die Folie ist die einzige Quelle dafür.

**Rund 130 Einzelaussagen** sind als *Nachtrag*-Abschnitte in m01–m11 gewandert,
sichtbar abgesetzt am Ende der jeweiligen Seite. Darunter: McDougall, Murray und
Maslow als motivationshistorischer Vorspann; die pädagogischen Perspektiven A–F;
das AMS; Black Box, Thorndike und Skinner; die Übungsfragen-Folie der VL Lernen; das
Schichtenmodell und die psychodynamischen Instanzen; die Team Identification Scale;
Jamieson und Pollard zum Heimvorteil; die fünf Asch-Modifikationen; das Unterrichtsklima
und die deutschsprachigen Kohäsionsfragebögen.

**Ein Befund zum Nachschlagen:** Die Seite sagt, der Moderator „Typ des erforderlichen
Teamworks" sei in der Carron-Meta-Analyse 2002 nicht signifikant. Das stimmt für die
Gesamttabelle (F(1,154) = 0.29), nicht aber für die GEQ-Teilauswertung, wo Sport Type
signifikant ist (F(1,87) = 5.76, p < .02). Beide Befunde stehen jetzt getrennt drin.

---

## Was weiterhin fehlt

Ehrlich, damit niemand sich in falscher Sicherheit wiegt:

- **Modul 13 (Expertise II)** ließ sich nicht prüfen. Die Seite zitiert 98-mal
  „VL Expertise II" bis Folie 51, aber die Datei liegt nicht mehr im Kursordner.
- **Modul 14 (Expertise & Talent)** ist mit 13 Fragen das dünnste Modul. Die Quelldatei
  „Seminar Expertise & Talent" fehlt ebenfalls.
- Ebenfalls zitiert, aber nicht mehr im Ordner: Seminar Kohäsion, Seminar Choking,
  Seminar Sozialer Einfluss (Konformität).
- **Begriffe, die das Material nur nennt, ohne sie zu erklären**, stehen bewusst nicht
  drin: Deliberate Practice und Deliberate Play, Self-Handicapping, IZOF, EASI-Modell,
  Theorie des geplanten Verhaltens, Elaboration Likelihood Model, kognitive Dissonanz,
  Shaping, Verstärkerpläne. Die gehören ins Lehrbuch nachgeschlagen — eine erfundene
  Definition, die man zwei Wochen einübt, ist schlimmer als eine Lücke, die man kennt.
- Der **Fragenbestand aus der Erstfassung** hat bei 27 % der Fragen die richtige Antwort
  als längste Option (der Nachtrag liegt bei 9 %). Wer viel damit übt, gewöhnt sich
  eine Heuristik an, die in der echten Klausur nicht trägt.

---

## Wie die Seite funktioniert

**Lernmechanik.** Leitner-Boxen mit fünf Fächern und verteiltem Üben; vor jeder Antwort
eine Konfidenzeinschätzung, weil sicher geglaubte Fehler am längsten haften
(Hypercorrection-Effekt, Metcalfe 2017). Fehlerjournal, Klausursimulation gegen die Uhr,
Export nach Anki und CSV, Druckansicht.

**Navigation.** Von Modul zu Modul wischen — mit Finger und Stift überall, mit der Maus
nur neben der Lesespalte, damit Markieren möglich bleibt. `←` und `→` blättern ebenfalls.
Der Hintergrund liegt als Filmband hinter der Seite: beim Wechsel fährt er um eine
Bildschirmbreite weiter, die Bilder stoßen bündig aneinander.

**Der Companion.** Ein Nilpferd, das Klicks folgt, sich werfen lässt, beim Seitenwechsel
hereinrollt und modulbezogene Sprüche hat. Auf der Trainer-Seite trägt es einen Anzug.
Ein- und ausschalten mit `A`.

Alle Details zu Aufbau, Messungen und den getroffenen Entscheidungen stehen in
`LIESMICH-technik.md`.
