# Predicting Chess Puzzle Difficulty

**BA576 Machine Learning for Business Analytics · Group 6 · Fall 2026**
Jonathan Sze, Nawaf Alsheikh, Alexander Lee, Aaron Cheung

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jsze-sys/BA576-Group-6-Project---Predicting-Chess-Puzzle-Ratings/blob/main/notebooks/BA576_Project_Workbook.ipynb)

## Question

When a new chess puzzle is created, can we predict how difficult players will find it (its Lichess rating) using only information available before anyone has tried it?

## Why it matters

A new puzzle starts with a placeholder rating, so online chess platforms serve it to the wrong players until hundreds of attempts correct it: beginners get puzzles that are far too hard, strong players get puzzles that are too easy. Predicting the rating at creation time lets platforms such as Lichess and Chess.com, training apps and coaches match new puzzles to the right players from day one.

## Data

A random sample of 30,000 puzzles from the [Lichess open puzzle database](https://database.lichess.org/#puzzles) (CC0 license, about 6.1 million puzzles in total). From each puzzle's position, solution and theme tags we build 19 predictors in four groups: board composition, position context, the known solution, and tactic themes. Information that exists only after players attempt a puzzle (number of plays, popularity, rating uncertainty) is excluded from the predictors. See [`data/README.md`](data/README.md) for column details.

## Methods

Every method taught in BA576, scored on the same 6,000-puzzle test set and tuned with 5-fold cross-validation on the training set: linear regression, forward and backward stepwise selection, Ridge, Lasso and Elastic Net, polynomial and interaction terms, k-nearest neighbors, decision trees with cost-complexity pruning, bagging, random forest, AdaBoost and a neural network.

## Key results

| Model | Test RMSE (rating points) | Test R² |
|---|---|---|
| Random forest | 373 | 0.55 |
| Bagging | 375 | 0.54 |
| Neural network | 376 | 0.54 |
| Polynomial + interactions (Lasso) | 380 | 0.53 |
| Decision tree (pruned) | 388 | 0.51 |
| Linear regression | 413 | 0.44 |
| Baseline: predict the average | 553 | 0.00 |

- The **random forest** cuts the typical prediction error by a third compared with assigning every new puzzle the same rating. It cannot give an exact rating (the median puzzle is off by about 250 points), but it places a new puzzle in the right difficulty tier (easy, medium, hard, very hard) about half the time, and within one tier 96% of the time.
- **The solution drives difficulty.** Solution length and whether the first move is a check are the two most important predictors. A model that sees only the board, without the solution, barely beats the baseline (519).
- The model is most accurate for mid-range puzzles and compresses very easy and very hard puzzles toward the middle. Part of the remaining error is noise in the Lichess ratings themselves.

## Repository

| Path | Contents |
|---|---|
| `notebooks/BA576_Project_Workbook.ipynb` | Full analysis: data, features, descriptive analysis, all models, comparison and conclusions |
| `data/processed/Lichess_Puzzle_Random_30000.csv` | The 30,000-puzzle sample |
| `data/README.md` | Data source and column descriptions |
| `presentation/figures/` | Charts used in the final presentation |
| `requirements.txt` | Python packages |

## Running the notebook

Click **Open in Colab** above and choose *Runtime → Run all*. The notebook installs its one extra package and loads the data from this repository automatically. A full run takes about 5 to 10 minutes.

To run locally: `pip install -r requirements.txt`, then open the notebook in Jupyter.

## References

- Lichess.org open database, puzzle collection. https://database.lichess.org/#puzzles
- James, Witten, Hastie, Tibshirani and Taylor. *An Introduction to Statistical Learning with Applications in Python*. https://www.statlearning.com
- Pedregosa et al. (2011). Scikit-learn: Machine Learning in Python. *JMLR* 12, 2825–2830.
- python-chess, by Niklas Fiekas. https://python-chess.readthedocs.io
- Claude (Anthropic) was used to help write and document code. All analysis choices, results and interpretations were reviewed and verified by the team.
