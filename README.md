# Web Chess — Beginner & Expert (Single-File HTML)

A lightweight, dependency-free chess you can run from a single `index.html`.  
It supports legal move generation (including castling, en passant, and promotion), click-to-move, last-move markers, check detection, undo, flip board, and two AI levels.

## Demo
Open `index.html` directly in your browser—no build steps, no servers required.

## Features
- **Two levels**
  - **Beginner**: fast, random-legal moves (slight bias for captures).
  - **Expert**: alpha-beta search (depth 3) with quiescence and simple move ordering; material + piece-square-table + mobility evaluation.
- **Full rules**: legal move filtering, **castling**, **en passant**, **promotion** (with a modal picker).
- **UX**
  - Click a piece → highlights legal targets.
  - Last move and “in check” visual markers.
  - Move list (UCI style), captured pieces tray, simple eval read-out.
  - **Undo** (rolls back your move and engine response), **Flip** board, choose **side** and **level**, **New Game**.

## How to Use
1. Download or clone the repo.
2. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari).
3. Use the controls on top:
   - **Side**: play as White or Black.
   - **Level**: Beginner or Expert.
   - **New Game**: start fresh with your selections.
   - **Undo**: revert last pair of moves (yours + AI).
   - **Flip**: change board orientation.

## Code Structure (in `index.html`)
- **Core chess**: FEN parsing, board state, pseudo-legal generation, legal filtering via in-check test, and state transitions with history for undo.
- **Rules covered**: standard chess moves, promotions (Q/R/B/N), en passant, castling rights tracking & validation, check/checkmate/stalemate detection.
- **AI**:
  - Beginner: random legal move (prefers captures).
  - Expert: alpha-beta (depth 3) + quiescence on captures, MVV-LVA-style ordering, simple evaluation (material + PST + mobility).

## Customization
- **Search Depth**: In the script, change `const depth = 3` to 4 for a stronger (but slower) Expert mode.
- **Style**: Tweak colors and radius in the `:root` CSS variables.
- **Evaluation**: Tune piece values or the piece-square tables in the `PIECE_VALUE` / `PST` constants.

## Known Trade-offs
- Expert search depth is fixed for responsiveness (suitable for browsers and mobile).
- Move list is displayed in UCI format for simplicity (e.g., `e2e4`, `e7e5`, `O-O`).

## License
This project is provided under the MIT License. See `LICENSE` if you add one to your repo.

## Notes
- Everything is self-contained in **one** file; there are **no external libraries** or network calls.
- Works fully offline.

## Roadmap Ideas (optional)
- Add opening book for faster, more human-like play.
- Transposition table / Zobrist hashing for stronger Expert mode.
- Threefold repetition and 50-move draw adjudication.
- PGN notation & export.
