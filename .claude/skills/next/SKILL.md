---
name: next
description: Work through the Timebits task list in NEXT.md, top item first, until nothing open is left. Use when the user types /next, says "continue with the list", or a /loop fires it.
argument-hint: (optional) "one" to do only a single item
---

Work through `NEXT.md` (repo root). Follow [CLAUDE.md](../../../CLAUDE.md) for everything you build.

Repeat for each item:

1. **Pick.** Read `NEXT.md` fresh. Take the top `- [ ]` line under **To do** that no session has claimed. If there is none, check **In progress** for an item with your own session name (left over from an interrupted run) and finish that. If nothing is left, say "NEXT.md is empty" in one line and stop.
   **Combine.** Then read the whole **To do** list and add any other open items that make sense to do in the same pass: same theme or same piece of code, or one item builds on or contradicts another (e.g. two fixes to the Jar). Only combine items that are small next to the top one and clearly related. Don't pull in big unrelated work just because it's on the list, and never take items another session has claimed. If two items contradict each other, ask the user instead of choosing one.
2. **Claim.** Move the picked line(s) to **In progress**, each as its own line `- [ ] <task> (<your session name>, started <HH:MM>)`. Change no other line. Use exact line edits, never rewrite the whole file, because the user may be adding lines at the same moment. Commit only `NEXT.md` right away, so parallel sessions don't take them.
3. **Do it.** Follow CLAUDE.md: read `docs/index.html` fresh right before each edit; test in the browser (headless Edge works: `--headless --dump-dom`, or export the canvas with `toDataURL` for a look); bump the cache in `docs/sw.js` after code changes; update `THEMES.md` for theme work. If the task is unclear or needs a decision only the user can make, don't guess: move it back to the top of **To do** with a short question in parentheses, commit, and go on to the next item.
4. **Commit** your work with explicit paths (no `git add -A`).
5. **Done.** Read `NEXT.md` fresh again, move each claimed line to **Done** as `- [x] <task> (<commit hash>) → <check link>` (combined items share the hash), commit only `NEXT.md`.
   The check link is a local preview URL that shows the change straight away, so the user can look later: `http://localhost:8765/?m=10&look=<theme name>`, plus `&passed=N` if the change only shows after some minutes, or a path like `http://localhost:8765/test-xyz.html` for a separate page. Without a visible change (e.g. docs, skills) write `→ no visual change` instead.
6. Write the user a short note for these items: what changed, the same check link, what was tested and what was not. Remind them that the link needs the preview server running (`cd docs && py -m http.server 8765`).

Then go back to step 1, unless the argument was "one". New lines the user adds while you work are picked up at the next step 1.
