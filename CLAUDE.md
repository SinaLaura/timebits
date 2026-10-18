# Timebits (Ordner „timebits“, früher „countdown“) – Regeln

Generelle Regeln für diese App. Gelten immer, wenn der User nichts Genaueres sagt.
Neue generelle Wünsche des Users hier ergänzen. Theme-Ideen und -Stand stehen in [THEMES.md](THEMES.md), mögliche künftige Probleme in [RISKS.md](RISKS.md).

## Projekt
- Die App ist eine PWA in `docs/`: reines HTML/JS in `docs/index.html`, kein Build. Vorschau: `cd docs && py -m http.server 8765` (Port 8000 belegt auf diesem Rechner die Go-Girls-Seite).
- Später soll sie mit Capacitor in den App Store (siehe [README.md](README.md)). Deshalb keine externen Abhängigkeiten oder CDNs, alles bleibt lokal.
- Ein Theme ist ein Eintrag in `MODES` in `docs/index.html`, mit Layout (`lay`) und optionalen Hooks (`pos`, `item`, `before`, `after`, `step`, `tap`, `bodyTap`, `endArt`, `noHead` …).
- Testen: `?m=10&look=<index oder name>.<palette>`, z.B. `?m=10&look=ducks`. Mit `&passed=5` sind schon 5 Minuten vorbei (nur in der lokalen Vorschau, online und in der App wirkungslos). `?pomo` startet einen Pomodoro, `?pomo=1` gleich mit der ersten Pause.
- **Dem User etwas zeigen: immer über die klickbare Vorschauseite** [docs/preview.html](docs/preview.html) (Hilfsseite nur für die lokale Vorschau, kein Teil der App), nie nur über einen blanken Look-Link: `http://localhost:8765/preview.html?look=<theme>&m=25`. Mehrere Looks nebeneinander (Vergleiche, Varianten): `look=a,b`. `&gone=1` (oder 2) = ein (zwei) Drittel schon vorbei, `&p=` Palette, `&raw=pomo=1` für Dinge ohne Look (z.B. Pomodoro). Die Seite hat Knöpfe für Minuten, „Already gone“, Palette, „Restart“ und „A minute is over“ (lässt eine Minute sofort vergehen, damit man sieht, wie das Item abgeht), dazu pro Bild eine Look-Auswahl und „+ Compare another look“. Alles bleibt in der Adresse. Die Bilder laden mit `&_=<Zeit>`, damit der Browser nie eine alte Kopie der App zeigt (der lokale Server schickt keine Cache-Regeln); unten steht die App-Version vom Server (Nummer in `docs/sw.js`). Der User öffnet sie im Simple Browser rechts neben dem Editor (Strg+Umschalt+P, „Simple Browser: Show“); Claude kann ihn nicht selbst öffnen. Gilt auch für die Check-Links unter „Done“ in `NEXT.md`. Neue Hilfen der Seite (Knöpfe) kommen in `docs/preview.html`, die zugehörigen Nachrichten in den `DEV`-Block in `docs/index.html`.

## Pomodoro
- Klassisch: 25 min Fokus, 5 min Pause, jede 4. Pause 15 min, endlos bis „Exit“. Die drei Zeiten stellt man auf dem Startbildschirm wie bei „Minutes“ ein (Zeile mit − Zahl + je Länge, bleiben gespeichert). Der normale Countdown bleibt („Minutes“, „Time“). Die drei Modi stehen als „Minutes / Time / Pomodoro“ nebeneinander (die Schrägstriche sind nicht antippbar).
- Am Phasenende geht das letzte Item mit Endton ab, dann startet die nächste Phase sofort in einem neuen zufälligen Look (kein End-Bildschirm). Der Untertitel zeigt „focus 2/4“, „break“ oder „long break“.
- In einer Pause heißt der Pause-Button „Skip break“ und startet sofort die nächste Fokus-Runde. Pausen sehen aus wie Fokus-Runden (neuer Look, nicht blass).
- Die Phase übersteht Neuladen; was bei geschlossener App abgelaufen ist, wird übersprungen (nach 12 h verworfen).

