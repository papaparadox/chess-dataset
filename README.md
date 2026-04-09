# Chess Games Analysis

### Data Analysis Project — Lichess Dataset

## Overview

This project analyses **20,058 chess games** sourced from the [Lichess platform via Kaggle](https://www.kaggle.com/datasets/datasnaek/chess). The goal was to explore patterns in game outcomes, player ratings, openings, and game length through data cleaning, transformation, and exploratory data analysis.

**Key columns of the Dataset:**

| Column                          | Type   | Description                                                                         |
| ------------------------------- | ------ | ----------------------------------------------------------------------------------- |
| `id`                            | string | Unique game identifier                                                              |
| `rated`                         | bool   | Shows if the game was rated or not                                                  |
| `turns`                         | int    | Number of moves done                                                                |
| `victory_status`                | string | How did the game ended, with outcomes such as `mate`, `resign`, `outoftime`, `draw` |
| `winner`                        | string | Determines the winner, with labels such as `white`, `black`, or `draw`              |
| `white_rating` / `black_rating` | int    | Elo ratings of each player                                                          |
| `increment_code`                | string | Time control format, e.g. `10+5` - 10 minutes with a 5 second increment             |
| `opening_name`                  | string | Full opening name with variation (e.g. Slav Defense:Chigorin Variation)             |
| `moves`                         | string | Full game in one string                                                             |

## Jupyter Notebooks

### `cleaning-dataset.ipynb` - Main Cleaning and Transformation of a Dataset

Contains step 1-4 of the hackathon requirements.

- **Step 1 - Collect a Dataset:** - Loads `games.csv`, verifies all dataset requirements (20000+ rows, 16 columns, mix of data types)
- **Step 2 - Questions & Hypotheses:** - Defines 5 analytical questions and testable hypotheses
- **Step 3 - Identify & Document:** - Inspects data types, missing values, and unique value counts with no modifications made
- **Step 4 - Clean & Transform:** - Creates `chess_games_clean.csv` ready for analysis

### `plotting_dataset.ipynb` — Exploratory Data Analysis (EDA)

Covers step 5. Has 2 questions and hypotheses proven

## Questions & Hypotheses

| №   | Question                                               | Type                              | Hypothesis                                                                                                                                            |
| --- | ------------------------------------------------------ | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Q1  | Does the higher-rated player win more often?           | Correlation between variables     | The winrate of a higher-rated player will be way above 50%                                                                                            |
| Q2  | Does playing as white give a bigger advantage?         | Comparison between groups         | White wins more than black, since they have an advantage of playing the first move. White's win rate will be above 50% across all games               |
| Q3  | Do higher-rated games last longer?                     | Correlation between variables     | Games between higher-rated players will likely last longer, due to masters playing more positionally than beginners that tend to go for quick tactics |
| Q4  | Does the opening choice affect the outcome?            | Impact of one variable on another | Certain openings will show very different win rates (by different outcomes)                                                                           |
| Q5  | Are rated games played differently from unrated games? | Comparison between groups         | Rated games will last longer and end in checkmate/resignation of the opponent more then timeouts, due to rated players taking the game more seriously |

## EDA — Visualisations & Findings

### Plot 1 — Game Outcomes

**Type:** Pie chart + bar chart  
White wins 4% more games than Black. Resignation is the most common ending, followed by checkmate.  
**Q2 verdict:** Partially proven — white wins slightly more (4%), supporting the theory of first-move matter

### Plot 2 — Rating Distributions & Difference

**Type:** Histogram  
Ratings for white and black are nearly identical and centred around 1500–1600 ELO, confirming balanced matchmaking. The higher-rated player wins significantly more than half of the time.  
**Q1 verdict:** Proven.

## Requirements

Install necessary libraries with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

## How to Run (Recommended to use Github Codespaces/Databricks)

1. Download `games.csv` from [Kaggle](https://www.kaggle.com/datasets/datasnaek/chess) and place it in the `datasets` folder
2. Open `chess_analysis.ipynb` and run all cells — this generates `chess_games_clean.csv`
3. Open `plotting_dataset.ipynb` and run all cells to see the visualisations
