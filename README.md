# AI Agentic System with RAG, LangGraph, Tools & Multi-Agent Routing

This project demonstrates a **production-style AI backend pipeline** combining:

- Retrieval-Augmented Generation (RAG)
- LangGraph agent workflows
- Tool-using LLM agents (ReAct style)
- Multi-agent routing
- Memory (conversation persistence)
- Streaming responses
- PDF ingestion + vector search

Built using **LangChain + LangGraph + OpenRouter-compatible OpenAI APIs**.

---

# 🚀 Features

## 1. RAG Pipeline
- Load PDFs from `data/`
- Chunk documents using recursive splitter
- Generate embeddings
- Store in FAISS vector database
- Retrieve relevant context dynamically

---

## 2. Basic + Advanced RAG
- Basic RAG: direct retrieval + answer
- Advanced RAG:
  - Query rewriting for better retrieval
  - Improved semantic search results

---

## 3. Tool-Using LLM (ReAct Agent)
Supports tools:

- ➕ Calculator
- ✖️ Multiply
- 📄 Document retrieval from vector DB

LLM can decide when to call tools automatically.

---

## 4. LangGraph Agent System
- State-based execution
- Conditional tool routing
- Loop between assistant and tools
- Memory persistence using `MemorySaver`

---

## 5. Multi-Agent Routing
Simple rule-based system:

- “code” → coding agent
- otherwise → research agent

---

## 6. Streaming Support
Real-time token streaming from LLM.

---

# 🏗️ Architecture

```
PDFs → Chunking → Embeddings → FAISS Vector DB
                              ↓
User Query → Retriever → Context → LLM → Answer

        +-----------------------------+
        | LangGraph Agent System      |
        | - Tool Calling              |
        | - Memory                   |
        | - ReAct Loop               |
        +-----------------------------+

        +-----------------------------+
        | Multi-Agent Router         |
        | - Research Agent           |
        | - Coding Agent             |
        +-----------------------------+



# ⚙️ Installation

## 1. Clone Repo

```bash
git clone <repo-url>
cd <repo-name>
```

---

## 2. Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

# 🔑 Environment Variables

Create `.env` file:

```env
ROUTER_API_TOKEN=your_openrouter_api_key
```

---

# 📦 Requirements

```
langchain
langgraph
langchain-openai
langchain-community
langchain-text-splitters
faiss-cpu
python-dotenv
pypdf
```

---

# ▶️ How to Run

```bash
python main.py
```

---

# 📌 Pipeline Breakdown

---

## 1. PDF Loading

- Reads all PDFs from `data/`
- Converts into LangChain Document objects

---

## 2. Chunking

- Splits text into 1000-token chunks
- 200-token overlap for context preservation

---

## 3. Embeddings

- Uses OpenAI-compatible embeddings:
  `text-embedding-3-small`

- Stored in FAISS vector store

---

## 4. Retrieval

```python
retriever.invoke(query)
```

Returns top-k similar chunks.

---

## 5. Prompt Flow

```
Context + Question → Prompt Template → LLM → Answer
```

---

# 🧠 RAG Types

## Basic RAG
- Direct retrieval
- Single query

## Advanced RAG
- Query rewriting
- Improved retrieval quality

---

# 🛠️ Tools Used

| Tool | Description |
|------|------------|
| calculator | Adds two numbers |
| multiply | Multiplies numbers |
| retrieve_documents | Searches vector DB |

---

# 🤖 LangGraph Agent System

## Flow

```
User → Assistant → (Tool Call?) → ToolNode → Assistant → Final Answer
```

---

## State

Uses `MessagesState`:

```python
state["messages"]
```

---

## Memory

- Uses `MemorySaver`
- Maintains conversation per thread_id

---

# 🔁 Multi-Agent Routing

Simple router:

```python
if "code" in query:
    coding_agent
else:
    research_agent
```

---

# ⚡ Streaming

Real-time response generation:

```python
for chunk in llm.stream("Explain embeddings"):
    print(chunk.content)
```

---

# 💡 Key Concepts Demonstrated

- Retrieval-Augmented Generation (RAG)
- Vector databases (FAISS)
- Embeddings
- Tool-using LLMs (ReAct pattern)
- LangGraph workflows
- Memory persistence
- Multi-agent systems
- Streaming LLM responses
- Query rewriting

---

# 🚀 Future Improvements

- Replace FAISS with Pinecone / pgvector
- Add FastAPI backend
- Add authentication (JWT)
- Add conversation DB persistence
- Add async tool execution
- Add caching layer (Redis)
- Add evaluation metrics
- Add UI (React / Streamlit)
- Deploy with Docker

---

# 📊 Why This Project Matters

This project simulates a real-world AI backend:

- RAG-powered enterprise assistant
- Tool-using agent system
- Multi-agent routing logic
- Production-style architecture thinking
