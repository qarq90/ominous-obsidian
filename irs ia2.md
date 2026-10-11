# 2 Marks

## 1. What is a feature vector in Multimedia IR? Give one example of an image feature.

- A feature vector is a numerical representation of measurable multimedia characteristics used for similarity-based retrieval.
- It represents properties such as colour, texture, shape, or other extracted features.
- Example: A colour histogram represents the distribution of colours within an image.
- Multimedia systems compare feature vectors to retrieve similar images or other media objects.

## 2. Differentiate between Browsing and Searching on the Web.

|Factor|Browsing|Searching|
|---|---|---|
|User goal|Vague information need|Clearly defined information need|
|Query requirement|No explicit query required|Query formulated before retrieval|
|Approach|Exploratory information discovery|Query-based information retrieval|
|User activity|Follows links and categories|Enters keywords or phrases|
|Direction|Less goal-directed exploration|More goal-directed exploration|
|Information need|Clarifies during exploration|Exists before searching|
|Result organisation|Categories, links, and overviews|Ranked list of documents|
|Example|Exploring YouTube homepage|Searching Google for information|

## 3. What are Starting Points in a search interface? Give two examples.

- Starting points help users begin information discovery when their information needs are unclear.
- They provide initial directions for exploring available information sources or collections.
- Example 1: Lists of collections, such as library database directories.
- Example 2: Overviews showing categories or clusters of similar documents.

## 4. What is SeeSoft? State its use.

- SeeSoft is a visualisation technique that represents text as coloured line strips.
- It was originally developed for visualising source-code changes.
- Each line strip represents text, allowing large amounts of content to be viewed compactly.
- Use: It helps users identify patterns and examine changes across large text files.

## 5. Define Metadata. List any two types of metadata.

- Metadata is structured information describing an object's properties rather than its actual content.
- It is commonly defined as data about data.
- Descriptive metadata: Helps users discover objects through titles, authors, subjects, and keywords.
- Structural metadata: Describes how components of compound objects are organised and connected.

## 6. Define a Meta-search engine. Give one example.

- A meta-search engine sends a user's query to multiple search engines or information sources.
- It collects results from those sources and presents them through a common interface.
- It helps users explore results from several search services without searching each separately.
- Example: Dogpile.

## 7. What is Stemming? Explain with any two examples.

- Stemming is a text-preprocessing technique that reduces related word forms to a common stem.
- It helps information retrieval systems match different morphological forms of words.
- Example 1: Playing → Play.
- Example 2: Connected → Connect.

## 8. What is Human Computer Interaction (HCI)? State its importance in an IR user interface.

- Human-Computer Interaction studies how people interact with computer systems and their interfaces.
- It focuses on designing systems that are usable, understandable, and effective.
- In Information Retrieval, HCI helps users formulate queries and interpret search results.
- It improves feedback, navigation, error recovery, and overall search usability.

## 9. What is KWIC (Key Word In Context)? Where is it used?

- KWIC stands for Key Word In Context.
- It displays a keyword together with the surrounding text in which it occurs.
- It helps users understand how a search term is used within a document.
- Use: Search-result snippets, document indexing, and information access interfaces.

## 10. Differentiate between HTML and XML.

|Factor|HTML|XML|
|---|---|---|
|Full form|HyperText Markup Language|eXtensible Markup Language|
|Primary purpose|Describes web pages|Stores and structures data|
|Tag vocabulary|Predetermined tag vocabulary|User-defined tag vocabulary|
|Main emphasis|Structure and presentation|Structure and meaning|
|Extensibility|Limited custom-tag support|Extensible tag definitions|
|Case sensitivity|Generally case-insensitive|Case-sensitive|
|Closing tags|Some closing tags optional|Every opened tag must close|
|Nesting rules|Browser handles certain errors|Proper nesting strictly required|
|Example tags|`<title>`, `<p>`, `<b>`|`<price>`, `<author>`, `<studentID>`|
|Typical usage|Web-page display|Data exchange and storage|

# 5 Marks

## 1. Explain Suffix Trees and Suffix Arrays with an example. Show how the pattern 'ana' is searched in the text 'banana'.

### A. Suffix Tree

- A suffix tree is a compressed trie representing all suffixes of a given text.
    
- Each suffix begins at a different position in the original text.
    
- Common prefixes are represented by shared paths, reducing unnecessary repetition.
    
- Leaves identify the starting positions of suffixes in the original text.
    
- It supports efficient substring searching by traversing edges matching the query pattern.
    
- For the text `banana`, the suffixes include `banana`, `anana`, `nana`, `ana`, `na`, and `a`.
    
- Searching for `ana` follows the matching path in the suffix tree.
    
- The pattern occurs at starting positions 2 and 4, using one-based indexing.
    

### B. Suffix Array

