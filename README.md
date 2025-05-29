# 🏀 NBA Game Predictor

This project builds a machine learning pipeline to predict NBA game outcomes (Win/Loss) using rolling performance metrics from the 2024–2025 NBA season.

## 📂 Project Overview

The notebook `nba_game_predictor.ipynb` walks through the full workflow of:

- Preprocessing and merging team box scores from October 2024 – April 2025
- Generating rolling averages for recent team performance
- Feature engineering for predictive modeling
- Training and evaluating multiple classifiers (Logistic Regression, Random Forest, HistGradientBoosting, XGBoost)
- Visualizing model results and feature importance

## 🔍 Objective

**Goal**: Predict if the home team will win using recent performance indicators.

## 📦 Dataset

Manually collected from [Basketball Reference](https://www.basketball-reference.com/leagues/NBA_2025_games.html), cleaned and split by month:

- `NBA_2024_October.csv`
- `NBA_2024_November.csv`
- `NBA_2024_December.csv`
- `NBA_2025_January.csv`
- `NBA_2025_February.csv`
- `NBA_2025_March.csv`
- `NBA_2025_April.csv`

Each file contains:

- Game date
- Away/Home teams and scores
- Attendance, arena, and win result (derived)

## 🧠 Feature Engineering

Derived features for modeling include:

| Feature                    | Description |
|---------------------------|-------------|
| `HOME_AVG_PTS_LAST5`      | Avg points scored by home team in last 5 games |
| `AWAY_AVG_PTS_LAST5`      | Avg points scored by away team in last 5 games |
| `HOME_WIN_RATE_LAST5`     | Home team win percentage in last 5 games |
| `AWAY_WIN_RATE_LAST5`     | Away team win percentage in last 5 games |
| `POINT_SPREAD`            | Difference in average points scored |
| `WIN_RATE_DIFF`           | Difference in recent win rates |
| `HOME_AVG_ALLOWED_LAST5`  | Avg points conceded by home team |
| `AWAY_AVG_ALLOWED_LAST5`  | Avg points conceded by away team |

## 🤖 Models Used

- **Logistic Regression**
- **Random Forest**
- **HistGradientBoostingClassifier**
- **XGBoostClassifier** (with GridSearchCV tuning)

### Model Evaluation

Evaluated using:

- Accuracy
- Precision / Recall / F1-score
- Permutation-based feature importance

## 📈 Final Results

| Model                    | Accuracy | Notes |
|--------------------------|----------|-------|
| Logistic Regression      | ~64%     | Baseline model |
| Random Forest            | ~61%     | Slightly underperforms |
| HistGradientBoosting     | ~61%     | More robust than Random Forest |
| **XGBoost (Tuned)**      | **63%**  | Best performance with hyperparameter tuning |

## 📊 Feature Importance (XGBoost)

- `HOME_AVG_ALLOWED_LAST5` and `AWAY_AVG_PTS_LAST5` were the most important predictors.
- Win rate metrics contributed modestly.

## 📝 Files

| File                    | Description |
|-------------------------|-------------|
| `nba_game_predictor.ipynb` | Full pipeline notebook |
| `NBA_2024_*.csv` / `NBA_2025_*.csv` | Raw box score data by month |

## 📌 Future Improvements

- Include player availability or injuries
- Add Elo ratings or betting spreads
- Track back-to-back fatigue/rest impact

## 🧪 Author

**Tae Kim**  
[GitHub Profile](https://github.com/opseoul)

---

## 📜 License

Licensed under the [Apache 2.0 License](./LICENSE).
