# BA576 Group 6: Predicting Chess Puzzle Ratings

Team project for BA576 Machine Learning for Business Analytics.

## Research question

Can we predict a Lichess chess puzzle's numeric difficulty rating from the position, the known solution, and tactical features available when a puzzle is created?

## Team

Jonathan Sze, Nawaf Alsheikh, Alexander Lee, Aaron Cheung

## Repository structure

- `notebooks/BA576_Project_Workbook.ipynb`: Colab compatible starter workbook.
- `data/README.md`: data access and sharing notes.
- `requirements.txt`: Python dependencies used by the notebook.

## Open in Google Colab

[Open the starter workbook in Colab](https://colab.research.google.com/github/jsze-sys/BA576-Group-6-Project---Predicting-Chess-Puzzle-Ratings/blob/main/notebooks/BA576_Project_Workbook.ipynb)

## Current project state

The team has a first phase problem and answers document and a four page proposal deck. The starter workbook is configured to load the first 30,000 rows from the Lichess source, audit them, create interpretable features, check the grouped train and test split, and establish a simple baseline. The notebook is intentionally a starting point, not a finished submission.

## Important modeling decision

The proposal includes features derived from the recorded solution, such as solution length, captures, and checks. That is valid only if the intended use case is rating a puzzle after its solution is known. If the intended use case is rating a position before a solution is available, those features are leakage and must be removed. The team should settle this framing before comparing models.

## Academic integrity

The BA576 syllabus requires citation of external resources, including AI tools. The notebook contains a reminder to document any external assistance and to verify all code and interpretations as a team before submission.