- A suffix array stores starting positions of all suffixes in lexicographical order.
    
- Unlike a suffix tree, it stores positions in an array rather than tree nodes.
    
- Each array entry identifies a suffix beginning at its corresponding text position.
    
- Binary search locates suffixes whose prefixes match the required pattern.
    
- For `banana`, the sorted suffix array is `[6, 4, 2, 1, 5, 3]`.
    
- The suffixes beginning at positions 4 and 2 both start with `ana`.
    
- Therefore, the pattern occurs at positions 2 and 4.
    

### Suffixes of `banana`

|Starting position|Suffix|
|---|---|
|1|banana|
|2|anana|
|3|nana|
|4|ana|
|5|na|
|6|a|

### Sorted suffixes and suffix array

|Sorted order|Starting position|Suffix|
|---|---|---|
|1|6|a|
|2|4|ana|
|3|2|anana|
|4|1|banana|
|5|5|na|
|6|3|nana|

### Searching for `ana`

#chatgpt-mermaid-_r_jg_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(237, 237, 237);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-_r_jg_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-_r_jg_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-_r_jg_ .error-icon{fill:rgb(48, 48, 48);}#chatgpt-mermaid-_r_jg_ .error-text{fill:rgb(237, 237, 237);stroke:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-_r_jg_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-_r_jg_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-_r_jg_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-_r_jg_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-_r_jg_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-_r_jg_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jg_ .marker.cross{stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jg_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-_r_jg_ p{margin:0;}#chatgpt-mermaid-_r_jg_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ .cluster-label text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ .cluster-label span{color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-_r_jg_ .label text,#chatgpt-mermaid-_r_jg_ span{fill:rgb(237, 237, 237);color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ .node rect,#chatgpt-mermaid-_r_jg_ .node circle,#chatgpt-mermaid-_r_jg_ .node ellipse,#chatgpt-mermaid-_r_jg_ .node polygon,#chatgpt-mermaid-_r_jg_ .node path{fill:rgb(9, 23, 44);stroke:rgb(31, 78, 148);stroke-width:1px;}#chatgpt-mermaid-_r_jg_ .rough-node .label text,#chatgpt-mermaid-_r_jg_ .node .label text,#chatgpt-mermaid-_r_jg_ .image-shape .label,#chatgpt-mermaid-_r_jg_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-_r_jg_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-_r_jg_ .rough-node .label,#chatgpt-mermaid-_r_jg_ .node .label,#chatgpt-mermaid-_r_jg_ .image-shape .label,#chatgpt-mermaid-_r_jg_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-_r_jg_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-_r_jg_ .root .anchor path{fill:rgb(175, 175, 175)!important;stroke-width:0;stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jg_ .arrowheadPath{fill:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jg_ .edgePath .path{stroke:rgb(175, 175, 175);stroke-width:1px;}#chatgpt-mermaid-_r_jg_ .flowchart-link{stroke:rgb(175, 175, 175);fill:none;}#chatgpt-mermaid-_r_jg_ .edgeLabel{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-_r_jg_ .edgeLabel p{background-color:rgb(0, 0, 0);}#chatgpt-mermaid-_r_jg_ .edgeLabel rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-_r_jg_ .labelBkg{background-color:rgba(0, 0, 0, 0.5);}#chatgpt-mermaid-_r_jg_ .cluster rect{fill:rgb(48, 48, 48);stroke:rgba(255, 255, 255, 0.15);stroke-width:1px;}#chatgpt-mermaid-_r_jg_ .cluster text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ .cluster span{color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(48, 48, 48);border:1px solid rgba(255, 255, 255, 0.15);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-_r_jg_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jg_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-_r_jg_ .icon-shape,#chatgpt-mermaid-_r_jg_ .image-shape{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-_r_jg_ .icon-shape p,#chatgpt-mermaid-_r_jg_ .image-shape p{background-color:rgb(0, 0, 0);padding:2px;}#chatgpt-mermaid-_r_jg_ .icon-shape .label rect,#chatgpt-mermaid-_r_jg_ .image-shape .label rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-_r_jg_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-_r_jg_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-_r_jg_ .node .neo-node{stroke:rgb(31, 78, 148);}#chatgpt-mermaid-_r_jg_ [data-look="neo"].node rect,#chatgpt-mermaid-_r_jg_ [data-look="neo"].cluster rect,#chatgpt-mermaid-_r_jg_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-_r_jg_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jg_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-_r_jg_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-_r_jg_-gradient);stroke-width:1px;}#chatgpt-mermaid-_r_jg_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jg_ [data-look="neo"].node .neo-line path{stroke:rgb(31, 78, 148);filter:none;}#chatgpt-mermaid-_r_jg_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-_r_jg_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jg_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-_r_jg_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-_r_jg_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jg_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-_r_jg_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jg_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(153, 206, 255);}#chatgpt-mermaid-_r_jg_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(153, 206, 255);}#chatgpt-mermaid-_r_jg_ .node tspan[font-weight="normal"],#chatgpt-mermaid-_r_jg_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-_r_jg_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(0, 14, 26);stroke:rgb(26, 62, 95);stroke-width:1px;}#chatgpt-mermaid-_r_jg_ .node rect,#chatgpt-mermaid-_r_jg_ .node circle,#chatgpt-mermaid-_r_jg_ .node ellipse,#chatgpt-mermaid-_r_jg_ .node polygon,#chatgpt-mermaid-_r_jg_ .node path{fill:rgb(0, 40, 77);stroke:rgba(255, 255, 255, 0.1);stroke-width:1px;}#chatgpt-mermaid-_r_jg_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-_r_jg_ .node.mermaid-decision .label-container{fill:rgb(0, 14, 26);stroke:rgb(26, 62, 95);stroke-dasharray:2px,2px;}#chatgpt-mermaid-_r_jg_ .edgePaths .flowchart-link{stroke:rgb(175, 175, 175);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-_r_jg_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jg_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}Original text: bananaConstruct suffix indexSearch pattern: anaSuffix at position 2: ananaSuffix at position 4: anaOccurrences at positions 2 and4

