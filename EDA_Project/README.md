# CoEDA – Students Performance Data Preprocessing & EDA

A Google Colab notebook that walks through a complete data preprocessing and exploratory data analysis (EDA) pipeline on the **Students Performance** dataset.

## Dataset

`StudentsPerformance.csv` – exam results of students along with demographic and background details.

| Column | Type | Description |
|---|---|---|
| gender | categorical | Student's gender |
| race/ethnicity | categorical | Group A–E |
| parental level of education | categorical | Highest parental education |
| lunch | categorical | Standard / free-reduced |
| test preparation course | categorical | Completed / none |
| math score | numeric | Score in math |
| reading score | numeric | Score in reading |
| writing score | numeric | Score in writing |

**Engineered columns:** `Total_Score` (sum of the three scores), `Average_Score` (Total / 3).

## What the notebook covers

1. **Data loading & inspection** – `head`, `tail`, `sample`, `info`, `describe`, dtypes
2. **Data quality checks** – missing values, duplicate rows
3. **Feature engineering** – `Total_Score`, `Average_Score`
4. **Label encoding** – `LabelEncoder` on `gender` and `lunch`
5. **Scaling** – `StandardScaler` (z-score) on numeric columns
6. **Feature selection**
   - Correlation of numeric features with `Average_Score`
   - Chi-squared test (`SelectKBest`) for categorical features vs. score category
7. **Feature extraction** – PCA with explained variance ratio
8. **Discretization** – `Average_Score` binned into Poor / Average / Good / Excellent (`[0,40,60,80,100)`)
9. **Data reduction** – numerosity reduction by group-by aggregation (mean scores)
10. **Visualization** – pairplot, score distribution, correlation heatmap, parental education count, lunch-type boxplot, test-prep barplot
11. **Export** – processed data saved as CSV

## Outputs

- `students_performance_original_with_features.csv` – original data + engineered features
- `students_performance_aggregated.csv` – aggregated (reduced) data

## Tech stack

- Python 3
- pandas, NumPy
- matplotlib, seaborn
- scikit-learn (`LabelEncoder`, `StandardScaler`, `SelectKBest`, `chi2`, `PCA`)
- Google Colab

## How to run

1. Open `CoEDA_PREPROCESSING.ipynb` in [Google Colab](https://colab.research.google.com/).
2. Run the upload cell and select `StudentsPerformance.csv`.
3. Run all cells in order (`Runtime → Run all`).
4. Download the generated CSV files from the last cell.

To run locally instead:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook CoEDA_PREPROCESSING.ipynb
```

> Replace the `google.colab` upload/download cells with a plain `pd.read_csv("StudentsPerformance.csv")` when running locally.

## Author

Sujithra – CSE, KPR Institute of Engineering and Technology
