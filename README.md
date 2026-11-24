# ⏱️ STUDY//TERM — study stopwatch

![macOS](https://img.shields.io/badge/macOS-Übersicht-3ef0ff?style=flat-square&logo=apple&logoColor=white&labelColor=040914) ![Vibecoded](https://img.shields.io/badge/vibecoded-with%20Claude-ff5ad9?style=flat-square&labelColor=040914)

A focus timer that **logs what you did**. Start it, pause it, and when you log the session, write one line about what you got done. Every logged session lands in a CSV, feeds a stats page and pays points into [WALLET//Ð](https://github.com/SlicingReaper/points-wallet-widget).

| File | What |
|:--|:--|
| `studyterm.jsx` | The widget (230 × 176, under 75//HARD by default; refreshes every second) |
| `studyterm.py` | Backend: timer, session log, wallet payment, stats page |
| `obsidian/` | My original edition, which writes to my Obsidian vault ([details](obsidian)) |

## Use it

| Button | Timer at 0 | Timer running / paused |
|:--|:--|:--|
| **Left** | `OPEN`: opens the stats page in your browser | `LOG`: asks *WHAT DID YOU DO?* → ⏎ logs it (Esc = back) |
| **Middle** | `▶` start | `❚❚` pause / `▶` resume |
| **Right** | (dimmed) | `DEL`: tap twice within 3 s to throw the session away |

- Tap the **subject line** (`▸ STUDY`) to cycle subjects.
- The note is required. No note, no log. That's the point: proof of work.
- Under 1 minute isn't logged. A study day rolls over at **04:00**, and a session belongs to the day it *started* in.
- The timer stores timestamps, not a counter, so it survives sleep, reboot and quitting Übersicht.

## Points

Every full **25-minute block** of a day's running total pays **15 Ð** into the wallet. Leftover minutes count toward the next block, so two 15-minute sessions still earn one block.

## Config

`~/Library/Application Support/STUDYTERM/standalone/data/studyterm-config.json` is created on first run:

```json
{ "subjects": ["STUDY", "CODING", "READING", "PROJECT"], "block_min": 25, "points_per_block": 15, "weekly_target_h": 10 }
```

`points_per_block: 0` turns off wallet payments. `weekly_target_h` drives the meter and the daily-share line on the stats page.

## Data

- `…/standalone/data/sessions.csv`: `date,subject,minutes,points,note`, one row per session (open it in any spreadsheet)
- `…/standalone/studyterm/state.json`: the running timer · `stats.html`: the last generated stats page

## 🚀 Install

1. Download this repo (green **Code** button → *Download ZIP*) and double-click **`install.command`**. The first time, macOS may block it: right-click → *Open*.
   It installs [Übersicht](https://tracesof.net/uebersicht/) if you don't have it and copies `studyterm.jsx` into its widgets folder, plus `studyterm.py` into `~/Library/Application Support/STUDYTERM/standalone/bin/`.
2. Click the widget to use it. If clicks fall through to the desktop: Übersicht menu-bar icon → this widget → turn on interaction.

- **Needs:** macOS 13+ · `python3` 3.8+ (run `xcode-select --install` if you don't have it)
- **By hand:** Copy `studyterm.jsx` into Übersicht's widgets folder (menu-bar icon → *Open Widgets Folder*) and `studyterm.py` into `~/Library/Application Support/STUDYTERM/standalone/bin/`.
- **Remove:** delete `studyterm.jsx` from the widgets folder. Your data in `~/Library/Application Support/STUDYTERM/standalone/data/` stays.

## 🎨 Look and position

Out of the box it sits in its default spot in the cyan terminal theme. Install [**WIDGET//CTL**](https://github.com/SlicingReaper/widgetctl) to drag it anywhere on a grid and pick from 16 colour schemes × 8 styles, and to get `⌃⌥⌘W`, which hides all widgets at once.

## 🧩 Part of a collection

This widget is one of fifteen that share the same retro-terminal look, the same theming and the same show/hide hotkey. Each works on its own; together they make a desktop dashboard.

| | Widget | What |
|:-:|:--|:--|
| 💰 | [**WALLET//Ð**](https://github.com/SlicingReaper/points-wallet-widget) | Points wallet: earn for habits, spend on rewards, lock savings, keep a streak |
| 🔥 | [**75//HARD**](https://github.com/SlicingReaper/75-hard-widget) | 75 Hard challenge tracker: 7 daily tasks, day counter, auto-fail on a missed day |
| ⏱️ | [**STUDY//TERM**](https://github.com/SlicingReaper/study-timer-widget) ← you are here | Study stopwatch that logs what you did, with a stats page and points |
| ✎ | [**NOTE//PAD**](https://github.com/SlicingReaper/notepad-widget) | Checklist notes with deadline countdowns, auto-expiry and a bin |
| “ | [**QUOTE//DAY**](https://github.com/SlicingReaper/quote-of-the-day-widget) | A new quote every midnight from a pool of 300, with likes and your own quotes |
| ▦ | [**TETRIS//GRID**](https://github.com/SlicingReaper/tetris-widget) | Tetris on the desktop: hold, ghost piece, levels, best score |
| ◉ | [**PONG//SOLO**](https://github.com/SlicingReaper/pong-widget) | Single-player Pong: keep the ball up, it speeds up every hit |
| ◎ | [**PONG//DUO**](https://github.com/SlicingReaper/pong-duo-widget) | Two-player Pong, 3 widgets wide: W/S vs ↑/↓, first to 7 |
| ⊞ | [**2048//TILE**](https://github.com/SlicingReaper/2048-widget) | 2048 with undo, keyboard or drag, saved between sessions |
| ⌂ | [**OUTPOST//**](https://github.com/SlicingReaper/outpost-colony-widget) | Colony-trading game: claim land, outfit robots, trade against 3 AI rivals |
| ☠ | [**DOOM//TERM**](https://github.com/SlicingReaper/doom-widget) | DOOM shareware Episode 1 in a 2-column widget: WebAssembly engine, savegames kept |
| ◍ | [**GLOBE//GUESS**](https://github.com/SlicingReaper/globe-widget) | Daily mystery country on a spinning globe: every guess glows hotter the closer it is |
| ◍ | [**ATLAS//QUIZ**](https://github.com/SlicingReaper/atlas-quiz-widget) | Sporcle-style map quiz: type a name, the country lights up green. World, continents, US states |
| W | [**WORDLE//**](https://github.com/SlicingReaper/wordle-widget) | The daily five-letter word game: six tries, streaks, guess distribution, unlimited practice |
| 🎛️ | [**WIDGET//CTL**](https://github.com/SlicingReaper/widgetctl) | Menu-bar app that arranges and themes all the widgets, plus a ⌃⌥⌘W show/hide hotkey |

**Install all of them at once:** [`vibecoded` → install-all.command](https://github.com/SlicingReaper/vibecoded) · 🤖 Vibecoded with [Claude](https://claude.ai): I designed, directed and tested it, the AI wrote most of the code.
