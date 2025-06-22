# 🧬 Embeddings Explained

## What is an Embedding?
An embedding is a numeric representation of a piece of text (word, sentence, or paragraph) in high-dimensional space.

## Why It Matters?
- Enables **semantic search**
- Powers vector databases
- Lets LLMs work with memory

## Use Cases
- Search your notes by meaning, not keyword
- Summarize related tickets
- Find duplicates or related bugs

## Key Concepts
- Dimensionality (e.g., 1536 for OpenAI)
- Cosine similarity
- Chunking strategy before embedding

## Tools
- OpenAI Embeddings (text-embedding-3-small)
- Ollama (mxbai, all-MiniLM)
- `llama-index`, `langchain`, `sentence-transformers`