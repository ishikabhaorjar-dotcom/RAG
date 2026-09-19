# 🎥 AI Video Q&A Chatbot — Retrieval-Augmented Generation (RAG)

> **Turn long-form video content into a searchable, conversational knowledge base.**

An end-to-end **Retrieval-Augmented Generation (RAG)** project that allows users to ask questions about video content in natural language. The system converts video speech into text using **OpenAI Whisper**, transforms the transcript into semantic embeddings, retrieves the most relevant context using **FAISS**, and generates a grounded response with a locally hosted **Ollama LLM**.

## ✨ Project Overview

Traditional video learning requires manually searching through long recordings to find a specific explanation. This project explores a more useful interface: **ask the video a question and retrieve an answer from its actual content.**

### Core pipeline

```text
Video
  ↓
Audio Extraction
  ↓
Whisper Speech-to-Text
  ↓
Transcript Cleaning / Chunking
  ↓
BGE-M3 Embeddings
  ↓
FAISS Semantic Search
  ↓
Relevant Context
  ↓
Ollama + Phi-3 Mini
  ↓
Grounded Answer
```

## 🧠 How RAG Works Here

The system does not simply send the entire transcript to an LLM.

1. **Ingestion** — A video is processed and its audio is extracted.
2. **Transcription** — Whisper converts spoken content into text.
3. **Chunking** — The transcript is divided into smaller searchable sections.
4. **Embedding** — Each chunk is converted into a vector representation using an embedding model.
5. **Indexing** — Embeddings are stored for efficient similarity retrieval with FAISS.
6. **Query** — The user asks a natural-language question.
7. **Retrieval** — Semantically similar transcript chunks are identified.
8. **Generation** — The retrieved context is passed to the local Ollama model.
9. **Response** — The model generates an answer grounded in the retrieved video content.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core development |
| OpenAI Whisper | Speech-to-text transcription |
| BGE-M3 | Semantic text embeddings |
| FAISS | Vector similarity search |
| Ollama | Local LLM runtime |
| Phi-3 Mini | Local response generation |
| Joblib | Persisting generated artifacts |
| FFmpeg | Audio/video processing |

## 📁 Project Artifacts

The project works with artifacts such as:

```text
embeddings.joblib
jsons/
prompt / response text files
video/audio processing scripts
transcripts
```

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/ishikabhaorjar-dotcom/AI-Video-RAG.git
cd AI-Video-RAG
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Install FFmpeg

FFmpeg is required for video/audio processing.

Verify:

```bash
ffmpeg -version
```

### 5. Install Ollama

Install Ollama and pull the local language model used by the project:

```bash
ollama pull phi3:mini
```

For the embedding model, the project uses **BGE-M3**.

### 6. Run the project

Run the project's main Python entry point according to the included scripts and configuration.

> **Note:** Exact filenames and commands may vary depending on the final repository structure. Keep the commands aligned with the files you upload to GitHub.

## 💬 Example

A user can ask a question such as:

```text
What is HTML?
```

Instead of searching manually through a long video, the system:

```text
Question
   ↓
Semantic Retrieval
   ↓
Relevant Transcript Context
   ↓
Local LLM
   ↓
Answer
```

This demonstrates how RAG can turn unstructured educational video content into an interactive knowledge source.

## 🔍 Why RAG?

A language model by itself does not automatically know the contents of a private video.

RAG introduces an external knowledge layer:

**Retrieve first → Generate second**

This makes it possible to ground the response in the information extracted from the user's video rather than relying only on the model's general knowledge.

## 🧩 Key Technical Concepts Demonstrated

- Retrieval-Augmented Generation
- Semantic Search
- Text Embeddings
- Vector Similarity Search
- Speech-to-Text
- Transcript Processing
- Chunking
- Local LLM Inference
- Prompt Engineering
- AI pipeline design
- Working with multimodal source content

## ⚙️ Challenges

### Large transcription models on limited hardware

Larger Whisper models can be computationally demanding. During development, the **Whisper large-v2** model was found to be heavy for the available laptop hardware.

This highlighted an important practical AI engineering consideration:

> Model selection must balance accuracy, latency, memory usage, and available compute.

### Local LLM constraints

Using Ollama made it possible to experiment with an LLM locally without depending on a paid hosted API, but local inference is constrained by available CPU/RAM.

## 📈 Future Improvements

- Add a Streamlit web interface
- Support multiple videos and collections
- Display source timestamps with answers
- Add conversation memory
- Add hybrid keyword + semantic retrieval
- Add reranking for improved retrieval
- Replace local vector artifacts with a production vector database
- Add evaluation metrics for retrieval quality
- Support additional languages
- Deploy as a cloud application

## 🎯 What This Project Demonstrates

This project demonstrates practical experience building an AI application beyond simply calling an LLM API.

It combines:

**Data ingestion → preprocessing → NLP → embeddings → vector search → retrieval → LLM generation**

That makes it a useful portfolio project for demonstrating foundational **Generative AI, NLP, and RAG engineering skills**.

## 👩‍💻 Author

**Ishika Bhaoorjar**

Data Science • Python • AI/ML • Generative AI

GitHub: [ishikabhaorjar-dotcom](https://github.com/ishikabhaorjar-dotcom)

---

⭐ If you find this project useful, consider giving the repository a star.