Conclusion: Suffix trees organise suffixes hierarchically, whereas suffix arrays store sorted suffix positions.

## 2. Explain the different Query Specification interfaces: Boolean, natural language, form-based and graphical, with suitable examples.

### A. Boolean Query Interface

- A Boolean query interface allows users to combine search terms using logical operators.
    
- The principal operators are AND, OR, and NOT.
    
- AND retrieves documents containing both specified terms.
    
- OR retrieves documents containing either term or both terms.
    
- NOT excludes documents containing the specified unwanted term.
    
- Boolean querying provides precise control over which documents satisfy the search conditions.
    
- However, pure Boolean retrieval generally returns matching documents without ranking them by relevance.
    
- Example: `information AND retrieval AND NOT database`.
    

### B. Natural Language Interface

- A natural language interface allows users to express information needs using ordinary sentences.
    
- Users can submit questions or descriptions without learning formal query syntax.
    
- The system interprets the submitted text and identifies potentially relevant documents.
    
- Retrieved documents may be ranked according to their estimated relevance.
    
- Question-answering systems can identify sentences containing important phrases from the question.
    
- This interface is convenient for beginners unfamiliar with Boolean operators.
    
- Example: `How does information retrieval work?`
    

### C. Form-Based Interface

- A form-based interface provides predefined fields and menus for specifying search conditions.
    
- Users enter information into fields without remembering complex query commands.
    
- Fields may represent attributes such as author, title, publication year, or subject.
    
- Users can combine multiple conditions to narrow their search.
    
- Faceted querying groups related alternatives while combining different categories of requirements.
    
- This interface is useful for structured searches and database catalogues.
    
- Example: A library catalogue form containing author, title, and publication-year fields.
    

### D. Graphical Query Interface

- A graphical query interface allows users to construct queries through visual elements.
    
- Users manipulate icons, circles, diagrams, or other graphical representations.
    
- Overlapping circles can represent AND operations between search terms.
    
- Selecting alternative regions can represent OR operations.
    
- Excluding a region can represent NOT operations.
    
- Direct manipulation makes query construction easier for users unfamiliar with command syntax.
    
- Example: A Venn-diagram interface combining information and retrieval.
    

### Diagram

