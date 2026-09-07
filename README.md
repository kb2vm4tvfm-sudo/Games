# Airplane Mode — Offline Games

Ten games in a single HTML file. No wifi, no cell signal, no ads, no tracking,
no external requests of any kind. Everything — code, styles, the word list, the
sound effects — lives inside `index.html`.

## Get it onto your phone before the flight

Pick whichever is easiest. **Option 1 is the one that cannot fail.**

### 1. Save the file (works with the phone in airplane mode)

1. On the phone, open the raw file and save it:
   - **iPhone:** open `index.html` in Safari → Share → **Save to Files**.
     Later, open the Files app and tap the file — Safari renders it offline.
   - **Android:** download `index.html` → open it from the Files/Downloads app
     and choose your browser.
2. That's it. Nothing else is needed — no server, no connection, ever.

Emailing or AirDropping the file to yourself works too; the file is ~79 KB.

### 2. Add to home screen (looks like a real app)

If you can serve the folder over HTTPS before you fly (GitHub Pages, or any
static host), open it once with a connection. `sw.js` caches the page, so it
keeps working in airplane mode and can be added to the home screen as a
full-screen app.

Serving it locally to test:

```
npx http-server . -p 8080     # then open http://localhost:8080
```

## The games

| | Game | What it is |
|---|---|---|
| 🔢 | **2048** | Swipe to merge tiles. Arrow keys on desktop. |
| 🐍 | **Snake** | Swipe to turn. Speeds up as you eat. |
| 🧱 | **Blocks** | Falling-block stacker with ghost piece, next preview, hard drop. |
| 💣 | **Minesweeper** | Three sizes. Tap to dig, hold to flag, tap a number to auto-clear. |
| 📓 | **Sudoku** | Generated on-device with a guaranteed unique solution. Notes, hints, timer. |
| 🃏 | **Solitaire** | Klondike. Tap a card, tap where it goes. Undo, draw 1 or 3, auto-finish. |
| 🔤 | **Word Five** | Guess the five-letter word in six tries. 792-word offline dictionary, unlimited rounds. |
| 🧨 | **Breakout** | Drag the paddle. Levels get faster and the paddle gets narrower. |
| 🧠 | **Memory** | Match every pair. 4×4, 4×5 or 4×6. |
| 🔴 | **Connect 4** | Alpha-beta opponent at three strengths. Hard searches six plies. |

Scores, times and settings are kept in `localStorage`, so they stay on the
device and survive closing the tab.

## Notes

- **Sound** is on by default (short WebAudio blips, no audio files). It respects
  the phone's silent switch.
- **Battery:** the arcade games use `requestAnimationFrame`, so they stop
  drawing when you leave the tab or lock the screen.
- Tap **←** to go back to the menu, **↻** to restart the current game.

## Files

```
index.html      everything — the whole thing is here
manifest.json   only used for "add to home screen"
sw.js           only used when served over HTTPS; ignored from a local file
```
