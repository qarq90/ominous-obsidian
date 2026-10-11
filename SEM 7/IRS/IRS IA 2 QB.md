### Q1 (2 Marks Each)

1. What is a feature vector in Multimedia IR? Give one example of an image feature.
2. Differentiate between Browsing and Searching on the Web (any two points).
3. What are Starting points in a search interface? Give two examples.
4. What is SeeSoft? State its use.
5. Define Metadata. List any two types of metadata.
6. Define a Meta-search engine. Give one example.
7. What is Stemming? Explain with any two examples.
8. What is Human Computer Interaction (HCI)? State its importance in an IR user interface.
9. What is KWIC (Key Word In Context)? Where is it used?
10. Differentiate between HTML and XML (any two points).

---

### Q2 (5 Marks Each)

1. Explain Suffix Trees and Suffix Arrays with an example. Show how the pattern 'ana' is searched in the text 'banana'.
2. Explain the different Query Specification interfaces (Boolean, natural language, form-based and graphical) with suitable examples.
3. Explain how Relevance Judgments are used in an IR user interface to improve search results. Describe relevance feedback in the interface.
4. Explain agglomerative hierarchical clustering. Apply the single-link method on the following distance matrix of five documents D1–D5 and draw the dendrogram.

   Distance matrix: D1-D2 = 2, D1-D3 = 6, D1-D4 = 10, D1-D5 = 9, D2-D3 = 5, D2-D4 = 9, D2-D5 = 8, D3-D4 = 4, D3-D5 = 5, D4-D5 = 3.

   **Answer check:** merges at 2 (D1,D2), 3 (D4,D5), 4 (D3 with D4,D5), 5 (final).

5. Consider the following documents (ignore the stop words: is, a, of, from, the):
   - D1: information retrieval is the study of information systems
   - D2: web search is a type of information retrieval
   - D3: data retrieval is different from information retrieval

   (a) Construct the inverted index (term, document id, term frequency).
   (b) Process: (information AND retrieval) AND NOT data; web OR data.

   **Answer check:** (information AND retrieval) AND NOT data = {D1, D2}; web OR data = {D2, D3}.

6. Describe the stages of the Information Access Process with a neat diagram, and evaluate how interface support can help the user at each stage.
7. Analyze the challenges faced in searching the Web. Explain the architecture of a typical Web search engine with a neat diagram.
