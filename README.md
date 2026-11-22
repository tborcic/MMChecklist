# MMChecklist — Majora's Mask 3D 100% Tracker

A single-page, offline checklist for **The Legend of Zelda: Majora's Mask 3D** (Nintendo 3DS). It tracks every collectible needed for 100%, explains how to get each one step by step, and helps you plan around the game's 3-day cycle.

No install, no account, no server: open `index.html` in any modern browser.

## What it tracks

| Category | Count |
|---|---|
| Masks | 24 |
| Pieces of Heart | 52 |
| Boss Heart Containers | 4 |
| Bottles | 7 |
| Great Fairy rewards (15 Stray Fairies per temple) | 4 |

All entries follow the **3DS version**, where several things moved or changed compared with the N64 original:
- Stone Mask: Shiro is in the Pirates' Fortress courtyard.
- Giant's Mask: you get it during the Twinmold fight.
- Koume's boat game gives a Bottle, and its Piece of Heart moved to the Night 3 grave beneath Ikana Graveyard.
- The Fisherman's jumping game is new to the 3DS version.
- Gorman's Mysterious Milk Bottle is new to the 3DS version.

## Features

- **Step-by-step sub-checklists:** each item is broken into individual in-game actions with locations and times. Ticking every step completes the item.
- **Required gear on every item:** green ✓ / red ✗ tags show what you have and what you're missing. Nothing is "optional". If a guide recommends an item, it's listed as required.
- **Collected gear panel:** tick off songs, equipment, trade items and masks. Masks stay in sync both ways with the checklist.
- **Items I Have On Me:** a filter that shows only what you can do with your current gear.
- **Prerequisite links:** every item shows **Needs first** and **Unlocks** links (for example, the Title Deed trading chain). Clicking a missing-gear tag jumps to where you get it.
- **Cycle Planner:** every timed event you still need, in order from Day 1 to Night 3. Items tagged **One cycle** must be finished without playing the Song of Time.
- **Right Now:** pick the day and time to see what's happening at that moment, ending soonest first.
- **Hide Completed** (on by default), with an Undo message.
- **Notes** on every item. The search box also searches your notes.
- **Stray Fairy counters** (0–15) for each temple.
- **Region progress bars** and a **Closest to done** sort.
- **Export / Import Progress** as a `.json` file to back up your save or move it between devices.
- Filters for category, day, time of day, region and status, plus full-text search.
- Keyboard accessible, works on mobile.

## Usage

1. Download or clone the repo and open `index.html` in a browser.
2. Tick the gear you already have in **Collected Items & Gear Checklist**.
3. Use the **Checklist**, **Cycle Planner** or **Right Now** tabs to decide what to do next.

Progress is saved automatically in your browser's `localStorage`, so it's tied to that browser. Use **Export Progress** to keep a backup.

### Hosting on GitHub Pages

Go to **Settings → Pages → Build and deployment**, choose **Deploy from a branch**, pick `main` / `(root)` and save. The tracker will be live at `https://tborcic.github.io/MMChecklist/`.

## Editing the data

Everything lives in `index.html`:

- `GEAR_ITEMS`: the collected-gear list.
- `ITEMS`: masks, heart pieces and heart containers. Bottles and fairies are added further down with `ITEMS.push(...)`.
- `SCHEDULES`: the time windows used by the Cycle Planner and Right Now. Times are on a 6 AM-based clock: `6` = 6:00 AM, `18` = 6:00 PM, `24` = midnight, `30` = 6:00 AM the next morning.
- `GEAR_SOURCE`, `EXTRA_NEEDS`, `SAME_CYCLE`: where gear comes from, extra dependencies, and items that must be done in one cycle.

> **Don't renumber item IDs.** They are stored in people's saves. Gaps such as `hp26` and `hp44` are deliberate. Always give new entries new, never-used IDs.

Sub-step checkmarks are keyed by a hash of each step's text, so adding or reordering steps is safe. Rewording a step resets only that step's checkmark.

## Accuracy

Details were checked against community guides (Zelda Dungeon, StrategyWiki, Zelda Wiki, Gamer Guides). A few planner times are approximate, such as minigame opening hours and some Anju & Kafei quest timings. Corrections are welcome. Open an issue or a pull request.

## License

[MIT](LICENSE). *The Legend of Zelda* and *Majora's Mask* are trademarks of Nintendo. This is an unofficial fan-made tool.
