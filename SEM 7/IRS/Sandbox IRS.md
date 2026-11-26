## Module 0: Prerequisite (Indexing and Searching Algorithms)

**Q. Apply the Boyer-Moore algorithm to construct the bad match table and find the index of the given pattern in the string below, showing all steps.**

**String: STUDENTS ARE SMART I LIKE SMART STUDENTS** 
**Pattern: SMART**. 

The **Boyer-Moore algorithm** is a fast string-matching algorithm that scans the pattern from **right to left** against a window of the text and uses a **bad match table** (bad-character shift table) to skip alignments safely upon a mismatch.

**Step 1: Construct the Bad Match Table**
- **Pattern (`P`)**: `S M A R T` (length $m = 5$, indices $0$ to $4$).
- **Shift Formula**: For any character `c` at index $i$ ($0 \le i < m - 1$), $\text{shift}(c) = m - 1 - i$. For any other character (`*` / default), $\text{shift}(*) = m = 5$.
  - `'S'` at index $0$: $5 - 1 - 0 = 4$
  - `'M'` at index $1$: $5 - 1 - 1 = 3$
  - `'A'` at index $2$: $5 - 1 - 2 = 2$
  - `'R'` at index $3$: $5 - 1 - 3 = 1$
  - `'T'` is at the last index ($4$), so default shift $5$ applies unless overridden.

| Character | `S` | `M` | `A` | `R` | Any Other (`*`) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Shift Value** | `4` | `3` | `2` | `1` | `5` |

**Step 2: Search Trace (0-Based Text Indices)**
- **Text (`T`)**: `S T U D E N T S _ A R E _ S M A R T _ I _ L I K E _ S M A R T _ S T U D E N T S` (length $39$).

**Iteration 1 (Window at text indices `0..4`: `S T U D E`)**
- Compare right-to-left from pattern index `4` (`'T'`) against text index `4` (`'E'`).
- Mismatch at right end: `'E'` vs `'T'`; `'E'` is not in `S M A R`, so shift by `5`.
- New window starts at index $0 + 5 = 5$.

**Iteration 2 (Window at text indices `5..9`: `N T S _ A`)**
- Compare at index `9` (`'A'`) vs pattern index `4` (`'T'`).
- Mismatch: `'A'` vs `'T'`; in bad match table, $\text{shift}('A') = 2$.
- New window starts at index $5 + 2 = 7$.

**Iteration 3 (Window at text indices `7..11`: `S _ A R E`)**
- Compare at index `11` (`'E'`) vs pattern index `4` (`'T'`).
- Mismatch: `'E'` vs `'T'`; default shift for `'E'` is `5`.
- New window starts at index $7 + 5 = 12$.

**Iteration 4 (Window at text indices `12..16`: `_ S M A R`)**
- Compare at index `16` (`'R'`) vs pattern index `4` (`'T'`).
- Mismatch: `'R'` vs `'T'`; in bad match table, $\text{shift}('R') = 1$.
- New window starts at index $12 + 1 = 13$.

**Iteration 5 (Window at text indices `13..17`: `S M A R T`)**
- Compare right-to-left: index `17` (`'T'`), `16` (`'R'`), `15` (`'A'`), `14` (`'M'`), `13` (`'S'`) all match `S M A R T`.
- **Match found at index `13`** (1-based position `14`).

**Iteration 6 (Continue Search for Next Occurrence — Shift by `5`)**
- After a full match at index `13`, shift by `5` to index $13 + 5 = 18$ (`_ I _ L`).
- Compare at index `22` (`'L'`) vs `'T'`; `'L'` is not in pattern, so shift by `5` to index `23` (`I K E _ S`).

**Iteration 7 (Window at text indices `23..27`: `I K E _ S`)**
- Compare at index `27` (`'S'`) vs `'T'`; $\text{shift}('S') = 4$.
- New window starts at index $23 + 4 = 27$.

**Iteration 8 (Window at text indices `27..31`: `S M A R T`)**
- Compare right-to-left: index `31` (`'T'`), `30` (`'R'`), `29` (`'A'`), `28` (`'M'`), `27` (`'S'`) all match `S M A R T`.
- **Second match found at index `27`** (1-based position `28`).

**Final Answer:**
- Pattern `SMART` occurs at **0-based indices `13` and `27`** (1-based positions **`14` and `28`**).

---

///
## Module I: Introduction

**Q. Discuss Objective of IRS (5 marks, Dec 2024)** 
**Q. Discuss Objective of IRS (5 marks, May 2024)** 
**Q. Recall objectives of Information Retrieval Process (5 marks, May 2025)** 

**Information Retrieval System (IRS)** is a system designed to collect, organize, store, and retrieve information that matches user queries from large-scale data collections.

- **Retrieve Required Information**: The core objective is to promptly locate and deliver information needed by users or document surrogates that partially or fully match their queries
- **Organize and Index Information Sources**: Process and index information sources through classification, metadata, and other methods to establish a foundation for efficient retrieval
- **Match User Queries**: Analyze user search statements and match them against the stored database to identify relevant records
- **Rank and Present Results**: Use ranking algorithms to score the relevance of retrieved documents and present the most relevant results to users first
- **Support Multimedia and Multi-type Data**: In addition to text, modern IRS also handles the organization, storage, and retrieval of audio, images, video, and other multimodal information
- **Adjust Based on Feedback**: Improve system performance and retrieval effectiveness based on user feedback
- **Minimize user overhead**: Reduce the total time a user spends on query formulation, execution, and scanning results to find needed information.
- **Ensure fast search performance**: Design the system so that searching through the database takes minimal time and effort.
- **Provide user-friendly interface**: Offer an accessible search interface with clear options such as keyword, author, title, and Boolean searches.
- **Balance precision and recall**: Maximize both the accuracy of retrieved results (precision) and the completeness of retrieval (recall).

---

**Q. Differentiate between Data Retrieval and Information Retrieval (5 marks, Dec 2025)** 
**Q. Differentiate between Information versus Data Retrieval (5 marks, May 2025)** 

| Factor           | Data Retrieval                                   | Information Retrieval                                        |
| ---------------- | ------------------------------------------------ | ------------------------------------------------------------ |
| **Definition**   | Retrieves exact data from structured databases   | Retrieves relevant information from unstructured collections |
| **Data Type**    | Handles structured, well-defined data fields     | Handles unstructured text, documents, multimedia             |
| **Query Nature** | Precise queries with exact match required        | Fuzzy queries with relevance-based matching                  |
| **Matching**     | Exact match determines retrieval success         | Partial, probabilistic, or best-match retrieval              |
| **Result**       | Single correct answer or exact records as needed | Ranked list of potentially relevant documents                |
| **Ambiguity**    | No ambiguity, deterministic results              | Ambiguity handled via relevance ranking                      |
| **Evaluation**   | Measured by precision and recall                 | Measured by relevance, precision, recall                     |
| **User Role**    | User formulates structured queries               | User expresses information need loosely                      |
| **Example**      | SQL query on employee database                   | Google search returning ranked web pages                     |

---

**Q. Explain the Retrieval Process with neat labelled diagram (5 marks, Dec 2025)** 

**Retrieval Process**: The retrieval process is the sequence of steps through which a user's information need is translated into a query, matched against stored documents, and returned as ranked relevant results.

**Steps:**
- **Information Need**: User recognizes a gap requiring specific information.
- **Query Formulation**: Need is expressed as keywords or search statement.
- **Query Preprocessing**: Query is tokenized, stopwords removed, terms stemmed.
- **Document Preprocessing**: Documents similarly processed and indexed offline.
- **Indexing**: Inverted index built for fast term-to-document mapping.
- **Query Representation**: Query converted into structured form (vector/terms).
- **Matching**: Query representation compared with index using similarity measure.
- **Ranking**: Results ordered by relevance score for presentation.
- **Feedback Loop**: User feedback refines query and improves later retrievals.

---

**Q. List and define different parameters to judge the quality of information (5 marks, May 2023)** 

Information quality is judged by parameters that evaluate the trustworthiness, usefulness, and reliability of a piece of information based on its source, content, and presentation .

- **Authority**: The source's author or publisher is identifiable and credible in the field.
- **Accuracy**: The information is correct, error-free, and provides a true description of reality.
- **Objectivity**: The content is presented impartially, without bias or commercial motive.
- **Currency**: The information is up-to-date and recent enough for the intended purpose.
- **Coverage**: The information is complete and covers the topic's breadth and depth adequately.
- **Reliability**: The source can be trusted to provide consistent and dependable information.
- **Verifiability**: The information is backed by evidence, citations, or transparent methods.
- **Relevance**: The information directly addresses the user's specific need or question.
- **Clarity**: The information is presented in a clear, logical, and easy-to-understand manner.

---

**Q. Different types of Information Systems (short note) (10 marks, May 2025)** 

An information system is an integrated set of components like hardware, software, data, people, and procedures that collects, processes, stores, and disseminates information to support decision-making and control in an organization. 
Different types of information systems serve different organizational levels and functional needs, typically classified by the management hierarchy they support.

- **Transaction Processing System (TPS)**: Records and processes daily routine transactions at the operational level, such as sales, payroll, and reservations.
- **Office Automation System (OAS)**: Supports data workers by managing documents, scheduling, and communication through tools like word processing and email.
- **Knowledge Work System (KWS)**: Provides specialized tools for knowledge workers to create and integrate new knowledge into the business.
- **Management Information System (MIS)**: Serves middle management by generating summary and exception reports from TPS data for routine monitoring.
- **Decision Support System (DSS)**: Combines data and analytical models to support semi-structured decision-making for managers.
- **Executive Support System (ESS)**: Provides top executives with aggregated, graphical information from internal and external sources for strategic decisions.
- **Expert System (ES)**: Encodes human expertise into a knowledge base to provide advice or diagnose problems in specific domains.
- **Enterprise Resource Planning (ERP)**: Integrates core business processes such as finance, HR, and supply chain into a single unified system across the organization.
- **Customer Relationship Management (CRM)**: Manages interactions with customers to improve relationships, sales, and service through centralized data.
- **Supply Chain Management (SCM)**: Facilitates information sharing with suppliers and distributors to optimize sourcing, production, and delivery.

---

///
## Module II: IR Models

**Q. Explain the taxonomy of Information retrieval model with classification diagram (10 marks, Dec 2023)** 
**Q. Show taxonomy of IR models and recall browsing models in detail (10 marks, May 2025)** 

An **IR Model** defines how documents and user queries are represented mathematically and how the relevance between them is computed.

**A. Classic Models**
- Treat each document as a bag of index terms (keywords).
- **Boolean Model:** Based on set theory and Boolean algebra (`AND`, `OR`, `NOT`). Gives binary output (relevant or not) with no partial matching or ranking.
- **Vector Space Model (VSM):** Represents documents and queries as vectors in a multi-dimensional space. Uses term weights (**TF-IDF**) and **Cosine Similarity** to rank documents.
- **Probabilistic Model:** Estimates the probability that a document is relevant to a query using probability theory (e.g., **BM25**, Binary Independence Model).

**B. Set-Theoretic Models**
- Extend the classic Boolean model to overcome strict binary matching.
- **Fuzzy Set Model:** Assigns a degree of membership between `0` and `1` for each term in a document, enabling partial matching and ranking.
- **Extended Boolean Model:** Combines Boolean query structure with vector space weighting using p-norm distance calculations.

**C. Algebraic Models**
- Overcome the term-independence assumption of VSM by capturing term relationships.
- **Generalized Vector Space Model (GVSM):** Models correlations between index terms using `minterm` vectors derived from document co-occurrence.
- **Latent Semantic Indexing (LSI):** Uses **Singular Value Decomposition (SVD)** to map high-dimensional term-document matrices into a lower-dimensional concept space, solving synonymy and polysemy.
- **Neural Network Model:** Uses interconnected nodes (query terms, document terms, documents) to spread activation signals and rank results.

**D. Structured Text Models**
- Exploit document layout and hierarchy (chapters, sections, titles) instead of treating text as flat.
- **Non-Overlapping Lists:** Divides text into separate, non-overlapping structural regions indexed independently.
- **Proximal Nodes:** Allows overlapping hierarchical structures (e.g., paragraphs inside sections) and queries based on node proximity.

**E. Browsing Models**
- Designed for exploratory search where users navigate without a formal query.
- **Flat Browsing:** Users scroll through a flat list or space of documents.
- **Structure-Guided Browsing:** Navigates through a hierarchical tree, folder system, or table of contents.
- **Hypertext Model:** Connects documents as nodes via hyperlinks for non-linear navigation (basis of the Web).

**Browsing Models and their working:**

1. **Flat Browsing**
	- **Structure:** Arranges all documents in a single flat list or 2D space without any hierarchy or links between items.
	- **Navigation:** Users scan items linearly or move across a visual map, inspecting documents one by one to find relevance.
	- **Limitation:** Simple to build, but users quickly lose context and feel overwhelmed when browsing very large collections.
	- **Example:** Scrolling sequentially through a single unorganized folder of files or standard search result pages.

2. **Structure-Guided Browsing**
	- **Structure:** Organizes documents into a strict hierarchical tree, nested directory, or structured table of contents.
	- **Navigation:** Users start at a broad root topic and drill down step-by-step through narrower sub-categories to target files.
	- **Benefit:** Reduces disorientation using clear path cues, though rigid trees make multi-topic items hard to classify.
	- **Example:** Navigating an e-commerce menu like Home > Electronics > Mobiles > Smartphones or computer file folders.

3. **Hypertext Model**
	- **Structure:** Models documents as interconnected nodes joined by directed hyperlinks inside a non-linear graph network.
	- **Navigation:** Users read a node and click embedded links to jump freely between related topics without a fixed sequence.
	- **Limitation:** Highly flexible for associative exploration, but users often suffer from the "lost in hyperspace" problem.
	- **Example:** Exploring interconnected Wikipedia articles or surfing pages across the World Wide Web via clickable links.

---

**Q. Explain Boolean Models in detail with example (10 marks, May 2025)** 
**Q. Compare Boolean model and vector model (5 marks, Dec 2023)** 

The **Boolean Information Retrieval Model** is a classic IR model based on set theory and Boolean algebra. It represents documents and queries using sets of index terms and retrieves documents using Boolean operators.

**Features of Boolean Model**

- Documents are represented as sets of keywords or index terms.
- Queries are formulated using Boolean operators AND, OR, and NOT.
- It uses an exact matching technique to retrieve documents.
- Each document is classified as either relevant (1) or non-relevant (0).
- It does not provide relevance-based ranking of results.

**Boolean Operators**

**1. AND Operator (∩)**
- Retrieves documents containing both specified keywords.
- Example: `Computer AND Science` retrieves documents containing both terms.

**2. OR Operator (∪)**
- Retrieves documents containing either one or both specified keywords.
- Example: `Computer OR Science` retrieves documents containing either term.

**3. NOT Operator (−)**
- Retrieves documents containing the first keyword but excluding the second keyword.
- Example: `Computer NOT Science` retrieves documents containing Computer but not Science.

