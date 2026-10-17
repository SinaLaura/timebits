# Timebits (Ordner „countdown“) – Regeln

Generelle Regeln für diese App. Gelten immer, wenn der User nichts Genaueres sagt.
Neue generelle Wünsche des Users hier ergänzen. Theme-Ideen und -Stand stehen in [THEMES.md](THEMES.md).

## Projekt
- Die App ist eine PWA in `docs/`: reines HTML/JS in `docs/index.html`, kein Build. Vorschau: `cd docs && py -m http.server 8765` (Port 8000 belegt auf diesem Rechner die Go-Girls-Seite).
- Später soll sie mit Capacitor in den App Store (siehe [README.md](README.md)). Deshalb keine externen Abhängigkeiten oder CDNs, alles bleibt lokal.
- Ein Theme ist ein Eintrag in `MODES` in `docs/index.html`, mit Layout (`lay`) und optionalen Hooks (`pos`, `item`, `before`, `after`, `step`, `tap`, `bodyTap`, `endArt`, `noHead` …).
- Testen: `?m=10&look=<index oder name>.<palette>`, z.B. `?m=10&look=ducks`. Mit `&passed=5` sind schon 5 Minuten vorbei (nur in der lokalen Vorschau, online und in der App wirkungslos). `?pomo` startet einen Pomodoro, `?pomo=1` gleich mit der ersten Pause.

## Pomodoro
- Klassisch: 25 min Fokus, 5 min Pause, jede 4. Pause 15 min, endlos bis „Exit“. Die drei Zeiten stellt man auf dem Startbildschirm wie bei „Minutes“ ein (Zeile mit − Zahl + je Länge, bleiben gespeichert). Der normale Countdown bleibt („Minutes“, „Time“). Die drei Modi stehen als „Minutes / Time / Pomodoro“ nebeneinander (die Schrägstriche sind nicht antippbar).
- Am Phasenende geht das letzte Item mit Endton ab, dann startet die nächste Phase sofort in einem neuen zufälligen Look (kein End-Bildschirm). Der Untertitel zeigt „focus 2/4“, „break“ oder „long break“.
- In einer Pause heißt der Pause-Button „Skip break“ und startet sofort die nächste Fokus-Runde. Pausen sehen aus wie Fokus-Runden (neuer Look, nicht blass).
- Die Phase übersteht Neuladen; was bei geschlossener App abgelaufen ist, wird übersprungen (nach 12 h verworfen).

## Texte
- Die App ist englisch, sehr knapp und minimalistisch.
- Keine Beispiele oder Vorschläge in Eingabefeldern („What for?“ steht ohne Vorschlag).
- Die Anzeige lautet „N left“, ohne „min“.
- Buttons: „Start“, „Exit“ (im Countdown und am Ende). Der Pause-Button zeigt jeden Tag einen anderen „ich bin kurz weg“-Text aus `AWAY` und in der Pause „I'm back“.
- Der Pause-Button steht immer einzeilig über „Exit“, damit sich die Höhe des Bildes beim Pausieren nicht ändert.

## Aussehen und Tippen
- Es gibt keine Design-Einstellungen. Das Aussehen ändert sich nur durch Tippen.
- Pro Minute gibt es ein Item.
- Die Menge, die man sieht, ist proportional zur Zeit: Die Items füllen zusammen ihren Bereich (z.B. die ganze obere Hälfte der Sanduhr), und ihre Größe richtet sich danach.
- Die Items nutzen den Platz des Browsers (nicht unbedingt ganz, aber deutlich): Kleine Zeiten ergeben große Items, nicht kleine Punkte in einer leeren Fläche. Das gilt auch für Bewegungen (ein Auto oder eine Ente fährt über den ganzen Bildschirm, Stacheln und Beine verteilen sich über die ganze Breite).
- **Tipp auf ein aktives Item:** kurze Reaktion (Puls, manchmal eine leicht andere Farbe nahe der Palettenfarbe, ggf. themespezifisch). Sonst passiert nichts.
- Der Puls-Ring beim Antippen bleibt proportional zum Item: Er liegt eng um das, was man sieht, und ist nie viel größer. Bei runden Items ein Kreis (ggf. `p.ring`), bei nicht runden Formen (Blütenblatt, Auto, Ente, Stachel, Schokolade, Perle) folgt er der Form mit dem Theme-Hook `halo` (Ellipse oder Rechteck, gedreht wie das Item).
- **Tipp auf ein vergangenes Item:** nichts.
- **Tipp auf ein neutrales Element** (Deko, Körper, Rahmen, Linien, Überschrift): nichts, außer das Theme hat bewusst eine eigene Reaktion (z.B. der Igel hüpft, `bodyTap`).
- **Nur ein Tipp auf leeren Hintergrund** wechselt zufällig Theme und Palette.
- Vergangene Items bleiben sichtbar (blass, klein, am Boden …), wenn es zum Theme passt.
- Themes mit Gesicht sind niedlich, im Stil von Raupe, Spinne und Igel.
- Ein Theme darf die Überschrift ersetzen (`noHead`) und die Zeit selbst zeigen, wie das Kino auf der Leinwand.
- Farben kommen immer aus der aktuellen Palette (`P.fg`, `P.bg`, `P.dim`, `P.text`), nie fest im Theme. Ausnahme auf Wunsch des Users: `thermometer` nutzt echte Temperaturfarben (rot → eisblau), nur Hintergrund und Glas folgen der Palette.