#chatgpt-mermaid-_r_jp_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(237, 237, 237);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-_r_jp_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-_r_jp_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-_r_jp_ .error-icon{fill:rgb(48, 48, 48);}#chatgpt-mermaid-_r_jp_ .error-text{fill:rgb(237, 237, 237);stroke:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-_r_jp_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-_r_jp_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-_r_jp_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-_r_jp_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-_r_jp_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-_r_jp_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jp_ .marker.cross{stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jp_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-_r_jp_ p{margin:0;}#chatgpt-mermaid-_r_jp_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ .cluster-label text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ .cluster-label span{color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-_r_jp_ .label text,#chatgpt-mermaid-_r_jp_ span{fill:rgb(237, 237, 237);color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ .node rect,#chatgpt-mermaid-_r_jp_ .node circle,#chatgpt-mermaid-_r_jp_ .node ellipse,#chatgpt-mermaid-_r_jp_ .node polygon,#chatgpt-mermaid-_r_jp_ .node path{fill:rgb(9, 23, 44);stroke:rgb(31, 78, 148);stroke-width:1px;}#chatgpt-mermaid-_r_jp_ .rough-node .label text,#chatgpt-mermaid-_r_jp_ .node .label text,#chatgpt-mermaid-_r_jp_ .image-shape .label,#chatgpt-mermaid-_r_jp_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-_r_jp_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-_r_jp_ .rough-node .label,#chatgpt-mermaid-_r_jp_ .node .label,#chatgpt-mermaid-_r_jp_ .image-shape .label,#chatgpt-mermaid-_r_jp_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-_r_jp_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-_r_jp_ .root .anchor path{fill:rgb(175, 175, 175)!important;stroke-width:0;stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jp_ .arrowheadPath{fill:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jp_ .edgePath .path{stroke:rgb(175, 175, 175);stroke-width:1px;}#chatgpt-mermaid-_r_jp_ .flowchart-link{stroke:rgb(175, 175, 175);fill:none;}#chatgpt-mermaid-_r_jp_ .edgeLabel{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-_r_jp_ .edgeLabel p{background-color:rgb(0, 0, 0);}#chatgpt-mermaid-_r_jp_ .edgeLabel rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-_r_jp_ .labelBkg{background-color:rgba(0, 0, 0, 0.5);}#chatgpt-mermaid-_r_jp_ .cluster rect{fill:rgb(48, 48, 48);stroke:rgba(255, 255, 255, 0.15);stroke-width:1px;}#chatgpt-mermaid-_r_jp_ .cluster text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ .cluster span{color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(48, 48, 48);border:1px solid rgba(255, 255, 255, 0.15);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-_r_jp_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_jp_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-_r_jp_ .icon-shape,#chatgpt-mermaid-_r_jp_ .image-shape{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-_r_jp_ .icon-shape p,#chatgpt-mermaid-_r_jp_ .image-shape p{background-color:rgb(0, 0, 0);padding:2px;}#chatgpt-mermaid-_r_jp_ .icon-shape .label rect,#chatgpt-mermaid-_r_jp_ .image-shape .label rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-_r_jp_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-_r_jp_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-_r_jp_ .node .neo-node{stroke:rgb(31, 78, 148);}#chatgpt-mermaid-_r_jp_ [data-look="neo"].node rect,#chatgpt-mermaid-_r_jp_ [data-look="neo"].cluster rect,#chatgpt-mermaid-_r_jp_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-_r_jp_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jp_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-_r_jp_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-_r_jp_-gradient);stroke-width:1px;}#chatgpt-mermaid-_r_jp_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jp_ [data-look="neo"].node .neo-line path{stroke:rgb(31, 78, 148);filter:none;}#chatgpt-mermaid-_r_jp_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-_r_jp_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jp_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-_r_jp_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-_r_jp_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jp_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-_r_jp_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_jp_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(153, 206, 255);}#chatgpt-mermaid-_r_jp_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(153, 206, 255);}#chatgpt-mermaid-_r_jp_ .node tspan[font-weight="normal"],#chatgpt-mermaid-_r_jp_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-_r_jp_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(0, 14, 26);stroke:rgb(26, 62, 95);stroke-width:1px;}#chatgpt-mermaid-_r_jp_ .node rect,#chatgpt-mermaid-_r_jp_ .node circle,#chatgpt-mermaid-_r_jp_ .node ellipse,#chatgpt-mermaid-_r_jp_ .node polygon,#chatgpt-mermaid-_r_jp_ .node path{fill:rgb(0, 40, 77);stroke:rgba(255, 255, 255, 0.1);stroke-width:1px;}#chatgpt-mermaid-_r_jp_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-_r_jp_ .node.mermaid-decision .label-container{fill:rgb(0, 14, 26);stroke:rgb(26, 62, 95);stroke-dasharray:2px,2px;}#chatgpt-mermaid-_r_jp_ .edgePaths .flowchart-link{stroke:rgb(175, 175, 175);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-_r_jp_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_jp_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}Query Specification InterfacesBoolean InterfaceNatural Language InterfaceForm-Based InterfaceGraphical InterfaceLogical operatorsOrdinary sentencesFields and menusVisual query construction

Conclusion: Different query interfaces support different levels of user expertise and query complexity.

## 3. Explain how Relevance Judgments are used in an IR user interface to improve search results. Describe relevance feedback in the interface.

### A. Relevance Judgments

- Relevance judgments determine whether retrieved documents satisfy the user's underlying information need.
    
- Users examine result titles, snippets, metadata, and document contents to assess usefulness.
    
- A relevant document provides information that addresses the user's actual requirement.
    
- An irrelevant document may contain query keywords without answering the user's question.
    
- Judgments help users distinguish useful results from superficially matching documents.
    
- They also reveal whether the original query accurately represented the information need.
    
- Relevance judgments support query refinement and improve subsequent retrieval.
    

### B. Relevance Feedback

- Relevance feedback uses user judgments to modify a search and improve subsequent results.
    
- Users identify retrieved documents as relevant or irrelevant through interface controls.
    
