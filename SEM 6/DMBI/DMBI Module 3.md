# DMBI Module 3

## Explaindifferent types of attributes used in data exploration with examples.

1. Nominal Attributes:
	- Categories with no order or ranking.
	- Measure of central tendency: mode only.
	- Examples: Gender (`Male`/`Female`), blood type (`A`/`B`/`O`/`AB`), country name.
2. Ordinal Attributes:
	- Categories with meaningful order but no fixed differences.
	- Measure of central tendency: median.
	- Examples: Satisfaction (`Poor`/`Average`/`Good`), education (`High School < Bachelor < Master`), shirt size (`S`/`M`/`L`).
3. Interval Attributes:
	- Numeric with equal differences but no true zero.
	- Measure of central tendency: mean.
	- Examples: Temperature (`°C` or `°F`), calendar years (`2020`, `2021`, `2022`), IQ scores.
4. Ratio Attributes:
	- Numeric with equal differences and a true absolute zero.
	- Measure of central tendency: mean, geometric mean.
	- Examples: Age (`0 means none`), height, weight, income, number of purchases.
5. Binary Attributes:
	- Binary attributes have only two possible values.
	- Measure of central tendency: proportion or mode.
	- Examples: 0/1, Yes/No, True/False, Male/Female, Pass/Fail.

---
## What is an outlier? List types of outliers. Describe methods used for outlier analysis.

An outlier is a data point that differs significantly from other observations. It may indicate variability, measurement error, or inconsistent behaviour.

| Type                             | Description                             | Example                                                |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------ |
| Point (Global) Outlier           | Single value far outside normal range   | `Age = 150` in a dataset of human ages                 |
| Contextual (Conditional) Outlier | Abnormal only within a specific context | 30°C in December (normal for July, outlier for winter) |
| Collective Outlier               | A group of points deviating together    | Three consecutive 0°C readings in a tropical climate   |
Methods:
1. Statistical (Z-Score) Method
	- Assumes normal distribution. Calculates `Z = (x - μ)/σ.`
	- Rule:` |Z| > 3 → outlier.`
	- Example: In test scores (`mean=70, σ=10`), a score of `30` has `Z = -4 → outlier.`
2. IQR (Interquartile Range) Method
	- Non-parametric. Compute `Q1` (25th percentile), `Q3` (75th percentile).
	- `IQR = Q3 - Q1. Outlier if: x < Q1 - 1.5×IQR or x > Q3 + 1.5×IQR.`
	- Example: Q1=50, Q3=80, IQR=30. Any value < 5 or > 125 is an outlier.
3. Visualization Methods
	- Box Plot: Points beyond whiskers = outliers.
	- Scatter Plot: Points far from main cluster.
4. Machine Learning Methods
	- DBSCAN (Density-based): Points in low-density regions = outliers.
	- Isolation Forest: Randomly isolates observations; outliers require fewer splits.

---
## What is Noisy Data?

Random errors, distortions, or meaningless variations in data that obscure true patterns
- Causes: Faulty sensors, data entry errors, transmission glitches, measurement inaccuracies
- Difference from outliers: Noise is random error; outliers are valid but extreme values
- Examples: A temperature reading of 88.5°C in a room at 25°C; age entered as "abc"; static in an audio recording

Handling Noisy Data:
- Binning: Group values into bins; replace with bin mean, median, or boundaries
- Clustering: Group similar points; discard points not belonging to any cluster
- Regression: Fit a smoothing function; replace values with predicted points on curve
- Moving Average: Replace each value with average of its neighbouring values
- Manual Inspection: Expert review for critical datasets

---
## Steps in data pre-processing

 1. Data Cleaning
	- Handle missing values (remove or impute).
	- Remove duplicates and irrelevant data.
	- Correct data entry errors.
2. Data Transformation
	- Convert data types (e.g., strings to numbers, dates to datetime).
	- Apply scaling/normalization (`Min-Max, Z-score`) for features with different units.
	- Log or power transforms for skewed distributions.
3. Handling Outliers
	- Detect outliers using `IQR`, `Z-score`, or visualization (`boxplots`, `scatter plots`).
	- Remove, cap (`winsorize`), or treat outliers based on domain knowledge.
4. Encoding Categorical Variables
	- Label encoding for ordinal categories (e.g., `low`/`medium`/`high`).
	- One-hot encoding for nominal categories (e.g., `red`/`green`/`blue` → `binary columns`).
	- Target encoding for high-cardinality features.
5. Feature Engineering & Selection
	- Create new features from existing ones (e.g., age from birth date, ratios, interactions).
	- Remove irrelevant or redundant features using correlation analysis, mutual information, or recursive elimination.
6. Data Splitting (for supervised learning)
	- Split data into training, validation, and test sets (e.g., `70`/`15`/`15` or `80`/`20`).
	- Use stratified splitting for classification to preserve class balance.
	- Ensure no data leakage (test data does not influence training).

