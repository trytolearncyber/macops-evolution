# 🚀 My First RAG API
## Infrastructure DevOps Engineer Version (No Coding)

---

# 🎯 Project Objective

একটি Local RAG (Retrieval-Augmented Generation) API তৈরি করা হবে যা:

- ✅ নিজের সম্পর্কে প্রশ্নের উত্তর দিতে পারবে
- ✅ Local Document থেকে তথ্য খুঁজে বের করবে
- ✅ AI ব্যবহার করে সঠিক উত্তর তৈরি করবে
- ✅ সম্পূর্ণ Local Machine-এ চলবে

> **💡 Note:** Python Programming জানা বাধ্যতামূলক নয়। শুধুমাত্র Step-by-Step কপি-পেস্ট করলেই হবে।

---

# 🏗️ Infrastructure Overview

```text
┌─────────────────────────────────────────────────────────┐
│                    LOCAL MACHINE                        │
│                                                         │
│  ┌─────────────┐    ┌─────────────┐    ┌────────────┐    │
│  │   Ollama    │    │  ChromaDB   │    │  FastAPI   │    │
│  │ (AI Model)  │    │ (Vector DB) │    │ (REST API) │    │
│  │ Port:11434  │    │             │    │ Port:8000  │    │
│  └─────────────┘    └─────────────┘    └────────────┘    │
│         │                  │                 │           │
│         └──────────────────┴─────────────────┘           │
│                                                         │
│     profile.txt → Knowledge Base → API Endpoint         │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

# 📁 Step 1: Infrastructure Setup

PowerShell ওপেন করুন (Administrator লাগবে না)

```powershell
mkdir C:\rag-api
cd C:\rag-api
code .
```

### Infrastructure Note

- `C:\rag-api` = Local Server Directory

---

# 🐍 Step 2: Python Virtual Environment

VS Code Terminal খুলুন।

```powershell
python -m venv venv
venv\Scripts\activate
```

### Infrastructure Note

Virtual Environment = Isolation Layer

---

# 📦 Step 3: Install Dependencies

```powershell
pip install fastapi uvicorn chromadb ollama
```

### Infrastructure Note

এগুলো API Server-এর Runtime Dependencies।

---

# 🤖 Step 4: Download AI Models

```powershell
ollama pull nomic-embed-text
ollama pull qwen2.5:0.5b
```

## Infrastructure Note

| Model | Purpose | Size |
|-------|----------|------|
| nomic-embed-text | Embedding Engine | ~274 MB |
| qwen2.5:0.5b | Generation Engine | ~400 MB |

**Total Storage:** ~674 MB

---

### Verify

```powershell
ollama list
```

---

# 📄 Step 5: Create Data Layer

Create a file named:

```text
profile.txt
```

Paste:

```text
My name is Rony.

I am an Infrastructure DevOps Engineer.

I work with AWS, Docker, Kubernetes, Terraform, and Ansible.

I have 5 years of experience in cloud infrastructure.

I am learning AI and Machine Learning.

My goal is to become an AI Infrastructure Engineer.

I enjoy building automation tools and CI/CD pipelines.

I have experience with Python, Go, and Bash scripting.

I live in Dhaka, Bangladesh.

My favorite programming language is Python.
```

Save:

```
Ctrl + S
```

---

### Infrastructure Note

```
Data Layer = Personal Knowledge Source
```

---

# 🧠 Step 6: Build Knowledge Base

Create:

```text
build_kb.py
```

Paste:

```python
import chromadb
from chromadb.utils.embedding_functions.ollama_embedding_function import OllamaEmbeddingFunction

print("🚀 Building Knowledge Base...")

with open("profile.txt", "r") as f:
    text = f.read()

chunks = [chunk.strip() for chunk in text.split("\n\n") if chunk.strip()]
print(f"✅ Loaded {len(chunks)} chunks")

client = chromadb.PersistentClient(path="./chroma_db")

ef = OllamaEmbeddingFunction(
    model_name="nomic-embed-text",
    url="http://localhost:11434"
)

collection = client.get_or_create_collection(
    name="profile",
    embedding_function=ef
)

collection.add(
    ids=[f"c{i}" for i in range(len(chunks))],
    documents=chunks,
)

print("✅ Knowledge base ready!")
```

---

### Run

```powershell
python build_kb.py
```

Output

```text
🚀 Building Knowledge Base...

✅ Loaded 4 chunks

✅ Knowledge base ready!
```

---

### Infrastructure Note

```
ETL Pipeline

Extract
     ↓
Transform
     ↓
Load
```

---

# 🚀 Step 7: Create API Layer

Create:

```text
main.py
```

Paste:

```python
from fastapi import FastAPI
import ollama
import chromadb
from chromadb.utils.embedding_functions.ollama_embedding_function import OllamaEmbeddingFunction

app = FastAPI(title="RAG Infrastructure API")

client = chromadb.PersistentClient(path="./chroma_db")

ef = OllamaEmbeddingFunction(
    model_name="nomic-embed-text",
    url="http://localhost:11434"
)

