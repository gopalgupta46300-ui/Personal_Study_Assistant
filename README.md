# Personal Study Assistant

<p align="center">
  <img src="https://images.unsplash.com/photo-1522202176988-66273c2fd55f?auto=format&fit=crop&w=1400&q=80" alt="Study Assistant Banner" width="100%" />
</p>

<p align="center">
  <a href="#features"><img src="https://img.shields.io/badge/Features-Study%20AI-6C63FF?style=for-the-badge" alt="Features" /></a>
  <a href="#tech-stack"><img src="https://img.shields.io/badge/Stack-Groq%20%2B%20Python-00C2A8?style=for-the-badge" alt="Stack" /></a>
  <a href="#how-it-works"><img src="https://img.shields.io/badge/Workflow-PDF%20to%20Notes-FF7F50?style=for-the-badge" alt="Workflow" /></a>
</p>

A smart AI-powered study assistant built in Python using Groq and Google Colab. It helps students turn uploaded study materials into clean summaries, key points, flashcards, and quiz questions.

## Overview

This project is designed for learners who want to process notes, PDFs, and documents quickly. Instead of manually reading large study material, the system extracts text, sends it to a large language model, and generates structured learning outputs.

## Features

- Upload PDF, TXT, and DOCX study files
- Extracts text automatically from supported formats
- Uses Groq-hosted LLMs for fast responses
- Generates:
  - summary
  - key points
  - flashcards
  - quiz questions with answers
- Saves the generated output to a text file
- Built for Google Colab workflows and rapid experimentation

## Tech Stack

- Python
- Groq API
- Google Colab
- PyPDF
- python-docx
- LLM prompt engineering

## Project Structure

```text
Personal_Study_Assistant/
├── README.md
├── personal_study_assistnt.ipynb
└── study_notes.txt (generated during execution)
```

## How It Works

1. Upload a study file (PDF, TXT, or DOCX)
2. Extract text from the uploaded document
3. Build a study prompt for the AI model
4. Generate:
   - summary
   - key concepts
   - flashcards
   - quiz questions
5. Save the final study notes

## Example Workflow

```python
uploaded = files.upload()
file_name = list(uploaded.keys())[0]

def extract_text(file_name):
    if file_name.endswith(".pdf"):
        reader = PdfReader(file_name)
        text = "".join(page.extract_text() or "" for page in reader.pages)
        return text
    elif file_name.endswith(".txt"):
        with open(file_name, "r", encoding="utf-8") as f:
            return f.read()
    elif file_name.endswith(".docx"):
        doc = docx.Document(file_name)
        return "\n".join(p.text for p in doc.paragraphs)
```

## AI Prompt Logic

The assistant is prompted to produce:

```text
1. Summary
2. Key Points
3. Flashcards
4. Quiz Questions with answers
```

This creates a structured study package that is easier to review and memorize.

## Installation

This notebook is intended to run in Google Colab.

```python
!pip install groq pypdf python-docx
```

Then add your API key:

```python
import os
os.environ["GROQ_API_KEY"] = "your_key_here"
```

## Run the Notebook

Open `personal_study_assistnt.ipynb` in Colab and execute the cells in order:

1. Install dependencies
2. Import libraries
3. Set the Groq API key
4. Upload your study material
5. Generate the summary and quiz output
6. Save `study_notes.txt`

## Screenshots

<p align="center">
  <img src="https://images.unsplash.com/photo-1503676260728-1c00da094a0b?auto=format&fit=crop&w=1200&q=80" alt="Study notes illustration" width="80%" />
</p>

## License

This project is available for educational and personal use. Please check the repository license if applicable.

---

Built to make studying smarter, faster, and more structured.
