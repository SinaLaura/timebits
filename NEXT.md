# Next steps

Write what you want next under **To do**, one line each, top = most important (or use `/later <task>`, `/later !<task>` for urgent).
Start working through the list with `/next`, or keep it running with `/loop 15m /next`.
Claude picks up the top open item whenever it is free, moves it to **In progress** (with its session name, so parallel sessions don't take the same one), and to **Done** with the commit and a localhost link to check it when finished (needs `cd docs && py -m http.server 8765`).

## To do

- [ ] [needs you, quick] Try on a real phone with your fingers (so far only simulated taps in headless Edge): playing quickly across the items of snake, rings, diamonds, spiral, clock and ducks, including taps in the gaps (open the preview server of the PC on the phone, same Wi-Fi: `http://PC-ADDRESS:8765/?m=40&look=snake`). Is the reach right (not too small, not too large)? Tapping clearly empty background should still change the look. Tell me what feels off.
- [ ] [needs you, big] (Last task, only when everything else is done.) The chocolate bar theme is hard to understand and feels strange. Come up with something better.
- [ ] [solo, big] (Last task, only when everything else is done.) Design another cool theme entirely on your own, a new idea of yours (not one from THEMES.md). I will review it tomorrow.

## In progress


## Done

- [x] (Last task, only when everything else is done.) Pick a theme idea from my ideas in THEMES.md and implement it entirely on your own, without asking me anything. You have a free hand in how, but follow the rules in CLAUDE.md. Built the balloons idea. (1249eda) → http://localhost:8765/?m=10&look=balloons (one pops each minute and its string dangles from the knot; tap a balloon to nudge it; also &m=60, &m=1, &passed=6)

- [x] Update the `/later` skill so that it no longer keeps the user's wording, but describes each new task in its own words in good English (the repo is public, and CLAUDE.md already says so); the skill file itself stays untouched until this task is picked up. (b41ce8f) → no visual change

- [x] Phone check of the Exit "Sure?" (Yes / No, gap above Exit) and of the small ducklings with the bigger mother at 60 and 150 minutes: both feel right on a real phone (no code change) → no visual change

- [x] [solo, big] In themes with sound whose items sit close together (little empty space between them), tapping several items in a row should work like playing an instrument: a tap that accidentally lands in a small gap must not count as a tap on the empty background (which switches the theme). This should also apply to themes that get sound later. (848e232) → http://localhost:8765/?m=40&look=snake (tap quickly across the dots, also in the gaps: each tap plays a note and the look stays; also &look=rings, diamonds, spiral, clock, ducks)

- [x] Move the pause button a little higher (more space above "Exit"), so nobody taps "Exit" by accident. (90ab8c2) → http://localhost:8765/?m=10&look=ducks (more space between the pause text and Exit)
- [x] Tapping "Exit" should first ask "Sure?" with the buttons "Yes" and "No", and only exit after "Yes". (90ab8c2) → http://localhost:8765/?m=10&look=ducks (tap Exit: Sure? Yes / No appear in the same place; the end page's Exit doesn't ask)

- [x] Das Ducks-Theme sah besser aus, als die Enten noch kleiner waren und es nicht mehr Reihen gab. Es soll wieder so werden. Damit es trotzdem gut aussieht, soll die Entenmutter größer sein als ihre Küken. (5f02651) → http://localhost:8765/?m=60&look=ducks (kleine Küken in einer Reihe auf der Runde, Mama deutlich größer; vergleiche &m=10, &m=25, &m=150)

- [x] the hedgehog's spikes should also not be clickable during pause (124665f) → http://localhost:8765/?m=10&look=hedgehog (pause, then tap a spike: nothing; resume: spikes react again)

- [x] Add a new file that collects possible (future) problems, or decisions made that may be ok now but problematic later. Example: the decision to follow the phone's silent mode and not play the sound for the boring themes; but a user might not want to be distracted by other notifications and still want to play around with the bits (the items of a theme). From then on, collect such things there by yourself whenever you notice one (add that as a rule to CLAUDE.md). (540adbc) → no visual change (new file RISKS.md with 8 entries, the rule is in CLAUDE.md under „Zusammenarbeit“)

- [x] The sound of the boring themes seems to not work on the first click, but only at the second? (9de9785) → http://localhost:8765/?m=10&look=honey (tap once: sound on the first tap; pause, tap: silent; also ducks, hedgehog)
- [x] The boring themes that have sound should not make a sound in pause mode. That is for every theme. (9de9785) → http://localhost:8765/?m=10&look=honey (tap once: sound on the first tap; pause, tap: silent; also ducks, hedgehog)
- [x] First-use finger tap demo: preview page only, not in the app yet (09bdd38) → http://localhost:8765/test-finger.html
- [x] Calming short sounds when clicking items of the boring themes (just them): soft, a bit futuristic, WebAudio so the silent switch is respected (faa695a) → http://localhost:8765/?m=10&look=snake (also spiral, clock, honey, rings, diamonds; tap an item)
- [x] For a lot of ducks it looks weak because they are too small. (06a740d) → http://localhost:8765/?m=60&look=ducks (many ducklings follow their mother on one winding path over the whole pond; try &m=25, &m=150, compare &m=10)
- [x] Remove the "Round and round." text. (870e44c) → http://localhost:8765/ (choose „Pomodoro“: the sentence ends after „break.“)
- [x] The Pomodoro menu looks good, but above it write a sentence about how the time setting will be then. Make a preview. (8b50b33) → http://localhost:8765/ (choose „Pomodoro“; the sentence changes as you tap − and +)

- [x] I don't like the display for Pomodoro. Rethink it (but it should stay consistent with the Minutes and Time menu). (2743c2b) → http://localhost:8765/ (choose „Pomodoro“: Focus, Break, Long break, each with − number + like Minutes)
- [x] When the browser or app is not visibly open, does the countdown still continue (as it should)? Will it still ring? (065447d) → http://localhost:8765/?m=1 (switch to another tab and wait: it ends and rings on time; on a phone a sleeping web page only catches up when opened, the store app notifies)
- [x] It should also send a notification when it's not in focus. (065447d) → http://localhost:8765/ (allow notifications on the first Start, then leave the tab)
- [x] When you click the done page 10 times, show the theme's picture after the last minute is gone, e.g. the hedgehog without any spikes, Saturn without any moons (and back to done after 3 clicks). (d6f6291) → http://localhost:8765/?m=1&look=hedgehog (wait a minute, then tap the done page 10 times)
- [x] Make the remaining time more consistent with the font and size of the pause button. It's a little too big. (8620c77) → http://localhost:8765/?m=10 (smaller, lighter, a bit of letter spacing like the buttons)
- [x] Don't display the end time when using Pomodoro. (8620c77) → http://localhost:8765/?pomo
- [x] Also don't show the end time when you use the mode "Time". (8620c77) → http://localhost:8765/ (choose „Time“ and start; with „Minutes“ the end time still shows)
- [x] The pause button and the exit button use one or two lines depending on whether it's paused or not, which looks bad on the phone because the image changes accordingly. Just keep them above each other. (233727b) → http://localhost:8765/?m=10 (tap the pause button and back: the picture keeps its size)
- [x] In some themes the items are cut off on top, for example when the time is very long. (92c159b) → http://localhost:8765/?m=120&look=caterpillar (antennae had no room; also stars and fuse; if you saw it in another theme, tell me which)
- [x] Enable changing the time of the pomodoro. (63cf4f8) → http://localhost:8765/ (choose „Pomodoro“, tap 25, 5 or 15 and type; kept for next time)
- [x] Disable zoom in. (b0326a4) → http://localhost:8765/?m=10 (on the phone: pinch and double-tap no longer zoom; desktop: ctrl+wheel / ctrl+plus do nothing)
- [x] The honey cells should not get a round outline when you click them, but a hexagonal one. (2e450eb) → http://localhost:8765/?m=10&look=honey (tap a cell)
- [x] The stars should also get a different outline shape when clicked (not round). (2e450eb) → http://localhost:8765/?m=10&look=stars (tap a star)
- [x] The hedgehog should get a spiky outline when clicked, and only at the edge of its spike. (2e450eb) → http://localhost:8765/?m=10&look=hedgehog (tap a spike)
- [x] Can you make the disappearing ducks take the longest way to leave, not the shortest. (717e42e) → http://localhost:8765/?m=3&look=ducks (wait a minute: the lost duckling heads to the far side)
- [x] The ducks' movements seem not so smooth anymore since you made the screen dynamically wide. (717e42e) → http://localhost:8765/?m=10&look=ducks (rounder loop, heading blends smoothly)
- [x] The snake's eyes should look in the direction as before, but change just for the click and the tongue movement: the right eye should visibly move more to the left, so it looks as if the snake changed its looking direction. (6e9cdf4) → http://localhost:8765/?m=10&look=snake (tap the head)
- [x] The car puff is great, but it should be directly where the car is, not so far away from it. (248c120) → http://localhost:8765/?m=10&look=cars (tap a car)
- [x] (Bigger task for when everything else is finished): make it pomodoro, repeating endlessly. Show a preview of the new look. (The mode without pomodoro should still be available). (9c39041) → http://localhost:8765/ (choose „Pomodoro“ on the start screen; or directly http://localhost:8765/?pomo, ?pomo=1 starts with a break)
- [x] What is the classical pomodoro technique? Choose that (for the pomodoro task above). (9c39041) → 25 min focus, 5 min break, every 4th break 15 min (the classic allows 15–30)
- [x] The snake's tongue looks strange, because her eyes don't move in the same direction. Fix it. (b0532fd) → http://localhost:8765/?m=10&look=snake (tap the head a few times; reload for another reaction)
- [x] In the browser the snake's tongue is also cut off, because still just the center is used (for every theme). So your latest change to use the full screen seems not to work. (b0532fd) → http://localhost:8765/?m=10&look=snake (in a wide window: the picture now spans the whole width, heading and buttons stay in the middle)
- [x] After I picked the app icon (no. 2): export it to icon-192, icon-512 and apple-touch-icon in docs/ and bump the cache name in sw.js. (26c6426) → no visual change in the app; icons are docs/icon-512.png etc., source lab/icon-final.svg

- [x] Generate more icon ideas, and then open it for me together with the old ones. (f75813e) → lab/icons.html (open the file directly; ideas 4–8 added, plus all eight at home-screen size)
- [x] For the car, clicking should not make a surrounding thing, but some puff from the exhaust (Auspuff). (433f8ca) → http://localhost:8765/?m=10&look=cars (tap a car)
- [x] From the removed boring themes re-introduce the 5 best of them. And tell me how many are thrown out now. (11b2b8b) → http://localhost:8765/?m=20&look=spiral (back: spiral, clock, honey, rings, diamonds; 4 thrown out: dots, squares, bars, tiles)

- [x] App icon: draw 3 logo suggestions based on the Ankabuti spider logo (../GoGirls-homepage/images/ankabuti-logo.jpg): (1) spider with a clock-face belly with two hands, no numbers, (2) spider hanging on its thread into a thin partly filled countdown ring, (3) round smiling spider body with tiny legs and a thin arc around it showing time left. Show the three on a localhost page (lab page) so I can pick. (4c9126d) → lab/icons.html (open the file directly)
- [x] When clicking items most themes make a circle around it, which is fine. But for shapes that are not round choose another suitable thing in shape and size that fits the shape and theme. (ffdf32a) → http://localhost:8765/?m=10&look=cars (tap a car; also ducks, flower, chocolate, abacus, hedgehog)
- [x] Same for the more advanced themes: a car or duck can leave using the whole screen, the dead spider legs or spikes of the hedgehog can spread more over the bottom of the whole screen, the star-net can go through the whole screen. (73b8ebe) → http://localhost:8765/?m=10&look=ducks (also cars, hedgehog with &passed=6, stars)
- [x] In general the items should be proportional and fill up the space. That is almost always not the case with the basic boring themes. Add that general instruction to CLAUDE.md and change it for the boring themes: use the full size of the browser (not necessarily filling it completely, but use it). (e578f70) → http://localhost:8765/?m=10&look=snake (offline themes were enlarged too, they're just not in rotation)
- [x] The caterpillar already gets a laughing mouth when clicked. A similar theme (maybe snake or so) should also react when clicked: smile, look sad, or pull in its feelers. The reaction is chosen randomly each time the theme appears, but stays the same for that whole run (every click in one iteration gives the same reaction). (bc6c6fb) → http://localhost:8765/?m=10&look=snake (tap the snake)
- [x] Saturn: include an animation for clicking Saturn. (8c36d09) → http://localhost:8765/?m=10&look=orbit (tap the planet or its ring)
- [x] Hourglass: make the bubbles bigger. It looks a little bit weird how they are stuck before free fall but just in the air, in the bottleneck, without actual physical limitation. (3777308) → http://localhost:8765/?m=10&look=hourglass
- [x] Hourglass: make the bigness of the circles proportional. The total size of them could/should fill up the whole half of the hourglass, to be proportionate to time, which it always (in general) should be. (3777308) → http://localhost:8765/?m=40&look=hourglass
- [x] Remove some of the boring themes (3852e51) → http://localhost:8765/?m=10 (tap the background a few times: only the 16 advanced themes + snake appear)
- [x] In the browser when I don't click in the centered void the theme doesn't change. Change that. (priority task) (20967f8) → http://localhost:8765/?m=10 (in a wide window, tap the empty space left or right of the column)
- [x] Fullscreen should start only after someone presses Start. (6c49cc7) → http://localhost:8765/ (first tap does nothing, Start goes fullscreen)
- [x] I like the new physics of the hourglass, but make the bubbles circles. (c745ece) → lab/hourglass-matter.html (open the file directly)
- [x] Make my app fullscreen by default (854294d) → http://localhost:8765/ (first tap or Start goes fullscreen)
- [x] The repo https://github.com/SinaLaura/countdown exists now. Bring it online (pushed; Pages workflow 42e67d5 – one click left for you: Settings → Pages → Source „GitHub Actions“) → https://sinalaura.github.io/countdown/
- [x] Hourglass: let's try to use threejs.org to make the physics for the hourglass better. But just as a test (separate test page, the app itself stays free of external libraries). Open it for me then (2D with Matter.js as chosen; c278d50) → lab/hourglass-matter.html (open the file directly, needs internet for Matter.js)
- [x] For the "solar system" make it collapse in the center during pause (ad7e6f9) → http://localhost:8765/?m=30&look=orbit
- [x] Solar system: same (collapse in the center during pause) for the solar system's stars arrangement (ad7e6f9) → http://localhost:8765/?m=30&look=stars
- [x] Jar: when a bubble jumps out of the jar on its own, it still looks different than when I tap it myself. Make it look more like tapping it myself (d8cb9a2) → http://localhost:8765/?m=10&look=jar
- [x] Die Raupe soll kurz einen lächelnden Mund bekommen, wenn man sie anklickt, dann geht es wieder weg (9146ad2) → http://localhost:8765/?m=10&look=caterpillar
- [x] The slider in the hourglass should be centered (dde30ae) → http://localhost:8765/?m=10&look=hourglass
- [x] Implement the next theme: Kugelbahn: Pro Minute rollt eine Kugel durch eine Zickzack-Bahn nach unten. (d54daf7) → http://localhost:8765/?m=10&look=marbles
- [x] Jar (meant: hourglass): the slider should be the same color as the jar's line (91804c9) → http://localhost:8765/?m=10&look=hourglass
- [x] Jar (meant: hourglass): the line should not be bigger in size (91804c9) → http://localhost:8765/?m=10&look=hourglass

