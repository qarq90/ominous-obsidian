## Simple Reflex Agent vs Model-Based Reflex Agent

| Factor                | Simple Reflex Agent      | Model-Based Reflex Agent       |
| --------------------- | ------------------------ | ------------------------------ |
| Internal state        | No internal state        | Maintains internal state       |
| World knowledge       | Only current percept     | Uses world model               |
| Decision basis        | Condition-action rules   | State + rules                  |
| Sensor history        | Ignores past             | Tracks unobserved aspects      |
| Handling partial info | Fails often              | Works better                   |
| Complexity            | Very low                 | Moderate                       |
| Example               | Thermostat, light switch | Autonomous car, robot explorer |

---

## Uniform Cost Search vs Best First Search

| Factor | Uniform Cost Search | Best First Search |
| --- | --- | --- |
| Search type | Uninformed (blind) | Informed (heuristic) |
| Cost handling | Uses path cost | Uses heuristic estimate |
| Expansion priority | Lowest cumulative cost | Lowest heuristic value |
| Completeness | Yes (finite costs) | Not guaranteed |
| Optimality | Always optimal | Not optimal |
| Memory usage | High (frontier storage) | High (open list) |
| Example | Shortest path in map | Greedy route finder |

---

##  Informed vs Uninformed Search + A*

| Factor        | Uninformed Search | Informed Search  | A* Algorithm                |
| ------------- | ----------------- | ---------------- | --------------------------- |
| Heuristic use | No heuristic      | Uses heuristic   | Yes, uses f(n) = g(n)+h(n)  |
| Efficiency    | Less efficient    | More efficient   | Very efficient              |
| Optimality    | BFS/UCSS optimal  | Not always       | Yes (admissible heuristic)  |
| Completeness  | BFS/DFS complete  | Often incomplete | Yes                         |
| Memory need   | High (BFS)        | Moderate         | High                        |
| Example       | BFS, DFS, UCS     | Greedy BFS, A*   | Pathfinding in games        |
| Category      | Uninformed        | Informed         | Informed (heuristic search) |

---

## Unification vs Skolemization

| Factor | Unification | Skolemization |
| --- | --- | --- |
| Purpose | Match logical terms | Eliminate existential quantifiers |
| Operation type | Syntactic substitution | Quantifier removal |
| Output | Most general unifier | Skolem function/constant |
| Preserves satisfiability | Yes | Yes (but not equivalence) |
| Used in | Resolution, Prolog | Converting to CNF |
| Replaces variables | Variable to term | Existential to constant/function |
| Example | unify(P(x), P(a)) = {x/a} | ∃x P(x) → P(c) |

---

## Data Scientist vs Big Data Professional vs Data Analyst

| Factor | Data Scientist | Big Data Professional | Data Analyst |
| --- | --- | --- | --- |
| Primary focus | Predictive modeling | Distributed systems | Descriptive analytics |
| Tools | Python, R, SQL | Hadoop, Spark, Kafka | Excel, SQL, Tableau |
| Skill level | Advanced ML/stats | Cluster management | Statistical basics |
| Output | Models, algorithms | Data pipelines | Reports, dashboards |
| Data size | Medium to large | Very large (PB) | Small to medium |
| Question type | Why & predict | How to store/process | What happened |
| Example role | Churn prediction | Spark streaming engineer | Sales dashboarding |

---

## Data Science vs Business Analytics vs Big Data

| Factor       | Data Science             | Business Analytics   | Big Data               |
| ------------ | ------------------------ | -------------------- | ---------------------- |
| Core goal    | Discover insights        | Drive decisions      | Handle volume          |
| Data volume  | Large                    | Small/medium         | Very large             |
| Techniques   | ML, DL, statistics       | Excel, SQL, BI tools | Distributed computing  |
| Output       | Predictive models        | KPIs, reports        | Infrastructure         |
| Example use  | Recommendation system    | Sales forecasting    | Clickstream processing |
| Time horizon | Long-term                | Short-term           | Infrastructure-long    |
| Users        | Engineers, statisticians | Managers, analysts   | Data engineers         |

---

## Data Scientist vs Big Data Professional vs Data Analyst

| Factor        | Data Scientist      | Big Data Professional | Data Analyst        |
| ------------- | ------------------- | --------------------- | ------------------- |
| Focus         | Advanced analytics  | Big data infra        | Business reporting  |
| Tools         | Jupyter, TensorFlow | HDFS, MapReduce       | Power BI, Excel     |
| ML skill      | High                | Low                   | Very low            |
| Engineering   | Moderate            | High                  | Low                 |
| Data cleaning | Yes                 | Pipeline level        | Basic               |
| Stakeholder   | Product team        | IT/DevOps             | Business units      |
| Example       | Fraud detection     | Optimize storage      | Monthly sales trend |