- The system analyses these judgments to adjust the query or retrieval model.
    
- Terms associated with relevant documents may be added to the revised query.
    
- Unhelpful terms or irrelevant documents may influence the system's subsequent retrieval decisions.
    
- The revised query retrieves documents more closely aligned with the user's information need.
    
- The user can evaluate these results and repeat the feedback process.
    

### C. Role of the IR User Interface

- Highlighting: Displays query terms within snippets, helping users locate relevant passages.
    
- Document surrogates: Show titles, sources, dates, and excerpts before opening documents.
    
- Relevance controls: Allow users to mark documents as useful or irrelevant.
    
- Query reformulation: Provides editing tools for changing keywords and search conditions.
    
- Search history: Preserves earlier queries and supports repeated searches.
    
- Result comparison: Helps users evaluate multiple documents before selecting useful information.
    
- Informative feedback: Shows how queries and retrieval results relate to one another.
    

### Diagram

#chatgpt-mermaid-_r_k2_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(237, 237, 237);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-_r_k2_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-_r_k2_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-_r_k2_ .error-icon{fill:rgb(48, 48, 48);}#chatgpt-mermaid-_r_k2_ .error-text{fill:rgb(237, 237, 237);stroke:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-_r_k2_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-_r_k2_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-_r_k2_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-_r_k2_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-_r_k2_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-_r_k2_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_k2_ .marker.cross{stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_k2_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-_r_k2_ p{margin:0;}#chatgpt-mermaid-_r_k2_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ .cluster-label text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ .cluster-label span{color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-_r_k2_ .label text,#chatgpt-mermaid-_r_k2_ span{fill:rgb(237, 237, 237);color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ .node rect,#chatgpt-mermaid-_r_k2_ .node circle,#chatgpt-mermaid-_r_k2_ .node ellipse,#chatgpt-mermaid-_r_k2_ .node polygon,#chatgpt-mermaid-_r_k2_ .node path{fill:rgb(9, 23, 44);stroke:rgb(31, 78, 148);stroke-width:1px;}#chatgpt-mermaid-_r_k2_ .rough-node .label text,#chatgpt-mermaid-_r_k2_ .node .label text,#chatgpt-mermaid-_r_k2_ .image-shape .label,#chatgpt-mermaid-_r_k2_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-_r_k2_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-_r_k2_ .rough-node .label,#chatgpt-mermaid-_r_k2_ .node .label,#chatgpt-mermaid-_r_k2_ .image-shape .label,#chatgpt-mermaid-_r_k2_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-_r_k2_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-_r_k2_ .root .anchor path{fill:rgb(175, 175, 175)!important;stroke-width:0;stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_k2_ .arrowheadPath{fill:rgb(175, 175, 175);}#chatgpt-mermaid-_r_k2_ .edgePath .path{stroke:rgb(175, 175, 175);stroke-width:1px;}#chatgpt-mermaid-_r_k2_ .flowchart-link{stroke:rgb(175, 175, 175);fill:none;}#chatgpt-mermaid-_r_k2_ .edgeLabel{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-_r_k2_ .edgeLabel p{background-color:rgb(0, 0, 0);}#chatgpt-mermaid-_r_k2_ .edgeLabel rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-_r_k2_ .labelBkg{background-color:rgba(0, 0, 0, 0.5);}#chatgpt-mermaid-_r_k2_ .cluster rect{fill:rgb(48, 48, 48);stroke:rgba(255, 255, 255, 0.15);stroke-width:1px;}#chatgpt-mermaid-_r_k2_ .cluster text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ .cluster span{color:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(48, 48, 48);border:1px solid rgba(255, 255, 255, 0.15);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-_r_k2_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(237, 237, 237);}#chatgpt-mermaid-_r_k2_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-_r_k2_ .icon-shape,#chatgpt-mermaid-_r_k2_ .image-shape{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-_r_k2_ .icon-shape p,#chatgpt-mermaid-_r_k2_ .image-shape p{background-color:rgb(0, 0, 0);padding:2px;}#chatgpt-mermaid-_r_k2_ .icon-shape .label rect,#chatgpt-mermaid-_r_k2_ .image-shape .label rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-_r_k2_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-_r_k2_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-_r_k2_ .node .neo-node{stroke:rgb(31, 78, 148);}#chatgpt-mermaid-_r_k2_ [data-look="neo"].node rect,#chatgpt-mermaid-_r_k2_ [data-look="neo"].cluster rect,#chatgpt-mermaid-_r_k2_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-_r_k2_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_k2_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-_r_k2_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-_r_k2_-gradient);stroke-width:1px;}#chatgpt-mermaid-_r_k2_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_k2_ [data-look="neo"].node .neo-line path{stroke:rgb(31, 78, 148);filter:none;}#chatgpt-mermaid-_r_k2_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-_r_k2_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_k2_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-_r_k2_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-_r_k2_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_k2_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-_r_k2_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-_r_k2_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(153, 206, 255);}#chatgpt-mermaid-_r_k2_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(153, 206, 255);}#chatgpt-mermaid-_r_k2_ .node tspan[font-weight="normal"],#chatgpt-mermaid-_r_k2_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-_r_k2_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(0, 14, 26);stroke:rgb(26, 62, 95);stroke-width:1px;}#chatgpt-mermaid-_r_k2_ .node rect,#chatgpt-mermaid-_r_k2_ .node circle,#chatgpt-mermaid-_r_k2_ .node ellipse,#chatgpt-mermaid-_r_k2_ .node polygon,#chatgpt-mermaid-_r_k2_ .node path{fill:rgb(0, 40, 77);stroke:rgba(255, 255, 255, 0.1);stroke-width:1px;}#chatgpt-mermaid-_r_k2_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-_r_k2_ .node.mermaid-decision .label-container{fill:rgb(0, 14, 26);stroke:rgb(26, 62, 95);stroke-dasharray:2px,2px;}#chatgpt-mermaid-_r_k2_ .edgePaths .flowchart-link{stroke:rgb(175, 175, 175);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-_r_k2_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-_r_k2_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI","Helvetica","Apple Color Emoji","Arial",sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}Enter Search QueryDisplay Ranked ResultsExamine Titles and SnippetsJudge Document RelevanceProvide Relevance FeedbackAdjust Query or ModelRetrieve Revised Results

