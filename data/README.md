# Data access

The source CSV is stored in the shared Google Drive folder rather than committed to this repository.

The workbook expects a source file with at least 30,000 rows. Accepted filenames include `Lichess_Puzzle_First_30000.csv`, `Lichess_Puzzle_30000.csv`, `lichess_db_puzzle.csv`, and the old `Lichess_Puzzle_Pilot_5000.csv` filename if it has been replaced with a larger file.

The notebook reads only the first 30,000 rows with `nrows=30000`, so the original six million row CSV can be used without loading the entire file into memory.

The starter notebook checks common Google Drive paths and then opens a Colab upload control if it cannot find the file. Do not commit private or unnecessarily large copies of the dataset without confirming the team and source license.