## Texte
- Die App ist englisch, sehr knapp und minimalistisch.
- Keine Beispiele oder Vorschläge in Eingabefeldern („What for?“ steht ohne Vorschlag).
- Die Anzeige lautet „N left“, ohne „min“.
- Auf dem Startbildschirm stellt man auch „Time“ wie „Minutes“ mit − Zahl + ein (5-Minuten-Schritte, gedrückt halten läuft). Die Zeit selbst ist reiner Text, nicht markier- oder kopierbar; ein Tipp darauf öffnet die Zeitauswahl des Handys (unsichtbares Zeitfeld darüber); ein kleines Uhr-Symbol neben der Zeit zeigt, dass es eine Uhrzeit ist. Darunter steht klein bei „Minutes“ das Ende („until 14:52“), bei „Time“ die Dauer („for 47 min“).
- Die Zahlen auf dem Startbildschirm (Minutes, Pomodoro) werden beim Antippen nie markiert und nicht geleert: der Cursor steht am Ende, man ändert sie durch Tippen (nur Ziffern, höchstens 3); bleibt das Feld leer, kommt die alte Zahl zurück.
- Buttons: „Start“, „Exit“ (im Countdown und am Ende). Der Pause-Button zeigt jeden Tag einen anderen „ich bin kurz weg“-Text aus `AWAY` und in der Pause „I'm back“.
- Pause-Button, „Exit“, „No“ und „Yes“ haben dieselbe Schriftgröße (auf schmalen Handys etwas kleiner, damit der Pause-Text einzeilig bleibt).
- Der Pause-Button steht immer einzeilig über „Exit“, damit sich die Höhe des Bildes beim Pausieren nicht ändert. Zwischen beiden bleibt deutlich Abstand, damit man nicht versehentlich „Exit“ trifft.
- „Exit“ im Countdown fragt erst „Sure?“ mit „No“ links und „Yes“ rechts (sie liegen genau an der Stelle von Pause und Exit, die Höhe des Bildes bleibt gleich; in der Mitte ist eine tote Lücke, damit ein Doppeltipp nie „Yes“ trifft; die Frage verschwindet nach 6 s, bei Esc und bei jedem neuen Start). „Exit“ auf dem End-Bildschirm fragt nicht.

## Aussehen und Tippen
- Es gibt keine Design-Einstellungen. Das Aussehen ändert sich nur durch Tippen.
- Pro Minute gibt es ein Item.
- Die Menge, die man sieht, ist proportional zur Zeit: Die Items füllen zusammen ihren Bereich (z.B. die ganze obere Hälfte der Sanduhr), und ihre Größe richtet sich danach.
- Die Items nutzen den Platz des Browsers (nicht unbedingt ganz, aber deutlich): Kleine Zeiten ergeben große Items, nicht kleine Punkte in einer leeren Fläche. Das gilt auch für Bewegungen (ein Auto oder eine Ente fährt über den ganzen Bildschirm, Stacheln und Beine verteilen sich über die ganze Breite).
- **Tipp auf ein aktives Item:** kurze Reaktion (Puls, manchmal eine leicht andere Farbe nahe der Palettenfarbe, ggf. themespezifisch). Sonst passiert nichts.
- Der Puls-Ring beim Antippen bleibt proportional zum Item: Er liegt eng um das, was man sieht, und ist nie viel größer. Bei runden Items ein Kreis (ggf. `p.ring`), bei nicht runden Formen (Blütenblatt, Auto, Ente, Stachel, Schokolade, Perle) folgt er der Form mit dem Theme-Hook `halo` (Ellipse oder Rechteck, gedreht wie das Item). Reagiert ein Item beim Antippen schon selbst deutlich (es springt, wird weggeschubst, sein Licht geht aus, es hüpft: Auto, Pinguin, Glas, Kugelbahn, Ballon, Hochhaus), fällt der Ring weg (`noRing`); Vorher/Nachher in der Vorschau mit `look=<theme>~ring,<theme>`.
- **Themes mit Ton spielt man wie ein Instrument** (`snd` oder `playable: true`, auch bei künftigen Themes mit Ton setzen): Ein Tipp in die kleine Lücke zwischen eng sitzenden Items zählt fürs nächste Item (Puls, Ton) und wechselt nicht den Look. Reichweite im `hitTest`: ¾ des Item-Abstands, höchstens ein halbes Item über den Treffer-Radius hinaus; weiter weg ist es wieder leerer Hintergrund.
- **Tipp auf ein vergangenes Item:** wechselt wie leerer Hintergrund den Look (auch in der Pause). Das gilt auch für Reste vergangener Minuten, die ein Theme getrennt zeichnet (Krümel, baumelnde Schnüre, schwimmende Pinguine, leere Kinosessel, der leere Teil des Thermometers): das Theme meldet sie beim Zeichnen mit `leftover(X, x, y, r)` an, auch künftige Themes.
- **Tipp auf ein neutrales Element** (Deko, Körper, Rahmen, Linien, Überschrift): nichts, außer das Theme hat bewusst eine eigene Reaktion (z.B. der Igel hüpft, `bodyTap`).
- **Nur ein Tipp auf leeren Hintergrund oder ein vergangenes Item** wechselt zufällig Theme und Palette.
- Vergangene Items bleiben sichtbar (blass, klein, am Boden …), wenn es zum Theme passt.
- Themes mit Gesicht sind niedlich, im Stil von Raupe, Spinne und Igel.
- Ein Theme darf die Überschrift ersetzen (`noHead`) und die Zeit selbst zeigen, wie das Kino auf der Leinwand.
- Farben kommen immer aus der aktuellen Palette (`P.fg`, `P.bg`, `P.dim`, `P.text`), nie fest im Theme. Ausnahme auf Wunsch des Users: `thermometer` nutzt echte Temperaturfarben (rot → eisblau), nur Hintergrund und Glas folgen der Palette. Ebenso `realpenguins`: echte Farben (schwarz-weiße Pinguine, orange Schnäbel, weißes Eis, blaues Meer); ein Theme bringt dafür mit `pal` eine eigene Palette mit, die dann auch Hintergrund und Texte färbt (`curPal()`).
- Paletten (`PALETTES`): Sie folgen der Einstellung des Handys (`prefers-color-scheme`): Ein dunkles Handy zeigt nur die dunklen Paletten, ein helles zeigt alle (hell und dunkel gemischt). Jede Gruppe hat deutlich verschiedene Hintergründe, nicht nur Schwarz oder Weiß: Dunkle haben sichtbare Farbe (höchstens zwei fast schwarz), helle sind getönt (höchstens eine fast weiß). Kein Hell- oder Dunkelmodus wird erzwungen (kein `only light`): Ein dunkles Handy sieht nie eine helle Palette. Neue Paletten gehören in eine der beiden Gruppen (`dark: true` bei den dunklen) und werden mit mehreren Themes angeschaut (z.B. `preview.html` mit `&p=` oder `?look=<theme>.<palette>`).

