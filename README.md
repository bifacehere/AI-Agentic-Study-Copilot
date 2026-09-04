# AI Agentic Study Copilot

An AI-powered study assistant that converts learning resources such as PDFs and YouTube lectures into structured study material like summaries, key concepts, and flashcards.

## Overview

While studying, I found myself spending a lot of time going through different resources and then manually creating notes for revision.

The idea behind this project was simple:

**Can I automate the process of turning raw learning content into something I can actually revise from?**

Instead of making a single AI summarization call, I designed the project as a sequence of smaller tasks. Each stage is responsible for one part of the workflow, from extracting the original content to generating the final study material.

## Problem Statement

Learning resources are often available in different formats such as:

* PDF notes
* YouTube lectures
* Long-form text

Going through all of this and preparing revision material manually can be time-consuming.

This project tries to automate that process by taking the original content and producing:

* Concise summaries
* Important concepts
* Revision notes
* Flashcards

## How It Works

The workflow is divided into multiple stages:

```text
PDF / YouTube Link
        ↓
Content Extraction
        ↓
Text Processing
        ↓
AI Summarization
        ↓
Study Material Generation
        ↓
Notes + Flashcards
```

### 1. Content Extraction

The system accepts either a PDF or a YouTube lecture.

For PDFs, the text is extracted from the document.

For YouTube videos, the available transcript is retrieved and converted into plain text.

### 2. Text Processing

The extracted content is cleaned and prepared before being sent to the language model.

This stage is important because raw extracted text can contain unnecessary whitespace, formatting issues, or other noise.

### 3. AI Summarization

The processed content is passed to the LLM with instructions to identify the important information rather than simply shortening every sentence.

The output focuses on:

* Main ideas
* Important concepts
* Key information
* Revision-friendly explanations

### 4. Study Material Generation

The generated summary is then used to create additional study material, such as flashcards in a question-and-answer format.

This makes the output more useful for revision than a normal paragraph-based summary.

## Agentic Approach

The main idea I explored in this project was breaking a larger problem into smaller responsibilities.

Instead of asking one model to:

> "Read this document and make everything for me."

I separated the workflow into stages:

* **Extractor** — obtains the original content
* **Processor** — cleans and prepares the content
* **AI/Summarization stage** — identifies and explains important information
* **Generator** — converts the result into revision material

This approach makes each stage easier to understand, test, and modify independently.

## Tech Stack

### Backend

* Python
* FastAPI

### AI

* OpenAI API

### Content Processing

* PyPDF
* YouTube Transcript API

### Storage / Utilities

* Python file handling
* Environment variables for API configuration

## Project Structure

```text
ai-agentic-study-copilot/
│
├── agents/
│   ├── extractor.py
│   ├── processor.py
│   ├── summarizer.py
│   └── generator.py
│
├── main.py
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

## Running the Project

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd ai-agentic-study-copilot
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure the API key

Create a `.env` file and add your API key:

```env
OPENAI_API_KEY=your_api_key_here
```

Do not commit your `.env` file to GitHub.

### 4. Start the FastAPI server

```bash
uvicorn main:app --reload
```

The API documentation can then be accessed through:

```text
http://127.0.0.1:8000/docs
```

## Example Workflow

For example, a student can provide a lecture PDF.

The system:

1. Extracts the text from the PDF.
2. Cleans and prepares the extracted content.
3. Sends the relevant content to the AI model.
4. Generates a structured summary.
5. Creates flashcards from the generated material.

The same general workflow can be used with a YouTube lecture transcript.

## What I Learned

This project taught me that building an AI application is not just about sending a prompt to an LLM.

The main things I learned were:

* How to break a larger problem into smaller, independent processing stages.
* How to design a practical LLM workflow around a real use case.
* How to work with unstructured data such as PDF text and video transcripts.
* How to expose an AI workflow through a REST API using FastAPI.
* How prompt structure and preprocessing can affect the quality of an LLM's output.

## Future Improvements

Some improvements I would like to add:

* Better handling of long documents through chunking
* Retrieval-based question answering
* A proper frontend for uploading and viewing study material
* Quiz generation
* Persistent storage for generated notes
* Evaluation of generated answers and flashcards

## Why I Built It

I wanted to build something that solved a problem I had actually experienced instead of creating an AI project just for demonstration.

The project also gave me a better understanding of how agentic workflows can be used to turn an open-ended task into a sequence of smaller, manageable operations.

## Author

**Sagar Mittal**

AI/ML Developer | Python | Generative AI | Cloud & AI Technologies
