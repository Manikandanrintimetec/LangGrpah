# Multi-Agent AI Workflow using LangGraph

A simple multi-agent AI system built using LangGraph and OpenAI-compatible LLM APIs.

This project demonstrates how multiple AI agents can collaborate in a workflow:

1. Planner Agent → creates a step-by-step plan
2. Coder Agent → generates Python code
3. Reviewer Agent → reviews and improves the generated code

The workflow is orchestrated using LangGraph.

---

# Features

- Multi-agent architecture
- Sequential AI workflow
- LangGraph state management
- OpenAI-compatible API integration
- OpenRouter support
- Modular agent design
- Easy extensibility

---

# Architecture

```text
User Input
    ↓
Planner Agent
    ↓
Coder Agent
    ↓
Reviewer Agent
    ↓
Final Output
```

---

# Tech Stack

- Python 3.10+
- LangGraph
- LangChain
- OpenAI-compatible APIs
- OpenRouter
- dotenv
