# DMBI Module 1

## Define data mining. Explain the KDD process with a suitable diagram.

Data Mining is the process of discovering meaningful patterns and insights from large datasets using statistical, machine learning and computational techniques. It helps organizations analyse historical data and make data-driven decisions.

Knowledge Discovery in Databases (KDD) is the overall process of extracting meaningful knowledge from large datasets. Data Mining is one step within KDD, focusing on applying algorithms to discover patterns. KDD ensures raw data is transformed into valid, useful, and understandable knowledge.

Steps in KDD Process:
1. Data Selection: Choose relevant data from multiple sources (databases, warehouses, files).
2. Data Cleaning & Pre-processing: Remove noise, handle missing values, correct inconsistencies.
3. Data Transformation / Reduction: Convert data into suitable formats (normalization, aggregation, dimensionality reduction).
4. Data Mining: Apply algorithms (classification, clustering, association rules) to discover patterns.
5. Pattern Evaluation: Assess discovered patterns for validity, usefulness, and novelty.
6. Knowledge Representation: Present results using visualization, reports, rules, or charts for decision-making.

```text
							1. DATA SOURCES
							         │
							         ▼
							2. DATA WAREHOUSE
							         │
							         ▼
							3. PRE-PROCESSING LAYER
							         │
							         ▼
							4. DATA MINING ENGINE
							         │
							         ▼
							5. PATTERN EVALUATION MODULE
							         │
							         ▼
							6. KNOWLEDGE PRESENTATION LAYER
```

KDD Architecture Layers:
1. Data Sources: Operational databases, flat files, external sources. 
2. Data Warehouse: Central repository integrating data from multiple sources.
3. Pre-processing Layer: Cleaning, integration, transformation of raw data.
4. Data Mining Engine: Core algorithms (classification, clustering, regression, association).
5. Pattern Evaluation Module: Validates interestingness of discovered patterns.
6. Knowledge Presentation Layer: Visualization tools, reports, dashboards for end-users.

---
## What is a Decision Support System?

A computer-based system that supports decision-making using data and models
- Helps in solving semi-structured and unstructured problems
- Provides what-if analysis and forecasting
- Supports managers in making informed decisions

Characteristics:
1. Interactive Interface: 
	- The graphical user interface is also user friendly hence users can interact with `DSS` easily in inputting their data and get the desired output.
2. Data Integration: 
	- It gets information from various sources like `DBMS`, data marts, Data warehouses and even data feeds to have complete data when processing data.
3. Support for Semi-structured and Unstructured Decisions: 
	- `DSS` on the other hand is intended for usage in cases where the decision-making process is not highly routinized as in the case of traditional management information systems.
4. Flexibility and Adaptability: 
	- The system can be applied to any type of decision-making environment and is versatile in the sense that it can be modified in exact conformity with the needs of the users or the organization.
5. What-if Analysis: 
	- It helps in what-if analysis where the assumptions or the values of the input variable can be varied to determine the impact of change on the result.
6. Timely and Relevant Information: 
	- `DSS` thus supplies timely and relevant information that can be used by the decision-makers to respond appropriately to requisite and volatile environments.
7. Support for Group Decision Making: 
	- Most of the available `DSS` have group support systems, where more than one person is involved in the decision-making process.

Types:
1. Model-driven DSS
    - *Description:* Uses statistical, financial, or mathematical models for analysis.
    - *Example:* Loan risk assessment
2. Data-driven DSS
    - *Description:* Emphasizes querying, sorting, and analysing large databases.
    - *Example:* Sales performance dashboard
3. Communication-driven DSS
    - *Description:* Supports group collaboration and shared decision-making.
    - *Example:* Executive meeting support system
4. Document-driven DSS
    - *Description:* Manages, retrieves, and analyses unstructured documents.
    - *Example:* Legal case research system
5. Knowledge-driven DSS
    - *Description:* Incorporates expert systems, rules, or AI logic.
    - *Example:* Medical diagnosis support