# LangChain RAG Implementation & Vector Search Pipeline

A complete Retrieval-Augmented Generation (RAG) implementation built with LangChain, Chroma vector database, Groq LLM inference, and Hugging Face local embeddings. 

This repository contains hands-on implementations covering document ingestion, hierarchical chunking, vector persistence, metadata management, MMR retrieval, and LCEL (LangChain Expression Language) orchestration.

---

## Architecture Overview

1. **Document Loading**: Ingestion of raw educational course files (`.docx`) using `Docx2txtLoader`.
2. **Chunking Strategy**: 
   - Structural splitting using `MarkdownHeaderTextSplitter` based on `# Course Title` and `## Lecture Title`.
   - Secondary chunking via `CharacterTextSplitter` with overlapping windows (`chunk_size=500`, `chunk_overlap=50`).
3. **Embeddings**: Open-source local vector representations via `sentence-transformers/all-MiniLM-L6-v2` (`langchain-huggingface`).
4. **Vector Store & Persistence**: Stored and retrieved on disk using `Chroma` (`langchain-chroma`).
5. **Retrieval**: Maximal Marginal Relevance (`MMR`) search to optimize relevancy while minimizing redundancy (`k=3`, `lambda_mult=0.7`).
6. **Inference & Generation**: Low-latency generation powered by Groq API using modern instruction models piped through custom LCEL prompts.

---

## Tech Stack

- **Framework**: LangChain (`langchain-core`, `langchain-community`)
- **LLM Engine**: Groq API (`langchain-groq`)
- **Embeddings**: Hugging Face Hub / `sentence-transformers`
- **Vector Database**: ChromaDB (`langchain-chroma`)
- **Environment Management**: `python-dotenv`

---

## Setup & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/MuhammadEhtisham776/Langchain-with-RAG.git
cd Langchain-with-RAG