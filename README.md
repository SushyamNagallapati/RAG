
# 🧠 RAG (Retrieval-Augmented Generation) with LLaMA 3.2 and Ollama

This project is a Retrieval-Augmented Generation (RAG) assistant that answers questions using:

- 🧠 **LLaMA 3.2** via [Ollama](https://ollama.com)
- 🔗 **LangChain** for orchestration
- 🧲 **BGE-large embeddings** (BAAI/bge-large-en)
- 📦 **ChromaDB** for vector storage
- 🐍 **Python**

It allows you to ask questions based on your **own PDF documents** using a **local LLM**.

---

## 🚀 Quickstart

### 1. 📥 Clone the Repository

```bash
git clone https://github.com/SushyamNagallapati/RAG.git
cd RAG
```

### 2. 🧠 Install Ollama and Pull LLaMA 3.2

Install Ollama (macOS, Linux, Windows):  
👉 https://ollama.com/download

Then pull the model:

```bash
ollama pull llama3
```

> 🟡 Make sure Ollama is running in the background before you use the model.

---

### 3. 🐍 Create a Virtual Environment & Install Dependencies

```bash
python3 -m venv venv
source venv/bin/activate          # On Windows: .\venv\Scripts\activate
pip install -r requirements.txt
```

---

### 4. 📂 Add Your PDFs

Put your PDF documents inside the `data/` folder.  
Example: `data/insurance_policy.pdf`

---

### 5. 🧠 Ingest Data into ChromaDB

Run the ingestion script:

```bash
python ingest.py
```

---

### 6. 💬 Ask Questions (Use the RAG Assistant)

Make sure Ollama is running in the background.

```bash
# Terminal 1
ollama run llama3.2:latest

# Terminal 2 (after activating venv)
python rag.py
```

Then type your question when prompted!

---

## ✅ Example Questions You Can Ask

- What’s covered under this health insurance policy?
- Is COVID-19 treatment included?
- What’s the claim filing process?
- When does the coverage period start and end?
- Is dental coverage included?

---

## 🗂️ File Structure

```
data/              # PDF documents
db/                # Chroma vector DB (auto-generated)
embeddings.py      # Embedding setup using HuggingFace
ingest.py          # PDF loader + ChromaDB population
llama_model.py     # Communicates with Ollama (LLaMA model)
retriever.py       # Finds relevant chunks
rag.py             # Main RAG orchestration loop
requirements.txt   # Python dependencies
.gitignore         # Ignored files/folders
```

---

## 🛠️ Troubleshooting

- ❌ **KeyError: 'response'** — Make sure model name matches `ollama list` in `llama_model.py`
- ❌ **Too many files showing in Git** — Add `.gitignore` to exclude `venv/`, `db/`, `.DS_Store`, etc.
- ❌ **Missing embeddings** — Make sure `ingest.py` has been run and `db/` is created

---

## 🌱 Future Improvements

- 🔌 Add FastAPI for tool calling
- 🧮 Enable schema-aware SQL generation
- 🎨 Add a web UI using Streamlit or Gradio
- 📝 Add citations with sources
- 📊 Optionally use Qdrant instead of Chroma

---

## 📝 License

MIT — use it freely, modify it, and share it.

---

> 🔧 Built with ❤️ by [Sushyam Nagallapati](https://github.com/SushyamNagallapati)

> MEng System Design Engineering, University of Waterloo
