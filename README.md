# 🎓 EduRAG: Multi-Course Academic Assistant

A **Standard Retrieval-Augmented Generation (RAG)** system built to answer student questions strictly from multi-format academic course materials (`PDF`, `DOCX`, `CSV`, `TXT`) with verified source citations.

## 🚀 Key Architectural Highlights
- **Multi-Format Document Loaders:** Uses specialized parsers (`PyMuPDFLoader`, `Docx2txtLoader`, `CSVLoader`, `TextLoader`) rather than a single generic loader.
- **Two-Stage Hybrid Chunking:** Combines `RecursiveCharacterTextSplitter` (semantic paragraph/sentence preservation with 20% overlap) and `TokenTextSplitter` (`tiktoken` window enforcement).
- **Consistent Vector Space:** Uses the exact same embedding model (`sentence-transformers/all-MiniLM-L6-v2`) across both indexing and query phases.
- **Metadata-Enriched Context & Filtering:** Preserves `course`, `file_name`, `file_type`, `page`, and `chunk_id` for per-course filtering and inline citations.
- **Strict Grounding & Hallucination Prevention:** Configured with `temperature=0.0` and strict system instructions to state *"I don't have enough proof in the provided course materials to answer this question."* when evidence is absent.
- **Interactive Gradio UI:** Features course filtering, Top-K tuning, live citation display, and dynamic document indexing.

## 🛠️ How to Run Locally
1. Clone this repository:
   ```bash
   git clone https://github.com
   cd EduRAG-Academic-Assistant
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Set your Groq API key:
   ```bash
   export GROQ_API_KEY="your_groq_api_key_here"
   ```
4. Launch the Gradio application:
   ```bash
   python app.py
   ```
