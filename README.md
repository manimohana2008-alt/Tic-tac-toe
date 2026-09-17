# Tic Tac Toe ❌⭕

A single-screen Android app, built with **MIT App Inventor**, that lets two players take turns marking a 3x3 grid until someone gets three in a row — or the board fills up in a draw.

## How it works

1. Player **X** goes first — tap any empty cell to place an X
2. Player **O** taps next — turns alternate automatically
3. The status label at the top shows whose turn it is
4. After each move, the app checks all 8 possible winning combinations
5. If a player gets three in a row, the status label announces the winner and the board locks
6. If all 9 cells fill up with no winner, the status label shows "It's a draw"
7. Tap **Reset** to clear the board and start a new game

## Features

- ❌⭕ Two-player turn-based gameplay on a 9-button grid
- 🏆 Automatic win detection across all 8 winning combinations (3 rows, 3 columns, 2 diagonals)
- 🤝 Draw detection when the board is full with no winner
- 🔄 One-tap **Reset** button to restart the game
- 🖥️ Live status label showing current turn, winner, or draw result

## Tech Stack

- **Platform:** MIT App Inventor (block-based, no native code)
- **Components:** `Button1`–`Button9` (grid cells), `Resetbutton`, `statuslbl` (status label)
- **Variables:**
  - `global winning_combos` — list of all 8 winning cell-index combinations
  - `global game_button` — list referencing all 9 grid buttons
  - `global current_player` — tracks whose turn it is (`"x"` or `"O"`)
  - `global game_active` — boolean flag for whether the game is still in play
- **Procedures:** `checkwinner`, `checkdraw`

## How the Blocks Work

| Event / Procedure | Action |
|---|---|
| `Screen1.Initialize` | Builds `global winning_combos` (all 8 winning combinations) via `add items to list` |
| `any Button.Click` (not Reset) | If the game is active: sets the tapped button's text to `current_player`, calls `checkwinner`, then calls `checkdraw` if the game is still active; toggles `current_player` between X and O and updates `statuslbl` |
| `any Button.Click` (Reset) | Loops through `game_button`, clears each button's text and background colour, resets `game_active` to true, `current_player` to X, and `statuslbl` to "Turn: x" |
| `checkwinner` | Loops through `winning_combos`; if all 3 buttons in a combo match the current player's mark, highlights them, sets `game_active` to false, and updates `statuslbl` with the winner |
| `checkdraw` | If no winner and all buttons are filled, sets `game_active` to false and updates `statuslbl` to "It's a draw" |

## Example

| Action              | Result                              |
|---------------------|---------------------------------------|
| Tap an empty cell    | Cell fills with current player's mark |
| Three X's in a row   | Status shows "x wins" and board locks |
| Board full, no winner| Status shows "It's a draw"            |
| Tap Reset            | Board clears, X goes first again      |

## Screenshot

![App Screenshot](screenshot.png)

*The app in action — a mid-game board with the turn status shown at the top.*

## Limitations (v1.0)

- Two-player local play only — no single-player/AI opponent
- No score tracking across multiple rounds
- No animations or sound effects for wins/draws
- Fixed 3x3 grid size

## Future Improvements

- Add a single-player mode with a basic AI opponent
- Track and display a running score across games
- Add win animations and sound effects
- Support different board sizes (e.g. 4x4)

---
*Built as a mini project — MIT App Inventor, block-based development.*
