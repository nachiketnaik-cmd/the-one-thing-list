# The One Thing List

A deliberately minimal to-do website built around a single rule: **you only ever see one task at a time.**

Live site: https://nachiketnaik-cmd.github.io/the-one-thing-list/

## What I'm trying to solve

My problem isn't a lack of to-do apps — it's concentration. Throughout the day my mind keeps throwing things at me: *oh, I need to do that*, *I haven't touched my hobby*, *that other task is still pending*. Worse, while I'm actually doing one task, the reminder of another task pulls my attention away and I lose focus on what's in front of me.

A normal to-do list makes this worse, not better. Seeing the whole list is itself the distraction — every item on screen is a little tug away from the one thing I'm supposed to be doing.

This site is my fix. It shows me **one task and nothing else**. There's nothing on screen to get distracted by, so I can actually finish the thing in front of me before moving on.

## How it works

The app has two modes: a day-to-day **focus** view and a **planning** view.

**Focus (the main screen).**
- It shows a single task — the top of my list — big, with a **Done** button. The rest of the list is hidden.
- Under it there's a **"park a thought"** box. When a stray idea or reminder pops up mid-task, I jot it into this box and it drops into an **inbox**, out of sight. I don't have to open the list or break focus — the thought is safely out of my head and I keep working.
- When I hit **Done**, I get a calm "You're done — tap when ready for the next one" screen. Doing nothing is a valid stop; or I tap **Next task** to pull the next one into focus.

**Planning (can be opened any time).**
- I open it from the focus screen with the **Planning mode** button. It can be opened whenever I want — nothing locks it to a particular time of day.
- It's the only place the whole list is revealed. Before opening it shows a quick confirm ("this reveals your whole list") as a small speed bump, but that's the only friction; it doesn't stop me opening it mid-task. Using it as a set nightly ritual is a habit I keep, not something the app enforces.
- Here I set up the line: add tasks, reorder them, promote one to #1, and triage the thoughts I parked in the inbox during the day — each inbox item either gets added to the line or discarded.

Everything — chores, errands, hobbies — lives in the same single line. There are no dates or times; the order is purely what I decide. The discipline is in consciously choosing what earns the #1 spot.

## Recurring tasks

Some tasks repeat (water the plants, daily review, exercise). I don't want those deleted forever every time I complete them.

- In planning mode, I mark a task recurring with the **↻** button. It lights up and shows a ↻ marker, and the focus screen notes "↻ recurring" so I know completing it won't delete it.
- When I hit **Done** on a recurring task, instead of vanishing it drops into a **Recurring** holding section in planning.
- From there I **send it back to the line** (→ line) whenever I need it again. I can also edit it, or delete it permanently if I'm done with it for good.

So recurring tasks cycle instead of disappearing. One-off tasks still get deleted on Done, as normal.

## How to edit things

- **Edit a task's text:** in planning mode, click the pencil (✎) on any task or inbox thought. The text becomes an editable field — **Enter** saves, **Esc** cancels (or use the ✓ / ✕ buttons). No deleting and retyping.
- **Reorder the line:** use ↑ / ↓ to move a task, or **⇧#1** to jump it straight to the top.
- **Make a task recurring:** the ↻ toggle in planning.
- **Remove a task:** ✕ deletes it. (For recurring tasks, ✕ in the Recurring section removes it permanently.)

## The Pre-Req Page

A second page (`prereq.html`), linked from the **Planning** view, for mapping what a task depends on. It has two levels:

- **Per-task diagram.** Click a task in the left list and it appears as the "final task" box at the bottom of the sandbox. Add prerequisite boxes above it (e.g. "Install Power BI", "Learn the basics") and draw downward arrows from each prereq into the task it feeds. One box can point into several; prereqs can have their own prereqs, so it builds up in layers.
- **Task-to-task view.** Click the **"Your tasks"** header to see every task as a box and draw dependencies *between whole tasks* (task 2 depends on task 1). Those cross-task links then show up on the individual task's page as a gold "coming from…" box with an arrow from the top.

Drag boxes to arrange them, click an arrow or a box's ✕ to delete it. Each task's diagram and the task-to-task links are saved in the browser (same local storage as the main app).

On the **main focus screen**, the current task now lists its prerequisites in small bold text just above it — pulled from both levels (the prereq boxes that feed into it at any depth, and any upstream tasks linked in the "Your tasks" view) — so you see what should come first before you start.

## My data

- Everything is stored in the browser's local storage on the device I'm using (my laptop). It is **not** synced across devices, and clearing site data resets the list. That's a deliberate trade-off for keeping the app dead simple with no backend.

## How I iterate on it

This is a personal product I improve over time as I actually use it. The loop is:

1. **Use it for real** and notice friction — something annoying, missing, or that breaks my focus rather than protecting it.
2. **Write down the change** as a plain request (e.g. "I can't edit a task, I have to delete and retype it" → add inline editing; "my recurring tasks keep getting deleted" → add the Recurring holding area).
3. **Make the change, test it, and push** to this repo. Because it's hosted on GitHub Pages from the `main` branch, every push updates the live site within about a minute.
4. **Keep this README current** so the thinking behind each feature — and the problem it's solving — doesn't get lost.

Changes so far have followed exactly this pattern: stripped out an escape-hatch button that undercut the "one thing" discipline, switched the font to Times New Roman, added inline editing, and added recurring tasks. The guiding test for any new feature is simple: *does it help me concentrate on one thing, or does it add something else to look at?* If it's the latter, it doesn't go in.

## Technical notes

- A single self-contained `index.html` — plain HTML, CSS, and vanilla JavaScript. No build step, no dependencies, no backend.
- State is kept in `localStorage` under the key `oneThingList.v1`.
- Hosted on GitHub Pages from the `main` branch.

### Running it locally

Open `index.html` directly in a browser, or serve the folder:

```
python3 -m http.server
```

then visit the printed `localhost` address.