**Working of Boolean Model**
1. **Document Representation:** Documents are represented as sets of keywords.
2. **Query Formulation:** Users enter search queries using AND, OR, and NOT operators.
3. **Query Processing:** The system processes the Boolean expression.
4. **Document Matching:** It compares query terms with indexed document terms.
5. **Result Retrieval:** Documents satisfying the Boolean expression are retrieved.

**Example**

Consider the following documents:

|Document|Content|
|---|---|
|D1|Computer Science|
|D2|Computer Networks|
|D3|Science Technology|
|D4|Computer Science Technology|

**Query: Computer AND Science**
The system retrieves documents containing both Computer and Science.

**Result:**
- D1 – Computer Science: Relevant
- D2 – Computer Networks: Not relevant
- D3 – Science Technology: Not relevant
- D4 – Computer Science Technology: Relevant

| Factor             | Boolean Model                        | Vector Model                             |
| ------------------ | ------------------------------------ | ---------------------------------------- |
| **Foundation**     | Set theory and Boolean algebra       | Vector space and linear algebra          |
| **Representation** | Documents as sets of terms           | Documents as term-weight vectors         |
| **Query Form**     | Boolean expression with AND/OR/NOT   | Natural language terms with weights      |
| **Matching**       | Exact match, binary yes/no           | Partial match via similarity measure     |
| **Ranking**        | No ranking, arbitrary order          | Ranked by cosine similarity score        |
| **Term Weighting** | All terms equally weighted           | TF-IDF weighted terms                    |
| **Output Size**    | Often too few or too many            | Controlled by similarity threshold       |
| **User Skill**     | Requires expertise in query logic    | Easy, intuitive natural language queries |
| **Main Weakness**  | No relevance ranking, rigid matching | Assumes term independence, less precise  |

---

**Q. Explain Classic Information Retrieval models (5 marks, May 2023)** 

Classic Information Retrieval (IR) models are formal frameworks used to represent documents and queries and to rank documents based on their relevance to a user's query. In these models, each document is represented as a set of representative keywords called index terms.

**Boolean Model**
- Based on set theory and Boolean algebra. Documents and queries are represented as sets of index terms.
- **Query Formulation**: Queries are expressed as Boolean expressions using operators like AND, OR, and NOT.
- **Retrieval Strategy**: Uses a binary decision criterion—a document is either relevant (1) or non-relevant (0) based on whether it satisfies the Boolean expression.
- **Limitation**: Does not provide partial matching or relevance ranking of retrieved documents, often leading to either too few or too many results.

**Vector Space Model (VSM)**
- Based on linear algebra. Both documents and queries are represented as t-dimensional vectors in a vector space, where t is the total number of index terms.
- **Term Weighting**: Terms are assigned non-binary weights (commonly calculated using TF-IDF: Term Frequency–Inverse Document Frequency) to reflect their importance.
- **Similarity Calculation:** Cosine Similarity = Dot Product / (Magnitude of Document × Magnitude of Query)

$${ \text{Cosine Similarity}= \frac{\text{Dot Product}} {\text{MD}\times\text{MQ}} }$$

**Where:**
- **Dot Product** = Dot product of document and query vectors.
- **MD** = Magnitude of Document (Length of the document vector)
- **MQ** = Magnitude of Query (Length of the query vector)
- **Advantage**: Allows partial matching and ranks retrieved documents in decreasing order of similarity.

**Probabilistic Model**
- Based on probability theory. It operates on the Probability Ranking Principle (PRP), which states that documents should be ranked in decreasing order of their probability of being relevant to the user's information need.
- **Estimation**: Estimates the probability $P(R \vert{} d_j)$ that a document $d_j$ belongs to the relevant set R versus the non-relevant set R̄.
- **Iterative Refinement**: Often starts with an initial guess of relevant documents and uses user relevance feedback (e.g., via the Okapi BM25 or Binary Independence Model) to iteratively improve probability estimates.

---

**Q. What is the significance of tf and idf? How can you calculate tf and idf in a vector model? (10 marks, Dec 2023)** 

In the **Vector Space Model (VSM)** of Information Retrieval (IR), documents and queries are represented as vectors of term weights, and **TF (Term Frequency)** and **IDF (Inverse Document Frequency)** are combined into **TF-IDF** to measure how important a term is to a specific document within a collection.

**Significance of TF and IDF:**
- **TF (Term Frequency)**: Captures intra-document importance; a term appearing often in a document likely reflects its local topic relevance.
- **IDF (Inverse Document Frequency)**: Captures term rarity across the corpus; rare terms carry higher discriminative power than ubiquitous words.
- **Combined TF-IDF Weight**: Rewards terms that are frequent in a given document yet rare across the collection, down-weighting common terms.
- **Vector Space Ranking**: Enables weighted term vectors so similarity metrics like **Cosine Similarity** rank relevant documents higher.

**Calculating TF in a Vector Model:**
- **Raw Term Frequency**: $\text{tf}_{t,d} = f_{t,d}$, where $f_{t,d}$ is the raw count of term $t$ in document $d$.
- **Log-Normalized TF**: $\text{tf}_{t,d} = 1 + \log_{10}(f_{t,d})$ if $f_{t,d} > 0$, else $0$, dampening diminishing returns of repeated words.
- **Augmented / Normalized TF**: Divides raw count by max term frequency in document $d$ or total terms in $d$ to adjust for document length.

**Calculating IDF in a Vector Model:**
- **Standard IDF**: $\text{idf}_t = \log_{10}\left(\frac{N}{\text{df}_t}\right)$, where $N$ is total documents in the collection and $\text{df}_t$ is documents containing term $t$.
- **Smoothed IDF**: $\text{idf}_t = \log_{10}\left(\frac{N}{1 + \text{df}_t}\right) + 1$ or $\log_{10}\left(\frac{N + 1}{\text{df}_t + 1}\right) + 1$, avoiding division by zero or negative/zero weights for unseen terms.
- **TF-IDF Term Weight**: Computed as $w_{t,d} = \text{tf}_{t,d} \times \text{idf}_t$ for each index dimension $t$ in document vector $\vec{v}_d$.

**Example Calculation:**
- Suppose $N = 100$ documents, term `"index"` appears $3$ times in `D1` ($f = 3$) and in $10$ documents total ($\text{df} = 10$).
- **Log TF**: $\text{tf} = 1 + \log_{10}(3) \approx 1.477$; **IDF**: $\text{idf} = \log_{10}(100 / 10) = 1.0$.
- **TF-IDF Weight**: $1.477 \times 1.0 = 1.477$ as the component value for `"index"` in `D1`'s vector.

---

**Q. Explain ranking and similarity measures with suitable example (10 marks, Dec 2023)** 

In Information Retrieval (IR), **ranking** orders retrieved documents by estimated relevance to a user query, while **similarity measures** quantify how closely a document's representation matches a query (or another document) in a vector or set space.

**Role of Ranking in IR:**
- **Relevance Ordering**: Places the most relevant documents at the top of search results so users do not scan entire collections.
- **Score Computation**: Assigns a numeric relevance score to each candidate document using term weights, similarity metrics, or probabilistic/learning models.
- **Top-$k$ Selection**: Sorts scored documents in descending order of similarity (or ascending order of distance) and returns the top-$k$ matches.

**Common Similarity & Distance Measures:**
- **Cosine Similarity**: Measures the cosine of the angle between query vector $\vec{q}$ and document vector $\vec{d}$, normalizing for document length ($\text{sim}(\vec{q}, \vec{d}) = \frac{\vec{q} \cdot \vec{d}}{\|\vec{q}\| \|\vec{d}\|} \in [0, 1]$ for non-negative weights).
- **Inner / Dot Product**: Computes $\sum_t w_{t,q} \cdot w_{t,d}$; simple and fast, but favors longer documents with higher term frequencies.
- **Euclidean Distance**: Measures straight-line geometric distance $\sqrt{\sum_t (w_{t,q} - w_{t,d})^2}$ in vector space; smaller distance means higher similarity.
- **Jaccard Coefficient**: Measures set overlap between query terms $Q$ and document terms $D$ as $\frac{|Q \cap D|}{|Q \cup D|}$, ignoring term frequency and weight magnitudes.

**Example (Cosine Similarity & Ranking):**
Consider query `Q` (`"data retrieval"`) and two documents (`D1`, `D2`) over terms `[data, retrieval, indexing]` using simple TF-IDF-like weights:
- **Query Vector $\vec{q}$**: `[1, 1, 0]` $\Rightarrow \|\vec{q}\| = \sqrt{1^2 + 1^2 + 0^2} = \sqrt{2} \approx 1.414$
- **Document `D1` Vector $\vec{d}_1$**: `[2, 1, 1]` $\Rightarrow \|\vec{d}_1\| = \sqrt{2^2 + 1^2 + 1^2} = \sqrt{6} \approx 2.449$
- **Document `D2` Vector $\vec{d}_2$**: `[1, 0, 2]` $\Rightarrow \|\vec{d}_2\| = \sqrt{1^2 + 0^2 + 2^2} = \sqrt{5} \approx 2.236$

**Similarity & Ranking Steps:**
- **Score for `D1`**: $\vec{q} \cdot \vec{d}_1 = (1)(2) + (1)(1) + (0)(1) = 3$; $\text{cos}(\vec{q}, \vec{d}_1) = \frac{3}{1.414 \times 2.449} \approx \frac{3}{3.464} \approx 0.866$.
- **Score for `D2`**: $\vec{q} \cdot \vec{d}_2 = (1)(1) + (1)(0) + (0)(2) = 1$; $\text{cos}(\vec{q}, \vec{d}_2) = \frac{1}{1.414 \times 2.236} \approx \frac{1}{3.162} \approx 0.316$.
- **Final Ranking**: Rank `D1` (`0.866`) above `D2` (`0.316`) because `D1` shares both query terms and has a smaller angular deviation from $\vec{q}$.

---

**Q. Vector Model Ranking Problem (10 marks, Dec 2024)**

**Consider the following documents and query:**
- **D1**: I went to the park to play
- **D2**: park is nearby to play
- **D3**: going to the park is fun
- **D4**: park nearby play
- **Q**: park nearby play

**Using the Vector Space Model, rank the documents D1, D2, D3, and D4 in order of relevance to the query Q. Show all steps involved in your computation, including term frequency, inverse document frequency, and similarity calculation.**

**Q. Vector Model Ranking Problem (10 marks, Dec 2025)**

**Consider the following documents and query:**
- **D1**: I went to the park to play
- **D2**: park is nearby to play
- **D3**: going to the park is fun
- **D4**: park nearby play
- **Q**: park nearby play

**Using the Vector Space Model, rank the documents D1, D2, D3, and D4 in order of relevance to the query Q. Show all steps involved in your computation, including term frequency, inverse document frequency, and similarity calculation.**

**Step 1 -- Vectors being defined**
- **Corpus Setup**: Total documents $N = 4$ (`D1`–`D4`) and query `Q` (`"park nearby play"`).
- **Term Dimensions**: Uses $10$ terms `[park, nearby, play, to, the, is, i, went, going, fun]`.
- **D1 Counts**: `park`=1, `nearby`=0, `play`=1, `to`=2, `the`=1, `is`=0, `i`=1, `went`=1, `going`=0, `fun`=0.
- **D2 Counts**: `park`=1, `nearby`=1, `play`=1, `to`=1, `the`=0, `is`=1, `i`=0, `went`=0, `going`=0, `fun`=0.
- **D3 Counts**: `park`=1, `nearby`=0, `play`=0, `to`=1, `the`=1, `is`=1, `i`=0, `went`=0, `going`=1, `fun`=1.
- **D4 & Q Counts**: `park`=1, `nearby`=1, `play`=1, and `0` for all remaining terms.

**Step 2 -- Calculate term frequency (TF)**
- **Formula**: $\text{TF} = 1 + \log_{10}(\text{tf})$ for $\text{tf} > 0$, and $\text{TF} = 0$ for $\text{tf} = 0$.
- **For D1**: `park`=$1$, `nearby`=$0$, `play`=$1$, `to`=$1+1.301$? Wait: $1+\log_{10}(2)=1.301$; `the`=$1$, `i`=$1$, `went`=$1$.
- **TF(D1)**: `(1, 0, 1, 1.301, 1, 0, 1, 1, 0, 0)`.
- **TF(D2)**: `(1, 1, 1, 1, 0, 1, 0, 0, 0, 0)`.
- **TF(D3)**: `(1, 0, 0, 1, 1, 1, 0, 0, 1, 1)`.
- **TF(D4) & TF(Q)**: `(1, 1, 1, 0, 0, 0, 0, 0, 0, 0)`.

**Step 3 -- Calculate inverse term frequency (ITF)**
- **Formula**: $\text{ITF} = \log_{10}(N / N_i)$, where $N = 4$ and $N_i$ is document count for term $i$.
- **ITF(park)**: $\log_{10}(4/4) = 0$.
- **ITF(play) & ITF(to)**: $\log_{10}(4/3) = 0.125$.
- **ITF(nearby), ITF(the) & ITF(is)**: $\log_{10}(4/2) = 0.301$.
- **ITF(i), ITF(went), ITF(going) & ITF(fun)**: $\log_{10}(4/1) = 0.602$.

**Step 4 -- TF × ITF**
- **For D1**: $\mu_1 = (0, 0, 0.125, 0.163, 0.301, 0, 0.602, 0.602, 0, 0)$.
- **For D2**: $\mu_2 = (0, 0.301, 0.125, 0.125, 0, 0.301, 0, 0, 0, 0)$.
- **For D3**: $\mu_3 = (0, 0, 0, 0.125, 0.301, 0.301, 0, 0, 0.602, 0.602)$.
- **For D4**: $\mu_4 = (0, 0.301, 0.125, 0, 0, 0, 0, 0, 0, 0)$.

**Step 5 -- Calculate for the query**
- **Query Terms**: `"park nearby play"` gives $\text{TF}_Q = (1, 1, 1, 0, 0, 0, 0, 0, 0, 0)$.
- **Query Weights**: Multiply $\text{TF}_Q$ by each term's $\text{ITF}$ to get $Z = (0, 0.301, 0.125, 0, 0, 0, 0, 0, 0, 0)$.

**Step 6 -- Calculating cosine similarity**
- **Formula**: $\text{Similarity} = \frac{\text{Dot Product}}{\text{MD} \times \text{MQ}}$, where magnitude is $\sqrt{a_1^2 + a_2^2 + \dots + a_n^2}$.
- **Query Magnitude**: $\text{MQ} = \sqrt{0.301^2 + 0.125^2} = 0.326$.
- **1. Document D1**: $\text{DP}_1 = 0.016$; $\text{MD}(D1) = 0.926$; $S(D1) = \frac{0.016}{0.926 \times 0.326} = 0.052$.
- **2. Document D2**: $\text{DP}_2 = 0.106$; $\text{MD}(D2) = 0.461$; $S(D2) = \frac{0.106}{0.461 \times 0.326} = 0.707$.
- **3. Document D3**: $\text{DP}_3 = 0$; $\text{MD}(D3) = 0.960$; $S(D3) = \frac{0}{0.960 \times 0.326} = 0$.
- **4. Document D4**: $\text{DP}_4 = 0.106$; $\text{MD}(D4) = 0.326$; $S(D4) = \frac{0.106}{0.326 \times 0.326} \approx 1$.

