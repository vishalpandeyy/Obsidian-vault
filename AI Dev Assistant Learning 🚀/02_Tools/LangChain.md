# 🔧 LangChain Quickstart

LangChain helps you build LLM apps that chain together prompts, tools, memory, and logic.

## Key Concepts
- **Chains**: Sequence of prompts/functions
- **Agents**: LLMs that decide which tools to use
- **Memory**: Stores conversation or task state
- **Retrievers**: Pull relevant data from vector DB

## Example Use
```python
from langchain.chains import RetrievalQA
from langchain.vectorstores import Chroma
from langchain.embeddings import OpenAIEmbeddings

db = Chroma(persist_directory="path_to_your_db", embedding_function=OpenAIEmbeddings())
qa = RetrievalQA.from_chain_type(llm=..., retriever=db.as_retriever())

qa.run("What is the ticket status from last week?")
```