# 🎯 Project: Infrastructure DevOps - Local AI Setup

## 📌 Project Objective

Infrastructure DevOps Engineer হিসেবে নিচের কাজগুলো সম্পন্ন করতে হবে।

- ✅ Ollama Install করতে হবে
- ✅ প্রথম AI Model Download করতে হবে
- ✅ AI-এর সাথে Chat করতে হবে
- ✅ Model-এর কাজ বুঝতে হবে
- ✅ Infrastructure হিসেবে AI Model Manage করতে হবে

---

# 🛠️ Step 1: Install Ollama

## Windows Installation

1. Browser-এ যান

> https://ollama.com/download/windows

2. **OllamaSetup.exe** Download করুন

3. Install শেষ হলে **PowerShell** Open করুন

### Verify Installation

```powershell
ollama --version
```

Expected Output

```text
ollama version is 0.x.x
```

---

# 🟢 Step 2: Verify Ollama Service

Run

```powershell
curl http://localhost:11434
```

Expected Output

```text
Ollama is running
```

---

# 📥 Step 3: Download the First AI Model

Download **llama3.2:1b**

```powershell
ollama pull llama3.2:1b
```

Check Installed Models

```powershell
ollama list
```

Expected Output

```text
NAME            ID              SIZE      MODIFIED
llama3.2:1b     xxxxxxxx        1.3 GB    Now
```

---

# 💬 Step 4: Chat with AI

Start Chat

```powershell
ollama run llama3.2:1b
```

Ask

```text
What is the capital of Bangladesh?
```

Expected Answer

```text
Dhaka
```

Exit Chat

```text
/bye
```

---

# 🧪 Step 5: Download Production Models

## 5.1 Coding Model

Download

```powershell
ollama pull qwen2.5-coder:7b
```

Test

```powershell
ollama run qwen2.5-coder:7b "Terraform দিয়ে AWS EC2 instance তৈরির কোড দাও"
```

---

## 5.2 Chat Model

Download

```powershell
ollama pull hermes3:latest
```

Test

```powershell
ollama run hermes3:latest "Infrastructure DevOps-এর ৫টি Best Practice বলো"
```

---

# 📋 Step 6: Compare Model Performance

Run

```powershell
ollama run llama3.2:1b "Kubernetes কী?"
ollama run qwen2.5-coder:7b "Kubernetes কী?"
ollama run hermes3:latest "Kubernetes কী?"
```

## Compare the Results

| Model | Observation |
|--------|-------------|
| **llama3.2:1b** | Fast Response, Less Detailed |
| **qwen2.5-coder:7b** | Excellent Technical Answer |
| **hermes3:latest** | Detailed and Easy to Understand |

---

# 📊 Step 7: Resource Management

Check Installed Models

```powershell
ollama list
```

Expected Dashboard

```text
NAME                    ID              SIZE      MODIFIED
llama3.2:1b             xxxxxxxx        1.3 GB    Now
qwen2.5-coder:7b        xxxxxxxx        4.7 GB    Now
hermes3:latest          xxxxxxxx        4.7 GB    Now
```

### Total Disk Usage

```text
10.7 GB
```

---

# 🔧 Step 8: Model Version Control

## Show Model Information

```powershell
ollama show llama3.2:1b
```

---

## Remove a Model

```powershell
ollama rm llama3.2:1b
```

---

# 📁 Step 9: Infrastructure as Code (IaC)

Create **ollama-setup.sh**

```bash
#!/bin/bash

# Ollama Setup - Infrastructure DevOps

echo "🔍 Checking Ollama..."

if ! command -v ollama &> /dev/null; then
    echo "📥 Installing Ollama..."
    curl -fsSL https://ollama.com/install.sh | sh
fi

echo "📥 Downloading Models..."
ollama pull llama3.2:1b

echo "✅ Done!"

ollama list
```

Run Script

```bash
bash ollama-setup.sh
```

---

# 🚀 Step 10: CI/CD Pipeline

Create

```text
.github/workflows/test.yml
```

Content

```yaml
name: Test Ollama

on:
  push:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - run: curl -fsSL https://ollama.com/install.sh | sh
      - run: ollama pull llama3.2:1b
      - run: ollama run llama3.2:1b "Hello"
```

---

# ✅ Project Completion Checklist

| Step | Task | Status |
|------:|------|:------:|
| 1 | Install Ollama | ✅ |
| 2 | Verify Service | ✅ |
| 3 | Download Base Model | ✅ |
| 4 | Download Coding Model | ✅ |
| 5 | Download Chat Model | ✅ |
| 6 | Compare Model Performance | ✅ |
| 7 | Resource Management | ✅ |
| 8 | Model Version Control | ✅ |
| 9 | Create Infrastructure as Code (IaC) | ✅ |
| 10 | Create CI/CD Pipeline | ✅ |

---

# 🎉 Project Completed

Infrastructure DevOps Engineer হিসেবে সফলভাবে সম্পন্ন করা হয়েছে:

- ✅ Local AI Infrastructure Setup
- ✅ AI Model Management System
- ✅ Infrastructure as Code (IaC)
- ✅ CI/CD Pipeline
- ✅ Local LLM Environment Ready for Development & Automation