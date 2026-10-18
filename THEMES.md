# Themes

Regeln für alle Themes stehen in [CLAUDE.md](CLAUDE.md). Testen: `?m=10&look=<index>.0` oder `?look=<name>`.

## Gebaut

Offline genommen (`off: true` in `ALL_MODES`, im Code erhalten, nicht mehr in der Rotation): dots, squares, bars, tiles (4 von 9 ausgemustert). Zurück in der Rotation: spiral, clock, honey, rings, diamonds. Die Nummern in `?look=` zählen nur die aktiven Themes; zum Zurückholen `off: true` entfernen.

Varianten zum Vergleichen (`lab: true` in `ALL_MODES`): nur über `?look=<name>` erreichbar, nie in der Zufallsrotation, hinten einsortiert (die Nummern der anderen bleiben). Nach der Entscheidung des Users bleibt eine Version, die andere wird gelöscht (und `lab` ggf. entfernt). Zurzeit gibt es keine; die Blume hatte eine (flowerring), sie ist jetzt die Blume selbst.

| # | Name | Was pro Minute passiert |
|---|---|---|
| 0 | dots | Punkt schrumpft zu grauem Punkt |
| 1 | squares | Quadrat schrumpft |
| 2 | snake | Schlange zieht den Schwanz ein; Antippen = Kopf reagiert (lächeln, traurig mit Träne oder Zunge züngeln), pro Durchlauf zufällig gewählt und dann immer gleich; Augen schauen geradeaus und beim Antippen kurz in Kopfrichtung (fernes Auge wandert mehr), Zunge kommt vorne raus, Rand lässt Platz für die Zunge; Test (`pitchGrid: true`, auch bei honey und diamonds): die Tonhöhe hängt vom Ort des Items ab statt vom Zufall, wie ein Tastenfeld aus 6 × 4 Feldern (Pentatonik A3 bis C6, oben links am höchsten, unten rechts am tiefsten, jede Reihe zwei Stufen tiefer); die übrigen Themes mit Ton (spiral, clock, rings) spielen noch zufällige Töne, bis der User entscheidet |
| 3 | spiral | Spirale läuft von außen nach innen ab |
| 4 | clock | Punkt im Uhr-Kreis erlischt |
| 5 | bars | Balken schrumpft |
| 6 | honey | Wabe schrumpft; Ton hängt vom Ort der Wabe ab (Tastenfeld wie bei der Schlange, `pitchGrid`) |
| 7 | rings | Ring wird zum Punkt |
| 8 | diamonds | Raute schrumpft; Ton hängt vom Ort der Raute ab (Tastenfeld wie bei der Schlange, `pitchGrid`) |
| 9 | tiles | Dreieck schrumpft |
| 10 | flower | Ein einziger Blütenblattkranz wie eine Margerite (der ältere Entwurf mit mehreren Lagen ist ersetzt, so gewünscht). Die Blätter sind nicht alle gleich: Länge, Breite und Winkel variieren leicht, über den Kranz läuft eine langsame Welle (manche Seiten etwas länger), bei sehr vielen Blättern wird die Streuung kleiner, damit der Kranz nicht struppig wirkt. Bei vielen Minuten wächst der Kern etwas (Sonnenblume, höchstens 0,41 × Radius), damit die Blätter Blätter bleiben und keine Nadeln; die Blätter fallen in verstreuter Reihenfolge (Goldener Winkel), der Kranz lichtet sich gleichmäßig wie bei einer gepflückten Margerite; sie bleiben blass am Boden liegen |
| 11 | orbit | Planet antippen = er quetscht sich und wackelt, der Ring schwingt; Mond driftet ins All; Pause = das ganze System fällt in den Planeten zusammen, danach geht es wieder auf |
| 12 | jar | Glas ist am Anfang voll, der Füllstand zeigt die Restzeit; pro Minute pulsiert der oberste Ball genau wie beim Antippen und springt in der Kugel-Physik hoch, nur hoch genug, um über den Rand zu kommen, fliegt seitlich raus und verschwindet (es bleibt nichts liegen, so gewünscht); Antippen = Ball hüpft, kommt aber nie raus |
| 13 | caterpillar | Raupe wird kürzer, am Ende Schmetterling; Antippen = sie lächelt kurz |
| 14 | hourglass | Körner so groß, dass sie die ganze obere Hälfte füllen (proportional zur Zeit), der Hals ist so weit wie ein Korn; Sandkorn rutscht zum Hals, fällt durch und rollt auf den Haufen (oben entsteht eine Mulde, unten ein Hügel; Körner unregelmäßig); Pause = ein kurzer Schieber (gleiche Farbe und Strichstärke wie das Glas) schließt den Hals, kein Ausblenden |
| 15 | fuse | Lunte brennt ab, am Ende Knall |
| 16 | tower | Hochhaus statt der Schokoladentafel (die Tafel sah schon fast wie eines aus): pro Minute eine Wohnung mit Licht im Fenster und etwas darin (Vorhänge, Pflanze, Lampe, Katze, Jalousie), Stockwerk auf Stockwerk (hohe Stockwerke, schlank wie ein Wolkenkratzer; ab und zu ruckelt ein Stockwerk kurz seitlich, als wollte es jemand umstoßen), oben ggf. ein schmaleres Penthouse; pro Minute wackelt eine Wohnung im obersten Stock, springt aus der Fassade und stürzt trudelnd aus dem Bild, ihr leerer Betonrahmen bleibt; ist ein Stockwerk leer, fällt das Dach mit kleinem Federn darauf (Antenne mit Blinklicht); Antippen = das Licht geht kurz aus; Pause = die Lichter gehen nacheinander aus |
| 17 | abacus | Perle rutscht nach rechts |
| 18 | stars | Stern im Sternbild erlischt; Pause = das Sternbild zieht sich in der Mitte zusammen, danach breitet es sich wieder aus |
| 19 | hedgehog | Stachel fällt ab, er wird rot; Körper antippen = hüpfen/schütteln; Pause = schläft (Augen zu, atmet langsam, kleine „z“ steigen auf, Fläche bleibt hell; weder Körper noch Stacheln reagieren aufs Antippen, das gilt in der Pause für alle Themes) |
| 20 | cinema | Gast verlässt den Saal, die Zeit läuft auf der Leinwand |
| 21 | spider | Bein fällt ab; Kopf antippen = federt am Faden, kneift glücklich die Augen zu; Pause = zieht die Beine ein |
| 22 | cars | Spielzeugauto fährt aus dem Bild (Antippen = kurz Gas geben mit Auspuffwölkchen statt Ring, Pause = einparken) |
| 23 | ducks | Ein zufälliges Küken verliert den Anschluss, schaut sich kurz um und paddelt schräg über den nächsten Rand davon (weder kürzester noch längster Weg, kreuzt die Reihe nie, nach höchstens 5 s weg), die anderen schließen auf; auch viele kleine Küken schwimmen zügig (eine Runde in etwa 35 s); Mama antippen = sie dreht sich um und quakt, die Reihe bleibt stehen, die Küken drehen sich nicht mit um, sie wackeln nur auf der Stelle (so gewünscht); Pause = Reihe stoppt, Mama schaut zurück; viele Küken bleiben klein und schwimmen in einer langen Reihe auf einer Runde um den Teich (so gewünscht; der Schlängelweg über den ganzen Teich aus Commit 06a740d ist wieder raus), dafür ist Mama deutlich größer (3× ein Küken, höchstens 120 px, mindestens 44 px) |
| 24 | thermometer | Oberstes Segment kühlt ab und verblasst, die Säule zeigt die vergangene Zeit (kein Frost am Glas, so gewünscht); es schneit immer stärker; Temperatur („12°“) ersetzt die Überschrift; Kugel antippen = Säule flackert auf; Pause = Strickmütze; Ende = zerspringt in Eissplitter |
| 25 | marbles | Kugelbahn: Die Kugeln warten oben hinter einer Klappe auf den Rampen; pro Minute kippt die Klappe, eine Kugel rollt die Zickzack-Bahn hinunter (fällt von Rampe zu Rampe, dreht sich sichtbar) in die Schale unten und bleibt dort blass liegen, die Warteschlange rückt nach; Antippen = Kugel hüpft kurz |
| 26 | balloons | Luftballon-Strauß, alle Schnüre an einem Knoten mit Schleife; der Strauß füllt die obere Fläche (Größe proportional zur Zeit), die Ballons treiben im Wind; pro Minute bläht sich ein äußerer Ballon kurz auf und platzt (Comic-Blitz, Gummifetzen fliegen und fallen), seine Schnur fällt herab und baumelt blass mit dem Gummiknoten am Knoten (vergangene Minuten bleiben als Quaste sichtbar); Antippen = Ballon wird angeschubst und schwingt an der Schnur zurück; bei vielen Ballons werden die Schnüre durchsichtiger |
| 27 | penguins | Eigene Idee: Pinguine mit Gesicht stehen dicht an dicht auf einer Eisscholle (gezackter Rand, dicke Eiskante mit Facetten, heller Frostrand, Risse und Schneewehen oben, der hellere Teil unter Wasser schimmert durch, ein paar lose Eisstücke treiben im Wasser) (Größe proportional zur Zeit, hintere Reihen zeigen nur die Köpfe); pro Minute watschelt ein äußerer Pinguin zum Rand, hüpft und taucht kopfüber ein (Spritzer, Ring auf dem Wasser) und schwimmt danach blass als kleiner Kopf (ohne Schatten oder Ring) im Wasser vor der Scholle und weicht den losen Eisstücken immer aus, schwimmt also nie hindurch (vergangene Minuten bleiben so sichtbar); Antippen = er ruft wie ein Pinguin (zwei nasale Töne, „ha-haah“, jedes Mal etwas anders), hüpft und flattert mit den Flügeln, kein Ring (so gewünscht); spielbar wie ein Instrument; blinzelt ab und zu; Pause = alle schlafen (Augen zu) |
| 28 | realpenguins | Dieselben Pinguine in echten Farben (so gewünscht, Ausnahme von der Palettenregel): schwarz-weiß mit orangem Schnabel und orangen Füßen, rosa Bäckchen, weiße Eisscholle, blaues Meer als Hintergrund des ganzen Bildschirms (eigene Palette `pal`) |
| 29 | flowerlayers | Variante zum Vergleichen (`lab`, nicht in der Rotation; in `preview.html?look=flower,flowerlayers` neben dem Kranz): die frühere Blume mit Blütenblättern in Lagen kommt zurück. Sparsam mit Lagen (`L` in `flowerLayers`): eine Lage bis 30 Minuten, zwei bis 75, danach alle 15 Minuten eine mehr, höchstens 6 (ab 136). So gewünscht: 25 Minuten gut mit einer Lage, 60 mit zwei statt drei, 120 mit fünf gut; gleichmäßige Regeln (eine pro 9, 14, 25 oder 40 Minuten) passten nie überall. Jede Lage hat ihre eigene Blattform (`PETAL_SHAPES`, von außen gezählt: breites Oval, einfaches Oval, Tropfen mit breiter Spitze, schlankes Oval …; die Formen unterscheiden sich nur mäßig, die früheren Löffel- und Zulaufformen sahen merkwürdig aus) und einen etwas anderen Farbton: außen die Palettenfarbe, nach innen immer ein Stück zum Hintergrund (bis 26 %, Richtung Farbe des Kerns). Die Blätter sind rund ohne spitze Ecken, mit etwas Luft dazwischen, sodass die versetzte nächste Lage durchscheint (bei zwei Lagen, also 31 bis 75 Minuten, sind sie breiter und dürfen sich überlappen, weil es sonst zu lange schmale Blätter wären; `ov` in `flowerLayers`: bei drei bis vier Lagen weniger, ab fünf unverändert; zu breit (mehr als etwa das 1,5-Fache des Abstands) verschmelzen sie zu einer Scheibe), jedes ein wenig anders (Länge, Breite, Rundung, leichte Drehung), flache Farbe ohne Rand (Rand und Verlauf wurden ausprobiert: wirkte matschig, die Lagen sind sonst nicht mehr zu erkennen). Sie fallen Lage für Lage von außen nach innen, innerhalb einer Lage in verstreuter Reihenfolge (Goldener Winkel), sodass sie sich gleichmäßig lichtet; auf dem Boden werden sie wieder einheitlich blass |

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
- [x] ★ **Luftballons:** gebaut als `balloons` (#26).
- [ ] **Pixel-Herz:** Pro Minute fällt ein Pixel heraus.

### Abstrakt
- [ ] **Wellen:** Konzentrische Ringe schwingen nach außen. Antippen erzeugt eine kleine Welle.
- [ ] **Equalizer:** Balken hüpfen im Takt, pro Minute verstummt einer.

★ = Favoriten, weil sie beim Antippen am lebendigsten reagieren.

## Neue Ideen
- [ ] **Gurke schneiden:** Pro Minute wird eine Scheibe von der Gurke abgeschnitten und fällt zur Seite, bis nur noch das Endstück übrig ist.
- [ ] **Turm wie die Türme von Hanoi:** Gestapelte Scheiben bilden einen Turm. Pro Minute wird eine Scheibe herausgenommen, bei Minute 0 bricht der ganze Turm zusammen. Antippen lässt den Turm von der angetippten Stelle aus wackeln.
