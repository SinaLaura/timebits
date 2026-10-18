# Themes

Regeln für alle Themes stehen in [CLAUDE.md](CLAUDE.md). Testen: `?m=10&look=<index>.0` oder `?look=<name>`.

## Gebaut

Offline genommen (`off: true` in `ALL_MODES`, im Code erhalten, nicht mehr in der Rotation): dots, squares, bars, tiles (4 von 9 ausgemustert). Zurück in der Rotation: spiral, clock, honey, rings, diamonds. Die Nummern in `?look=` zählen nur die aktiven Themes; zum Zurückholen `off: true` entfernen.

| # | Name | Was pro Minute passiert |
|---|---|---|
| 0 | dots | Punkt schrumpft zu grauem Punkt |
| 1 | squares | Quadrat schrumpft |
| 2 | snake | Schlange zieht den Schwanz ein; Antippen = Kopf reagiert (lächeln, traurig mit Träne oder Zunge züngeln), pro Durchlauf zufällig gewählt und dann immer gleich; Augen schauen geradeaus und beim Antippen kurz in Kopfrichtung (fernes Auge wandert mehr), Zunge kommt vorne raus, Rand lässt Platz für die Zunge |
| 3 | spiral | Spirale läuft von außen nach innen ab |
| 4 | clock | Punkt im Uhr-Kreis erlischt |
| 5 | bars | Balken schrumpft |
| 6 | honey | Wabe schrumpft |
| 7 | rings | Ring wird zum Punkt |
| 8 | diamonds | Raute schrumpft |
| 9 | tiles | Dreieck schrumpft |
| 10 | flower | Blütenblatt fällt ab |
| 11 | orbit | Planet antippen = er quetscht sich und wackelt, der Ring schwingt; Mond driftet ins All; Pause = das ganze System fällt in den Planeten zusammen, danach geht es wieder auf |
| 12 | jar | Glas ist am Anfang voll, der Füllstand zeigt die Restzeit; pro Minute pulsiert der oberste Ball genau wie beim Antippen und springt in der Kugel-Physik hoch, nur hoch genug, um über den Rand zu kommen, fliegt seitlich raus und verschwindet (es bleibt nichts liegen, so gewünscht); Antippen = Ball hüpft, kommt aber nie raus |
| 13 | caterpillar | Raupe wird kürzer, am Ende Schmetterling; Antippen = sie lächelt kurz |
| 14 | hourglass | Körner so groß, dass sie die ganze obere Hälfte füllen (proportional zur Zeit), der Hals ist so weit wie ein Korn; Sandkorn rutscht zum Hals, fällt durch und rollt auf den Haufen (oben entsteht eine Mulde, unten ein Hügel; Körner unregelmäßig); Pause = ein kurzer Schieber (gleiche Farbe und Strichstärke wie das Glas) schließt den Hals, kein Ausblenden |
| 15 | fuse | Lunte brennt ab, am Ende Knall |
| 16 | chocolate | Stück bricht ab |
| 17 | abacus | Perle rutscht nach rechts |
| 18 | stars | Stern im Sternbild erlischt; Pause = das Sternbild zieht sich in der Mitte zusammen, danach breitet es sich wieder aus |
| 19 | hedgehog | Stachel fällt ab, er wird rot; Körper antippen = hüpfen/schütteln; Pause = schläft (Augen zu, atmet langsam, kleine „z“ steigen auf, Fläche bleibt hell; weder Körper noch Stacheln reagieren aufs Antippen, `sleeps: true`) |
| 20 | cinema | Gast verlässt den Saal, die Zeit läuft auf der Leinwand |
| 21 | spider | Bein fällt ab; Kopf antippen = federt am Faden, kneift glücklich die Augen zu; Pause = zieht die Beine ein |
| 22 | cars | Spielzeugauto fährt aus dem Bild (Antippen = kurz Gas geben mit Auspuffwölkchen statt Ring, Pause = einparken) |
| 23 | ducks | Ein zufälliges Küken verliert langsam den Anschluss und paddelt auf Umwegen davon, auf dem längsten Weg zur gegenüberliegenden Seite, die anderen schließen auf; Mama antippen = sie dreht sich um und quakt; Pause = Reihe stoppt, Mama schaut zurück; bei vielen Küken wird die Runde zu einem Schlängelweg über den ganzen Teich (eine Reihe hinter Mama), damit die Küken groß bleiben |
| 24 | thermometer | Oberstes Segment kühlt ab und verblasst, die Säule zeigt die vergangene Zeit (kein Frost am Glas, so gewünscht); es schneit immer stärker; Temperatur („12°“) ersetzt die Überschrift; Kugel antippen = Säule flackert auf; Pause = Strickmütze; Ende = zerspringt in Eissplitter |
| 25 | marbles | Kugelbahn: Die Kugeln warten oben hinter einer Klappe auf den Rampen; pro Minute kippt die Klappe, eine Kugel rollt die Zickzack-Bahn hinunter (fällt von Rampe zu Rampe, dreht sich sichtbar) in die Schale unten und bleibt dort blass liegen, die Warteschlange rückt nach; Antippen = Kugel hüpft kurz |

## Offene Ideen

### Mit Gesicht
- [ ] **Oktopus:** Tentakel bewegen sich wellenförmig, pro Minute zieht er einen ein. Antippen lässt einen Tentakel sich ringeln.
- [ ] ★ **Kuchen mit Kerzen:** Jede Kerze flackert, pro Minute geht eine aus und ein Rauchwölkchen steigt auf. Antippen lässt die Flamme aufflackern.
- [ ] ★ **Fisch im Aquarium:** Luftblasen steigen auf, pro Minute platzt eine an der Oberfläche. Der Fisch schwimmt zur angetippten Stelle.

### Natur
- [ ] **Baum im Herbst:** Blätter segeln einzeln herab, unten entsteht ein Laubhaufen.
- [ ] **Regenwolke:** Pro Minute fällt ein Tropfen, unten wächst eine Pfütze. Antippen lässt einen Tropfen wackeln.
- [ ] **Mond-Phasen:** Kleine Monde nehmen ab bis zum Neumond.

### Physik und Spielzeug
- [ ] **Dominosteine:** Pro Minute kippt einer um.
- [ ] ★ **Luftballons:** Sie schweben an Schnüren und wackeln im Wind, pro Minute platzt einer. Antippen schubst einen Ballon an.
- [ ] **Pixel-Herz:** Pro Minute fällt ein Pixel heraus.

### Abstrakt
- [ ] **Wellen:** Konzentrische Ringe schwingen nach außen. Antippen erzeugt eine kleine Welle.
- [ ] **Equalizer:** Balken hüpfen im Takt, pro Minute verstummt einer.

★ = Favoriten, weil sie beim Antippen am lebendigsten reagieren.

## Neue Ideen
- [ ] **Gurke schneiden:** Pro Minute wird eine Scheibe von der Gurke abgeschnitten und fällt zur Seite, bis nur noch das Endstück übrig ist.
