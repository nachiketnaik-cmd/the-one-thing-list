# The One Thing List

A deliberately minimal to-do app built around a single rule: **you only ever see one task at a time.**

Live site: https://nachiketnaik-cmd.github.io/the-one-thing-list/

## Why it exists

The usual problem with a to-do list is that *seeing* the whole list is itself a distraction. Ideas and reminders arrive all day ("oh, I should do that", "I haven't touched my hobby"), and while working on one task you get pulled toward another. This app fixes that by hiding everything except the one task at the top of the line, so there's nothing to get distracted *by*.

## How it works

- **Your one thing.** The main screen shows a single task — the top of the queue — and nothing else. A **Done** button clears it.
- **Park a thought.** A capture box sits under the task. Jot down any stray idea or reminder and it drops into an **inbox**, out of sight, without revealing the list. This lets you offload a thought without breaking focus.
- **Done → rest.** Finishing a task shows a calm "You're done — tap when ready for the next one" screen. Doing nothing is a valid stop; or tap **Next task** to pull the next one into focus.
- **Recurring tasks.** In planning mode, mark any task recurring with the ↻ button. When you complete a recurring task it isn't deleted — it drops into a **Recurring** holding area in planning, from which you send it back into the line whenever you need it again. This way repeating tasks (water plants, daily review, exercise) cycle instead of vanishing.
- **Planning mode.** Reveals the whole line (behind a confirm, so you don't idly peek). Here you add tasks, edit them inline, reorder them, promote one to #1, mark them recurring, delete, re-add recurring tasks, and triage inbox thoughts into the line. Intended for a nightly or set planning time.

Hobbies, chores and errands all share the same single line — ordering is purely manual, with no dates or times. The discipline is in consciously deciding what earns the #1 slot.

## Technical notes

- A single self-contained `index.html` — plain HTML, CSS and vanilla JavaScript. No build step, no dependencies, no backend.
- Data is stored in the browser's `localStorage` under the key `oneThingList.v1`. It lives on whichever browser/device you use it in and is **not** synced across devices. Clearing site data resets the list.
- Hosted on GitHub Pages from the `main` branch.

## Running it locally

Just open `index.html` in a browser, or serve the folder:

```
python3 -m http.server
```

then visit the printed `localhost` address.
