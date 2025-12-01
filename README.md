
---

# 📘 MediFlow AI — Context-Aware Medical Triage Assistant

**Smart, reliable, and multi-agent healthcare triage powered by Google Gemini + ADK**

MediFlow AI is a **multi-agent, context-aware medical triage assistant** designed to help users understand symptoms, assess possible conditions, and optionally find nearby doctors — powered by **Google ADK Agents**, **Gemini models**, and **tool-calling workflows**.

This project includes everything required for development, evaluation, and deployment — including a full Hugging Face Spaces app, ADK agent definitions, local evaluation tests, session management, and optional local SQLite history logging.

---

## 🚀 Features (Core Highlights)

* **Multi-Agent System**
  Triage Agent (“Tara”) + Google Search Agent (“Silent Librarian”).

* **Context-Aware Triage Workflow**
  Symptom intake → emergency detection → enrichment → condition estimation.

* **Real-Time Google Search Integration**
  Weather, AQI, outbreaks, medical causes, home remedies, doctor lookup.

* **Session Management**
  InMemorySessionService + optional SQLite storage for CLI mode.

* **Evaluation Suite**
  Custom evalset, ADK eval config, reproducible testing.

* **Deploy Anywhere**
  Hugging Face Spaces (Web UI)
  Jupyter Notebook
  CLI Mode
  ADK Sandbox

---

## 🏗 Project Structure

```
.
├── database/
│   └── chat_history.db            # (Optional) Local CLI chat history storage
│
├── logs/                          # All the logs are saved here (only when you run via python)
│   └── critical.log
│   └── debug.log
│   └── error.log
│   └── info.log
│   └── warning.log 
│
├── src/
│   └── mediflow_ai/
│       ├── __pycache__/
│       ├── .adk/                  # ADK metadata
│       ├── __init__.py
│       ├── agent.py               # LLM agents + tools + runner factory
│       ├── sqlite_store.py        # Optional SQLite backend for CLI sessions
│       └── mediflow_ai.egg-info/  # Build metadata
│
├── main.ipynb                     # Local notebook interface
│
├── tests/
│   ├── mediflow_evalset.json      # Custom evaluation dataset
│   └── test_config.json           # ADK evaluation configuration
│
├── .env                           # Local dev environment variables
├── .gitignore
├── .python-version
├── adk_config.yaml                # ADK project configuration
├── LICENSE
├── pyproject.toml                 # Build config (if packaged)
├── README.md                      # (You are reading this)
├── requirements.txt               # Python dependencies
├── run.ipynb                      # Live development notebook
└── setup.py                       # Package installer script
```

---

## 🤖 Agent Architecture Overview

### **1. Triage Agent — “Tara”**

Handles:

* symptom intake (loop)
* emergency detection
* context enrichment
* condition ranking with confidence
* recommendations (home remedy / monitor / consult doctor)
* uses Google Search Agent when needed

### **2. Google Search Agent — “Silent Librarian”**

Handles:

* all Google Search API interactions
* strictly factual retrieval
* zero clinical interpretation

### **Tools Used**

* **Google Search Tool** → real-time environment + medical context
* **Custom Doctor Lookup**
* **Preload Memory (ADK)** for startup consistency

### **Session Engine**

* **InMemorySessionService** (HF deployment)
* **SQLite Session Store** (CLI only, optional)

---


## 🧩 Installation (Local Development)

### **1. Clone the Repo**

```bash
git clone https://github.com/<your-username>/mediflow_ai.git
cd mediflow_ai
```

### **2. Install Dependencies**

```bash
pip install -r requirements.txt
```

### **3. Add Environment Variables**

Create `.env`:

```
GOOGLE_API_KEY=your_key_here
GOOGLE_GENAI_MODEL=gemini-2.0-flash-exp
```

---

## ▶️ Running Locally

### **1. Run via Python**
Run this from Root Directory
```bash
python -m src.mediflow_ai.agent
```

### **2. Run the Notebook**

Open and Intructions are written inside the file:

```
main.ipynb  
```

### **3. Run via ADK web**
Run this from src directory
```bash
cd src  # run this first
adk web  
```
And choose 'mediflow ai' agent in ADK web

---

# 🌐 MediFlow AI Deployement

### MediFlow AI is Deployed through HuggingFace Spaces

Anyone can access it from here: https://huggingface.co/spaces/bidit06/mediflow_ai

Further the code and documentation for MediFlow AI Deployement is here

This guide will walk you through everything—from project structure, agent behavior, and file explanation, to deploying the system on Hugging Face Spaces.

Feel Free to go and access it.

---

## 🧪 Evaluation

This repo contains:

* `tests/mediflow_evalset.json` → realistic patient cases
* `tests/test_config.json` → ADK evaluation configuration

Run:

```bash
adk eval --config tests/test_config.json
```

---

## 🛠 Customization

To adapt MediFlow AI for another domain:

* swap triage rules
* add new tools
* change Google Search queries
* extend the workflow phases
* plug in additional memory systems

---

## ⚠️ Medical Disclaimer

*MediFlow AI is not a medical device or a replacement for licensed professionals.
It provides informational suggestions based on symptoms and public data.*

---

## ⭐ Acknowledgements

* Google AI Developer Kit (ADK)
* Gemini Models

## Ending Warm Message By Bidit!
🎉 Thank You for Exploring MediFlow AI

Thank you for taking the time to explore MediFlow AI.
We hope this project inspires you to build meaningful, responsible, and intelligent agent systems that make a real impact.
If you’d like to extend, remix, or integrate MediFlow AI into your own workflows, feel free to do so—this project is designed to grow with your ideas.
Happy building! 🚀
