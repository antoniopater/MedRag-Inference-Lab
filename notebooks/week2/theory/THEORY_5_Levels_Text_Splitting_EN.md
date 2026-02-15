# 📚 Theory: 5 Levels of Text Splitting

> *"Your goal is not to split text for the sake of splitting. Your goal is to prepare data in a format that enables valuable retrieval later."*

---

## 🎯 What is Text Splitting?

**Text splitting** (chunking) is the process of dividing data into smaller pieces — an essential step before the retrieval stage in RAG systems.

### Key Question

> **What is the optimal way to pass the language model exactly the data it needs to perform its task?**

---

## 🔍 What is Retrieval?

**Retrieval** is the process of gathering relevant information for the language model. It is the orchestration of tools and techniques aimed at "fetching" exactly what the model needs.

### Why not pass "everything"? (The "kitchen sink" approach)

1. **Context limits** — models have an upper bound on the amount of data they can process
2. **Signal-to-noise ratio** — too much irrelevant information in the context destroys performance. Models perform better when unnecessary noise is removed from the data

---

## 📊 Two Approaches to Strategy

| Approach | Analogy | Focus |
|----------|---------|-------|
| **Naive** | Sorting books by size and shelf space | Physical structure of text (character count, paragraphs, code syntax) |
| **Semantic & agentic** | Categorizing books by genre and topic | Meaning (what and why is written) and context |

---

## 🪜 5 Levels of Text Splitting

### Level 1: Character Splitting

- **Description:** Simplest, rigid method — splitting at a fixed number of characters
- **Drawbacks:** Often cuts words or sentences in half — rarely useful in production
- **Use case:** Quick prototyping, testing

---

### Level 2: Recursive Character Splitting

- **Description:** Takes into account text structure (paragraphs, newlines, punctuation)
- **Principle:** Splits text logically, keeping related fragments together
- **Recommendation:** ⭐ **Recommended starting point** for most projects

---

### Level 3: Document-Specific Splitting

- **Description:** Adapting the strategy to the file format
- **Formats:** Markdown, Python/JS code, PDFs with tables and images
- **Goal:** Leverage natural separators (headers, class definitions, sections) to group information

---

### Level 4: Semantic Splitting

- **Description:** Uses embeddings (vector representations of text)
- **Mechanism:** The algorithm examines the meaning of sentences. When the distance (semantic difference) between sentences is large → a split occurs (*break point*)
- **Result:** Grouping thematically similar content

---

### Level 5: Agentic Splitting

- **Description:** Experimental method — system acting as an agent
- **Process:** Analyzes text sentence by sentence and decides: *Does this sentence fit the current chunk, or should it start a new one?*
- **Characteristics:** Slow and costly, but **closest** to how a human would split text

---

## 🚀 Bonus: Advanced Retrieval Tactics

Strategies that go beyond mere text splitting:

1. **Separating indexing from generation**  
   Search based on text summaries or hypothetical questions, but pass the full raw document to the model.

2. **Parent Document Retrieval**  
   Search for a small, precise fragment (better match), but return that fragment to the model **with broader context**.

---

## 📋 Summary

| Level | Name | Complexity | Recommendation |
|:-----:|------|------------|----------------|
| 1 | Character | Low | Prototypes |
| 2 | Recursive Character | Medium | **Start for most** |
| 3 | Document Specific | Medium–High | Specialized documents |
| 4 | Semantic | High | Quality optimization |
| 5 | Agentic | Very High | Experiments |