**Step 7 -- Ranking similarities**
- **Final Order**: $D4 > D2 > D1 > D3$.

---

**Q. Vector Space Ranking Problem (10 marks, May 2025)**

**Consider the following documents and query:**
- **D1**: beautiful garden
- **D2**: evening garden time
- **D3**: garden time is beautiful
- **Q**: garden time

**Using the Vector Space Model with TF-IDF weighting and cosine similarity, rank the documents D1, D2, and D3 in order of relevance to the query Q. Show all steps involved in your computation, including term frequency (TF), inverse document frequency (IDF), TF-IDF weights, and cosine similarity calculation.**

**Step 1 -- Vectors being defined**
- **Corpus Setup**: Total documents $N = 3$ (`D1`–`D3`) and query `Q` (`"garden time"`).
- **Term Order**: Uses $5$ normalized terms `[garden, time, beautiful, evening, is]` across vectors.
- **D1 Counts**: `garden`=1, `time`=0, `beautiful`=1, `evening`=0, `is`=0.
- **D2 Counts**: `garden`=1, `time`=1, `beautiful`=0, `evening`=1, `is`=0.
- **D3 Counts**: `garden`=1, `time`=1, `beautiful`=1, `evening`=0, `is`=1.
- **Q Counts**: `garden`=1, `time`=1, `beautiful`=0, `evening`=0, `is`=0.

**Step 2 -- Calculate term frequency (TF)**
- **Formula**: $\text{TF} = 1 + \log_{10}(\text{tf})$ for $\text{tf} > 0$, and $\text{TF} = 0$ for $\text{tf} = 0$.
- **Base Values**: Since every present term has $\text{tf} = 1$, $1 + \log_{10}(1) = 1.000$.
- **TF(D1)**: `(1, 0, 1, 0, 0)`.
- **TF(D2)**: `(1, 1, 0, 1, 0)`.
- **TF(D3)**: `(1, 1, 1, 0, 1)`.
- **TF(Q)**: `(1, 1, 0, 0, 0)`.

**Step 3 -- Calculate inverse document frequency (IDF)**
- **Formula**: $\text{IDF} = \log_{10}(N / N_i)$, where $N = 3$ and $N_i$ is document count for term $i$.
- **ITF(garden)**: $\log_{10}(3/3) = 0$.
- **ITF(time) & ITF(beautiful)**: $\log_{10}(3/2) \approx 0.176$.
- **ITF(evening) & ITF(is)**: $\log_{10}(3/1) \approx 0.477$.

**Step 4 -- TF-IDF weights for documents**
- **Weighting Rule**: Multiply each document's TF vector by $\text{IDF} = (0, 0.176, 0.176, 0.477, 0.477)$.
- **W(D1)**: `(0, 0, 0.176, 0, 0)`.
- **W(D2)**: `(0, 0.176, 0, 0.477, 0)`.
- **W(D3)**: `(0, 0.176, 0.176, 0, 0.477)`.

**Step 5 -- TF-IDF weight for query**
- **Query Terms**: `"garden time"` gives $\text{TF}_Q = (1, 1, 0, 0, 0)$.
- **Query Weight Vector**: $W_Q = (0, 0.176, 0, 0, 0)$ since `garden` has $\text{IDF} = 0$.

**Step 6 -- Calculating cosine similarity**
- **Formula**: $\text{Similarity} = \frac{\text{Dot Product}}{\text{MD} \times \text{MQ}}$, where magnitude is $\sqrt{a_1^2 + a_2^2 + \dots + a_n^2}$.
- **Query Magnitude**: $\text{MQ} = \sqrt{0.176^2} = 0.176$.
- **1. Document D1**: $\text{DP}_1 = 0$; $\text{MD}(D1) = 0.176$; $S(D1) = \frac{0}{0.176 \times 0.176} = 0$.
- **2. Document D2**: $\text{DP}_2 = 0.176^2 = 0.031$; $\text{MD}(D2) = \sqrt{0.176^2 + 0.477^2} \approx 0.508$; $S(D2) = \frac{0.031}{0.508 \times 0.176} \approx 0.346$.
- **3. Document D3**: $\text{DP}_3 = 0.176^2 = 0.031$; $\text{MD}(D3) = \sqrt{0.176^2 + 0.176^2 + 0.477^2} \approx 0.537$; $S(D3) = \frac{0.031}{0.537 \times 0.176} \approx 0.328$.

**Step 7 -- Ranking similarities**
- **Final Order**: $D2 > D3 > D1$.

---

**Q. Explain Probabilistic Retrieval Model. Compare and contrast Belief Network Model and Inference Network Model (10 marks, Dec 2024)** 

**Probabilistic Model**
- Based on probability theory. It operates on the Probability Ranking Principle (PRP), which states that documents should be ranked in decreasing order of their probability of being relevant to the user's information need.
- **Estimation**: Estimates the probability $P(R \vert{} d_j)$ that a document $d_j$ belongs to the relevant set R versus the non-relevant set R̄.
- **Iterative Refinement**: Often starts with an initial guess of relevant documents and uses user relevance feedback (e.g., via the Okapi BM25 or Binary Independence Model) to iteratively improve probability estimates.

| Factor                   | Belief Network Model                    | Inference Network Model                  |
| ------------------------ | --------------------------------------- | ---------------------------------------- |
| Primary Developer        | Ribeiro-Neto and Muntz                  | Turtle and Croft                         |
| Sample Space             | Explicitly defined concept space        | Implicit, less clearly defined           |
| Core Probability         | Uses P(doc\|term) relationship          | Uses P(term\|doc) relationship           |
| Document-Query Status    | Symmetric, both are concepts            | Asymmetric, query is goal                |
| Term Dependence          | Handles term dependencies               | Assumes term independence                |
| Generality Level         | More general, subsumes inference        | Less general, specific structure         |
| Classic Model Coverage   | Subsumes Boolean, vector, probabilistic | Limited to specific inference strategies |
| Ranking Capability       | Can replicate cosine similarity         | Cannot fully replicate cosine            |
| Practical Implementation | Less standard, research-focused         | Implemented in InQuery system            |

---

**Q. Explain the process of Structured Text retrieval model (5 marks, Dec 2024)** 
**Q. What is Structured text retrieval Models? Explain different types with example (10 marks, Dec 2025)** 

**Structured Text Retrieval Models** are IR models that explicitly utilize the **logical and hierarchical structure** of documents alongside their textual content. They allow users to query specific structural components (e.g., chapters, sections, tables, or tags) and combine content-based conditions with structural constraints.

**Process of Structured Text Retrieval**