---

## Barplot vs Histogram

| Factor            | Barplot          | Histogram           |
| ----------------- | ---------------- | ------------------- |
| Data type         | Categorical      | Continuous          |
| Bars separated    | Yes (gaps)       | No (touching)       |
| X-axis meaning    | Category names   | Binned intervals    |
| Ordering          | Reorderable      | Fixed numeric order |
| Height meaning    | Count or value   | Frequency density   |
| Example           | Car colors sales | Age distribution    |
| Cumulative option | No               | Yes (ogive)         |

---

## Z-Test vs T-Test vs ANOVA

| Factor              | Z-Test                | T-Test                   | ANOVA                    |
| ------------------- | --------------------- | ------------------------ | ------------------------ |
| Sample size         | Large (n>30)          | Small (n<30)             | Any, but balanced        |
| Population variance | Known                 | Unknown                  | Estimated within         |
| Groups compared     | 1 or 2                | 1 or 2                   | 3 or more                |
| Distribution        | Normal                | T-distribution           | F-distribution           |
| Test statistic      | Z-score               | T-statistic              | F-ratio                  |
| Example             | Population mean check | Medicine effect pre/post | Crop yield by fertilizer |
| Pairwise need       | No                    | Optional                 | Post-hoc tests           |

---

## Univariate vs Multivariate EDA

| Factor | Univariate EDA | Multivariate EDA |
| --- | --- | --- |
| Variables analyzed | One variable only | Two or more variables |
| Goal | Understand distribution | Find relationships |
| Graphical tools | Histogram, boxplot | Scatterplot, heatmap |
| Statistical measures | Mean, variance | Correlation, covariance |
| Example question | What is age spread? | Age vs income relation |
| Outlier detection | Possible | In joint space |
| Dimensionality | Low | High (curse of dimension) |

---

## Business Intelligence vs Data Science

| Factor | Business Intelligence | Data Science |
| --- | --- | --- |
| Focus | Past & present | Future prediction |
| Data type | Structured | Unstructured + structured |
| Time horizon | Descriptive/diagnostic | Predictive/prescriptive |
| Tools | Tableau, Power BI | Python, R, MLlib |
| Users | Managers, analysts | Engineers, scientists |
| Output | Dashboards, reports | Models, algorithms |
| Example | Quarterly sales report | Customer churn forecast |

---

## Linear Regression vs Logistic Regression

| Factor            | Linear Regression      | Logistic Regression      |
| ----------------- | ---------------------- | ------------------------ |
| Output type       | Continuous value       | Probability/class        |
| Equation          | y = wx + b             | p = 1/(1+e^-(wx+b))      |
| Loss function     | MSE                    | Log loss (cross-entropy) |
| Range             | (-∞, +∞)               | (0, 1)                   |
| Decision boundary | Not applicable         | Linear in log-odds       |
| Diagram           | Straight line fit      | S-shaped curve (sigmoid) |
| Example           | House price prediction | Email spam detection     |

---

## SVM vs Logistic Regression

| Factor | SVM | Logistic Regression |
| --- | --- | --- |
| Core principle | Maximize margin | Maximize likelihood |
| Output | Class label | Probability |
| Kernel trick | Yes (nonlinear) | No (linear only) |
| Overfitting control | Regularization parameter C | L1/L2 penalty |
| Outlier sensitivity | Low (support vectors) | Moderate |
| Performance high-dim | Excellent | Moderate |
| Example | Image classification | Credit risk scoring |

---

## Linear Regression vs Logistic Regression

| Factor             | Linear Regression    | Logistic Regression     |
| ------------------ | -------------------- | ----------------------- |
| Dependent var      | Continuous           | Categorical             |
| Formula            | y = β₀ + β₁x         | log(p/(1-p)) = β₀ + β₁x |
| Error distribution | Normal               | Binomial                |
| Estimation         | OLS                  | MLE                     |
| Interpretation     | Slope change         | Odds ratio              |
| Diagram            | Straight line        | Sigmoid curve           |
| Example            | Temperature vs sales | Pass/fail prediction    |

---

## Linear Regression vs Logistic Regression

| Factor              | Linear Regression | Logistic Regression |
| ------------------- | ----------------- | ------------------- |
| Response type       | Quantitative      | Binary/categorical  |
| Model form          | Linear equation   | Logit function      |
| Residuals           | Homoscedastic     | Not applicable      |
| R-squared           | Used              | Pseudo R-squared    |
| Coefficient meaning | Unit change in y  | Log-odds change     |
| Diagram type        | Scatter + line    | Probability curve   |
| Example             | Fuel efficiency   | Tumor malignant?    |
