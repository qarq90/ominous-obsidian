# DMBI Module 2

## Define data warehouse. Explain data warehouse architecture with a diagram.

A Data Warehouse is a centralized repository that stores integrated, historical, and non-volatile data collected from multiple heterogeneous sources, specifically structured for querying, reporting, and analysis.

Data warehouse architecture:

```text
		┌─────────────────────────────────────────────────────────────┐
		│                    1. DATA SOURCE TIER                       │
		│    Operational DBs  |  Flat Files  |  External Data          │
		└───────────────────────────┬─────────────────────────────────┘
		                            │
		                            ▼
		┌─────────────────────────────────────────────────────────────┐
		│                    2. ETL / STAGING TIER                     │
		│         Extract → Transform (clean, integrate) → Load        │
		└───────────────────────────┬─────────────────────────────────┘
		                            │
		                            ▼
		┌─────────────────────────────────────────────────────────────┐
		│                   3. DATA WAREHOUSE TIER                     │
		│    Central Warehouse → Data Marts (optional)                 │
		│    (Star/Snowflake Schema – Facts & Dimensions)              │
		└───────────────────────────┬─────────────────────────────────┘
		                            │
		                            ▼
		┌─────────────────────────────────────────────────────────────┐
		│                   4. CLIENT / BI TIER                        │
		│    Reports  |  OLAP  |  Data Mining  |  Dashboards           │
		└─────────────────────────────────────────────────────────────┘
```

1. DATA SOURCE TIER:
	- Includes all source systems such as operational databases, flat files, and external feeds.
	- This tier provides raw, unprocessed data needed for business analysis.
2. ETL / STAGING TIER:
	- Extracts data from sources, transforms it by cleaning, validating, and integrating, then loads it into the warehouse. 
	- Prepares consistent, high-quality data.
3. DATA WAREHOUSE TIER:
	- Central repository storing integrated, historical data using star or snowflake schemas. 
	- May include data marts for department-specific reporting and analysis.
4. CLIENT / BI TIER:
	- The top layer where users access data via reports, `OLAP` cubes, dashboards, and mining tools. 
	- This tier delivers insights and decision support.

---
## Give the difference between OLAP and OLTP.

| Factor         | OLAP (Online Analytical Processing) | OLTP (Online Transaction Processing) |
| :------------- | :---------------------------------- | :----------------------------------- |
| Primary Goal   | Analysis & Reporting                | Transaction Processing               |
| Workload       | Complex queries                     | Short updates                        |
| Data Structure | Star/Snowflake schema               | Normalized schema (`3NF`)            |
| Query Type     | Read-heavy (`SELECT`)               | Read/Write balance                   |
| Response Time  | Seconds to minutes                  | Milliseconds                         |
| Data Volume    | Historical, massive                 | Current, limited                     |
| Concurrency    | Low to medium                       | Very high                            |
| Indexing       | Bitmap, composite                   | Primary, foreign key                 |
| Data Updates   | Periodic batch                      | Real-time (`ACID`)                   |
| User Type      | Analysts, managers                  | Clerks, customers                    |

---
## Compare star schema, snowflake schema, star constellation.

| Feature                          | Star Schema                                                                          | Snowflake Schema                                                                                    | Star Constellation (Fact Constellation)                                                                           |
| -------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Definition**                   | One central fact table connected directly to multiple denormalized dimension tables. | A normalized version of star schema; dimension tables are broken into sub-dimensions (snowflaking). | Multiple fact tables sharing common, conformed dimension tables (fact constellation).                             |
| **Normalization**                | Denormalized (dimension tables contain redundant data).                              | Highly normalized (dimension tables are in 3NF or BCNF).                                            | Mixed – facts are usually denormalized; dimensions are often shared and can be either normalized or denormalized. |
| **Structure**                    | ⭐ Fact table in middle, dimensions around it (like a star).                          | ❄️ Fact table in middle, dimensions split into multiple related tables (like a snowflake).          | 🌌 Multiple fact tables (stars) that share dimension tables (like a constellation).                               |
| **Query Performance**            | **Fast** – fewer joins (single join from fact to each dimension).                    | **Slower** – more joins needed to traverse normalized sub-dimensions.                               | **Good** for cross-fact queries – but complexity increases with multiple fact tables.                             |
| **Ease of Use**                  | Simple, intuitive for business users.                                                | More complex due to many tables.                                                                    | Complex – requires understanding of multiple facts and shared dimensions.                                         |
| **Storage Space**                | Higher – data redundancy in dimension tables.                                        | Lower – no redundant data; efficient storage.                                                       | Moderate – depends on number of facts and whether dimensions are shared.                                          |
| **Data Integrity / Maintenance** | Harder to maintain – update anomalies possible (e.g., address change in many rows).  | Easier – changes made in one place (normalized).                                                    | Moderate – shared dimensions ease maintenance; but multiple facts complicate ETL.                                 |
| **Typical Use Case**             | Simple, read-heavy reporting, data marts, OLAP cubes.                                | Complex data warehouse with limited storage, high insert/update activity.                           | Multiple business processes (e.g., sales & inventory) that need to be analyzed together.                          |
| **Example**                      | Fact: Sales. Dims: Date, Product, Store (each flat, denormalized).                   | Fact: Sales. Dims: Product → Category → Supplier (separate tables).                                 | Fact: Sales and Fact: Inventory. Both share Dim_Date and Dim_Product.                                             |

---
## Dimensional Modelling.

Dimensional Modelling is a design technique for data warehouses that structures data into facts and dimensions to make it easy for users to query and analyse. It is widely used in Business Intelligence BI systems.

- Fact Table:
	- Contains quantitative data (measures) such as sales, revenue, or quantity.
	- Linked to dimension tables via foreign keys.
- Dimension Tables:
	- Contain descriptive attributes (who, what, when, where, how).
	- Examples: Customer, Product, Time, Location.
- Schemas Used:
	- Star Schema: Central fact table connected directly to dimension tables.
	- Snowflake Schema: Dimension tables normalized into multiple related tables.
- Advantages:
	- Simplifies complex queries.
	- Improves performance of `OLAP` operations.
	- Provides intuitive structure for business users.

---
## BI Architectures

| Architecture                | Core Approach                                                                                         | Data Movement             | Typical Latency       | Best For                                                           |
| --------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------- | --------------------- | ------------------------------------------------------------------ |
| **Traditional / Waterfall** | Linear, sequential phases (requirements → design → ETL → DW → reporting). Batch processing.           | High (full copies)        | Hours to days         | Stable enterprises with predictable reporting needs                |
| **ETL / Cloud**             | Extract-Transform-Load (or ELT) using cloud storage and compute. Batch or micro-batch.                | Moderate to high          | Minutes to hours      | Modern data teams leveraging cloud scalability                     |
| **Independent Marts**       | Decentralized; each department builds its own mart directly from source systems.                      | Medium (department-level) | Hours                 | Single-department quick wins (but creates silos)                   |
| **Lakehouse**               | Single platform combining data lake (cheap storage, raw data) and data warehouse (ACID, performance). | Moderate                  | Minutes               | Organizations needing both BI and data science on one copy of data |
| **Realtime**                | Stream processing with sub-second latency. Events → stream processor → serving layer.                 | Low (in-memory/streams)   | Sub-second to seconds | Time-sensitive decisions (fraud detection, IoT monitoring)         |