Conclusion: Relevance judgments and feedback make retrieval more interactive, adaptive, and responsive to user needs.

## 4. Explain agglomerative hierarchical clustering. Apply the single-link method to the given distance matrix and draw the dendrogram.

### A. Agglomerative Hierarchical Clustering

- Agglomerative hierarchical clustering is a bottom-up technique for grouping similar documents.
    
- Initially, each document forms an individual cluster.
    
- The algorithm identifies the two closest clusters using their distance values.
    
- These clusters merge to form a larger cluster.
    
- Distances between clusters are recalculated after each merger.
    
- The process continues until all documents belong to one cluster.
    
- The resulting hierarchy can be represented using a dendrogram.
    
- The dendrogram displays the order and distance levels of successive mergers.
    

### B. Single-Link Method

- Single-link clustering measures distance using the closest pair of documents across two clusters.
    
- The distance between clusters is the minimum pairwise distance between their members.
    
- It can connect documents through intermediate documents forming a chain.
    
- The smallest available distance determines the next merger.
    
- The process repeats until the final cluster contains every document.
    

The single-link distance is:

\[ D(A,B)=\min_{a\in A,\;b\in B}d(a,b) \]

### C. Given Distance Matrix

|Pair|Distance|
|---|---|
|D1–D2|2|
|D1–D3|6|
|D1–D4|10|
|D1–D5|9|
|D2–D3|5|
|D2–D4|9|
|D2–D5|8|
|D3–D4|4|
|D3–D5|5|
|D4–D5|3|

### D. Clustering Steps

Step 1: Merge D1 and D2

- The smallest distance is \(d(D1,D2)=2\).
    
- Merge D1 and D2 to form cluster \(C_1=\{D1,D2\}\).
    
- The first merger occurs at distance 2.
    

Step 2: Merge D4 and D5

- The next smallest available distance is \(d(D4,D5)=3\).
    
- Merge D4 and D5 to form cluster \(C_2=\{D4,D5\}\).
    
- The second merger occurs at distance 3.
    

Step 3: Merge D3 with cluster C2

- The distance from D3 to C2 is \(\min(4,5)=4\).
    
- The distances are D3–D4 = 4 and D3–D5 = 5.
    
- Merge D3 with C2 to form \(C_3=\{D3,D4,D5\}\).
    
- The third merger occurs at distance 4.
    

Step 4: Perform the final merger

- The distance between C1 and C3 is the minimum cross-cluster distance.
    
- The smallest cross-cluster distance is D2–D3 = 5.
    
- Merge both clusters to obtain \(\{D1,D2,D3,D4,D5\}\).
    
- The final merger occurs at distance 5.
    

### E. Dendrogram

|Iteration|Clusters merged|Distance|
|---|---|---|
|1|D1, D2|2|
|2|D4, D5|3|
|3|D3, (D4, D5)|4|
|4|(D1, D2), (D3, D4, D5)|5|

Final result: The merger sequence is 2 → 3 → 4 → 5, as specified in the question.

## 5. Construct the inverted index and process the Boolean queries.

Given documents:

- D1: information retrieval is the study of information systems
    
- D2: web search is a type of information retrieval
    
- D3: data retrieval is different from information retrieval
    

