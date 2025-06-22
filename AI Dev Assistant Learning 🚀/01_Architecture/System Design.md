# 🧱 System Design – AI Dev Assistant

## 🧠 Components
- **Knowledge Base**: Obsidian vault (daily notes, tickets, docs)
- **Embeddings Engine**: Local or remote vector store (Chroma, Weaviate)
- **Retriever**: Semantic search via LangChain or LlamaIndex
- **LLM Interface**: OpenAI, Ollama, or LM Studio
- **Agents**: Modular task handlers (summarizer, coder, refactorer)
- **Interface**: CLI, VS Code Extension, or chatbot

## 🔄 Data Flow
1. Obsidian notes → parsed + chunked
2. Each chunk embedded + stored in vector DB
3. Query → matched vectors → sent as context to LLM
4. Output → returned to user or written to file

## 🧱 Design Choices
- Local-first where possible (security, privacy)
- Incremental feature growth
- Modularity: each feature should be swappable