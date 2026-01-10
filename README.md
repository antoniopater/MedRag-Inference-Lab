# MedRAG-Inference-Lab

A repository dedicated to learning and implementing advanced **Retrieval-Augmented Generation (RAG)** systems with a special focus on the medical domain.

The main goal is to progress from basic RAG to agent-based and graph-based systems, ensuring high precision, no hallucinations, and security of medical data.

---

## 🛤️ Development Roadmap (8 Weeks)

### Week 1: Foundations and Privacy (Local LLMs)

- **Topic:** RAG architecture, vectorization, and local environment setup (Ollama/vLLM).
- **To Watch:** [LangChain for LLM Application Development](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/)
- **To Read:** Qdrant documentation (HNSW Indexing).

### Week 2: Parsing and Semantic Chunking

- **Topic:** Intelligent splitting of medical articles using NLP.
- **To Watch:** [5 Levels Of Text Splitting (Greg Kamradt)](https://www.youtube.com/watch?v=8OJC21T2SL4)
- **To Read:** `unstructured` library and `SciSpacy` documentation.

### Week 3: Hybrid Search and Intelligent Routing

- **Topic:** Combining vectors with BM25 and query routing.
- **To Read:** Paper: _A Simple but Tough-to-Beat Baseline for Hybrid Search_.
- **Task:** Implementation of RRF (Reciprocal Rank Fusion) algorithm.

### Week 4: Advanced Retrieval (Parent-Child & Reranking)

- **Topic:** Context optimization and selection of best chunks.
- **To Watch:** [Building and Evaluating Advanced RAG](https://www.deeplearning.ai/short-courses/building-evaluating-advanced-rag/)
- **To Read:** Cohere Rerank documentation.

### Week 5: Scientific Evaluation (RAGAS Methodology)

- **Topic:** Measurable quality: Faithfulness, Relevancy, Groundedness.
- **To Read:** Paper: _RAGAS: Automated Evaluation of Retrieval Augmented Generation_.
- **Task:** Creation of a test "Ground Truth" dataset.

### Week 6: Agentic RAG (Self-Correction)

- **Topic:** Decision loops and real-time error correction.
- **To Watch:** [AI Agents in LangGraph](https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/)
- **Tools:** LangGraph.

### Week 7: Medical Domain (GraphRAG & Ontologies)

- **Topic:** Utilizing UMLS, MeSH, and knowledge graphs.
- **To Read:** Paper: _From Local to Global: A GraphRAG Approach_.
- **To Read:** Paper: _Med-RAG: Finding Answers in 10 Million Medical Papers_.

### Week 8: Optimization and Publication

- **Topic:** Finalization of API (FastAPI), UI (Streamlit), and results analysis.
- **Tools:** Arize Phoenix (Observability).

---

## 🛠️ Technology Stack

- **Language:** Python 3.10+
- **Orchestration:** LlamaIndex / LangGraph
- **Vector Database:** Qdrant (Docker)
- **Models:** Llama 3.1 (Local via Ollama), GPT-4o (for evaluation)
- **Evaluation:** RAGAS / DeepEval

---

## 📁 Project Structure

```
MedRAG-Inference-Lab/
├── data/                   # Input data
│   ├── raw/                # Original PDFs/articles from PubMed
│   └── processed/          # Parsed JSONs/texts after chunking
├── notebooks/              # Jupyter Notebooks for quick experiments
├── src/                    # Main application source code
│   ├── ingestion/          # ETL: loading and indexing data
│   ├── retrieval/          # Search logic
│   ├── chains/             # RAG flow (LangGraph / LlamaIndex)
│   └── utils/              # Helper functions (logging, PII anonymization)
├── evaluation/             # Quality testing scripts (RAGAS)
├── api/                    # Server layer
├── ui/                     # User interface
├── config/                 # Configuration files
└── tests/                  # Unit tests (Pytest)
```

---

## 🔬 Research Methodology

Within this project, two hypotheses will be tested:

1. **Hybrid Search Impact:** Introducing hybrid search (BM25 + Vectors) significantly improves precision in searching medical terminology (UMLS).

2. **Re-ranking Module Effectiveness:** Applying a re-ranking module minimizes the "Lost in the Middle" phenomenon in long context windows.

---

## 📚 Key Resources

### Courses

- [LangChain for LLM Application Development](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/)
- [Building and Evaluating Advanced RAG](https://www.deeplearning.ai/short-courses/building-evaluating-advanced-rag/)
- [AI Agents in LangGraph](https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/)

### Videos

- [5 Levels Of Text Splitting (Greg Kamradt)](https://www.youtube.com/watch?v=8OJC21T2SL4)

### Papers

- _A Simple but Tough-to-Beat Baseline for Hybrid Search_
- _RAGAS: Automated Evaluation of Retrieval Augmented Generation_
- _From Local to Global: A GraphRAG Approach_
- _Med-RAG: Finding Answers in 10 Million Medical Papers_

### Documentation

- [Qdrant Documentation](https://qdrant.tech/documentation/) - HNSW Indexing
- [Unstructured Library](https://unstructured-io.github.io/unstructured/)
- [SciSpacy](https://spacy.io/universe/project/scispacy)
- [Cohere Rerank](https://cohere.com/rerank)

---

## 🚀 Getting Started

_More details coming soon as the project develops._

---

## 📝 License

See [LICENSE](LICENSE) for details.
