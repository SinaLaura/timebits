# Risks and decisions to revisit

Possible future problems, and decisions that are fine today but may hurt later. Nothing here is broken right now; it is a list to look at when a user complains, when the app goes to the stores, or before a bigger change.

New entries are added whenever someone notices one (rule in [CLAUDE.md](CLAUDE.md)). Each entry says what was decided, why that is fine for now, when it could bite, and a way out. When an entry is dealt with, move it to **Resolved** with a short note.

## Open

### Tap sounds follow the phone's silent mode
- **Decision:** The calm tap sounds of the simple themes (snake, spiral, clock, honey, rings, diamonds), the hedgehog squeak and the end tone use WebAudio. WebAudio respects the silent switch on iPhone, so a muted phone stays quiet.
- **Why it is fine now:** Nobody is startled by sounds in a meeting or a library.
- **When it could bite:** Someone puts the phone on silent or Do Not Disturb only to avoid *other* notifications and still wants to play with the bits of a theme (or hear the end tone). They tap and hear nothing, and may think the app is broken.
- **Way out:** A small sound on/off switch that overrides the silent mode (an HTML audio element, or the Capacitor native audio, can play despite the silent switch), or a short hint when sound is muted.

### Zooming is disabled
- **Decision:** Pinch, double-tap and ctrl+wheel/plus are blocked (`user-scalable=no`, touch-action, key and wheel handlers).
- **Why it is fine now:** Accidental zoom while tapping items would break the picture; the layout already fills the screen.
- **When it could bite:** People with low vision cannot enlarge the small texts (buttons, the "N left" line, the pause text). Browser zoom is a basic accessibility feature, and App Store or accessibility reviews may point at it.
- **Way out:** Allow zoom on the start screen only, or offer a larger-text option, or make the small texts bigger by default.

### A web page cannot ring while the phone sleeps
- **Decision:** In the browser a single timer fires at the end, and a notification is sent if the page is not in front. On a phone, a sleeping browser page usually does not run, so the countdown only catches up when the page is opened again. Only the store app (LocalNotifications) really notifies on time.
- **Why it is fine now:** The app is still a web app, and keeping the screen on (wake lock) covers the common case of a timer lying on the desk.
- **When it could bite:** Users on the web version trust it for cooking or study timers, lock the phone, and are not notified. Reviews like "didn't ring".
- **Way out:** Say it plainly in the README / on the page, push the store app, or (later) Web Push from a server, which would break the "no external services" rule.

### Notification permission is asked on the first Start
- **Decision:** The browser asks for notification permission the first time someone presses Start.
- **When it could bite:** A permission prompt before the user has seen anything work is easy to refuse, and a refusal is hard to undo (browser settings). On iPhone, web notifications only work for the installed home-screen app at all.
- **Way out:** Ask later, e.g. only when the first countdown is left in the background, or explain with one line before the system prompt.

### Up to 999 minutes means up to 999 items
- **Decision:** One item per minute, shown in proportion; the minute fields accept 1 to 999.
- **When it could bite:** The physics and path themes (jar, hourglass, marbles, ducks, orbit) get slow with several hundred items on a weak phone, and the items become very small even though they use the whole screen. Battery drain grows too, since everything animates continuously.
- **Seen in ducks:** since the ducklings swim in one long line on a loop again (a wish, so they stay small and calm), several hundred minutes make them tiny (about 10 px at 150 min, about 1 px at 999 min in a small window); only the bigger mother stays visible. The earlier winding-path version (commit 06a740d) kept them bigger.
- **Way out:** Lower the maximum, group minutes into bigger items above a limit (e.g. one item per 5 min), or skip the physics for long times. Test the heavy themes with `?m=999` on a real older phone.

### Playing like an instrument leaves less room to change the look
- **Decision:** In themes with sound, a tap in the small gap between tightly packed items counts for the nearest item (reach: 3/4 of the item spacing, at most half an item beyond the item's own hit radius), so quick runs of taps never switch the theme by accident.
- **When it could bite:** In a dense layout (a long countdown in snake, rings or diamonds) almost every spot inside the field now belongs to an item, so a user who wants a different look has to tap outside the field, and may think changing the look is broken. The same happens on very small screens.
- **Way out:** A smaller reach for very dense layouts, a short hint the first time, or a dedicated way to change the look (long press, a corner tap).

### No way to keep a favourite look
- **Decision:** There are no design settings; the look changes only by tapping the empty background, and every Start and every Pomodoro phase picks a random look.
- **When it could bite:** Someone loves one look (the hourglass, say) and cannot keep it, or wants a calm look for a work session and gets something playful.
- **Way out:** A long-press on the background to lock the current look, or a "last look stays" switch. This goes against the "no settings" idea in CLAUDE.md, so it would be a deliberate change.

### One big file, several sessions editing it
- **Decision:** The whole app is one `docs/index.html` of about 2800 lines with no build step; several Claude sessions work in it at the same time.
- **When it could bite:** Merge conflicts and lost edits (a session overwriting the file from an old copy), long load of the file into every session, and hard-to-find side effects between themes sharing helpers (such as the tap chime or the pause handling).
- **Way out:** Keep the rule "read fresh, edit with exact replacements, commit at once". If it keeps hurting, split the themes into separate script files (still no build, still local) and list them in `sw.js`.

### Pomodoro state is dropped after 12 hours
- **Decision:** A running Pomodoro survives closing the app and skips the phases that ended meanwhile, but is thrown away if more than 12 hours have passed. All settings and the running state live in `localStorage`.
- **When it could bite:** Browsers can clear `localStorage` (private windows, storage cleanup, "clear site data", iOS cleaning rarely used sites), so the saved Pomodoro lengths and an unfinished run may vanish. The code ignores storage errors silently, so nobody would notice why.
- **Way out:** Mention it only if people report it; in the store app the storage is safer. Capacitor Preferences would be the sturdier place.

## Resolved

Nothing yet.
