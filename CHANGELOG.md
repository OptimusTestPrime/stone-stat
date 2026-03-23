# StoneStat Changelog

All notable changes to StoneStat will be documented here.

-----

## [Unreleased]

-----

## [1.0.0] - 2026-03-23

### Initial Release

StoneStat is a browser-based curling shot scorer for two teams of four players, built as a single-file HTML app deployable via GitHub Pages. No install or account required.

-----

## Features at Launch

### Game Setup

- Configurable number of ends (4, 6, 8, 10)
- Hammer selection for End 1
- Team names and player names (Lead, Second, Third, Skip) for both teams
- 3-player team option (no Third) per team — shot distribution becomes Lead x3, Second x3, Skip x2
- Fields to Record selector — toggle Handle/Rotation, Shot Type, Miss Type, and Notes on/off per game
- Load Saved Team dropdown to pre-fill team and player names from the Team Editor
- Random name generator for team and player names (🎲 Random button)
- Yellow team displayed first to match common club conventions

### Shot Recording

- WCF shot order followed automatically — non-hammer team throws first, alternating
- **Handle / Rotation** — In-Turn or Out-Turn (mandatory)
- **Shot Type** — Guard, Draw, Tap, Raise, Runback, Takeout, Peel (mandatory)
- **Miss Type** — Heavy, Light, Wide, Tight (optional, multi-select); Heavy/Light and Wide/Tight are mutually exclusive pairs
- **Score** — 0–4 scale plus X (Throwaway, excluded from percentages)
- **Notes** — optional free text per shot
- Throwaway (X) bypasses all mandatory field checks
- Skip button (top right of Record Shot panel) to pass on a shot without recording
- Tap any shot dot in the player panels to jump to that shot for editing
- Current shot highlighted with a white outline ring in both pip tracker and player dots
- Prev Shot button to navigate back one shot, restoring all field selections
- Skip to End Score button to jump directly to end score entry

### End Score Entry

- +/- stepper buttons per team (no keyboard required), values 0–8
- Only one team scores per end
- Hammer rotates automatically based on who scored
- **Handshakes / End Game** button — saves current end score and opens Game Over screen at any point

### Scoreboard

- Per-end scores and running totals
- Tappable end numbers and score cells to jump directly to any end
- Hammer indicator (🥌 icon) next to the team with hammer

### Player Statistics (live during game)

- Shot dots coloured by score (red = missed, teal = perfect)
- Per-type percentages broken down by handle — e.g. D In:72% (3) D Out:68% (2)
- Only types and handles with recorded shots are shown
- Dynamic player name column width

### Game Statistics Screen

- Full-page stats screen (replaces modal) accessible via Stats button
- Team overall percentage
- Per-team shot type breakdown
- Per-player overall percentage, shot count, and per-type/handle breakdown
- Colour-coded key for all abbreviations

### Game Over

- Triggered by End Game button (last end) or Handshakes / End Game button (any end)
- Shows final score and winner
- Close to stay on game screen and review/edit shots
- Save & Exit to save game to history and return to setup

### Game History

- Last 20 completed games saved automatically in localStorage
- Expandable game cards with end scores and player stats
- Export per game: CSV (with Turn, Shot Type, Miss Type, Score, Label, Note columns), JSON, Text
- Delete game with confirmation prompt
- iOS share sheet triggered on export (falls back to data URI download, clipboard, or new window)

### Team Editor

- Separate screen accessible from header
- Create, edit, and save teams with team name and four player names
- Teams persist in localStorage indefinitely
- Search box to filter teams by name
- A→Z sort button
- Add Team button at top; new teams appear at top of list
- 🎲 Random button per card to generate random team and player names
- Green flash feedback on Save
- Saved teams available in Game Setup via Load Saved Team dropdown

### Help Page

- Separate screen with full documentation
- Sections: Getting Started, Recording a Shot, Score Scale, Navigation, Statistics, Shot Type Key, Game History and Export, Saved Data and Storage, Tips
- Also Try section: HammerTime delivery timer
- Connect section: Instagram (@hammertimecurling), Buy Me a Coffee

### Data Persistence

- Active game auto-saved to localStorage after every shot — survives page refresh
- Restore Game prompt on page load if an unfinished game is detected
- Draft cleared on Save & Exit or New Game

### Export Formats

- **CSV**: End scores, full shot log (End, Shot, Team, Player, Position, Turn, Shot Type, Miss Type, Score, Label, Note), player stats
- **JSON**: Complete raw game data
- **Text**: Plain text report with per-shot detail in parentheses

### iOS / Koder Compatibility

- All JavaScript base64-encoded to survive iOS autocorrect quote corruption
- No smart quotes, no template literals, no optional chaining
- `-webkit-` prefixed flexbox throughout
- `-webkit-appearance:none` on all inputs
- `touch-action:manipulation` on buttons
- Works offline once loaded
- Add to Home Screen supported (standalone app mode)

-----

## Known Shot Type Abbreviations

|Label|Full Name|
|-----|---------|
|G    |Guard    |
|D    |Draw     |
|Tp   |Tap      |
|R    |Raise    |
|RB   |Runback  |
|T    |Takeout  |
|P    |Peel     |

-----

## Deployment

- GitHub Pages: https://optimustestprime.github.io/stone-stat/
- Single file: `index.html`
- No build step, no dependencies, no server required