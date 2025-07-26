# 🔍 Neural Search Engine for Scientific Research Papers

This project presents a **hybrid neural search engine** that enables **context-aware** and **equation-based** search for scientific research papers. It is specifically designed to address the limitations of traditional keyword-based search systems in understanding deep semantic meaning and mathematical expressions.

---

## 💡 Motivation

The explosive growth of academic literature (e.g., on arXiv) has made it difficult for researchers and students to find the most relevant papers using conventional search engines. These engines rely heavily on keyword matching and struggle with:
- Understanding **semantic meaning**
- Interpreting **LaTeX equations**
- Matching documents **without exact keyword overlap**

This project addresses these challenges through a **hybrid search engine** that combines both **lexical and semantic techniques** for accurate, flexible, and domain-specific scientific paper retrieval.

---

## 🎯 Objectives

- ✅ Support **natural language** and **LaTeX-based equation** queries
- ✅ Retrieve scientific papers using both **keyword** and **semantic** matching
- ✅ Use **BM25** for initial lexical ranking
- ✅ Use **SciBERT + FAISS** for semantic and equation retrieval
- ✅ Provide an **interactive interface** using Streamlit

---

## ⚙️ Technical Methodology

### 1. **Data Preprocessing**
- Academic papers (from arXiv dataset) were extracted from a JSONL file
- Text fields: title + abstract → merged into one document
- LaTeX equations were normalized and cleaned
- Tokenization applied using **NLTK** for BM25 compatibility
- Semantic embeddings generated using **SciBERT**

---

### 2. **Lexical Search: BM25**
- Implemented using the `rank_bm25` library
- Scores documents based on TF-IDF-like logic:
  - High frequency → higher relevance
  - Document length normalization
- BM25 is fast and efficient but cannot capture deep meaning or context

---

### 3. **Semantic Search: SciBERT + FAISS**
- **SciBERT**: A domain-specific version of BERT pretrained on scientific corpora
- Embeddings represent contextual meaning in text and equations
- **FAISS**: Facebook AI Similarity Search for vector-based retrieval
- Cosine similarity used to rank vectors based on semantic closeness

---

### 4. **Equation-Based Search**
- LaTeX-formatted equations embedded as vectors using SciBERT
- FAISS index used to find the nearest vector match for given queries
- Supports pure equation queries (e.g., `\int_{a}^{b} f(x) dx = F(b) - F(a)`)

---

### 5. **Hybrid Retrieval Pipeline**
- **Text Query Flow:**
  - Step 1: BM25 selects top-N candidate documents
  - Step 2: SciBERT + FAISS re-ranks them by semantic similarity

- **Equation Query Flow:**
  - Directly retrieves most similar equation vectors using FAISS

- The hybrid system ensures:
  - High **precision** and **recall**
  - Contextually relevant results even when keywords differ

---

## 🛠️ Tools & Technologies

| Component          | Tool/Library                     |
|--------------------|----------------------------------|
| Programming Lang   | Python 3.8+                      |
| Tokenization       | NLTK                             |
| Lexical Search     | rank_bm25                        |
| Semantic Model     | SciBERT (via HuggingFace)        |
| Vector Search      | FAISS (Facebook AI)              |
| Frontend           | Streamlit                        |
| Evaluation         | Cosine Similarity, Manual Tests  |

---

## 📌 Limitations

- Supports either text **or** equation queries (not combined multimodal)
- Equation embeddings lose meaning if LaTeX is malformed or too short
- FAISS indexing on large datasets requires significant memory (RAM)
- Some subtle LaTeX constructs may not be fully parsed using regex-based cleaning

---

## 🚀 Future Enhancements

- Enable **multi-modal queries** (text + equation together)
- Add **OCR support** for equation input from scanned images
- Improve equation understanding using **MathBERT**
- Add **user feedback loop** for personalized relevance learning
- Enable **multi-lingual scientific paper search**

---

## 📄 Project Report

For detailed design, implementation architecture, module descriptions, and testing results:  
📘 [View Full Project Report (PDF)](./SearchIQ_Report.pdf)

---

## 👩‍💻 Team

- **Deekshitha S K** – 1RVU22CSE047  
- **Nayana C V** – 1RVU22CSE110  
- **Varsha C** – 1RVU22CSE185  
Guided by: **Prof. Uma Shankari**, RV University, Bengaluru

---
