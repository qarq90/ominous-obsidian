# DMBI Module 5

## Explain decision tree classifier.

A Decision Tree is a supervised machine learning algorithm used for both classification and regression tasks (though commonly for classification). It models decisions and their possible consequences as a tree-like structure.

- Root Node: Represents the entire dataset and the best feature to split on first.
- Internal Nodes (Decision Nodes): Represent a feature (attribute) with branches leading to possible values.
- Branches: Represent the outcome of a test (e.g., `Age < 30`).
- Leaf Nodes (Terminal Nodes): Represent a class label (decision).

It recursively partitions the data based on feature values, selecting the most informative feature at each step until all data in a subset belongs to the same class or a stopping criterion is met.

---
## Steps for ID3 algorithm with example.

---
## Decision Tree Induction and Attribute Selection

Induction:
- Definition: A supervised learning method that builds a tree-like model to make decisions based on data features.
- Process: Recursively partitions the dataset by selecting the best attribute at each node.
- Split Criteria: Uses metrics like *Information Gain*, *Gini Index*, or *Gain Ratio* to choose the best attribute for splitting.
- Nodes:
    - Root Node: Topmost node containing the entire dataset.
    - Internal Nodes: Represent tests on attributes (e.g., `Age > 30?`).
    - Leaf Nodes: Represent the final class label or prediction.
- Stopping Rules: Stops when all data is classified, max depth is reached, or no further gain is possible.
- Advantages: Easy to interpret, handles both numeric/categorical data, and requires little pre-processing.
- Disadvantages: Prone to overfitting; small data changes can alter the tree significantly.
- Solutions: Uses pruning (removing weak branches) to improve generalization.
- Algorithms: Includes `ID3`, `C4.5`, and `CART`.

Attribute Selection:
- Attribute selection identifies which feature best splits the data at each node. The goal is to select the attribute that creates the purest child nodes (nodes with mostly one class).

---
## Explain the concept of information gain and Gini value used in the decision tree algorithm.
## Information Gain
- Based on: Entropy (measure of randomness or impurity).
- Goal: Measures the reduction in uncertainty after a split.
- Selection Criterion: Higher Information Gain → Better attribute.
- Used in Algorithms: `ID3`, `C4.5`.
- Formula Concept:
$$
  IG = Entropy(before) - Entropy(after)
$$
- Example: Splitting data by "Outlook" significantly reduces confusion about "Play/No Play" → High Information Gain.

2. Gini Index
- Based on: Impurity of a node.
- Goal: Measures how often a randomly chosen element would be misclassified.
- Selection Criterion: Lower Gini Value → Better split `(0 = Pure, 1 = Impure`).
- Used in Algorithms: CART (Classification and Regression Trees).
- Formula Concept:
$$
  Gini = 1 - \sum (p_i)^2
$$
  (Where \(` p_i` \) is the probability of a class)
- Example: A node containing mostly "`Yes`" results in a very low Gini value, indicating a clean split.

---
## Naïve Bayes Classifier

Definition: A probabilistic machine learning algorithm based on Bayes' Theorem with a strong "`naïve`" assumption that all features are independent of each other given the class label.

Bayes' Theorem:
$$
P(y | X) = \frac{P(X | y) \cdot P(y)}{P(X)}
$$
Where:
- \( P(y | X) \) = Posterior probability of class \( `y` \) given features \( `X` \)
- \( P(X | y) \) = Likelihood (probability of features given class)
- \( P(y) \) = Prior probability of class
- \( P(X) \) = Evidence (normalizing constant)

The "Naïve" Assumption:
$$
P(X | y) = P(x_1 | y) \times P(x_2 | y) \times ... \times P(x_n | y)
$$
Advantages:
- Works well with high-dimensional data (e.g., text classification)
- Requires small training data
- Very fast and scalable
Disadvantages:
- Feature independence assumption is often unrealistic
- Poor performance with correlated features
Applications: Spam filtering, sentiment analysis, document classification.

---
## Simple Linear Regression

Definition: A statistical method that models the relationship between a single independent variable (`X`) and a dependent variable (Y`)` using a straight line.

Equation:
$$
Y = \beta_0 + \beta_1 X + \epsilon
$$
Where:
- \( Y \) = Dependent variable (output / prediction)
- \( X \) = Independent variable (input / feature)
- \( \beta_0 \) = Intercept (value of `Y` when `X` = 0)
- \( \beta_1 \) = Slope (change in `Y` per unit change in X`)`
- \( \epsilon \) = Error term (random noise)

Formula for Slope:
$$
\beta_1 = \frac{\sum (X_i - \bar{X})(Y_i - \bar{Y})}{\sum (X_i - \bar{X})^2}
$$
Assumptions:
1. Linear relationship between `X` and `Y`
2. Independence of errors
3. Homoscedasticity (constant variance of errors)
4. Normality of errors

Example: Predicting house price (`Y`) based on house size in sq. ft. (`X`).
Evaluation Metric: Mean Squared Error (`MSE`) or R-squared (\(`R^2`\)).