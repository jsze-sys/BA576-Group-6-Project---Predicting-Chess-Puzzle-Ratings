# Data

## Source

[Lichess.org open database, puzzle collection](https://database.lichess.org/#puzzles), released under the Creative Commons CC0 license. The full collection contains about 6.1 million puzzles taken from real games played on Lichess.

## File

`processed/Lichess_Puzzle_Random_30000.csv` is a random sample of 30,000 puzzles from the full collection, with one row per puzzle and the original 11 columns.

| Column | Description |
|---|---|
| `PuzzleId` | Unique puzzle code |
| `FEN` | Board position before the opponent's last move, in Forsyth–Edwards Notation |
| `Moves` | The opponent's last move followed by the solution, in UCI notation |
| `Rating` | Puzzle difficulty rating (Glicko-2). **This is the outcome the project predicts.** |
| `RatingDeviation` | Uncertainty of the rating |
| `Popularity` | Net player votes, from -100 to 100 |
| `NbPlays` | Number of times the puzzle has been attempted |
| `Themes` | Tactic and phase tags, separated by spaces |
| `GameUrl` | Link to the source game and move |
| `OpeningTags` | Opening name (only for puzzles from the opening phase) |
| `DailyDate` | Date featured as Lichess "Puzzle of the Day", if ever |

`Rating` and every column used to build predictors are complete, with no missing values. Every puzzle in the sample comes from a different source game.

## Loading

The notebook loads this file automatically: from the local `data/processed/` folder when run from a copy of the repository, or directly from GitHub when opened in Google Colab.
