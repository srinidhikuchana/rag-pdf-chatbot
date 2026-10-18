# 📄 RAG PDF Chatbot using Gemini, ChromaDB & Gradio

An AI-powered **Retrieval-Augmented Generation (RAG) chatbot** that allows users to upload PDF documents and ask questions based on their content.

The application combines **Google Gemini 2.5 Flash**, **Sentence Transformers**, **ChromaDB**, and **Gradio** to deliver context-aware answers using information retrieved from uploaded documents.

## 🚀 Features

- 📄 **PDF Upload:** Upload PDF documents for processing.
- 🔍 **Semantic Search:** Retrieve relevant document sections using vector embeddings.
- 🤖 **AI-Powered Answers:** Generate context-aware responses using Gemini 2.5 Flash.
- 🧠 **RAG Architecture:** Combine document retrieval with large language model generation.
- 💾 **Vector Database:** Store and retrieve document embeddings using ChromaDB.
- 🌐 **Interactive UI:** Simple web interface built with Gradio.
- 🔒 **Document-Grounded Responses:** Prompt the model to answer using only the retrieved document context.
- ⚡ **Efficient Embeddings:** Uses the lightweight `all-MiniLM-L6-v2` embedding model.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Backend development |
| Google Gemini 2.5 Flash | Large Language Model |
| Sentence Transformers | Text embeddings |
| ChromaDB | Vector database |
| Gradio | Web interface |
| PyPDF | PDF text extraction |
| UUID | Unique chunk identifiers |

## 🏗️ System Architecture

```text
           User
             |
             v
       Gradio Interface
             |
             v
        PDF Upload
             |
             v
     PDF Text Extraction
          (PyPDF)
             |
             v
       Text Chunking
        (500 words)
             |
             v
     Sentence Transformers
       (MiniLM-L6-v2)
             |
             v
       Vector Embeddings
             |
             v
          ChromaDB
       (Vector Storage)
             |
             |
      User Question
             |
             v
       Query Embedding
             |
             v
      Similarity Search
        (Top 3 Chunks)
             |
             v
       Retrieved Context
             |
             v
      Gemini 2.5 Flash
             |
             v
      Generated Answer
             |
             v
       Gradio Interface
```

## ⚙️ Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment.

**Windows:**

```bash
venv\Scripts\activate
```

**Linux / macOS:**

```bash
source venv/bin/activate
```

### 3. Install Dependencies

Create a `requirements.txt` file containing:

```txt
gradio
chromadb
google-generativeai
pypdf
sentence-transformers
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

### 4. Configure Gemini API Key

Obtain your API key from [Google AI Studio](https://aistudio.google.com/apikey).

Set the environment variable.

**Windows PowerShell:**

```powershell
$env:GOOGLE_API_KEY="your_api_key"
```

**Linux / macOS:**

```bash
export GOOGLE_API_KEY="your_api_key"
```

**Important:** Never commit your API key to GitHub.

### 5. Run the Application

```bash
python app.py
```

Open the Gradio interface at:

```text
http://localhost:7860
```

## 📖 How It Works

### Step 1: PDF Processing

The user uploads a PDF document through the Gradio interface.

PyPDF extracts text from each page of the document.

### Step 2: Text Chunking

The extracted text is divided into chunks of approximately 500 words.

Chunking helps process large documents and enables efficient information retrieval.

### Step 3: Embedding Generation

Each text chunk is converted into a numerical vector using the Sentence Transformer model:

`all-MiniLM-L6-v2`

These embeddings capture semantic relationships between text passages.

### Step 4: Vector Storage

The generated embeddings and their corresponding text chunks are stored in a persistent ChromaDB collection.

Indexing a new PDF replaces the previously indexed document collection.

### Step 5: Semantic Retrieval

When a user submits a question:

1. The question is converted into an embedding.
2. ChromaDB performs similarity search.
3. The top 3 relevant document chunks are retrieved.

### Step 6: Answer Generation

The retrieved chunks are passed to Gemini 2.5 Flash along with the user's question.

The prompt instructs Gemini to answer using only the provided context.

If the answer is unavailable, the model is instructed to respond:

> I couldn't find the answer in the document.

### Step 7: Display Response

The generated answer is displayed through the Gradio interface.

## 📁 Project Structure

```text
RAG-PDF-Chatbot/
│
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
│
└── chroma_db/       # Created automatically
```

### Recommended `.gitignore`

```gitignore
venv/
.venv/
__pycache__/
*.pyc
.env
chroma_db/
```

## 💡 Example Usage

**Uploaded Document:** Machine Learning Notes.pdf

**User Question:**

```text
What is overfitting in machine learning?
```

**Example Response:**

```text
Overfitting occurs when a machine learning model
learns the training data too closely, including
noise and irrelevant patterns, resulting in poor
generalization to unseen data.
```

*The actual response depends on the uploaded PDF.*

## ⚠️ Current Limitations

- Supports PDF documents only.
- Processes one document collection at a time.
- Uses fixed-size word-based chunking without overlap.
- Does not provide page-level source citations.
- Scanned PDFs without extractable text may require OCR.
- Requires an internet connection for Gemini API calls.
- Answers depend on retrieval quality and model behavior.

## 🔮 Future Enhancements

- [ ] Support multiple PDF documents simultaneously.
- [ ] Implement conversational memory for follow-up questions.
- [ ] Add source citations and page references.
- [ ] Improve retrieval with overlapping chunks.
- [ ] Support DOCX and TXT documents.
- [ ] Integrate hybrid search and reranking.
- [ ] Add OCR support for scanned PDFs.
- [ ] Implement document management and deletion.
- [ ] Deploy the application to a cloud platform.

## 🎯 Learning Outcomes

This project demonstrates practical experience with:

- Retrieval-Augmented Generation (RAG)
- Large Language Model integration
- Natural Language Processing (NLP)
- Semantic search and vector embeddings
- Vector database management
- PDF processing and text chunking
- Building AI applications using Python
- Developing interactive interfaces with Gradio

## 👩‍💻 Author

**Sri Nidhi Kuchana**

B.Tech – Computer Science and Engineering

[LinkedIn](https://linkedin.com/in/srinidhikuchana)

## ⭐ Support

If you find this project useful, consider giving the repository a star!

---

**Built with Python, Gemini, ChromaDB, Sentence Transformers, and Gradio.**
