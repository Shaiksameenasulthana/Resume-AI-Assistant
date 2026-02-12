# 🤖 Resume AI Assistant

An AI-powered Resume Screening and Analysis system built with **LlamaIndex** and **OpenAI GPT**, enabling HR professionals to intelligently query, filter, and evaluate candidate resumes using natural language.

---

## 📌 Project Overview

This project provides two core capabilities:

**1. Resume Filtering & Analysis** — Upload multiple resumes and ask natural language questions like *"Who has Python skills?"*, *"Which candidate fits a Data Scientist role?"*, or *"Generate interview questions for the best candidate."*

**2. Resume Query Assistant (Flask API)** — A web API that lets users query resumes through HTTP endpoints, making it easy to integrate resume intelligence into any application.

---

## 📁 Repository Structure

```
├── Resume_filtering_Llama_index.ipynb    # Interactive resume screening & analysis
├── Resume_assistant_Llama_index.ipynb    # Flask-based REST API for resume queries
└── README.md
```

---

## ✨ Features

### Resume Filtering (`Resume_filtering_Llama_index.ipynb`)
- Load and index multiple PDF resumes from a directory
- Query candidate names, skills, education, and experience
- Filter candidates by specific job roles (Data Scientist, Data Analyst, etc.)
- Get AI-powered recommendations on role suitability with reasoning
- Compare candidates and identify the best fit
- Auto-generate interview questions based on resume content
- Identify why candidates are or aren't suitable for specific roles

### Resume Assistant API (`Resume_assistant_Llama_index.ipynb`)
- **Flask REST API** to query resumes via HTTP
- `GET /ask_documents/?q=your question` — Ask any question about the loaded resumes
- `GET /search/?q=name` — Simple search endpoint
- Easy to integrate with frontend applications or chatbots

---

## 💡 Example Queries

```
"Provide me the list of people who have Python programming skills"
"Which role is suitable for Jyothi's resume and give me a reason"
"As a HR, select candidates suitable for a Data Scientist role with reasons"
"Which is the best resume? Select it and generate interview questions"
"Provide key points on Rajasri Gudikandula's resume"
"Provide college names of all candidates"
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| LLM | OpenAI GPT (via API) |
| Framework | LlamaIndex (RAG-based document Q&A) |
| Vector Index | LlamaIndex VectorStoreIndex |
| Document Loader | SimpleDirectoryReader (supports PDF, DOCX, etc.) |
| Web API | Flask |
| Language | Python 3.x |
| Environment | Jupyter Notebook |

---

## 🏗️ Architecture

```
Resume PDFs (Directory)
        │
        ▼
┌──────────────────────┐
│  SimpleDirectoryReader │
│  (Load & Parse PDFs)  │
└────────┬─────────────┘
         ▼
┌──────────────────────┐
│  VectorStoreIndex     │
│  (Embedding + Index)  │
└────────┬─────────────┘
         ▼
┌──────────────────────┐
│  Query Engine         │
│  (similarity_top_k)   │
└────────┬─────────────┘
         ▼
   ┌─────┴──────┐
   │             │
Jupyter       Flask API
Notebook      /ask_documents/
(Interactive)  (HTTP Access)
   │             │
   ▼             ▼
  AI-Powered Responses
  (Filtering, Ranking,
   Interview Questions)
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install llama-index openai flask
```

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/Shaiksameenasulthana/Resume-AI-Assistant.git
   cd Resume-AI-Assistant
   ```

2. Set your OpenAI API key:
   ```python
   import os
   os.environ["OPENAI_API_KEY"] = "your-api-key-here"
   ```

3. Place your resume PDFs in a folder and update the path in the notebook:
   ```python
   documents = SimpleDirectoryReader("path/to/resumes", recursive=True).load_data()
   ```

4. Run the notebooks in Jupyter:
   ```bash
   jupyter notebook
   ```

### Running the Flask API

After running `Resume_assistant_Llama_index.ipynb`, the API will be available at:

```
http://127.0.0.1:5000/ask_documents/?q=your question here
```

---

## ⚠️ Important Notes

- You need a valid **OpenAI API key** to run this project.
- Resume files should be in **PDF format** placed in a single directory.
- The `similarity_top_k` parameter controls how many resume chunks are considered per query (set to 25–100 depending on the notebook).
- This is a development server; for production use, deploy with a WSGI server like Gunicorn.

---

## 🙋‍♀️ Author

**Shaik Sameena Sulthana**

- GitHub: [@Shaiksameenasulthana](https://github.com/Shaiksameenasulthana)

---

## 📄 License

This project is open source and available for educational purposes.

---

⭐ If you found this project helpful, please consider giving it a star!
