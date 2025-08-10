# 🎥 YouTube RAG Notes

A Python project that extracts transcripts from YouTube videos, summarizes them into notes using a local LLaMA model via Ollama, and stores them in a Chroma vector database for semantic search and retrieval-augmented generation (RAG).

## 🚀 Features
- **Transcript Extraction** – Fetches video transcripts in English using [`youtube-transcript-api`](https://github.com/jdepoix/youtube-transcript-api).  
- **Local AI Summarization** – Uses [Ollama](https://ollama.ai) with LLaMA 3 to generate concise notes locally — no API keys required.  
- **Vector Database Storage** – Stores notes as embeddings in a [ChromaDB](https://www.trychroma.com/) persistent database.  
- **Semantic Search** – Quickly find relevant videos or notes based on natural language queries.  
- **RAG Question Answering** – Retrieves relevant notes and uses them as context to answer user questions.

## 🛠️ Installation
1. **Clone the Repository**
    ```bash
    git clone https://github.com/your-username/yt-rag-notes.git
    cd yt-rag-notes
    ```
2. **Install Dependencies**
    ```bash
    pip install youtube-transcript-api chromadb ollama
    ```
3. **Install and Run Ollama**
    - Download Ollama from: [https://ollama.ai](https://ollama.ai)  
    - Start Ollama server:
      ```bash
      ollama serve
      ```
    - Pull required models:
      ```bash
      ollama pull llama3
      ollama pull nomic-embed-text
      ```

## 📄 Usage
1. **Set the YouTube Video ID** in `main.py`:
    ```python
    yt_video_id = "VIDEO_ID_HERE"
    ```
2. **Run the Script**
    ```bash
    python main.py
    ```
3. **Search Your Notes**
    ```python
    query_text = "Explain transformers vs RNN"
    ```
4. **Ask Questions with RAG**
    ```python
    context_doc = retrieved_notes
    ollama.chat(
        model="llama3",
        messages=[{"role": "user", "content": question_with_context}]
    )
    ```

## 📂 Project Structure
```bash
yt-rag-notes/
├── main.ipynb              # Main script for transcript extraction, summarization, and storage
├── temp_transcript.txt     # Raw transcript (generated)
├── temp_notes.txt          # AI-generated notes (generated)
└── README.md               # Project documentation
