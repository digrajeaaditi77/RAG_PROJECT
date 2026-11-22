# PROJECT_RAG
# 📚 ResearchGPT – AI Research Paper Chatbot

ResearchGPT is an AI-powered research paper chatbot that allows users to upload research papers in PDF format and ask questions in natural language. It uses **Retrieval-Augmented Generation (RAG)** to retrieve relevant information from uploaded documents and generate context-aware answers using a locally running Large Language Model (LLM).

The application simplifies the process of understanding lengthy research papers by allowing users to interact with their documents through a chatbot interface.

## 🚀 Features

- **Multiple PDF Upload:** Upload multiple research papers through an interactive interface.
- **PDF Text Extraction:** Extract text and metadata from uploaded research papers.
- **Text Chunking:** Split extracted text into smaller chunks for efficient retrieval.
- **Embedding Generation:** Convert document chunks into numerical vector representations.
- **Semantic Search:** Retrieve relevant document chunks based on the meaning of user queries.
- **AI-Powered Question Answering:** Generate answers using retrieved document content and Ollama.
- **Source Information:** Display paper title, filename, page number, and supporting evidence.
- **Local LLM Integration:** Run the language model locally using Ollama.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Streamlit | Frontend and user interface |
| FastAPI | Backend API development |
| PostgreSQL | Store research paper metadata |
| ChromaDB | Vector database for embeddings |
| Sentence Transformers | Generate text embeddings |
| Ollama (Llama 3.1) | Local LLM for answer generation |
| PyMuPDF | Extract text and metadata from PDFs |

## 🏗️ System Architecture

```text
                User
                  |
                  v
             Streamlit UI
                  |
                  v
             FastAPI Backend
                  |
          PDF Upload / Question
                  |
          +-------+-------+
          |               |
          v               v
     PDF Processing   Question Processing
          |               |
          v               v
     Text Extraction  Query Embedding
          |
          v
      Text Chunking
          |
          v
   Sentence Transformers
          |
          v
       ChromaDB
          |
          v
     Semantic Search
          |
          v
   Relevant Text Chunks
          |
          v
      Ollama (LLM)
          |
          v
    Generated Answer
          |
          v
       Streamlit UI
```

## 🔄 How It Works

### 1. Document Upload
The user uploads one or more research papers in PDF format through the Streamlit interface.

### 2. PDF Processing
FastAPI receives the uploaded documents and extracts their text and metadata using PyMuPDF.

### 3. Text Chunking
The extracted text is divided into smaller chunks to make document retrieval more effective.

### 4. Embedding Generation
Sentence Transformers converts each text chunk into a numerical vector (embedding).

### 5. Data Storage
- **ChromaDB:** Stores document embeddings and associated metadata for semantic search.
- **PostgreSQL:** Stores structured research paper information and metadata.

### 6. Question Processing
When a user asks a question, the question is converted into an embedding using the same embedding model.

### 7. Semantic Retrieval
ChromaDB searches for the most relevant document chunks based on semantic similarity.

### 8. Answer Generation
The retrieved chunks are passed as context to Ollama (Llama 3.1), which generates an answer based on the provided document content.

### 9. Source Display
The generated answer and supporting document information are displayed in the Streamlit interface.

## 🧠 Understanding RAG

**RAG stands for Retrieval-Augmented Generation.**

It combines two main processes:

1. **Retrieval:** Finds relevant information from uploaded documents.
2. **Generation:** Uses an LLM to generate an answer based on the retrieved information.

This approach helps the chatbot answer questions using the user's uploaded research papers rather than relying only on the model's general knowledge.

## 📂 Project Structure

```text
ResearchGPT/
│
├── backend/
│   └── app/
│       ├── main.py
│       ├── models/
│       ├── routes/
│       ├── services/
│       └── utils/
│
├── frontend/
│   └── app.py
│
├── chromadb/
│
├── requirements.txt
├── .env
└── README.md
```

*Note: Update this structure to match your actual project folders and files.*

## ⚙️ Installation and Setup

### Prerequisites

- Python 3.10+
- PostgreSQL
- Ollama
- Git

### 1. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd ResearchGPT
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure PostgreSQL

Create a PostgreSQL database and configure the database connection in your backend environment settings.

### 5. Install and Run Ollama

Download Ollama from:

https://ollama.com/

Pull the Llama 3.1 model:

```bash
ollama pull llama3.1
```

Start Ollama:

```bash
ollama serve
```

### 6. Start the FastAPI Backend

From the project directory:

```bash
cd backend
uvicorn app.main:app --reload
```

Backend URL:

```text
http://127.0.0.1:8000
```

Swagger API documentation:

```text
http://127.0.0.1:8000/docs
```

### 7. Start the Streamlit Frontend

Open another terminal:

```bash
cd frontend
streamlit run app.py
```

Open the application:

```text
http://localhost:8501
```

## 💻 Application Usage

1. Open ResearchGPT in your browser.
2. Upload one or more research papers in PDF format.
3. Wait for document processing and embedding generation.
4. Enter a question related to the uploaded papers.
5. Click the Ask button.
6. View the AI-generated answer.
7. Expand the source section to inspect the paper details, page number, and supporting evidence.

## 🔮 Future Enhancements

- Research paper summarization.
- Improved retrieval using reranking techniques.
- Retrieval confidence scoring.
- PDF evidence highlighting.
- Better document filtering and search.
- User authentication and document management.

## 👩‍💻 Project Goal

The goal of ResearchGPT is to make research papers easier to understand by combining document processing, semantic search, and Generative AI into an interactive question-answering application.