collection = client.get_or_create_collection(
    name="profile",
    embedding_function=ef
)

@app.get("/")
def root():
    return {
        "status": "running",
        "infrastructure": "RAG API",
        "vector_db": "ChromaDB",
        "ai_engine": "Ollama"
    }

@app.get("/ask")
def ask(question: str):

    results = collection.query(
        query_texts=[question],
        n_results=2
    )

    context = "\n\n".join(results["documents"][0])

    prompt = f"""
Context:

{context}

Question:

{question}

Answer:
"""

    response = ollama.chat(
        model="qwen2.5:0.5b",
        messages=[
            {
                "role": "user",
                "content": prompt
            }
        ]
    )

    return {
        "question": question,
        "answer": response["message"]["content"],
        "context_used": results["documents"][0]
    }
```

Save

```
Ctrl + S
```

---

### Infrastructure Note

```
FastAPI = Production API Server
```

---

# ▶️ Step 8: Start API Server

```powershell
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

Output

```text
INFO: Uvicorn running on http://0.0.0.0:8000

INFO: Application startup complete.
```

⚠️ Terminal বন্ধ করবেন না।

---

### Infrastructure Note

| Option | Meaning |
|----------|----------|
| --reload | Development Mode |
| --host 0.0.0.0 | Listen on all interfaces |
| --port 8000 | API Port |

---

# 🧪 Step 9: Test API

## Health Check

Browser

```text
http://127.0.0.1:8000/
```

Output

```json
{
  "status": "running",
  "infrastructure": "RAG API",
  "vector_db": "ChromaDB",
  "ai_engine": "Ollama"
}
```

---

## Ask API

```text
http://127.0.0.1:8000/ask?question=What is my name?
```

Output

```json
{
  "question": "What is my name?",
  "answer": "Your name is Rony.",
  "context_used": [
    "My name is Rony."
  ]
}
```

---

# 🏛 Infrastructure Architecture

```text
┌───────────────────────────────────────────────────────────────┐
│                 LOCAL AI INFRASTRUCTURE                      │
│                                                              │
│  Layer 1                                                     │
│  📄 profile.txt                                              │
│                                                              │
│             │                                                │
│             ▼                                                │
│  ETL Pipeline                                                │
│                                                              │
│             ▼                                                │
│  Layer 2                                                     │
│  💾 ChromaDB                                                 │
│                                                              │
│             │                                                │
│             ▼                                                │
│  Layer 3                                                     │
│  🧠 Ollama                                                   │
│  • nomic-embed-text                                          │
│  • qwen2.5:0.5b                                              │
│  Port:11434                                                  │
│                                                              │
│             │                                                │
│             ▼                                                │
│  Layer 4                                                     │
│  🚀 FastAPI                                                  │
│  Port:8000                                                   │
│  /ask                                                        │
└───────────────────────────────────────────────────────────────┘
```

---

# 📊 System Resources

| Component | Technology | Port | Storage |
|-----------|------------|------|----------|
| AI Engine | Ollama | 11434 | ~700 MB |
| Vector Database | ChromaDB | Local | ~10 MB |
| API Server | FastAPI | 8000 | ~50 MB |
| **Total** | | | **~750 MB** |

---

# 🔧 Troubleshooting Guide

| Problem | Check | Solution |
|----------|--------|----------|
| API not running | `curl http://localhost:8000` | Start Uvicorn |
| AI not responding | `curl http://localhost:11434` | Run `ollama serve` |
| Vector DB error | `ls chroma_db` | Run `python build_kb.py` |
| Port conflict | `netstat -ano \| findstr 8000` | Use another port |

---

# ✅ Infrastructure Checklist

| Component | Status |
|------------|--------|
| Data Layer (profile.txt) | ✅ |
| Vector DB (ChromaDB) | ✅ |
| AI Engine (Ollama) | ✅ |
| API Server (FastAPI) | ✅ |
| Health Check | ✅ |
| `/ask` Endpoint | ✅ |

---

# 🎉 Infrastructure Deployment Complete

```text
┌──────────────────────────────────────────────────────┐
│        ✅ RAG Infrastructure Deployment Complete     │
│                                                      │
│ 📄 Data Layer     : profile.txt                      │
│ 💾 Vector DB      : ChromaDB                         │
│ 🧠 AI Engine      : Ollama                           │
│ 🚀 API Server     : FastAPI (Port 8000)              │
│                                                      │
│ 🌐 API URL        : http://localhost:8000            │
│ 📚 Swagger UI     : http://localhost:8000/docs       │
└──────────────────────────────────────────────────────┘
```

---

# 🚀 Next Infrastructure Task

পরবর্তী ধাপে এই RAG API-কে **n8n Workflow**-এর সাথে সংযুক্ত করে একটি **AI Automation Pipeline** তৈরি করা হবে।

- ✅ n8n HTTP Request Node
- ✅ RAG API Integration
- ✅ AI Chat Workflow
- ✅ Enterprise Automation Pipeline