## Pause (Standard, wenn nichts anderes gewünscht)
- Der Countdown friert ein, und das Ende verschiebt sich um die Pausendauer.
- Die Pause übersteht Neuladen und Schließen der App.
- Die Fläche wird blass (ca. 30 %), und der Untertitel zeigt „paused“. Themes mit `noHead` zeigen „paused“ selbst.
- Bewegungen kommen sanft zur Ruhe (`calm` geht gegen 0) und laufen danach weiter. Neue bewegte Themes nehmen deshalb `X.t` als Zeit, nicht `X.now`.
- Ein Theme darf eine eigene, ruhige Pausen-Reaktion haben (z.B. der Igel schläft, die Autos parken).
- Zeigt ein Theme die Pause selbst deutlich genug, bleibt die Fläche mit `noDim` hell (z.B. die Sanduhr mit ihrem Schieber).

## Ende
- Groß steht das Label in Großbuchstaben mit „!“ (ohne Label „DONE!“), dazu der Button „Exit“.
- Der Endton ist zufällig futuristisch, kein Piepen.
- Das letzte Item geht wie alle anderen mit seiner Animation ab, während der Endton spielt. Erst danach (je nach `goneMs`, max. 3 s) kommt der End-Bildschirm.
- Ein Theme darf eine End-Animation haben (`endArt`, z.B. Schmetterling nach der Raupe, Knall nach der Lunte).
- Geheimnis: 10× auf die Done-Seite tippen zeigt das letzte Bild des Looks (alle Minuten weg, z.B. Igel ohne Stacheln); 3 Tipps führen zurück.
- Im Hintergrund: ein eigener Timer genau aufs Ende, damit ein Browser-Tab im Hintergrund pünktlich endet und klingelt. Ist die Seite nicht im Vordergrund, kommt eine Benachrichtigung (Erlaubnis wird beim ersten Start gefragt; in der App über LocalNotifications). Auf dem Handy schläft eine Webseite im Hintergrund meist, dann hilft nur die App.

## Barrierefreiheit
- Bei `prefers-reduced-motion` gibt es keine Dauer-Animationen (`still`).

## Privatsphäre
- Nichts Privates veröffentlichen (Commits, Code, Kommentare, Dateien im Repo, GitHub). Im Zweifel vorher fragen.

## Zusammenarbeit (mehrere Claude-Sitzungen arbeiten parallel)
- `docs/index.html` direkt vor dem Bearbeiten frisch lesen und nie aus einem alten Stand komplett neu schreiben.
- Nach jeder fertigen Änderung sofort committen, und zwar nur die eigenen Dateien mit expliziten Pfaden, kein `git add -A`. Ausnahme: Neue Aufgaben in `NEXT.md` (`/later`) werden nicht einzeln committet, sie gehen mit dem nächsten Commit von `NEXT.md` mit.
- Bei Code-Änderungen den Cache-Namen in `docs/sw.js` hochzählen.
- Wird ein Theme gebaut oder eine Idee verworfen, `THEMES.md` aktualisieren.
- [NEXT.md](NEXT.md) ist die Aufgabenliste des Users. Wer frei ist, nimmt die oberste offene Aufgabe, trägt sie mit Sitzungsnamen unter „In progress“ ein (gleich committen, damit keine zweite Sitzung sie nimmt) und verschiebt sie nach „Done“ mit dem Commit und einem localhost-Link zum Nachschauen (z.B. `http://localhost:8765/?m=10&look=jar`). Skills dafür: `/later <Aufgabe>` trägt ein, `/next` arbeitet die Liste ab (Ablauf steht in `.claude/skills/`).
- Wünsche des Users beim Eintragen (z.B. in `NEXT.md`) wörtlich und in der Sprache des Users übernehmen, nur offensichtliche Tippfehler korrigieren.
