# 🤖 Domain Knowledge Co-Pilot

A production-ready **RAG (Retrieval-Augmented Generation)** system that lets users upload PDFs and get accurate, citation-backed answers to their questions — built end-to-end with authentication, vector search, and a polished UI.

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-Backend-009688.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-Frontend-FF4B4B.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

## 📖 Overview

**Domain Knowledge Co-Pilot** turns any PDF into an interactive knowledge base. Upload a document, ask questions in natural language, and get accurate answers — each one traceable back to the exact source passage it came from. Built with a secure multi-user authentication layer so each user's documents and chat history stay private.

---

## ✨ Features

- 📤 **PDF Upload & Processing** — Upload any PDF and have it automatically chunked, embedded, and indexed
- 💬 **Natural Language Q&A** — Ask questions and get context-aware answers powered by LLMs
- 🔍 **Citation Tracing** — Every answer links back to the exact source passage/page it was generated from
- 🔐 **Secure Authentication** — JWT-based signup/login system with hashed passwords
- ⚡ **Fast Semantic Search** — ChromaDB vector store for low-latency retrieval
- 🧠 **LLM-Agnostic** — Plug in OpenAI or Groq APIs interchangeably
- 🎨 **Clean UI** — Responsive Streamlit interface with a smooth chat experience
- 📝 **Post-processing Actions** — Summarize or convert answers into bullet points on demand

---

## 🏗️ Architecture

\`\`\`
┌─────────────────┐         REST API          ┌──────────────────┐
│                  │ ──────────────────────────▶│                  │
│  Streamlit UI    │                            │  FastAPI Backend │
│  (Frontend)      │ ◀──────────────────────────│                  │
└─────────────────┘                            └────────┬─────────┘
                                                          │
                                    ┌─────────────────────┼─────────────────────┐
                                    ▼                     ▼                     ▼
                              ┌───────────┐        ┌─────────────┐      ┌──────────────┐
                              │ ChromaDB  │        │  SQLite +   │      │ OpenAI/Groq  │
                              │ (Vectors) │        │ SQLAlchemy  │      │     API      │
                              └───────────┘        │   (Auth)    │      └──────────────┘
                                                    └─────────────┘
\`\`\`

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | FastAPI |
| Frontend | Streamlit |
| Orchestration | LangChain |
| Vector Store | ChromaDB |
| Authentication | JWT, Passlib (bcrypt) |
| Database | SQLite + SQLAlchemy |
| LLM Providers | OpenAI API / Groq API |
| Deployment | Render (backend), Streamlit Community Cloud (frontend) |

---

## 📂 Project Structure

\`\`\`
domain-knowledge-copilot/
├── backend/
│   ├── main.py              # FastAPI entry point
│   ├── auth/                # JWT auth & user models
│   ├── rag/                 # RAG pipeline (chunking, embedding, retrieval)
│   ├── routes/               # API route definitions
│   └── requirements.txt
├── frontend/
│   ├── app.py                # Streamlit entry point
│   └── requirements.txt
├── .env.example
├── .gitignore
└── README.md
\`\`\`

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- OpenAI or Groq API key

### 1. Clone the repo
\`\`\`bash
git clone https://github.com/<your-username>/domain-knowledge-copilot.git
cd domain-knowledge-copilot
\`\`\`

### 2. Set up the backend
\`\`\`bash
cd backend
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
\`\`\`

### 3. Configure environment variables
Create a `.env` file in `backend/`:
\`\`\`env
JWT_SECRET_KEY=your_secret_key_here
OPENAI_API_KEY=your_openai_key_here
GROQ_API_KEY=your_groq_key_here
\`\`\`

### 4. Run the backend
\`\`\`bash
uvicorn main:app --reload
\`\`\`

### 5. Run the frontend
\`\`\`bash
cd ../frontend
pip install -r requirements.txt
streamlit run app.py
\`\`\`

The app will be live at `http://localhost:8501` 🎉

---

## 🔑 API Endpoints (Sample)

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/auth/signup` | Register a new user |
| `POST` | `/auth/login` | Authenticate and get JWT token |
| `POST` | `/upload` | Upload a PDF for processing |
| `POST` | `/query` | Ask a question against uploaded docs |
| `GET` | `/health` | Health check |

---

## ☁️ Deployment

- **Backend**: Deployed on [Render](https://render.com) as a Web Service
- **Frontend**: Deployed on [Streamlit Community Cloud](https://streamlit.io/cloud)

> ⚠️ Note: Free-tier ChromaDB storage is ephemeral on Render — for persistent storage, use a paid disk or a hosted vector DB.

---

## 🗺️ Roadmap

- [ ] Multi-document cross-referencing
- [ ] Support for additional file types (DOCX, TXT)
- [ ] Chat history export
- [ ] Dockerized deployment

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙋 Author

Built by **Shiwanshu** as a capstone project for the **New Age Software Engineering** program (iHUB DivyaSampark, IIT Roorkee).