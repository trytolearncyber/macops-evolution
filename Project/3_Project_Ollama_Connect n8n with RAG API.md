# 🔗 Infrastructure Task
# Connect n8n with RAG API (Easy Version)

---

# 🎯 Project Objective

n8n Workflow থেকে Local RAG API-তে প্রশ্ন পাঠাতে হবে এবং API-এর উত্তর সংগ্রহ করতে হবে।

### Learning Goals

 

---

# 🏗️ Infrastructure Overview

```text
┌─────────────────────────────────────────────────────────────┐
│                   LOCAL INFRASTRUCTURE                      │
│                                                             │
│  ┌──────────┐     ┌──────────┐     ┌──────────┐             │
│  │   n8n    │────▶│ RAG API  │────▶│ ChromaDB │            │
│  │ Port5678 │     │ Port8000 │     │ VectorDB │             │
│  └──────────┘     └──────────┘     └──────────┘             │
│        │                 │                  │               │
│        └─────────────────┴──────────────────┘               │
│                          │                                  │
│                          ▼                                  │
│                  ┌──────────────┐                           │
│                  │    Ollama    │                           │
│                  │  AI Engine   │                           │
│                  │ Port:11434   │                           │
│                  └──────────────┘                           │
└─────────────────────────────────────────────────────────────┘
```

---

# 📋 Step 1: Verify RAG API

Browser খুলুন।

```text
http://127.0.0.1:8000/
```

Expected Output

```json
{
  "message": "RAG API is running!"
}
```

---

### If API is not running

```powershell
uvicorn main:app --reload
```

---

# 📋 Step 2: Verify n8n

Browser খুলুন।

```text
http://localhost:5678
```

Expected Result

```
n8n Login Page
```

---

### If n8n is not running

```powershell
docker compose up -d
```

---

# 📋 Step 3: Create Workflow

Inside n8n

```
Workflows
        ↓
New Workflow
```

Workflow Name

```text
RAG API
```

---

# 📋 Step 4: Add Manual Trigger

Click

```
+
```

Search

```
Manual
```

Select

```
Manual Trigger
```

Workflow

```text
Manual Trigger
```

---

# 📋 Step 5: Add HTTP Request Node

Click

```
+
```

Search

```
HTTP Request
```

Select

```
HTTP Request
```

---

## Configure Node

| Field | Value |
|--------|-------|
| Method | GET |
| URL | `http://host.docker.internal:8000/ask?question=What is my name?` |

---

### If Docker Host Name Doesn't Work

Use

```text
http://localhost:8000/ask?question=What is my name?
```

---

# 📋 Step 6: Execute Workflow

Click

```
Execute Workflow
```

Then

```
Manual Trigger
```

The HTTP Request Node will call the RAG API.

---

# 📋 Step 7: Expected Output

```json
{
  "question": "What is my name?",
  "answer": "Your name is Rony.",
  "context_used": [
    "My name is Rony."
  ],
  "model_used": "qwen2.5:0.5b"
}
```

---

# 📋 Step 8: Try Different Questions

Example 1

```text
http://host.docker.internal:8000/ask?question=What is your job?
```

Example 2

```text
http://host.docker.internal:8000/ask?question=Where do you live?
```

Example 3

```text
http://host.docker.internal:8000/ask?question=What technologies do you use?
```

---

# 📦 Import Workflow JSON

Copy the following JSON and import it into n8n.

```json
{
  "name": "RAG API",
  "nodes": [
    {
      "name": "Manual Trigger",
      "type": "n8n-nodes-base.manualTrigger",
      "position": [250, 300],
      "parameters": {}
    },
    {
      "name": "Call RAG API",
      "type": "n8n-nodes-base.httpRequest",
      "position": [450, 300],
      "parameters": {
        "method": "GET",
        "url": "http://host.docker.internal:8000/ask?question=What is my name?"
      }
    }
  ],
  "connections": {
    "Manual Trigger": {
      "main": [
        [
          {
            "node": "Call RAG API",
            "type": "main"
          }
        ]
      ]
    }
  }
}
```

---

# 📥 Import into n8n

Inside n8n

```
Workflows
      ↓
Import from File
      ↓
Paste JSON
      ↓
Import
```

---

# 🏛 Infrastructure Architecture

```text
                User
                  │
                  ▼
          Manual Trigger
                  │
                  ▼
        HTTP Request Node
                  │
                  ▼
        FastAPI RAG Server
                  │
        ┌─────────┴─────────┐
        │                   │
        ▼                   ▼
   ChromaDB            Ollama AI
(Vector Database)    (LLM Engine)
        │                   │
        └─────────┬─────────┘
                  ▼
            AI Response
                  │
                  ▼
             n8n Output
```

---

# 🔧 Troubleshooting Guide

| Problem | Solution |
|----------|----------|
| ECONNREFUSED | Start the RAG API using `uvicorn main:app --reload` |
| `host.docker.internal` not working | Use `localhost` instead |
| API not responding | Open `http://localhost:8000` in the browser |
| n8n not opening | Run `docker compose up -d` |
| Empty response | Verify `profile.txt` exists and rebuild with `python build_kb.py` |

---

# 📊 Infrastructure Ports

| Service | Port | Purpose |
|----------|------|----------|
| n8n | 5678 | Workflow Automation |
| FastAPI | 8000 | REST API |
| Ollama | 11434 | AI Engine |
| ChromaDB | Local Storage | Vector Database |

---

# ✅ Infrastructure Checklist

| Task | Status |
|------|--------|
| RAG API Running | ✅ |
| n8n Running | ✅ |
| Workflow Created | ✅ |
| Manual Trigger Added | ✅ |
| HTTP Request Node Added | ✅ |
| API URL Configured | ✅ |
| Workflow Executed | ✅ |
| API Response Received | ✅ |

---

# 🎉 Infrastructure Deployment Complete

```text
┌────────────────────────────────────────────────┐
│        ✅ n8n + RAG API Connected              │
│                                                │
│ 🌐 n8n        : http://localhost:5678          │
│ 🚀 RAG API    : http://localhost:8000          │
│ 🧠 Ollama     : http://localhost:11434         │
│ 💾 ChromaDB   : Local Storage                  │
│                                                │
│ 🔗 Connection Status : SUCCESS ✅              │
└────────────────────────────────────────────────┘
```

---

# 🚀 Next Infrastructure Task

পরবর্তী ধাপে সম্পূর্ণ Local AI Stack Docker-এ Containerize করা হবে।

সেখানে শিখবেন:

- ✅ Dockerfile তৈরি করা
- ✅ Docker Compose ব্যবহার করা
- ✅ FastAPI Container
- ✅ Ollama Container
- ✅ ChromaDB Persistent Volume
- ✅ n8n Container
- ✅ One Command Deployment (`docker compose up -d`)