Ignore the stop words `is`, `a`, `of`, `from`, and `the`.

### A. Inverted Index

An inverted index maps each term to the documents containing it, together with its term frequency.

Step 1: Preprocess the documents

Remove the specified stop words and retain the remaining terms.

- D1: information, retrieval, study, information, systems
    
- D2: web, search, type, information, retrieval
    
- D3: data, retrieval, different, information, retrieval
    

Step 2: Identify terms and frequencies

Count how often each term appears in every document.

|Term|Document ID|Term frequency|
|---|---|---|
|data|D3|1|
|different|D3|1|
|information|D1|2|
|information|D2|1|
|information|D3|1|
|retrieval|D1|1|
|retrieval|D2|1|
|retrieval|D3|2|
|search|D2|1|
|study|D1|1|
|systems|D1|1|
|type|D2|1|
|web|D2|1|

Observation: The term `information` occurs twice in D1, while `retrieval` occurs twice in D3.

### B. Boolean Query Processing

Boolean retrieval uses AND, OR, and NOT to combine document sets.

#### Query 1: `(information AND retrieval) AND NOT data`

Step 1: Retrieve documents containing information

\[ I=\{D1,D2,D3\} \]

Step 2: Retrieve documents containing retrieval

\[ R=\{D1,D2,D3\} \]

Step 3: Apply AND

Both terms must appear in the document.

\[ I\cap R=\{D1,D2,D3\} \]

Step 4: Find documents containing data

\[ D=\{D3\} \]

Step 5: Apply NOT data

Exclude documents containing the term `data`.

\[ (I\cap R)-D=\{D1,D2\} \]

Final answer: \(\boxed{\{D1,D2\}}\)

#### Query 2: `web OR data`

Step 1: Retrieve documents containing web

\[ W=\{D2\} \]

Step 2: Retrieve documents containing data

\[ D=\{D3\} \]

Step 3: Apply OR

OR combines documents containing either term.

\[ W\cup D=\{D2,D3\} \]

Final answer: \(\boxed{\{D2,D3\}}\)

### C. Query Processing Diagram

Conclusion: The inverted index supports efficient Boolean retrieval without scanning every document individually.

## 6. Describe the stages of the Information Access Process with a neat diagram. Evaluate how interface support can help the user at each stage.

### A. Information Access Process

The Information Access Process describes how users identify information needs, retrieve documents, evaluate results, and refine searches.

### B. Stages and Interface Support

1. Information Need

- The user recognises a gap between existing knowledge and required information.
    
- The information need may initially be vague or incompletely understood.
    
- Interface support: Examples, guided discovery, and suggested topics help clarify the need.
    

2. Select System and Collection

- The user selects a suitable information retrieval system and collection.
    
- Selection depends on the topic, available sources, and expected information.
    
- Interface support: Collection directories, source lists, and automated source recommendations guide selection.
    

3. Formulate a Query

- The user translates the information need into searchable words or phrases.
    
- Query formulation determines which documents the system can retrieve.
    
- Interface support: Autocomplete, spelling suggestions, example queries, and advanced search forms assist formulation.
    

4. Send the Query

- The formulated query is submitted to the retrieval system.
    
- The system processes the query and searches its available index.
    
- Interface support: Clear search controls, keyboard accessibility, and query validation simplify submission.
    

5. Receive Results

- The system presents documents matching the submitted query.
    
- Results may be ranked according to their estimated relevance.
    
- Interface support: Titles, URLs, snippets, and relevance-based ordering help users inspect results.
    

6. Scan, Evaluate, and Interpret

- The user examines retrieved documents to determine their usefulness.
    
- Titles, excerpts, and document contents help establish relevance.
    
- Interface support: Highlighting, previews, metadata, and comparison tools reduce evaluation effort.
    

7. Decide Whether to Stop

- The user decides whether the retrieved information satisfies the original need.
    
- Satisfactory results allow the user to finish the search.
    
- Interface support: Saved documents, clear result organisation, and easy access support decision-making.
    

8. Reformulate the Query

- The user changes the query when results are insufficient or irrelevant.
    
- Reformulation may involve new terms, synonyms, or more specific conditions.
    
- Interface support: Search history, query editing, spelling correction, and relevance feedback improve subsequent searches.
    

### C. Information Access Process Diagram

### D. Evaluation of Interface Support

- Reduced cognitive load: Visible choices reduce the need to remember commands and search steps.
    
- Informative feedback: Results and query previews help users understand system behaviour.
    
- Error recovery: Editing, undoing, and repeating searches help users correct mistakes.
    
- Better relevance assessment: Highlighted terms and excerpts help users judge documents efficiently.
    
- Improved query formulation: Suggestions and guided forms assist inexperienced users.
    
- Search continuity: Search history and saved results preserve earlier work.
    