## Pause (Standard, wenn nichts anderes gewünscht)
- Der Countdown friert ein, und das Ende verschiebt sich um die Pausendauer.
- Die Pause übersteht Neuladen und Schließen der App.
- Die Fläche wird blass (ca. 30 %), und der Untertitel zeigt „paused“. Themes mit `noHead` zeigen „paused“ selbst.
- Bewegungen kommen sanft zur Ruhe (`calm` geht gegen 0) und laufen danach weiter. Neue bewegte Themes nehmen deshalb `X.t` als Zeit, nicht `X.now`.
- Ein Theme darf eine eigene, ruhige Pausen-Reaktion haben (z.B. der Igel schläft, die Autos parken).
- Zeigt ein Theme die Pause selbst deutlich genug, bleibt die Fläche mit `noDim` hell (z.B. die Sanduhr mit ihrem Schieber).
- In der Pause reagiert kein Theme auf Tippen: Items und Körper (`bodyTap`) bleiben still (kein Puls, keine Farbe, kein Ton, keine Theme-Reaktion). Das gilt zentral im Tipp-Handler für alle Themes, auch neue; nur ein Tipp auf leeren Hintergrund wechselt weiter den Look. Ausnahmen nur auf Wunsch des Users.

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
- [RISKS.md](RISKS.md) sammelt mögliche künftige Probleme und Entscheidungen, die jetzt okay sind, später aber stören könnten (z.B. Töne folgen dem Stumm-Schalter). Wer so etwas bemerkt, auch bei der eigenen Arbeit und ohne dass der User fragt, trägt es dort selbst ein (englisch, im Format der vorhandenen Einträge: Entscheidung, warum jetzt okay, wann es stören könnte, Ausweg) und committet die Datei mit der Änderung, die den Anlass gab. Erledigte Einträge wandern nach „Resolved“.
- [NEXT.md](NEXT.md) ist die Aufgabenliste des Users. Wer frei ist, nimmt die oberste offene Aufgabe, trägt sie mit Sitzungsnamen unter „In progress“ ein (gleich committen, damit keine zweite Sitzung sie nimmt) und verschiebt sie nach „To review“ (wenn der User es sich ansehen sollte: neues Theme, Aussehen, Gefühl, eigene Entscheidungen, nicht ganz Testbares) oder bei Trivialem gleich nach „Done“, jeweils mit dem Commit und einem localhost-Link zum Nachschauen (z.B. `http://localhost:8765/?m=10&look=jar`). Skills dafür: `/later <Aufgabe>` trägt ein, `/next` arbeitet die Liste ab (Ablauf steht in `.claude/skills/`). Modi für `/next` (frei kombinierbar): `solo` (Standard: alles ohne den User) oder `co` (nur, was den User braucht, mit Rückfragen), `all` (Standard) oder `one` (nur eine Aufgabe), `quick` (Schnelles zuerst) oder `big` (Aufwendiges zuerst), sonst Listenreihenfolge. Offene Zeilen in NEXT.md tragen dafür Tags wie `[solo, quick]` oder `[needs you, big]`; `/next` setzt sie, vom User geänderte Tags gelten.
- Wünsche des Users beim Eintragen (`NEXT.md`, `/later`, Commits, Doku, Issues) nicht zitieren: Das Repo ist öffentlich, also in eigenen Worten und gutem Englisch beschreiben (in deutschen Dateien in gutem Deutsch; `NEXT.md` ist englisch). Die Bedeutung bleibt, Tippfehler, Grammatik und holprige Formulierungen werden geglättet, rohe Chat-Nachrichten werden nie eingefügt.
