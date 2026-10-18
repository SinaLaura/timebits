---
name: next
description: Work through the Timebits task list in NEXT.md, with modes (solo or co, one or all, quick or big first). Use when the user types /next [modes], says "continue with the list", or a /loop fires it.
argument-hint: (optional, any order) solo | co · one | all · quick | big   — default: solo all, in list order
---

Work through `NEXT.md` (repo root). Follow [CLAUDE.md](../../../CLAUDE.md) for everything you build.

## Modes

Read the argument `$ARGUMENTS` for these words (any order, case doesn't matter, German synonyms are fine, a leading `/` or `-` is ignored, so `/next /co /quick` means the same as `/next co quick`). Pick one word per group, or none for the default. If a group has two conflicting words, ask which one.

- **Who is needed**
  - `solo` (default): do everything you can **without the user**. Skip items that need them (see below); never wait for an answer.
  - `co` (as in co-working): the opposite. Work **only on the items that need the user** (the user is at the computer now): ask your questions, then build with the answers.
- **How many**
  - `all` (default): keep going until nothing eligible is left.
  - `one`: exactly one task, then stop. Don't combine items in this mode.
- **Order**
  - none (default): list order, top first.
  - `quick`: quick items first, i.e. small and in one place (a text, a size, a position, a flag, a one-line rule). Among equals, list order.
  - `big`: time-consuming items first, i.e. a new theme, a redesign, several parts, a new file or page. Among equals, list order.

An item whose line starts with "(Last task" (after its tags, see below) is always taken last, only when no other eligible item is left, whatever the order.

**Needs the user** means: the wording is unclear; it is a matter of taste or a choice between options ("come up with something better", "which one do you like"); it needs something only they can do or see (a store or account setting, their phone, a decision about money or publishing); or the line already carries a question in parentheses that is still unanswered. Everything else is `solo`. Judge from the line and the code; when in doubt between solo and needs-user, treat it as solo and ask later in step 3 if you really get stuck.

**Tags.** Every open line in `NEXT.md` carries its classification as a prefix, so the user (and the next run) can see it: `- [ ] [solo, quick] <task>`. One word per group, in this order: `solo` or `needs you`, then `quick` or `big` (same meaning as the modes above). Rules:
- Tag every untagged **To do** line at the start of a run, before picking, with exact line edits (no commit of its own; the tags go into the claim commit in step 2). Also tag lines the user adds while you work, at the next step 1.
- A tag the user wrote or changed is never overwritten. If only one group is there, add the missing one. The user's tag wins over your own judgement.
- Re-tag when you learn more: an item you move back with a question becomes `needs you`; once the user has answered it, it becomes `solo` again.
- Tags stay on the line in **In progress** and are dropped when the line moves to **Done**.
- Lines from other sessions in **In progress** are not touched.

Start with one line telling the user which modes you understood, e.g. "Modes: solo · all · quick first." Then repeat for each item:

1. **Pick.** Read `NEXT.md` fresh and tag any untagged **To do** lines (see Tags). From the **To do** lines that no session has claimed, keep the ones that fit the mode (`solo`: tagged `solo`; `co`: tagged `needs you`), sort them by the order mode and take the first. If there is none, check **In progress** for an item with your own session name (left over from an interrupted run) and finish that. If still nothing, say in one line why you stop ("NEXT.md is empty", or "nothing left that works solo, N items need you: run /next co") and stop.
   **Combine** (not in `one` mode). Add other open items that make sense to do in the same pass: same theme or same piece of code, or one item builds on or contradicts another (e.g. two fixes to the Jar). Only combine items that fit the mode, are small next to the picked one and are clearly related. Don't pull in big unrelated work just because it's on the list, and never take items another session has claimed. If two items contradict each other, ask the user instead of choosing one (in `solo` mode: leave both and say so in the final note).
2. **Claim.** Move the picked line(s) to **In progress**, each as its own line `- [ ] [<tags>] <task> (<your session name>, started <HH:MM>)`. Change no other line. Use exact line edits, never rewrite the whole file, because the user may be adding lines at the same moment. Commit only `NEXT.md` right away, so parallel sessions don't take them.
3. **Do it.** Follow CLAUDE.md: read `docs/index.html` fresh right before each edit; test in the browser (headless Edge works: `--headless --dump-dom`, or export the canvas with `toDataURL` for a look); bump the cache in `docs/sw.js` after code changes; update `THEMES.md` for theme work.
   - `solo`: if you find out the task needs the user after all, don't guess: move it back to the top of **To do** with a short question in parentheses, re-tag it `needs you`, commit, and go on to the next item.
   - `co`: first ask the user (AskUserQuestion; up to four questions per call, options with a recommendation, previews for visual choices; for something only they can do, tell them exactly what to do). If several picked items need answers, ask them all in one go before building anything. Then build with the answers. If they skip an item, move it back to **To do** unchanged and go on.
4. **Commit** your work with explicit paths (no `git add -A`).
5. **Done.** Read `NEXT.md` fresh again, move each claimed line to **Done** as `- [x] <task> (<commit hash>) → <check link>`, without its tags (combined items share the hash), commit only `NEXT.md`.
   The check link is a link to the clickable preview page, so the user can look later: `http://localhost:8765/preview.html?look=<theme name>&m=10`, plus `&gone=1` if the change only shows after some minutes, `look=a,b` to show two looks side by side (for variants and before/after), `&raw=pomo=1` for things that are not a look (see "Dem User etwas zeigen" in CLAUDE.md). The page has a "A minute is over" button, so changes that happen when a minute passes can be watched. Only for something that is no look at all, use a path like `http://localhost:8765/test-xyz.html`. Without a visible change (e.g. docs, skills) write `→ no visual change` instead.
6. Write the user a short note for these items: what changed, the same check link, what was tested and what was not. Remind them that the link needs the preview server running (`cd docs && py -m http.server 8765`) and open it in VS Code's Simple Browser beside the editor (Ctrl+Shift+P, "Simple Browser: Show").

Then go back to step 1, unless the mode is `one`. New lines the user adds while you work are picked up at the next step 1.

When a `solo all` run ends and items that need the user are left, name them in the last note (one line each) so the user knows what `/next co` will ask.