- Flexible exploration: Links and category overviews support users whose needs evolve during searching.
    

Conclusion: Effective interfaces support every stage of information access, from recognising a need to evaluating and refining results.

## 7. Analyze the challenges faced in searching the Web. Explain the architecture of a typical Web search engine with a neat diagram.

### A. Challenges Faced in Web Searching

1. Massive Scale

- The Web contains billions of documents distributed across millions of independently operated servers.
    
- Searching every document sequentially would be inefficient and computationally expensive.
    
- Search engines use indexing to locate relevant documents quickly.
    

2. Lack of Coordination

- The Web has no centrally controlled structure governing how pages are created.
    
- Different websites use different formats, structures, and publishing practices.
    
- Search engines must process heterogeneous content from independent sources.
    

3. Unstructured Data

- Web pages contain text, images, multimedia, and other heterogeneous content.
    
- Unlike relational databases, these documents do not follow one common schema.
    
- Search engines must extract useful information and construct searchable indexes.
    

4. Dynamic Content

- Web pages are frequently created, modified, deleted, or relocated.
    
- Previously indexed information can become outdated or unavailable.
    
- Crawlers must revisit pages to maintain an updated search index.
    

5. Adversarial Behaviour and Spam

- Some website owners manipulate content to influence search-engine rankings.
    
- Search-engine optimisation techniques can be used to improve visibility artificially.
    
- Search engines must identify spam and resist attempts to manipulate results.
    

6. Hyperlinked Structure

- Web pages contain hyperlinks connecting documents across different websites.
    
- Links provide useful information about relationships between pages.
    
- Analysing link structures adds complexity but supports ranking techniques such as PageRank.
    

7. Ambiguous Queries

- Short queries may represent several different user information needs.
    
- The same word can have multiple meanings depending on context.
    
- Search engines must interpret queries and identify documents matching likely user intent.
    

8. Relevance and Ranking

- A query may match thousands or millions of documents.
    
- Search engines must estimate which documents best satisfy the user's information need.
    
- Ranking combines relevance signals to place useful results near the top.
    

### B. Architecture of a Typical Web Search Engine

A Web search engine is an Information Retrieval system operating at the scale of the World Wide Web.

It collects web pages, builds indexes, processes user queries, and returns ranked results.

### 1. Web Crawler

- The crawler discovers web pages by following hyperlinks from previously discovered pages.
    
- It downloads page content from web servers for subsequent processing.
    
- Crawling policies determine which pages to visit and when to revisit them.
    

### 2. Document Repository

- The repository stores downloaded web pages and their associated content.
    
- It provides a source for text extraction, indexing, and later processing.
    
- Stored documents can be updated when the crawler retrieves newer versions.
    

### 3. Document Processor and Indexer

- The processor extracts useful text and document information from downloaded pages.
    
- Text preprocessing may include tokenisation, normalisation, and removal of stop words.
    
- The indexer constructs an inverted index mapping terms to documents containing them.
    
- The index allows efficient retrieval without scanning every stored page.
    

### 4. Inverted Index

- The inverted index stores searchable relationships between terms and document identifiers.
    
- Posting lists identify documents containing particular query terms.
    
- Additional information can support frequency calculations and relevance ranking.
    
- Efficient indexing reduces the time required to process search queries.
    

### 5. Query Processor

- The query processor accepts a user's search terms through the search interface.
    
- It processes the query into a representation suitable for retrieval.
    
- It consults the index to identify candidate documents matching the query.
    
- Query processing may include spelling correction, term normalisation, and query expansion.
    

### 6. Ranking Component

- The ranking component estimates how relevant candidate documents are to the user's query.
    
- It considers textual relevance and other useful ranking signals.
    
- Link-based measures, including PageRank, can help assess the importance of web pages.
    
- The system orders documents to present the most promising results first.
    

### 7. Search Results Interface

- The interface displays ranked documents with titles, URLs, and descriptive snippets.
    
- Highlighted query terms help users identify useful passages quickly.
    
- Users can open results, refine queries, or perform additional searches.
    

### C. Architecture Diagram

### D. Offline and Online Processing

Offline processing

- Crawling discovers and downloads web pages before individual queries arrive.
    
- Document processing extracts text and prepares content for indexing.
    
- Index construction creates searchable structures for efficient future retrieval.
    
- The repository and index are updated as new information becomes available.
    

Online processing

- The user enters a query through the search interface.
    
- The query processor searches the index for candidate documents.
    
- The ranking component orders candidates according to estimated relevance.
    
- The interface displays results for user evaluation and further exploration.
    

### E. Conclusion

A Web search engine combines crawling, indexing, query processing, and ranking to retrieve relevant information efficiently.

Its architecture addresses the Web's enormous scale, unstructured content, changing pages, and lack of coordination.