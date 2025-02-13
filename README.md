# PDF-RAG: Retrieval-Augmented Generation for ArXiv Papers

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline tailored to handle ArXiv papers. It focuses on multi-format content (text, images, tables) in PDFs, enabling efficient query-based retrieval and response generation.

---

## Project Structure

```
pdf-rag/
├── .git/                # Git version control folder
├── backend/             # Backend logic for RAG pipeline
├── faiss_storage/       # FAISS index storage for vectorized embeddings
├── json_vectorization/  # Handles JSON-based text and image vectorization
├── llm-integration/     # Code for integrating with Language Models
├── pdf_scraping/        # Scripts for scraping and downloading ArXiv PDFs
├── pdf-rag-venv/        # Python virtual environment
├── rocks_storage/       # RocksDB storage for key-value metadata
├── tests/               # Unit and integration test cases
├── .gitignore           # Files and folders to ignore in Git
├── Dockerfile           # Docker configuration for containerizing the app
├── handler/             # API or main service handler
├── main.py              # Main entry point of the application
├── README.md            # Project documentation
```

---

## Features

1. **PDF Scraping**: Automatically downloads and preprocesses ArXiv papers from a specified topic and time range.
2. **Metadata Storage**:
   - RocksDB for fast key-value lookups of structured metadata.
   - FAISS for vector-based similarity searches.
3. **Vectorization**: Text and images from papers are converted to 512-dimensional embeddings using OpenAI's CLIP model.
4. **RAG Integration**: Retrieval-Augmented Generation ensures that user queries retrieve relevant content and generate coherent responses.
5. **LLM Integration**: Combines metadata and embeddings for accurate, context-specific responses.

---

## Prerequisites

- **Python Version**: 3.10 or higher
- **Libraries**:
  - `arxiv`
  - `requests`
  - `PyPDF2`
  - `pandas`
  - `tqdm`
  - `faiss`
  - `rockdb-python`
  - `clip`
  - `torch`
  - `langchain`
- **Optional**: Docker for containerized deployment

---

## Setup

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd pdf-rag
   ```

2. Set up the virtual environment:

   ```bash
   python3 -m venv pdf-rag-venv
   source pdf-rag-venv/bin/activate  # Linux/Mac
   pdf-rag-venv\Scripts\activate     # Windows
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Configure environment variables (if required) in `.env`.

---

## Usage

### 1. Scrape PDFs

Run the scraper to download and preprocess ArXiv papers:

```bash
python pdf_scraping/main.py
```

### 2. Vectorize Content

Convert the scraped content into embeddings:

```bash
python json_vectorization/vectorize.py
```

### 3. Run the Backend

Start the backend server to handle user queries:

```bash
python main.py
```

---

## Future Enhancements

- Cloud-based object storage for scalability.
- Real-time querying through web-based UI.
- Support for additional academic repositories.

---

For detailed information, refer to individual module documentation or contact the contributors.