1. **Document Representation (Parsing Structure):**
    - The system parses the document to identify its logical hierarchy (e.g., `Title` → `Section` → Paragraph) `alongside` its plain text.
    - Structural elements are represented using formalisms like **trees** (`XML`/DOM`),` **directed acyclic graphs (`DAGs`)**, or **regions/spans** (start and end byte/word positions).
2. **Indexing (Content + Structure):**
    - **Text Index:** An inverted index maps each keyword to the documents and exact positions where it occurs.
    - **Structural Index:** A separate or integrated index records the start and end positions (intervals) of every structural unit (e.g., starts at word 1, ends at word 8).
3. **Query Formulation:**
    - The user submits a structured query specifying both **content conditions** (keywords) and **structural constraints** (containment, proximity, or hierarchy).
    - _Example:_ Finding the word `"retrieval"` specifically inside a that has a containing `"models"`.
4. **Query Processing & Matching:**
    - The retrieval engine evaluates content matches against the text index and structural matches against the structural index.
    - It applies structural operators (such as _contains_, _contained-in_, _follows_, or _near_) by comparing the position intervals of keywords with the intervals of structural elements.
5. **Result Extraction & Ranking:**
    - Instead of returning only whole documents, the model returns the exact matching **structural components** (e.g., a specific paragraph or section).
    - Results are ranked based on term weights (like TF-IDF) combined with structural importance (e.g., a match in a scores higher than a match in a footnote).

**1. Non-Overlapping Lists Model**  
Divides a document into flat, non-overlapping text regions (chapters, sections, paragraphs), indexing each type in a separate list.
- Regions in the same list cannot overlap, though different lists can represent different levels of detail.
- Finds regions containing a keyword or regions nested inside another region.
- **Example:** Searching for `"indexing"` strictly within the `"Chapter 4"` list of an e-book.

**2. Proximal Nodes Model**  
Models document structure as a strict hierarchical tree (e.g. `book` → `chapter` → `section`) separated from the text index.
- Evaluates keyword matches first, then filters results using tree relationships (parent, child, ancestor) to find nearby structural nodes.
- Retrieves nodes structurally close ("`proximal`") to matched text.
- **Example:** Finding a node whose contains `"Neural"` and contains `"Backpropagation"`.

**3. Tree Matching (XML Retrieval) Models**  
Treats both the document and the query as labeled trees, primarily used for semi-structured XML and HTML data.
- Combines path expressions (XPath/XQuery) with IR ranking (like BM25F) to score and return matching subtrees, often weighting tags differently (e.g., over ).
- Exact path matching, descendant searches (`//`), and ranked element retrieval.
- **Example:** Using `//article[contains(title, "Cloud")]//section[contains(., "Security")]` to retrieve only relevant tags.

---

**Q. Explain Object Oriented and Object Relational DBMS (10 marks, May 2023)** 

**Object-Oriented Database Management System (OODBMS)**

An Object-Oriented Database Management System (OODBMS) is a database system that stores data in the form of objects, similar to object-oriented programming languages such as Java, C++ and Python.
It combines the features of object-oriented programming and database management systems.

**Features of OODBMS:**
1. **Objects:** Data is stored as objects containing both attributes (data) and methods (functions).
2. **Classes:** Objects are grouped into classes based on their common properties.
3. **Inheritance:** One class can inherit properties and methods from another class.
4. **Encapsulation:** Data and methods are combined into a single unit called an object.
5. **Polymorphism:** The same method can perform different operations depending on the object.
6. **Object Identity:** Each object has a unique identity independent of its values.
7. **Complex Objects:** It can store complex data such as images, audio, video and multimedia.

**Advantages:**
- Handles complex data efficiently.
- Supports code reusability through inheritance.
- Suitable for multimedia and engineering applications.
- Reduces the gap between programming languages and databases.

**Disadvantages:**
- Lacks a universal, standardized query language like SQL (though OQL exists, adoption is limited).
- Steeper learning curve for developers accustomed to relational models.

**Applications**
- Computer-aided design (CAD).
- Multimedia applications.
- Scientific research.
- Artificial intelligence.

**Examples:** ObjectDB, db4o and ObjectStore.

**Object-Relational Database Management System (ORDBMS)**

An Object-Relational Database Management System (ORDBMS) is a database system that combines the features of a traditional Relational DBMS (RDBMS) with object-oriented concepts.
It stores data in tables (rows and columns) while also supporting object-oriented features such as user-defined data types, inheritance and complex objects.

**Features of ORDBMS:**
1. **Tables:** Data is stored in the form of rows and columns like an RDBMS.
2. **User-Defined Data Types:** Users can create their own data types according to requirements.
3. **Inheritance:** Tables or types can inherit properties from other types.
4. **Complex Data Types:** Supports complex data such as images, audio and video.
5. **Functions:** Supports functions and triggers associated with user-defined types.
6. **SQL Support:** Uses SQL to store, retrieve and manipulate data.
7. **Object Identity:** Can support object references to connect related objects.

**Advantages:**
- Combines the benefits of relational and object-oriented databases.
- Supports complex data types.
- Maintains relational database features such as SQL and transactions.
- Provides flexibility and scalability.

**Disadvantages:**
- Increased system complexity and higher storage/processing overhead compared to a pure RDBMS.
- Still has a slight mismatch in how data is structured compared to a pure object-oriented database.

**Applications**
- Banking systems.
- Geographic Information Systems (GIS).
- Enterprise applications.
- Multimedia database applications.

**Examples:** PostgreSQL, Oracle Database and IBM Db2.

| OODBMS                                          | ORDBMS                                                       |
| ----------------------------------------------- | ------------------------------------------------------------ |
| Stores data as objects.                         | Stores data mainly in tables.                                |
| Based on object-oriented concepts.              | Combines relational and object-oriented concepts.            |
| Does not primarily use tables.                  | Uses rows and columns.                                       |
| Object identity is important.                   | Uses primary keys and can support object references.         |
| Supports inheritance and encapsulation.         | Supports user-defined types and inheritance.                 |
| Suitable for complex object-based applications. | Suitable for relational applications requiring complex data. |
| Examples: ObjectDB, db4o.                       | Examples: PostgreSQL, Oracle.                                |

---

**Q. What is flat browsing and hypertext browsing? Explain (10 marks, Dec 2023)** 

**Flat Browsing:**

Flat browsing is a browsing technique in which information is displayed in a simple, sequential or list format. The user navigates through records one by one without following links between related information.

**Features:**
1. Information is displayed in a linear or sequential manner.
2. Users can move from one record to another using options like Next and Previous.
3. It does not provide direct links between related information.
4. It is simple and easy to understand.
5. Users may need to search or scroll through many records to find specific information.
6. It is suitable for simple databases containing structured records.

**Examples:** Photo galleries with "Next/Previous" buttons, step-by-step installation wizards, paginated search results, and basic directory listings.

**Hypertext Browsing:**

Hypertext browsing is a browsing technique in which information is connected through hyperlinks. Users can navigate from one document or information item to another by clicking on links.
It allows non-linear navigation, meaning users can access information in any order.

**Features:**
1. Information is connected through hyperlinks.
2. Users can jump directly from one topic to another.
3. It supports non-linear navigation.
4. It allows easy access to related information.
5. It can contain text, images, audio, video and other multimedia content.
6. It is widely used on the World Wide Web.

**Examples:** The World Wide Web (WWW), Wikipedia articles with embedded cross-references, and modern e-commerce product recommendations.

---

**Q. Define Natural Language with features and applications (5 marks, May 2023)** 
**Q. Write different issues for modeling natural language and find solution for it (10 marks, Dec 2024)**
**Q. Explain Natural language modelling issues and its solution (10 marks, May 2025)** 
**Q. Summarize different issues for modeling natural language (short note) (10 marks, Dec 2025)** 

In an information retrieval (IR) system, **natural language** is everyday human language (written or spoken, such as English or Hindi) used to express search queries and store unstructured text in documents. 
Instead of forcing users to write rigid commands or structured database queries like SQL, natural language lets people ask for information in conversational phrases or full questions.

**Features of Natural Language:**
- **Ambiguity:** A single word or sentence can have multiple meanings depending on the context (e.g., _"bank"_ can mean a financial institution or a river edge).
- **Context-Dependency:** The true meaning of an utterance relies heavily on the surrounding conversation, tone, and shared world knowledge.
- **Dynamic & Evolving:** New words, slang, and grammatical shifts constantly emerge over time, while older terms become obsolete.
- **Redundancy & Flexibility:** Ideas can be expressed in many different syntactic ways while preserving the exact same meaning.
- **Creativity (Productivity):** Humans can combine a finite set of words and grammar rules to generate an infinite number of completely new sentences.

**Applications of Natural Language Processing (NLP):**
- **Machine Translation:** Automatically translating text or speech from one language to another (e.g., Google Translate).
- **Sentiment Analysis:** Determining the emotional tone behind text, widely used in customer feedback and social media monitoring.
- **Virtual Assistants & Chatbots:** Understanding and responding to spoken or typed human queries (e.g., Siri, Alexa, customer support bots).
- **Information Extraction & Summarization:** Automatically pulling key facts or generating concise summaries from large documents.
- **Spam Detection & Autocorrect:** Filtering unwanted emails and predicting or correcting typing errors in real time.

**Modelling Issues and their solution:**
1. **Lexical & Syntactic Ambiguity**
	- **Issue**: Words and sentences often carry multiple meanings or grammatical structures.
	- Solution: Use context-aware Transformers to resolve meaning.
2. **Data Sparsity & Out-of-Vocabulary (OOV) Words**
	- **Issue**: Rare words, slang, and domain terms frequently lack sufficient training data.
	- **Solution**: Apply subword tokenization methods like WordPiece to split rare words.
3. **Long-Range Dependencies**
	- **Issue**: Retaining context across long paragraphs or documents is computationally hard.
	- **Solution**: Use self-attention mechanisms in Transformers to link distant words directly.
4. **Sarcasm, Idioms, & Figurative Language**
	- **Issue**: Literal word meanings often contradict the speaker's actual intended sentiment.
	- **Solution**: Train LLMs on diverse conversational datasets with fine-tuning.
5. **Multilingual & Low-Resource Languages**
	- **Issue**: Most languages lack massive labeled datasets required to train accurate models.
	- **Solution**: Use cross-lingual transfer learning and multilingual models.
6. **Bias, Hallucination, & Ethical Concerns**
	- **Issue**: Models inherit societal biases from training data and fabricate false facts.
	- **Solution**: Apply Retrieval-Augmented Generation (RAG) and data filtering.
7. **Named Entity Recognition (NER)**
	- **Issue**: Identifying names of people, places, organizations, dates, and other entities correctly can be difficult.
	- **Solution**: Use NER techniques and fine-tuned language models to identify and classify entities accurately.
8. **Noise & Spelling Errors**
	- **Issue**: Text often contains spelling mistakes, grammatical errors, abbreviations, and informal language, making processing difficult.
	- **Solution**: Apply text preprocessing techniques such as spell correction, normalization, and noise removal.
9. **Context & Domain Understanding**
	- **Issue**: The same word may have different meanings in different domains, such as medicine, law, and technology.
	- **Solution**: Use domain-specific datasets and fine-tune language models for better contextual understanding.

---

///
## Module III: Query Processing and Operations

**Q. What is the purpose of using keyword-based query? Briefly explain any 3 types of keyword-based queries (10 marks, Dec 2025)** 
**Q. What is the purpose of using keyword based query? Briefly explain any 3 types of keyword based queries (10 marks, May 2024)** 
**Q. What is the purpose of using keyword based query? Briefly explain any 3 types of keyword based queries (10 marks, May 2025)** 
**Q. Illustrate different types of keyword-based queries (5 marks, Dec 2023)** 
**Q. Illustrate different types of keyword-based queries (5 marks, Dec 2024)** 

The primary purpose of using a **keyword-based query** is to retrieve relevant documents, records, or web pages from a database or search engine by matching specific user-entered words (terms) against an indexed collection of text. 
It allows users to find information quickly without needing to know complex query languages (like SQL) or the exact structure of the underlying database.
The system retrieves documents containing these keywords and ranks them by relevance scores. This approach simplifies user interaction while maintaining effective retrieval through statistical ranking methods.

**Purpose of Keyword-Based Queries:**
1. **Simplicity and Ease of Use:** 
	- Keyword queries are easy for users to construct without requiring specialized knowledge of complex query languages or search systems.
	- **Example**: A user searching for `"best smartphones 2024"` can quickly find relevant results without needing detailed syntax.
2. **Efficient Document Matching:** 
	- Keywords directly map to the terms indexed by the system, enabling fast and straightforward matching against stored documents.
	- **Example**: An e-commerce search engine uses the keywords `"laptop under $1000"` to retrieve matching products.
3. **Relevance-Based Retrieval:** 
	- By using keywords, the system identifies and ranks documents based on the occurrence and importance of the terms, such as using TF-IDF or BM25 for relevance scoring.
4. **Flexibility Across Domains:** 
	- Keywords work across diverse systems, including databases, search engines, and AI-driven applications.
	- **Example**: Legal databases respond to keywords like `"contract breach"` to provide relevant case law or statutes.
5. **Customizable Queries:** 
	- Users can fine-tune their searches by adding or removing keywords, using Boolean operators (like `AND`, `OR`, `NOT`), or applying filters for greater precision.
	- **Example**: `"climate change AND policy"` retrieves more targeted results than `"climate change"` alone.

**Types:**
1. **Single-Word Query:**
	- User enters a single term without any operators or modifiers.
	- Matches documents containing that term anywhere in the text.
	- **Example**: `"python"` matches programming, snake, or Monty Python content.
2. **Phrase Query:**
	- User encloses multiple words in quotation marks for exact sequence matching.
	- Matches documents containing the exact adjacent word order specified.
	- **Example**: `"state bank of india"` finds only documents with that precise phrase.
3. **Proximity Query:**
	- User specifies two terms must appear within a defined word distance.
	- Matches documents where terms occur close together even if not adjacent.
	- **Example**: information and retrieval within 5 words finds related concepts near each other.
4. **Boolean Query:**
	- Boolean queries combine keywords using AND, OR and NOT.  
	- They help narrow searches using specific conditions.
	- **Examples**:
		- **AND:** Database AND Management
		- **OR:** Computer OR Laptop
		- **NOT:** Database NOT SQL
5. **Proximity Query:**
	- Users search using simple, natural language sentences.  
	- NLP ranks documents by how closely they match.
	- **Example**: Query = ``"What are the best techniques for information retrieval?"``

---

**Q. State the different types of queries. Explain the pattern matching query concept with an example (10 marks, Dec 2023)** 

**Types of queries:**
1. **Keyword-Based Queries:** Search using single or multiple keywords to retrieve documents containing those terms and rank them based on relevance.
2. **Boolean Queries:** Combine keywords using AND, OR, and NOT operators to include or exclude specific terms and refine search results.
3. **Phrase Queries:** Search for an exact sequence of words in the same order to retrieve documents containing the complete phrase.
4. **Proximity Queries:** Find documents where two or more search terms appear within a specified number of words of each other.
5. **Wildcard Queries:** Use special symbols like * or ? to find different variations of words, including prefixes, suffixes, and partial terms.
6. **Natural Language Queries:** Enter complete questions or sentences in everyday language to retrieve relevant results using NLP techniques.
7. **Fuzzy Queries:** Find words that are similar to the search term by handling spelling mistakes, typing errors, and variations in word formation.

**Pattern Matching:**

Pattern Matching Query is a search technique used in Information Retrieval Systems to find words or documents that match a specified pattern rather than searching for an exact word.
It uses special symbols called wildcards to match different variations of words.

- **Wildcard Symbols:** Systems use placeholders like `*` to match zero or more characters and `?` to match any single character.
- **Regular Expressions:** Use patterns like `[0-9]{4}` to match specific character combinations, such as a four-digit year.
- **Character Range** `[ ]`**:** Matches any one character within a specified range. Example: `colou[rs]` matches colors and colors.
- **Negation** `[ ^ ]`**:** Matches any single character except those specified. Example: `[^0-9]` matches any non-digit character.
- **OR Operator** `|`**:** Matches either of two patterns. Example: `cat|dog` matches cat or dog.
- **Repetition** `{ }`**:** Specifies how many times a character or pattern can repeat. Example: `[0-9]{3}` matches exactly three digits.
- **Optional** `?`**:** Makes the preceding character or pattern optional. Example: `colou?r` matches `color` and `colour`.
- **Start Anchor** `^`**:** Matches a pattern only at the beginning of a string. Example: `^Info` matches words starting with `Info`.
- **End Anchor** `$`**:** Matches a pattern only at the end of a string. Example: `ing$` matches words ending in `ing`.
- **One or More** `+`**:** Matches one or more occurrences of a character. Example: `go+gle` matches `gogle` and `google`.

**Example**
- **Query:** `comput*`
- **Pattern Rule:** Match any term starting with the prefix `comput` followed by zero or more characters.
- **Retrieved Matches:** The IR system expands the pattern against its dictionary and retrieves documents containing **`compute`**, **`computer`**, **`computers`**, **`computing`**, and **`computation`**.

---

**Q. Compare and contrast Proximity Queries and Wildcard Queries (5 marks, May 2024)** 

| Factor          | Proximity Queries                                    | Wildcard Queries                                    |
| --------------- | ---------------------------------------------------- | --------------------------------------------------- |
| Definition      | Finds terms within specified distance in text        | Matches patterns using symbols like asterisk        |
| Purpose         | Captures word relationships and contextual closeness | Handles unknown or variable word forms              |
| Operators used  | NEAR, WITHIN, ADJ, phrase operators                  | Asterisk (*), question mark (?), truncation symbols |
| Matching basis  | Positional distance between query terms              | Character pattern matching against terms            |
| Example query   | "information NEAR system" within 5 words             | "comput*" matches computer, computing, computation  |
| Precision level | High precision, reduces false matches                | Lower precision, may return irrelevant terms        |
| Flexibility     | Rigid distance values must be specified              | Flexible, adapts to spelling variations             |
| Common use      | Legal, patent, and full-text database search         | Dictionary, catalog, and general web search         |
| Limitation      | Requires careful tuning of distance values           | Can produce noisy, over-broad result sets           |

---

**Q. What is User relevance feedback: How this will contribute to get results (10 marks, May 2024)** 
**Q. User relevance feedback (short note) (5 marks, Dec 2023)** 
**Q. User relevance feedback (short note) (5 marks, Dec 2024)** 
**Q. How user relevance feedback model can be applied to improve search results in search recommendation engine (short note) (10 marks, Dec 2025)** 
**Q. Explain Relevance Feedback. Discuss the contribution of relevance feedback for quality IR (10 marks, May 2023)** 

**User Relevance Feedback** is a technique used in Information Retrieval (IR) systems to improve search results based on user feedback.
In this technique, the user identifies which retrieved documents are relevant and which are irrelevant. The system uses this feedback to modify the original query and provide more accurate results.

**Process:**
1. **Query Submission:** The user enters an initial search query to find relevant information from the Information Retrieval System.
2. **Initial Retrieval:** The system processes the query and retrieves a list of matching documents from the database.
3. **Relevance Assessment:** The user examines the retrieved documents and marks them as relevant or irrelevant based on their needs.
4. **Feedback Collection:** The system collects user feedback and identifies useful keywords from relevant and irrelevant documents.
5. **Query Modification:** The system adds useful terms and adjusts existing keyword weights to improve the original search query.
6. **Re-Retrieval:** The system uses the modified query to search again and retrieve more relevant documents.
7. **Iteration:** The user can provide feedback repeatedly until the search results become satisfactory.

**Contribution of Relevance Feedback to Quality IR:**
- **Solves Vocabulary Mismatch:** Identifies synonyms used in relevant documents and adds them to the query to improve recall and retrieve more useful information.
- **Resolves Ambiguity:** Identifies the intended meaning of a search term using feedback and removes unrelated results to improve precision.
- **Reduces User Effort:** Users only need to identify relevant documents instead of creating complex queries or learning technical search operators.
- **Optimizes Term Weighting:** Adjusts the importance of query keywords based on their frequency and significance in relevant documents.
- **Adapts to User Needs:** Continuously modifies the search query based on feedback to match the user's changing interests and information needs.

**Types of Relevance Feedback**

**1. Explicit Relevance Feedback**:
- Users manually mark documents as relevant or irrelevant.
- The system uses this feedback to improve future search results.
- **Example**: Clicking the Like or Dislike option on search results.

**2. Implicit Relevance Feedback**:
- The system automatically collects feedback from user behavior.
- It observes activities such as clicks, browsing time, and download history.
- **Example**: A search engine observes which results users frequently click.

**3. Pseudo-Relevance Feedback**:
- The system assumes that the top-ranked search results are relevant.
- It automatically uses these documents to modify the original query.
- No direct user feedback is required.
- **Example**: The system assumes the top 5 results are relevant and uses their keywords to improve the search.

---

**Q. Discuss automatic local analysis, with suitable example (10 marks, May 2023)** 
**Q. Discuss automatic local analysis, with suitable examples (10 marks, May 2024)** 

Automatic Local Analysis is a technique used in Information Retrieval (IR) to improve search queries automatically by analyzing the top-ranked documents retrieved from an initial search.
It does not require users to manually select relevant documents. It automatically assumes that the top-ranked documents are relevant.

**Process of Automatic Local Analysis**
1. **Query Submission:** The user enters an initial search query into the Information Retrieval System.
2. **Initial Retrieval:** The system searches the database and retrieves a list of documents matching the user's query.
3. **Top Document Selection:** The system automatically selects the top-ranked documents, assuming they are relevant to the user's query.
4. **Term Extraction:** The system identifies important keywords and frequently occurring terms from the selected documents.
5. **Term Weight Calculation:** The system calculates the importance of extracted terms based on their frequency and relevance.
6. **Query Expansion:** The system adds important extracted terms to the original query to improve its searching capability.
7. **Final Retrieval:** The system searches again using the expanded query and retrieves more relevant documents.

**Example:**
Consider a user searching a technical database with the ambiguous query: **"Java"**.
- **Initial Query:** `Java`
    - The search engine retrieves the top 5 documents, which happen to be predominantly about _Java programming_ (rather than _Java coffee_ or _Java island_).
- **Local Set Analysis:**
    - The system scans the text of these top 5 documents and counts the most frequent non-common words appearing near the word "Java".
    - Top extracted terms: `programming`, `JVM`, `object-oriented`, `class`, `compiler`
- **Query Expansion:**
    - The system selects the top 2 terms (`programming` and `JVM`) and automatically modifies the query to:  
        `Java + programming + JVM`
- **Final Retrieval:**
    - The expanded query runs again. Documents about coffee or geography are pushed down, while relevant software development articles are ranked at the top.

---

**Q. Discuss Multimedia IR Model (10 marks, May 2023)** 

A Multimedia Information Retrieval (MMIR) Model is a framework designed to index, search, and retrieve non-textual or mixed-media objects such as images, audio, video, and 3D models.

**Data Representation & Feature Extraction**
- Raw multimedia files are converted into searchable descriptors since pixels and waveforms cannot be queried directly:
  - **Metadata (Text Annotations)**: Manual tags, captions, filenames, transcripts, and EXIF properties like date and location.
  - **Low-Level Content Features**: Automatically extracted mathematical feature vectors representing visual or audio signals:
    - **Images**: Color histograms, texture patterns, edge shapes, and spatial layout descriptors.
    - **Audio**: Pitch, tempo, frequency spectra, and Mel-Frequency Cepstral Coefficients (MFCCs).
    - **Video**: Shot boundaries, representative keyframes, and object motion trajectories.
  - **High-Level Semantic Features**: Deep learning embeddings (CNNs, Transformers) mapping raw signals to human concepts.

**Multidimensional Indexing**
- Feature vectors live in high-dimensional spaces where standard inverted indexes fail to scale efficiently.
- Uses spatial trees (R-trees, kd-trees) or Locality-Sensitive Hashing (LSH) to group similar vectors fast.

**Query Paradigms**
- **Query by Keyword**: Searches multimedia collections using text descriptions, captions, or metadata tags.
- **Query by Example (QBE)**: Uses a sample image, audio clip, or video to retrieve visually or acoustically similar items.
- **Query by Sketch / Humming**: Draws a rough shape or hums a tune to match against stored feature vectors.

**Similarity Matching & Ranking**
- Computes closeness between query and media vectors using Euclidean Distance, Manhattan Distance, or Cosine Similarity.
- Ranks retrieved items in ascending order of distance so the highest similarity appears first.

**Relevance Feedback**
- Users mark initial retrieved media results as relevant or non-relevant based on their intent.
- Dynamically updates feature weights and refines the query vector across iterations to improve accuracy.

---

**Q. Define data modeling? Explain any two types of data models (5 marks, May 2024)** 

**Data Modeling** is the process of creating a visual or conceptual representation of an information system or database to define how data is structured, stored, connected, and constrained. It acts as a blueprint that bridges business requirements and physical database implementation so data remains consistent, organized, and easy to retrieve.

**1. Relational Data Model**
- **Structure**: Organizes data into two-dimensional tables of rows (tuples) and columns (attributes).
- **Relationships**: Connects tables via primary keys and foreign keys referencing another table's key.
- **Advantages**: Ensures integrity via constraints, cuts redundancy via normalization, and supports SQL.
- **Example**: University database with Students, Courses, and Enrollments linked by IDs.

**2. Object-Oriented Data Model**
- **Structure**: Stores data as objects bundling attributes and methods, grouped into classes.
- **Relationships & Features:** Supports inheritance, encapsulation, and unique object identity.
- **Advantages**: Matches OOP languages and handles complex or multimedia data without heavy joins.
- **Example**: Vehicle class with Car and Truck subclasses having `engineNo` and `calculateMileage()`.

**3. Hierarchical Data Model**
- **Structure**: Arranges data in an inverted tree of parent and child records across levels.
- **Relationships & Features**: Uses strict 1:N parent-child links where each child has one parent.
- **Advantages**: Offers fast traversal along fixed tree paths and fits natural hierarchies cleanly.
- **Example**: File directory or org chart where each file sits under one parent folder.

**4. Network Data Model**
- **Structure**: Models data as a graph of record nodes linked by edges, extending trees.
- **Relationships & Features**: Supports M:N links where a child can have multiple parents for flexible paths.
- **Advantages**: Fits complex linked data better than trees and lowers record duplication.
- **Example**: Enrollment system linking multiple Students to multiple Courses and vice versa.

---

///
## Module IV: Text Processing

**Q. Illustrate different markup languages with its applications (5 marks, Dec 2024)** 
**Q. Illustrate any 2 markup languages and its applications (10 marks, Dec 2025)** 
**Q. Different markup languages and its applications (short note) (10 marks, May 2025)** 

A **markup language** is a system for annotating a document in a way that is syntactically distinguishable from the text, using tags or markers to define structure, formatting, presentation, or semantic meaning. 
In Information Retrieval (IR) and text processing, markup languages help parse document structure, extract metadata, and index specific sections.
  
**Types of Markup Languages:**

- **HTML (HyperText Markup Language)**: 
	- Uses predefined tags (such as `<h1>`, `<p>`, `<a href="...">`) to structure web pages, format display elements, and create hyperlinks between documents.
	- **Applications**: Building web pages and web applications, structuring content for browsers, and enabling hypertext navigation across the World Wide Web.
- **XML (eXtensible Markup Language)**: 
	- Allows users to define custom, hierarchical tags to describe the structure and semantic meaning of data rather than how it looks.
	- **Applications**: Data exchange between systems and APIs, configuration files, document storage, and structured text / XML information retrieval.
- **SGML (Standard Generalized Markup Language)**: 
	- An ISO-standard meta-language used to define markup languages and document grammars via Document Type Definitions (DTDs).
	- **Applications**: Large-scale technical documentation, publishing workflows, and serving as the historical foundation for HTML and XML.
- **Markdown**: 
	- A lightweight markup language that uses plain-text formatting syntax (such as `#`, `*`, `-`, and `` ` ``) to create clean, readable documents that can easily convert to HTML.
	- **Applications**: Technical documentation, README files, notes, blogs, and collaborative writing platforms.
- **LaTeX**: 
	- A document preparation system and markup language based on TeX that uses commands and environments (such as `\frac`, `\begin{equation}`, `\section`) for precise typesetting.
	 - **Applications**: Academic research papers, mathematical equations, scientific reports, theses, and books.

---

**Q. Importance of metadata and its types (5 marks, May 2025)** 
**Q. What is Metadata? Explain Descriptive and Semantic Metadata in detail (10 marks, Dec 2025)** 

**Metadata** is structured or semi-structured "data about data" that describes, locates, and manages resources to aid retrieval and indexing.

**Importance of Metadata:**

- **Discoverability**: Finds resources via author, title, date, or subject even without exact body keywords.
- **Organization & Indexing**: Uses structured fields to make cataloging, browsing, and indexing faster and cleaner.
- **Context & Provenance**: Captures origin, ownership, licensing, and format details to judge trust and fit.
- **Interoperability**: Uses standard schemas like Dublin Core so data shares and reuses across systems easily.
- **Lifecycle Management**: Tracks versions, retention rules, and access rights over time for preservation.

**Types of Metadata:**

- **Descriptive Metadata**: Identifies and describes items for discovery via title, author, keywords, and date.
- **Structural Metadata**: Shows how compound items assemble, such as page order, chapters, or media tracks.
- **Administrative Metadata**: Manages resources through rights, access rules, file format, and preservation logs.
- **Semantic Metadata**: Captures domain concepts and entity links using ontologies, taxonomies, or linked data.

**Descriptive Metadata**

Descriptive metadata identifies, describes, and locates resources so users can search for and distinguish items easily.
- **Core Elements**: Includes title, author, abstract, keywords, date, publisher, format, language, and IDs.
- **Role in IR**: Supports fielded search by author or year, facet filters, and clear result citations.
- **Standards & Formats**: Uses schemas like Dublin Core and MARC, plus HTML `<meta>` tags or image EXIF data.
- **Example**: Paper record with Title "Neural Ranking Models", Author "A. Sharma", Year 2024, and DOI.

**Semantic Metadata**

Semantic metadata defines explicit content meaning and concept links so systems reason beyond plain string matching.
- **Core Components**: Uses vocabularies, taxonomies, thesauri, and RDF/OWL ontologies for typed entity links.
- **Role in IR**: Bridges vocabulary gaps, resolves ambiguous terms, aids semantic search, and feeds graphs.
- **Pros & Challenges**: Enables smart inference and integration, but needs domain skill and careful upkeep.
- **Example**: Linking "Vector Space Model" as a subclass of "IR Model" using "Cosine Similarity".

---

**Q. Discuss various phases of text preprocessing within a document. Discuss any one application for the same (10 marks, Dec 2024)** 
**Q. Discuss various phases of text preprocessing within a document. Discuss any one application for the same (10 marks, May 2024)** 

**Text preprocessing** is the foundational sequence of cleaning, transforming, and normalizing raw unstructured text into clean, standardized tokens suitable for indexing, searching, and analysis in an Information Retrieval (IR) or Natural Language Processing (NLP) system.

**Phases of Text Preprocessing:**

- **Noise & Case Normalization**: Removes tags, punctuation, and extra spaces; lowercases words so variants match uniformly.
- **Tokenization**: Splits continuous text streams into discrete word or subword tokens using boundaries and rules.
- **Stopword Removal**: Drops high-frequency filler words like "the", "is", and "and" to shrink indexes and speed search.
- **Stemming**: Trims word affixes via rules so inflected forms like "search" and "searching" share a common root.
- **Lemmatization**: Maps words to valid dictionary base forms using grammar and vocabulary for higher accuracy.
- **Term Filtering & N-Grams**: Prunes noisy rare terms and builds n-grams or index terms to support matching and ranking.

**Applications of Text Preprocessing:**

- **Search Engines**: Normalizes documents and queries before indexing for faster lookups and better variant matching.
- **Sentiment Analysis**: Cleans slang, casing, and noise in reviews or social posts to classify opinion polarity reliably.
- **Spam Detection**: Tokenizes and filters email text to isolate spam keywords and patterns for accurate blocking.
- **Chatbots**: Normalizes messy user messages and word forms so intent detection and replies stay consistent.

---

**Q. Lexical analysis (short note) (5 marks, May 2023)** 

**Lexical analysis** is the first phase of text preprocessing in an Information Retrieval (IR) system that converts a stream of raw characters from a document or user query into a sequence of meaningful, discrete units called **tokens** (words or terms).

**Key Operations in Lexical Analysis:**
- **Tokenization**: Splits continuous text into individual words using delimiters like whitespace, tabs, and line breaks.
- **Digit & Number Handling**: Identifies numeric strings and decides whether to discard, keep, or normalize dates and figures.
- **Hyphen & Apostrophe Resolution**: Determines whether hyphenated words (e.g., `"state-of-the-art"`) or contractions (e.g., `"don't"`) stay single tokens or split.
- **Punctuation Removal**: Strips non-alphanumeric symbols (commas, periods, brackets) that carry no indexing value.
- **Case Folding**: Converts all uppercase letters to lowercase so variants like `"Information"` and `"information"` match uniformly.

**Example:**
- **Input Text:** `"Information-Retrieval (IR) systems process 100+ documents!"`
- **Output Tokens:** `["information", "retrieval", "ir", "systems", "process", "documents"]`

**Importance in IR:**
- **Standardizes Vocabulary**: Ensures queries and documents produce identical token forms for accurate index matching.
- **Reduces Index Size**: Eliminates redundant punctuation and case variations before stopword removal and stemming.

---

**Q. Write a note on Scalar and Metrics Clusters (10 marks, May 2023)** 

**Term clustering** in Information Retrieval (IR) groups related index terms together to handle synonymy, expand queries, and improve recall when exact query words do not appear in documents. **Scalar clusters** and **metric clusters** are two classical approaches to measuring similarity between terms for clustering.

**Scalar Clusters**

**Scalar clustering** groups terms based on the similarity of their **co-occurrence profiles** with other terms across documents, rather than whether the two terms appear directly next to each other.

- **Core Principle**: Two terms are scalar-similar if they share similar patterns of co-occurrence with surrounding vocabulary.
- **Representation**: Each term is represented by a vector of association or co-occurrence weights across all other terms in the collection.
- **Similarity Measure**: Compares term association vectors using vector similarity metrics such as Cosine Similarity or inner product.
- **Strengths**: Captures indirect semantic relationships and synonyms that rarely appear together in the same sentence.
- **Limitations**: Computationally expensive for large vocabularies and sensitive to noisy or sparse co-occurrence counts.

**Metric Clusters**

**Metric clustering** groups terms based on **direct positional proximity** or co-occurrence within documents or fixed text windows.

- **Core Principle**: Terms occurring close to one another frequently are assumed to be topically or contextually related.
- **Distance / Proximity Basis**: Measures word distance (such as number of intervening words or sentences) or co-occurrence within a window.
- **Similarity Measure**: Often weights co-occurrences inversely by the distance between terms so adjacent or nearby terms score higher.
- **Strengths**: Captures phrase-like and contextually tight relationships directly observable in document text.
- **Limitations**: Misses synonyms that do not appear near each other and depends heavily on window size choices.

| Factor                  | Scalar Clusters                             | Metric Clusters                                  |
| :---------------------- | :------------------------------------------ | :----------------------------------------------- |
| **Basis of Similarity** | Shared co-occurrence profiles across terms  | Direct word proximity or distance in text        |
| **Relationship Type**   | Indirect / structural vocabulary similarity | Direct / positional local closeness              |
| **Computation**         | Compares term-term association vectors      | Evaluates token distance or window co-occurrence |
| **Best For**            | Identifying synonyms and related concepts   | Capturing nearby or phrase-level term pairs      |

---

**Q. Document clustering (short note) (10 marks, May 2024)** 

**Document clustering** is an unsupervised text mining and Information Retrieval (IR) technique that partitions a collection of documents into distinct groups (clusters) such that documents within the same cluster are highly similar to one another and dissimilar to documents in other clusters, without using predefined category labels.

**Key Concepts & Workflow:**
- **Document Representation**: Converts text documents into feature vectors (such as TF-IDF or semantic embeddings) so similarity can be computed mathematically.
- **Similarity / Distance Measure**: Quantifies closeness between documents using metrics like Cosine Similarity, Euclidean Distance, or Jaccard similarity.
- **Clustering Algorithms**: Groups documents using partitioning methods (e.g., *k*-means), hierarchical clustering (agglomerative or divisive trees), or density/probabilistic methods.
- **Cluster Labeling & Evaluation**: Summarizes each cluster using top terms or centroids and evaluates quality via cohesion, separation, or silhouette scores.

**Types of Document Clustering:**
- **Hard vs. Soft Clustering**: Hard clustering assigns each document to a single cluster, whereas soft (fuzzy) clustering assigns membership weights across multiple topics.
- **Hierarchical vs. Flat Clustering**: Hierarchical clustering builds a nested tree of subtopics (dendrogram), while flat clustering creates a fixed number of non-nested clusters.

**Role in Information Retrieval:**
- **Result Organization & Browsing**: Groups large search result sets into topical clusters so users can explore subtopics quickly without scanning long flat lists.
- **Improves Efficiency & Recall**: Supports cluster-based retrieval and narrows search spaces across massive document collections.

---

**Q. Information Retrieval in digital libraries (short note) (5 marks, Dec 2023)** 
**Q. Information Retrieval in digital libraries (short note) (5 marks, Dec 2024)** 

Information Retrieval (IR) in digital libraries is the process of searching, accessing, and retrieving relevant information from digitally stored resources such as e-books, research papers, journals, articles, and multimedia documents.

**Main Features:**

**1. Document Collection**
- Digital libraries collect and store e-books, journals, research papers, and other digital resources.
- They provide centralized access to large collections of digital information.

**2. Indexing**
- Documents are indexed using keywords, titles, authors, subjects, and metadata.
- Indexing helps users locate required information quickly and efficiently.

**3. Query Processing**
- Users enter search queries using keywords, author names, titles, or subjects.
- The system processes queries to identify matching documents.

**4. Searching and Matching**
- The system compares user queries with the stored index to find relevant documents.
- It retrieves documents that match the user's information requirements.

**5. Relevance Ranking**
- Retrieved documents are ranked according to their relevance and usefulness.
- The most relevant documents are displayed at the top of search results.

**6. User Interface**
- Digital libraries provide user-friendly interfaces for searching and browsing resources.
- Users can access books, journals, articles, and other resources easily.

**7. Access and Retrieval**
- Users can read, download, or access required digital documents online.
- It saves time and provides easy access to information from anywhere.

---

///
## Module V: Indexing and Searching

**Q. Explain inverted file indexing with suitable examples (5 marks, Dec 2023)** 
**Q. Describe the process of creating an inverted index. How can this be optimized with the help of block addressing? (10 marks, Dec 2023)** 
**Q. Describe the process of creating an inverted index with an example. How can this process be optimized using block addressing? (10 marks, May 2023)** 
**Q. Describe the process of creating an inverted index with an example. How can this process be optimized using block addressing? (10 marks, May 2024)** 
**Q. What is inverted Index? Describe the process of creating an inverted index without stop words for the following example (10 marks, Dec 2024)** 
**Q. What is inverted Index? Describe the process of creating an inverted index without stop words with example (10 marks, Dec 2025)** 

An **inverted index** is an indexing data structure in Information Retrieval (IR) that maps each unique index term to the list of documents (and optionally frequencies or positions) in which it appears, enabling fast term-based lookups without scanning every document sequentially. When stop words are excluded, high-frequency filler words (such as `is`, `the`, `and`, `in`, `to`) are removed so only content-bearing terms are indexed.

**Process of Creating an Inverted Index (Without Stop Words):**
1. **Document Collection & Parsing**: Gather input documents, assign each a unique document ID (`docID`), and extract raw text from structural or formatting markup.
2. **Tokenization & Case Normalization**: Split text into individual word tokens and convert characters to lowercase so words match consistently.
3. **Stop Word Removal**: Filter out common stop words so the index remains compact and focuses on meaningful keywords.
4. **Term-Document Mapping & Sorting**: Emit `(term, docID)` pairs for remaining terms, sort them alphabetically by `term` (and by `docID` within each term), and merge duplicates.
5. **Dictionary & Postings Construction**: Build the sorted vocabulary list with document frequencies (`df`) and attach each term's postings list of matching `docID`s.

**Example (Without Stop Words):**
Consider the following documents:
- **Doc 1**: `the cat sat on the mat`
- **Doc 2**: `a dog sat on the log`
- **Doc 3**: `cats and dogs are pets`

After lowercasing and removing stop words (`the`, `on`, `a`, `and`, `are`):
- **Doc 1 tokens**: `cat`, `sat`, `mat`
- **Doc 2 tokens**: `dog`, `sat`, `log`
- **Doc 3 tokens**: `cats`, `dogs`, `pets` *(or stemmed to `cat`, `dog`, `pet` if stemming is applied)*

| Term | Document Frequency | Postings List |
| :--- | :--- | :--- |
| `cat` | 1 | `Doc 1` |
| `cats` | 1 | `Doc 3` |
| `dog` | 1 | `Doc 2` |
| `dogs` | 1 | `Doc 3` |
| `log` | 1 | `Doc 2` |
| `mat` | 1 | `Doc 1` |
| `pets` | 1 | `Doc 3` |
| `sat` | 2 | `Doc 1, Doc 2` |

**Optimization Using Block Addressing:**
- **Motivation**: Storing individual pointers or ungrouped entries for every term and posting increases memory consumption and disk seeks in large collections.
- **Vocabulary Block Addressing**: Groups sorted dictionary terms into fixed-size or variable-size blocks; only the lead term of a block stores a pointer to its postings area, reducing dictionary pointer overhead.
- **Postings Block Addressing**: Divides long postings lists into blocks (with block headers, `docID` bounds, or byte offsets), allowing faster block skipping during query evaluation and better cache/compression alignment.
- **Trade-off**: Saves space and speeds up block-level traversal, while requiring a short scan within a block to locate a specific term or posting.

---

**Q. Explain Suffixes, Suffix Trie and Suffix tree, Suffix array and Supra Index with example (10 marks, Dec 2024)** 
**Q. Construct a Suffix, suffix trie and suffix tree, suffix array and supra index for the given sample text : `Roses are red. Red roses are beautiful. Many people like red roses.` (10 marks, May 2025)** 

In text indexing and Information Retrieval (IR), **suffix-based data structures** index all suffixes of a text or string collection to support fast substring, prefix, and pattern matching without scanning the entire text sequentially.

**Core Concepts & Data Structures:**

- **Suffixes**: A suffix of a string $S$ of length $n$ is any substring starting at position $i$ ($0 \le i < n$) and running to the end $S[i..n-1]$ (often terminated by a unique sentinel character like `$`).
- **Suffix Trie**: A compressed or uncompressed trie containing all suffixes of a string as paths from the root, where each edge is labeled with a character and each leaf represents a starting suffix index.
- **Suffix Tree**: A compressed trie (radix tree) of all suffixes where non-branching single-child chains of nodes are merged into single edges labeled with substrings, reducing space from $O(n^2)$ nodes to $O(n)$ nodes.
- **Suffix Array**: A lexicographically sorted array of all starting indices of the suffixes of a string, using much less memory than a suffix tree while supporting fast pattern search via binary search (often paired with an LCP array).
- **Supra Index**: An auxiliary multi-level or block-level index built over a sorted suffix array or text blocks (storing sampled/boundary entries or supra-keys) to accelerate lookups and reduce disk/memory access overhead on large texts.

**Quick Example on a Small String (`S = "banana$"`):**

- **Suffixes**:
  - `0`: `banana$`
  - `1`: `anana$`
  - `2`: `nana$`
  - `3`: `ana$`
  - `4`: `na$`
  - `5`: `a$`
  - `6`: `$`
- **Sorted Order (Suffix Array)**: `[6, 5, 3, 1, 0, 4, 2]` corresponding to `$`, `a$`, `ana$`, `anana$`, `banana$`, `na$`, `nana$`.
- **Suffix Trie vs. Suffix Tree**: The suffix trie has separate character-by-character branches for `a-n-a-$` and `a-n-a-n-a-$`, whereas the suffix tree merges the shared `ana` path and compresses non-branching chains into single substring edges.
- **Supra Index**: Stores every $k$-th suffix (e.g., every 2nd or 3rd entry in the sorted suffix array) as a coarse guidepost so binary search jumps directly to a candidate block before scanning locally.

**Construction on Sample Text:**
**Text**: `"Roses are red. Red roses are beautiful. Many people like red roses."` *(Length $N = 67$ characters, 0-indexed)*

- **Selected Suffixes (0-indexed starting positions)**:
  - `0`: `Roses are red. Red roses are beautiful. Many people like red roses.`
  - `6`: `are red. Red roses are beautiful. Many people like red roses.`
  - `10`: `red. Red roses are beautiful. Many people like red roses.`
  - `15`: `Red roses are beautiful. Many people like red roses.`
  - `19`: `roses are beautiful. Many people like red roses.`
  - `25`: `are beautiful. Many people like red roses.`
  - `29`: `beautiful. Many people like red roses.`
  - `40`: `Many people like red roses.`
  - `45`: `people like red roses.`
  - `52`: `like red roses.`
  - `57`: `red roses.`
  - `61`: `roses.`

- **Suffix Trie Construction**:
  - Insert every suffix $S[i..N-1]$ character by character starting from the root node.
  - Shared prefixes share path edges from the root (for example, paths starting with `r` or `R` branch where characters diverge, such as `red...` vs. `roses...`).
  - Each terminal node records the starting offset $i$ of that suffix.

- **Suffix Tree Construction**:
  - Compress every non-branching path in the suffix trie into a single edge labeled with the concatenated substring.
  - For example, `beautiful. Many people like red roses.` (at index `29`) becomes a single edge directly from the root if no other suffix starts with `b`.
  - Branches occur at exact split points (such as distinguishing `red. Red roses...` at index `10` from `red roses.` at index `57`).

- **Suffix Array Construction (Lexicographical Sort of Suffixes)**:
  - Sort all suffixes in ASCII/lexicographical order (note: uppercase letters `'M'`, `'R'` sort before lowercase letters `'a'`, `'b'`, `'l'`, `'p'`, `'r'` in standard ASCII):

| Rank | Start Index | Suffix Preview |
| :--- | :--- | :--- |
| 1 | `40` | `Many people like red roses.` |
| 2 | `15` | `Red roses are beautiful. Many people like red roses.` |
| 3 | `0` | `Roses are red. Red roses are beautiful. Many people like red roses.` |
| 4 | `25` | `are beautiful. Many people like red roses.` |
| 5 | `6` | `are red. Red roses are beautiful. Many people like red roses.` |
| 6 | `29` | `beautiful. Many people like red roses.` |
| 7 | `52` | `like red roses.` |
| 8 | `21` | `ses are beautiful. Many people like red roses.` |
| 9 | `62` | `oses.` |
| 10 | `57` | `red roses.` |
| 11 | `10` | `red. Red roses are beautiful. Many people like red roses.` |
| 12 | `19` | `roses are beautiful. Many people like red roses.` |
| 13 | `61` | `roses.` |

- **Supra Index Construction**:
  - Partition the sorted suffix array into blocks (for instance, blocks of size $4$) and extract a supra-index of sampled boundary suffixes:
    - **Block 1 (Ranks 1–4)**: Entry `40` (`Many people like red roses.`)
    - **Block 2 (Ranks 5–8)**: Entry `6` (`are red. Red roses are beautiful. Many people like red roses.`)
    - **Block 3 (Ranks 9–12)**: Entry `62` (`oses.`)
    - **Block 4 (Rank 13+)**: Entry `61` (`roses.`)
  - Searching for a pattern first binary-searches the compact supra-index to select the target block, then narrows down within that block's suffix array range.

---

**Q. Discuss Huffman Algorithm in detail with suitable example (10 marks, Dec 2024)** 

The **Huffman algorithm** (Huffman coding) is a greedy, lossless data compression algorithm that assigns variable-length binary prefix codes to characters or symbols based on their frequencies of occurrence. Frequent symbols receive shorter binary codes and rare symbols receive longer codes, minimizing the overall encoded bit length while guaranteeing **prefix-free** decoding (no code is a prefix of another).

**Key Properties & Concepts:**
- **Prefix Property**: Because all symbols reside at leaf nodes of a binary tree, no codeword is a prefix of any other codeword, allowing unambiguous left-to-right bit decoding without delimiters.
- **Greedy Bottom-Up Tree Construction**: Repeatedly merges the two nodes with the lowest frequencies into a new internal node whose weight is their sum.
- **Weighted Path Length**: Minimizes $\sum_{i} f_i \cdot l_i$, where $f_i$ is symbol frequency and $l_i$ is codeword length in bits.
- **Role in Information Retrieval**: Compresses text, vocabularies, postings lists, or term frequencies to reduce storage and speed up I/O.

**Steps of Huffman Coding:**
1. **Count Frequencies**: Compute the occurrence frequency of each symbol in the input data.
2. **Create Leaf Nodes**: Build a priority queue (min-heap) of leaf nodes ordered by frequency.
3. **Merge Lowest Frequencies**: Extract the two minimum-frequency nodes, create a parent node with frequency equal to their sum, assign `0` to one branch and `1` to the other, and insert the parent back into the queue.
4. **Repeat Until One Root**: Continue merging until a single root node remains, forming the **Huffman tree**.
5. **Assign Codewords**: Traverse from the root to each leaf to read off its binary codeword.

**Example:**
Consider the string `"ABRACADABRA"` (total length = $11$ characters):
- **Frequencies**: `A`: $5$, `B`: $2$, `R`: $2$, `C`: $1$, `D`: $1$.

**Tree Construction Steps:**
- **Step 1**: Lowest frequencies are `C` ($1$) and `D` ($1$). Merge into node `CD` with weight $1 + 1 = 2$.
- **Step 2**: Remaining lowest weights are `B` ($2$), `R` ($2$), and `CD` ($2$). Merge `B` ($2$) and `R` ($2$) into node `BR` with weight $2 + 2 = 4$.
- **Step 3**: Lowest weights are `CD` ($2$), `BR` ($4$), and `A` ($5$). Merge `CD` ($2$) and `BR` ($4$) into node `CDBR` with weight $2 + 4 = 6$.
- **Step 4**: Merge `A` ($5$) and `CDBR` ($6$) into the root node with weight $5 + 6 = 11$.

**Generated Prefix Codes (assuming left edge = `0`, right edge = `1`):**

| Symbol | Frequency | Codeword | Code Length (bits) | Total Bits |
| :--- | :--- | :--- | :--- | :--- |
| `A` | 5 | `0` | 1 | $5 \times 1 = 5$ |
| `C` | 1 | `100` | 3 | $1 \times 3 = 3$ |
| `D` | 1 | `101` | 3 | $1 \times 3 = 3$ |
| `B` | 2 | `110` | 3 | $2 \times 3 = 6$ |
| `R` | 2 | `111` | 3 | $2 \times 3 = 6$ |

- **Compressed Bit Length**: $5 + 3 + 3 + 6 + 6 = 23\text{ bits}$ (versus $11 \times 8 = 88\text{ bits}$ for 8-bit ASCII or $11 \times 3 = 33\text{ bits}$ for a 3-bit fixed-length code).
- **Encoded Output for `"ABRACADABRA"`**: `0 110 111 0 100 0 101 0 110 111 0` (23 bits total).

**Time Complexity & Limitations:**
- **Time Complexity**: $O(n \log n)$ using a min-heap for $n$ distinct symbols (or $O(n)$ if symbols are already sorted by frequency).
- **Space Complexity**: $O(n)$ to store the tree and code table.
- **Limitations**: Requires two passes over data (one for frequencies, one for encoding) unless adaptive Huffman coding is used, and requires transmitting/storing the tree or code table alongside compressed data.

---

**Q. Statistical text compression and Dictionary based text compression (short note) (5 marks, May 2023)** 

**Statistical Text Compression**

Statistical text compression reduces file size by **assigning variable-length codes to characters based on their frequency of occurrence**.
- **Core Principle:** Frequently occurring characters are given shorter bit codes, while rare characters are assigned longer bit codes.
- **Encoding Process:** It builds a probability or frequency model of the source text (either statically using pre-calculated averages or dynamically as the file is read) to generate prefix-free codes.
- **Common Algorithms:** Huffman Coding, Shannon-Fano Coding, and Arithmetic Coding.
- **Advantage:** Achieves high compression efficiency when character frequencies vary significantly.

**Dictionary-Based Text Compression**

Dictionary-based text compression reduces file size by **replacing recurring strings or phrases with shorter references (pointers) to a dictionary**.
- **Core Principle:** Instead of encoding single characters by frequency, it looks for repeated patterns or words in the text and maps them to a single index or token.
- **Encoding Process:**
    - _Static Dictionary:_ Uses a fixed, pre-built dictionary known to both compressor and decompressor.
    - _Dynamic (Adaptive) Dictionary:_ Builds the dictionary on the fly as the text is scanned (e.g., using a sliding window).
- **Common Algorithms:** LZ77, LZ78, LZW (Lempel-Ziv-Welch), and DEFLATE (used in ZIP and GZIP).
- **Advantage:** Very fast decompression and excels at compressing text with high word or phrase repetition.

---

**Q. Sequential searching (short note) (5 marks, Dec 2023)** 
**Q. Sequential Search (short note) (10 marks, May 2024)** 

**Sequential Search (Linear Search)** is the simplest searching algorithm used to find the position of a target element within a list or array by checking every element one by one from the beginning until a match is found or the end of the list is reached.

**Working Principle**:
1. Start from the first element (index `0`) of the array.
2. Compare the current element with the target value (`key`).
3. If the current element matches the `key`, return its index and stop the search.
4. If it does not match, move to the next element.
5. Repeat steps 2 to 4 until the `key` is found or the end of the array is reached.
6. If the end of the array is reached without a match, return `-1` (indicating the element is not present).

```js
function sequentialSearch(arr, target) {
	for (let i = 0; i < arr.length; i++) {
		if (arr[i] === target) {
			    return i;
		    }
	}
	return -1;
}
```

**Time Complexity:**
- **Best case: O(1)**: target is the first element.
- **Worst case: O(n)**: target is the last element or not present.
- **Average case: O(n)**: on average, you scan about half the array (n/2 comparisons).

**Example:**
Consider an array `A = [15, 42, 7, 23, 89]` and `key = 23`:
- **Pass 1 (`i = 0`):** Compare `15` with `23` → No match.
- **Pass 2 (`i = 1`):** Compare `42` with `23` → No match.
- **Pass 3 (`i = 2`):** Compare `7` with `23` → No match.
- **Pass 4 (`i = 3`):** Compare `23` with `23` → **Match found!** Return index `3`.

**Advantages:**
- **No sorting required:** Works effectively on both sorted and unsorted datasets.
- **Easy to implement:** Simple logic with minimal memory overhead.
- **Data structure flexibility:** Works seamlessly on arrays as well as linked lists (where random access is not possible).

**Disadvantages:**
- **Slow for large datasets:** Time grows linearly with the number of elements (n), making it inefficient compared to Binary Search $O(log n)$ on sorted data.

---

**Q. Define Multimedia information retrieval. Discuss indexing and searching (10 marks, Dec 2023)** 
**Q. Define Multimedia information retrieval. Discuss Multimedia indexing and searching (10 marks, Dec 2024)** 
**Q. Multimedia indexing (short note) (10 marks, May 2024)** 

**Multimedia Information Retrieval (MMIR)** is the process of representing, indexing, searching, and retrieving non-textual or multi-modal media objects—such as images, audio, video, animations, and combined text-media documents—based on their metadata, extracted content features, or semantic meaning. Unlike traditional text IR that matches discrete words or tokens, MMIR operates over continuous signals, spatial-temporal structures, and high-dimensional feature vectors.

**Multimedia Indexing:**
- **Feature Extraction**: Converts raw media signals into numeric descriptors, such as color histograms, textures, and shapes for images; pitch, tempo, and MFCCs for audio; and keyframes or shot boundaries for video.
- **Metadata & Annotation Indexing**: Indexes textual annotations, captions, transcripts, tags, and EXIF/technical metadata using standard text or inverted indexes.
- **High-Dimensional / Spatial Indexing**: Uses multidimensional index structures—such as R-trees, kd-trees, VA-files, or Locality-Sensitive Hashing (LSH)—to group similar feature vectors and avoid linear scans across large collections.
- **Dimensionality Reduction & Quantization**: Applies PCA, SVD, or visual/acoustic codebooks (bag-of-features) to reduce feature space dimensions and speed up index lookups and storage.

**Multimedia Searching:**
- **Query by Keyword / Text**: Retrieves media items using text queries matched against tags, captions, filenames, speech transcripts, or semantic embeddings.
- **Query by Example (QBE)**: Accepts a sample image, audio clip, or video segment as the query and finds media items with similar extracted feature representations.
- **Query by Sketch / Humming / Melody**: Matches rough user-drawn shapes or hummed tunes against visual shape descriptors or pitch/rhythm features.
- **Similarity Matching & Ranking**: Computes closeness between the query vector and stored media vectors using distance or similarity metrics (e.g., Euclidean distance, Manhattan distance, or Cosine similarity) and ranks results by relevance.
- **Relevance Feedback**: Refines query vectors or feature weights using user judgments (relevant vs. non-relevant) on initial results to bridge the semantic gap between low-level features and human perception.

---

**Q. Explain Video Information Retrieval (VIR) and Image Information Retrieval (IIR) — 3 techniques each; how they improve user experience in multimedia search (10 marks, Dec 2025)** 

**Video Information Retrieval (VIR)** and **Image Information Retrieval (IIR)** are specialized subfields of Multimedia Information Retrieval (MMIR) that index, query, and rank video and still-image collections using visual content features, temporal dynamics, audio/speech cues, and textual metadata.

**Video Information Retrieval (VIR) Techniques:**
- **Shot Boundary & Keyframe Extraction**: Segments continuous video streams into shots and selects representative keyframes to index and preview scenes compactly.
- **Spacio-Temporal & Motion Feature Indexing**: Extracts object motion trajectories, camera pan/zoom cues, and optical flow across frames to retrieve action or movement patterns.
- **Multimodal Transcript & Visual-Audio Alignment**: Combines Automatic Speech Recognition (ASR) transcripts, OCR on-screen text, audio events, and visual embeddings for scene-level search.

**Image Information Retrieval (IIR) Techniques:**
- **Color, Texture & Shape Descriptors (CBIR)**: Represents visual appearance using color histograms, Gabor/GLCM textures, and edge/contour shapes for content-based similarity matching.
- **Local Feature Matching & Visual Bag-of-Words**: Detects local keypoints (e.g., SIFT/ORB) and quantizes descriptors into visual words or inverted indexes for scalable object and landmark search.
- **Deep Visual Embeddings & Semantic Tagging**: Uses Convolutional Neural Networks (CNNs) or vision-language embeddings to map pixel arrays to high-level objects, scenes, and concepts.

**How VIR and IIR Improve User Experience in Multimedia Search:**
- **Direct Scene & Visual Jumping**: Lets users jump straight to relevant video shots or matching images instead of scrubbing entire videos or browsing unindexed galleries.
- **Query-by-Example & Visual Discovery**: Supports finding visually similar products, designs, or clips when exact text keywords are hard to phrase or unknown.
- **Faster & More Relevant Results**: Combines multimodal cues and visual similarity ranking to surface accurate matches quickly and reduce browsing effort.

---

**Q. Automatic feature extraction (short note) (5 marks, May 2023)** 

**Automatic Feature Extraction** is a process in machine learning and deep learning where algorithms automatically identify, select, and transform raw input data into relevant, meaningful representations (features) without requiring manual human intervention or domain-specific feature engineering.

- **Replaces manual digitizing**: Automates the slow, tedious, and expensive task of hand-digitizing features from imagery.
- **Learns from analyst examples**: Machine learning algorithms learn on-the-fly from a small set of user-labeled examples.
- **Uses spatial context**: Extracts features by considering neighboring pixels (e.g., pavement next to white lines) for accuracy.
- **Hierarchical learning**: Iteratively improves results by removing false positives in successive passes.
- **Batch processing capability**: Generates scripts to apply trained models to large volumes of additional images.
- **Deep learning approach**: Autoencoders can find suitable feature representations automatically, drastically reducing dimensionality.

**Process:**

- **Raw Data Input:** Models ingest unstructured or raw data directly (such as raw pixel values of an image, audio waveforms, or raw text).
- **Hierarchical Learning:** Using multi-layered architectures (such as Convolutional Neural Networks or Autoencoders), the system learns patterns progressively.
    - _Early layers_ detect low-level features (e.g., edges, corners, or basic textures in images).
    - _Deeper layers_ combine these into complex, high-level concepts (e.g., shapes, faces, or specific objects).
- **Optimization:** Through training (e.g., backpropagation), the algorithm adjusts its internal parameters to retain only the features that best minimize prediction error.

---

**Q. Discuss concept of Text search engine (5 marks, Dec 2023)** 

A **Text Search Engine** is a specialized software system designed to rapidly find, retrieve, and rank relevant text documents or web pages from a massive database in response to a user’s search query.
Instead of scanning every word of every document in real time, a text search engine relies on pre-processed data structures to deliver results in milliseconds.

**1. Web Crawling**
- Search engines use automated programs called crawlers or spiders to visit websites and collect web pages.
- They follow hyperlinks to discover new web pages and collect raw text documents from different websites.

**2. Tokenization**
- The collected web pages are divided into individual words or tokens to identify important keywords.
- These tokens are extracted and prepared for further processing and indexing.

**3. Indexing**
- The search engine analyzes collected web pages and stores important information such as keywords, titles, and content.
- It creates an **Inverted Index**, which maps each term to the list of documents containing it.

**4. Query Processing**
- The search engine accepts search queries entered by users and analyzes their keywords.
- It processes the query to understand the user's requirements and identify suitable search terms.

**5. Searching**
- The search engine compares the user's query with the stored inverted index to find matching documents.
- It searches the indexed collection and identifies web pages containing the entered keywords.

**6. Matching**
- The search engine checks how closely the retrieved documents match the user's search query.
- It identifies relevant documents based on matching keywords and retrieves them for further ranking.

**7. Relevance Ranking**
- The scorer or ranker calculates relevance scores for retrieved web pages based on their usefulness and quality.
- It arranges the results in decreasing order of relevance, displaying the most useful pages first.

**8. Displaying Search Results**
- The search engine displays results on the **Search Engine Results Page (SERP)**.
- Results contain page titles, URLs, and short descriptions called snippets for easy understanding.

**9. Feedback and Learning**
- The search engine observes user clicks and collects relevance feedback to understand useful results.
- A feedback learner uses this information to improve the accuracy of future search results.

---

**Q. Explain search engine Architecture (5 marks, May 2023)** 
**Q. What is the purpose of a search engine? List the steps of search operation by search engine (5 marks, May 2024)** 

A **Search Engine** is a software system used to search and retrieve information from the World Wide Web based on keywords or queries entered by users.

**Purposes of a Search Engine:**
- Helps users find relevant information quickly.
- Provides access to millions of web pages.
- Saves time by organizing search results.
- Helps locate images, videos, documents, and websites.
- Displays relevant results according to the user's query.

**Steps of search operation:**

**1. Web Crawling**
- Search engines use automated programs called crawlers or spiders to visit websites and collect web pages.
- They follow hyperlinks to discover new web pages and collect raw text documents from different websites.

**2. Tokenization**
- The collected web pages are divided into individual words or tokens to identify important keywords.
- These tokens are extracted and prepared for further processing and indexing.

**3. Indexing**
- The search engine analyzes collected web pages and stores important information such as keywords, titles, and content.
- It creates an **Inverted Index**, which maps each term to the list of documents containing it.

**4. Query Processing**
- The search engine accepts search queries entered by users and analyzes their keywords.
- It processes the query to understand the user's requirements and identify suitable search terms.

**5. Searching**
- The search engine compares the user's query with the stored inverted index to find matching documents.
- It searches the indexed collection and identifies web pages containing the entered keywords.

**6. Matching**
- The search engine checks how closely the retrieved documents match the user's search query.
- It identifies relevant documents based on matching keywords and retrieves them for further ranking.

**7. Relevance Ranking**
- The scorer or ranker calculates relevance scores for retrieved web pages based on their usefulness and quality.
- It arranges the results in decreasing order of relevance, displaying the most useful pages first.

**8. Displaying Search Results**
- The search engine displays results on the **Search Engine Results Page (SERP)**.
- Results contain page titles, URLs, and short descriptions called snippets for easy understanding.

**9. Feedback and Learning**
- The search engine observes user clicks and collects relevance feedback to understand useful results.
- A feedback learner uses this information to improve the accuracy of future search results.

---

**Q. Identify the various task performed by web search engine (5 marks, May 2025)** 

A web search engine performs **three core tasks** crawling, indexing, and ranking/retrieval to find and display relevant web pages for a user's query.

**1. Web Crawling**
- Search engines use automated programs called crawlers or spiders to visit websites and collect web pages.
- They follow hyperlinks to discover new web pages and collect raw text documents from different websites.

**2. Tokenization**
- The collected web pages are divided into individual words or tokens to identify important keywords.
- These tokens are extracted and prepared for further processing and indexing.

**3. Indexing**
- The search engine analyzes collected web pages and stores important information such as keywords, titles, and content.
- It creates an **Inverted Index**, which maps each term to the list of documents containing it.

**4. Query Processing**
- The search engine accepts search queries entered by users and analyzes their keywords.
- It processes the query to understand the user's requirements and identify suitable search terms.

**5. Searching**
- The search engine compares the user's query with the stored inverted index to find matching documents.
- It searches the indexed collection and identifies web pages containing the entered keywords.

**6. Matching**
- The search engine checks how closely the retrieved documents match the user's search query.
- It identifies relevant documents based on matching keywords and retrieves them for further ranking.

**7. Relevance Ranking**
- The scorer or ranker calculates relevance scores for retrieved web pages based on their usefulness and quality.
- It arranges the results in decreasing order of relevance, displaying the most useful pages first.

**8. Displaying Search Results**
- The search engine displays results on the **Search Engine Results Page (SERP)**.
- Results contain page titles, URLs, and short descriptions called snippets for easy understanding.

**9. Feedback and Learning**
- The search engine observes user clicks and collects relevance feedback to understand useful results.
- A feedback learner uses this information to improve the accuracy of future search results.

---

**Q. Describe meta searchers and its merits with example (5 marks, Dec 2025)** 

A **meta-search engine** or **meta searchers** is a system that sends a user's query to **multiple independent search engines simultaneously**, aggregates their results, and presents a unified ranked list.

**Merits:**
- **Wider Coverage:** No single search engine indexes the entire web. Meta searchers combine databases to uncover results that an individual engine might miss.
- **Time-Saving:** You get results from multiple platforms in a single search without manually repeating your query across different websites.
- **Reduced Bias:** Pulling results from multiple algorithms helps balance out the ranking biases or commercial preferences of any single search engine.
- **Privacy Protection:** Many modern meta searchers act as a proxy, stripping away your IP address and personal tracking data before passing your query to major search engines.

**Examples:**
- **General Web Search:** **Dogpile**, **MetaCrawler**, and **Startpage** (aggregates Google results privately).
- **Travel & Booking:** **Kayak**, **Skyscanner**, and **Trivago** (compare flight and hotel prices across hundreds of airline and booking sites simultaneously).

---

**Q. Web information retrieval system (short note) (5 marks, May 2023)** 

A **Web Information Retrieval (Web IR) System** is a specialized software system designed to search, index, and retrieve relevant information from the World Wide Web in response to a user's query (e.g., Google, Bing).

**Architecture:**

**1. Web Crawling**
- Search engines use automated programs called crawlers or spiders to visit websites and collect web pages.
- They follow hyperlinks to discover new web pages and collect raw text documents from different websites.

**2. Tokenization**
- The collected web pages are divided into individual words or tokens to identify important keywords.
- These tokens are extracted and prepared for further processing and indexing.

**3. Indexing**
- The search engine analyzes collected web pages and stores important information such as keywords, titles, and content.
- It creates an **Inverted Index**, which maps each term to the list of documents containing it.

**4. Query Processing**
- The search engine accepts search queries entered by users and analyzes their keywords.
- It processes the query to understand the user's requirements and identify suitable search terms.

**5. Searching**
- The search engine compares the user's query with the stored inverted index to find matching documents.
- It searches the indexed collection and identifies web pages containing the entered keywords.

**6. Matching**
- The search engine checks how closely the retrieved documents match the user's search query.
- It identifies relevant documents based on matching keywords and retrieves them for further ranking.

**7. Relevance Ranking**
- The scorer or ranker calculates relevance scores for retrieved web pages based on their usefulness and quality.
- It arranges the results in decreasing order of relevance, displaying the most useful pages first.

**8. Displaying Search Results**
- The search engine displays results on the **Search Engine Results Page (SERP)**.
- Results contain page titles, URLs, and short descriptions called snippets for easy understanding.

**9. Feedback and Learning**
- The search engine observes user clicks and collects relevance feedback to understand useful results.
- A feedback learner uses this information to improve the accuracy of future search results.

---

///
## Module VI: User Interface and Visualization

**Q. Discuss starting points. Explain list of collection and overviews in detail (10 marks, Dec 2023)** 
**Q. What is the starting point? Explain list of collections and overviews in detail (10 marks, May 2024)** 
**Q. Starting points (short note) (5 marks, Dec 2024)** 

A **starting point** is an entry point or initial location from which a user begins searching for information in an Information Retrieval (IR) system.

- It helps users identify where to start their search.
- It provides access to different information resources and collections.
- It guides users towards relevant documents without requiring them to know the exact search query.
- It makes information searching easier, faster and more organized.

**Advantages of Starting Points**
1. Makes information searching easier.
2. Saves users' time and effort.
3. Helps beginners navigate an IR system.
4. Provides organized access to information.
5. Helps users identify relevant collections and topics.
6. Reduces confusion during the searching process.

**List of Collections**

A **list of collections** is a structured list of available information resources or databases provided by an Information Retrieval System.
It helps users select a suitable collection based on their information requirements.

**Features:**
1. **Organized Information:** Collections are arranged systematically according to subjects, categories or topics.
2. **Easy Navigation:** Users can easily browse different collections and select the required one.
3. **Subject-Based Classification:** Information is grouped into subjects such as Science, Technology, Medicine, Education, etc.
4. **Collection Description:** Each collection may provide a short description explaining the type of information it contains.
5. **Direct Access:** Users can directly access a particular collection without searching the entire database.
6. **Time Saving:** It reduces searching time by helping users choose the appropriate information source.

**Example:**
A digital library may provide the following list of collections:
- Books and E-books
- Research Papers
- Journals and Magazines
- Newspapers
- Theses and Dissertations
- Conference Proceedings

**Overviews**

An **overview** provides a general summary or broad picture of the information available in a particular subject, topic or collection.
It helps users understand the available information before performing a detailed search.

**Features:**
1. **General Introduction:** Provides basic information about a subject or collection.
2. **Broad Coverage:** Gives users an overall understanding of the available information.
3. **Topic Identification:** Helps users identify important topics and subtopics related to their search.
4. **Search Guidance:** Guides users towards relevant information sources and specific search areas.
5. **Hierarchical Structure:** Information may be arranged from broader topics to narrower subtopics.
6. **Easy Understanding:** Helps beginners understand a subject and decide what information they need.

**Example:**
Suppose a user wants information about Computer Science. An overview may display the following topics:
- Computer Networks
- Database Management Systems
- Artificial Intelligence
- Operating Systems
- Information Retrieval
- Software Engineering

| List of Collections                            | Overviews                                            |
| ---------------------------------------------- | ---------------------------------------------------- |
| Lists available information resources.         | Provides a general summary of information.           |
| Focuses on available databases or collections. | Focuses on subjects, topics and their relationships. |
| Helps users select a collection.               | Helps users understand a subject.                    |
| Provides access to information sources.        | Provides guidance for further searching.             |
| Example: Books, journals and research papers.  | Example: AI, networking and databases.               |

---

**Q. Student result management system scenario: identify starting point of program, describe List and Collection interfaces, advantages of Collection Framework (10 marks, Dec 2025)** 

In a **Student Result Management System** built in Java, the application organizes student records, subjects, and marks using object-oriented structure and the **Java Collections Framework (JCF)** to store, search, sort, and update result data dynamically.

**Starting Point of the Program:**
- **Entry Point (`main` Method)**: Execution starts at `public static void main(String[] args)` inside the main driver or controller class (e.g., `ResultManagementApp`).
- **Initialization Role**: Creates initial data structures (such as a `List` of `Student` objects), loads sample or user input records, and launches the menu or workflow.
- **Flow Control**: Invokes service or manager methods to add results, compute grades/GPA, search records, and display reports cleanly.

**`Collection` Interface:**
- **Definition**: Root interface of the Java Collections Framework (`java.util.Collection`) representing a group of individual objects treated as a single unit.
- **Core Operations**: Provides standard methods like `add()`, `remove()`, `size()`, `isEmpty()`, `contains()`, `clear()`, and `iterator()`.
- **Role in System**: Acts as a general contract for storing groups of student records or subject marks without mandating index positions or uniqueness rules.

**`List` Interface:**
- **Definition**: Sub-interface of `Collection` (`java.util.List`) that maintains an **ordered sequence** of elements, allows **duplicate elements**, and supports **positional (index-based) access**.
- **Key Operations**: Adds index-aware methods such as `get(index)`, `set(index, elem)`, `add(index, elem)`, `remove(index)`, `indexOf()`, and `listIterator()`.
- **Role in System**: Ideal for storing student result lists (via `ArrayList` or `LinkedList`) in insertion or roll-number order, accessing entries by position, and sorting by marks or CGPA.

**Advantages of the Collection Framework:**
- **Dynamic Sizing**: Grows and shrinks automatically as students enroll or drop subjects, avoiding fixed-size array limits.
- **Ready-Made Data Structures & Algorithms**: Offers proven implementations (`ArrayList`, `LinkedList`, `HashSet`, `HashMap`) and utilities (`Collections.sort()`, binary search).
- **Type Safety & Code Reuse**: Uses generics (`List<Student>`) to catch type errors at compile time and standardizes operations across collections.
- **Better Performance & Maintainability**: Provides tailored structures for fast lookups, insertions, or ordering, reducing custom boilerplate code.

---

**Q. What is Query Specification? Describe direct manipulation and natural language in the context to Boolean query formulation (10 marks, May 2023)** 

**Query Specification**

**Query Specification** is the process of expressing a user's information need in a form that an Information Retrieval System (IRS) can understand and process to retrieve relevant documents.

- It allows users to specify search terms and conditions.
- It uses Boolean operators such as **AND, OR, NOT** to combine keywords.
- It helps the system identify relevant documents from the database.

**Direct Manipulation**

**Direct manipulation** is a method of query formulation in which users interact directly with graphical interface elements to create search queries.

**Features:**
- Users select keywords and Boolean operators using buttons, menus, or checkboxes.
- No need to remember complex query syntax.
- Users can easily add, remove, or modify search conditions.
- It provides a user-friendly way to construct Boolean queries.

**Boolean Context:** Users select options like "All words" (AND), "Any words" (OR), or "None of these words" (NOT) from an Advanced Search form instead of remembering Boolean syntax.

**Natural Language**

**Natural Language** query formulation allows users to enter search queries using ordinary human language instead of using Boolean operators and special syntax.

**Features:**
- Users can type queries in simple English.
- The system uses Natural Language Processing (NLP) to understand the user's intention.
- It identifies important keywords and relationships between words.
- The system converts the query into a suitable search representation.
- It makes searching easier for non-technical users.

**Boolean Context:** The system translates natural phrasing into underlying Boolean logic behind the scenes:
- Conjunctions like _"and"_, _"with"_, or _"both"_ are mapped to `AND`.
- Alternatives like _"or"_ or _"either"_ are mapped to `OR`.
- Negations like _"without"_, _"excluding"_, or _"not"_ are mapped to `NOT`.

---

**Q. What is human-computer interaction? List and discuss any four design principles for information access interfaces (10 marks, May 2023)** 
**Q. What is human-computer interaction? List and discuss any four design principles for information access interfaces (10 marks, May 2024)** 

**Human-computer interaction (HCI)** is a cross-disciplinary field that studies the theory, design, implementation, and evaluation of how humans use and interact with computing devices. For information access interfaces specifically, design principles focus on reducing cognitive burden and supporting the iterative, exploratory nature of search. 
Below are eight principles adapted from Shneiderman's golden rules and information retrieval interface research.

- **Strive for Consistency**: Use identical terminology, layouts, and action sequences across all screens so users transfer learning effortlessly.
- **Cater to Universal Usability**: Design for novice and expert differences by providing simple defaults with optional advanced controls or shortcuts.
- **Offer Informative Feedback**: For every search action, show system status such as result counts, applied filters, or query interpretation so users understand the outcome.
- **Reduce Short-Term Memory Load**: Keep prior queries, selected facets, and results visible across screens to avoid forcing users to remember information from one display to the next.
- **Support Internal Locus of Control**: Let users initiate and steer the search process, with the system responding predictably to their actions rather than surprising them.
- **Permit Easy Reversal of Actions**: Allow users to undo filters, revert queries, or return to earlier result sets without penalty, encouraging exploration of unfamiliar options.
- **Prevent Errors with Constructive Recovery**: Constrain inputs (e.g., validate query syntax) and, when errors occur, provide specific guidance on how to fix them.
- **Design for Closure**: Organize multi-step search tasks so users receive clear signals when a stage is complete, helping them decide when to refine or stop.

---

**Q. Interface support for the search process (short note) (5 marks, Dec 2023)** 
**Q. Interface support for the search process (short note) (5 marks, Dec 2024)** 
**Q. Interface support for the search process (short note) (10 marks, May 2024)** 

**Interface support for the search process** involves designing user interface (UI) features that guide users through the four main stages of information retrieval: formulating a query, reviewing results, refining the search, and managing findings.

- **Query Formulation Aid**: Helps users express needs via search boxes, term suggestions, and error markers.
- **Browsing Support**: Enables exploratory navigation through categorized or linked content without exact queries.
- **Relevance Feedback**: Lets users mark results as relevant to automatically refine subsequent queries.
- **Results Presentation**: Displays document surrogates with highlighted query terms to show why items matched.
- **Search History Record**: Keeps a visible trace of prior queries and actions for reuse and reflection.
- **Iterative Dialogue Model**: Supports evolving queries since users learn and refine needs during interaction.
- **Vocabulary Assistance**: Bridges gap between user terms and system index terms via thesauri or suggestion features.
- **Visualization Tools**: Uses graphical representations to show term distribution or relationships among results.
- **Collaboration Support**: Allows sharing of search processes or results for cooperative problem solving.

---

**Q. Summarize two visualization techniques with respect to user interface design (10 marks, May 2024)** 
**Q. Summarize various visualization techniques with respect to user interface design (10 marks, May 2025)** 

In User Interface (UI) design, **visualization techniques translate complex, abstract data into intuitive visual representations**, reducing cognitive load and enabling users to quickly identify patterns, trends, and anomalies.

- **Node-Link Diagrams**: Represent entities as nodes and relationships as connecting lines for network exploration .
- **Document Maps**: Plot documents in 2D space by semantic similarity to reveal topical clusters .
- **Topographic Overlays**: Superimpose relevance contours on a document map to show aspect-specific importance .
- **Interactive Charts**: Enhance static charts like histograms or pie charts with dynamic user-driven adjustments .
- **Spatial Navigation Metaphors**: Use 3D or spatial models of information space for browsing and orientation .
- **Iconic Representations**: Use icons or glyphs to encode document attributes and support visual scanning .
- **Highlighting and Color Coding**: Apply visual cues like color to mark visited or new areas in information space .
- **Temporal Fusion Views**: Link multiple simultaneous representations so changes in one explain relationships in another .
- **Query Visual Language**: Compact visual encodings of query intent to explain result relevance .

**Types of Data Visualization:**
- **Line Charts:** It serves the purpose of showcasing the trends and patterns over the time.
- **Bar Charts:** Suitable for statistical comparison of categorical data.
- **Pie Charts:** Show the part-to-whole ratio.
- **Scatter Plots:** Illustrate the interchange between the two variables.
- **Heatmaps:** Visualize the data distribution or density in a given area, where it can be for instance a breakdown across a geographic or grid-based map.
- **Infographics:** Mix different visual attributes to show a story or create some narrative with your data.

---

**Q. Recommend visualization techniques for a mobile banking app UX (account activity, financial trends) (5 marks, Dec 2025)** 

In User Interface (UI) design, **visualization techniques translate complex, abstract data into intuitive visual representations**, reducing cognitive load and enabling users to quickly identify patterns, trends, and anomalies.

For a mobile banking app, visualization techniques should prioritize instant clarity on small screens, using visual encodings that reduce cognitive load for quick balance checks and spending awareness.

- **Line Graph**: Best for account balance history and financial trends over time.
- **Categorized Spending Trends**: Breaks down expenses by category against monthly targets to show where money goes.
- **Color-Coded Transaction Rows**: Uses subtle status tags and amount colors for fast vertical scanning of activity.
- **Interactive Charts**: Supports pinch-zoom and tap gestures so users can explore dense financial data fluidly.
- **Progressive Disclosure**: Hides complex details behind expandable sections to keep the main activity view scannable.
- **Visual Money Representation**: Uses graphical magnitudes instead of raw numbers to aid users with lower numeracy.
- **Default-Visible Activity Feed**: Shows recent transactions immediately without requiring date-filters, reducing user anxiety.
- **Dark Mode-Ready Charts**: Ensures charts remain legible with high-contrast colors in dark themes.
- **Budget Progress Indicators**: Shows remaining budget or overspending visually (e.g., percentage left) for quick financial health checks.

---

**Q. Importance of Context in Information retrieval (short note) (10 marks, Dec 2025)** 

Context in Information Retrieval (IR) refers to the dynamic set of implicit and explicit factors such as user profile, task, location, time, and interaction history that surround and influence how a searcher interacts with a retrieval system and interprets results.

- **Resolves query ambiguity**: The same query can mean different things; context disambiguates user intent for accurate retrieval.
- **Enables personalization**: Adapting results to a user's background, expertise, or age improves relevance and usability.
- **Supports task-specific retrieval**: Knowing the user's current goal or work task helps the system prioritize appropriate information.
- **Leverages interaction history**: Past clicks, queries, and relevance feedback inform better ranking for current searches.
- **Adapts to spatio-temporal factors**: Location and time constraints filter results to what is situationally relevant.
- **Accounts for environmental context**: Device type, noise level, and surrounding conditions shape how results should be presented.
- **Constrains the search space**: Contextual data reduces complexity by filtering out irrelevant documents before ranking.
- **Improves relevance judgment**: Context aids users in assessing whether retrieved information meets their actual need.
- **Drives intelligent IR systems**: Moving beyond statistical matching to context-aware retrieval is essential for next-generation search engines.