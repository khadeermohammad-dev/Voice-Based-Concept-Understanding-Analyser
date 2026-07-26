<div align="center">

# 🎙️ Voice-Based Concept Understanding Analyser (VBCUA)

[![Python Version](https://img.shields.io/badge/Python-3.10%2B-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![React Version](https://img.shields.io/badge/React-18.0-61DAFB.svg?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.30%2B-FF4B4B.svg?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![Google Gemini API](https://img.shields.io/badge/Gemini--API-Enabled-8E44AD.svg?style=for-the-badge&logo=google&logoColor=white)](https://ai.google.dev/)
[![Sentence-BERT](https://img.shields.io/badge/Model-Sentence--BERT-FF6F00.svg?style=for-the-badge&logo=tensorflow&logoColor=white)](https://www.sbert.net/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

*An AI-powered, multi-dimensional evaluation platform for assessing oral technical explanations using Speech Recognition, Sentence Embeddings, Generative LLM Fact-Checking, and Vocal Signal Processing.*

---

[Key Features](#-key-features) •
[System Architecture](#%EF%B8%8F-system-architecture) •
[Installation & Quick Start](#-installation--quick-start) •
[Directory Structure](#-repository-structure) •
[Screenshots](#-screenshots--user-interface) •
[Testing](#-testing-suite) •
[License](#-license)

</div>

---

## 📖 Executive Overview

Traditional student evaluation relies heavily on written exams, which frequently fail to capture verbal articulation, conceptual depth, and real-time explanation clarity. Oral assessments (*viva-voce*) solve this but suffer from evaluator fatigue, subjectivity, and lack of scalability.

**Voice-Based Concept Understanding Analyser (VBCUA)** automates oral concept evaluation by combining state-of-the-art NLP, generative AI, and acoustic signal processing into a unified evaluation pipeline:

1. **Speech Transcription**: Converts student audio into accurate text using OpenAI Whisper.
2. **Semantic Similarity Vector Matching**: Computes cosine similarity between student transcripts and reference concept definitions using Sentence-BERT (`all-MiniLM-L6-v2`).
3. **LLM Fact Validation**: Evaluates factual accuracy, detects missing sub-concepts, and provides natural-language suggestions via Google Gemini API.
4. **Vocal & Acoustic Analytics**: Measures speech fluency, RMS audio energy, unnatural pauses, and filler word frequency ("um", "uh", "like") via Librosa.
5. **Dynamic PDF Report Export**: Compiles scores and visual charts into downloadable PDF assessment certificates powered by ReportLab.

---

## ✨ Key Features

- **🎙️ Speech-to-Text Processing**: Supports `.wav`, `.mp3`, `.m4a`, and `.ogg` formats with OpenAI Whisper model integration.
- **🧠 Semantic Vector Matching**: Deep sentence embedding comparison beyond surface-level keyword lookup.
- **⚡ Google Gemini AI Reasoning**: Generative factual analysis flagging missing technical sub-concepts.
- **📊 Vocal Fluency Metrics**: Detects hesitations, silence pauses (>0.5s), and filler word usage.
- **📄 ReportLab PDF Export**: Instant generation of structured PDF assessment reports with scorecards.
- **💻 Dual Frontend Support**: Modern React + Vite web dashboard alongside a lightweight Python Streamlit app.

---

## 🏗️ System Architecture

```mermaid
graph TB
    subgraph Client Layer
        ReactApp[React + Vite Web App]
        StreamlitApp[Streamlit App]
    end

    subgraph Backend Application Controller
        App[App Core Controller app.py]
    end

    subgraph Intelligence & Analytics Core
        STT[Speech-to-Text Whisper Engine]
        SBERT[Sentence-BERT Vector Similarity]
        Gemini[Google Gemini API Fact Checker]
        Acoustic[Librosa Vocal Signal Processor]
        Scoring[Unified Multi-Metric Scoring Engine]
        PDFEngine[ReportLab PDF Generator]
    end

    ReactApp -->|REST / Multipart Form| App
    StreamlitApp -->|Direct Integration| App
    App --> STT
    App --> SBERT
    App --> Gemini
    App --> Acoustic
    STT --> Scoring
    SBERT --> Scoring
    Gemini --> Scoring
    Acoustic --> Scoring
    Scoring --> PDFEngine
    Scoring --> ReactApp
    Scoring --> StreamlitApp
```

---

## 🔁 Sequence & Data Flow

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant Dashboard as Web Interface
    participant Whisper as Whisper STT
    participant SBERT as SBERT Embeddings
    participant Gemini as Google Gemini API
    participant Librosa as Librosa Acoustic Processor
    participant PDF as PDF Generator

    Student->>Dashboard: Select Concept & Upload Audio Recording
    Dashboard->>Whisper: Pass Audio File
    Whisper-->>Dashboard: Return Text Transcript
    Dashboard->>SBERT: Compare Transcript vs Reference Concept
    SBERT-->>Dashboard: Return Cosine Similarity Score
    Dashboard->>Gemini: Prompt Factual Validation
    Gemini-->>Dashboard: Return Fact Score & Improvement Suggestions
    Dashboard->>Librosa: Extract Acoustic Features
    Librosa-->>Dashboard: Return Filler Count, Pauses, RMS Energy
    Dashboard->>PDF: Render Assessment Data into PDF
    PDF-->>Dashboard: Generated Evaluation Report PDF
    Dashboard-->>Student: Display Dashboard & PDF Download Link
```

---

## 🗄️ Database & Entity Relationship Diagram

```mermaid
erDiagram
    EVALUATION_SESSIONS {
        int session_id PK
        string student_name
        string reference_concept
        string transcript
        float similarity_score
        float factual_score
        float fluency_score
        int filler_word_count
        int pause_count
        datetime created_at
    }
```

---

## 📁 Repository Structure

```
.
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── workflows/
│       └── python-app.yml
├── 01_Brainstorming/
│   ├── Brainstorming.md
│   └── Idea.md
├── 02_Requirement_Analysis/
│   └── Requirements.md
├── 03_Project_Design/
│   └── Design.md
├── 04_Project_Planning/
│   └── Planning.md
├── 05_Project_Development/
│   ├── backend/
│   │   ├── app.py
│   │   ├── audio_utils.py
│   │   ├── fact_checker.py
│   │   ├── gemini_utils.py
│   │   ├── landing_page.py
│   │   ├── reference_concepts.json
│   │   ├── report_generator.py
│   │   ├── requirements.txt
│   │   ├── scoring_engine.py
│   │   ├── semantic_eval.py
│   │   ├── speech_to_text.py
│   │   ├── style_utils.py
│   │   ├── .env.example
│   │   ├── test_audio.py
│   │   ├── test_fact_checker.py
│   │   ├── test_gemini.py
│   │   ├── test_similarity.py
│   │   ├── waveform/
│   │   └── website/
│   ├── frontend/
│   │   ├── public/
│   │   ├── src/
│   │   ├── index.html
│   │   ├── package.json
│   │   └── vite.config.js
│   └── start_project.bat
├── 06_Project_Testing/
│   └── Testing.md
├── 07_Project_Documentation/
│   └── Project_Report.md
├── 08_Project_Demonstration/
│   └── Demonstration.md
├── Screenshots/
│   ├── README.md
│   └── [UI Screenshots & Diagrams]
├── video_demo/
│   └── README.md
├── .env.example
├── .gitignore
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

---

## 🚀 Installation & Quick Start

### Prerequisites
- **Python**: Version 3.10 or higher
- **Node.js**: Version 18.0 or higher
- **FFmpeg**: Required for audio processing (`choco install ffmpeg` on Windows, `brew install ffmpeg` on macOS)

### 1. Clone the Repository
```bash
git clone <your_repository_url>
cd main-sub-project
```

### 2. Configure Environment Variables
Copy `.env.example` to `.env` inside `05_Project_Development/backend/`:
```bash
cp .env.example 05_Project_Development/backend/.env
```
Open `05_Project_Development/backend/.env` and add your Google Gemini API key:
```env
GEMINI_API_KEY=AIzaSyYourActualGeminiKeyHere
SIMILARITY_THRESHOLD=0.75
PORT=8501
```

### 3. Quick Run via Batch Script (Windows)
```cmd
cd 05_Project_Development
start_project.bat
```

### 4. Manual Setup & Run

#### Backend Setup:
```bash
cd 05_Project_Development/backend
python -m venv venv

# Windows Activation:
venv\Scripts\activate
# macOS/Linux Activation:
source venv/bin/activate

pip install -r requirements.txt
streamlit run app.py
```
*Access Streamlit app at:* `http://localhost:8501`

#### Frontend Setup:
```bash
cd 05_Project_Development/frontend
npm install
npm run dev
```
*Access React app at:* `http://localhost:5173`

---

## 📸 Screenshots & User Interface

### Main Dashboard Interface
![Dashboard](Screenshots/dashboard.png)

### Waveform Signal Analytics
![Waveform](Screenshots/wave.png)

### AI Brain Concept Analysis Banner
![Brain AI](Screenshots/brain.png)

---

## 🧪 Testing Suite

Automated backend unit tests verify audio processing, similarity algorithms, and API connections:

```bash
cd 05_Project_Development/backend
python test_audio.py
python test_similarity.py
python test_fact_checker.py
```

---

## 🔒 Security & Data Privacy

- **Sanitized Credentials**: `.env` files containing `GEMINI_API_KEY` are ignored in `.gitignore` and never committed to git repositories.
- **In-Memory Audio Processing**: Uploaded audio files are processed without long-term persistent storage.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🤝 Acknowledgements

- **OpenAI Whisper** for state-of-the-art speech transcription.
- **Sentence-Transformers (SBERT)** for semantic embeddings.
- **Google Gemini API** for generative factual validation.
- **Librosa** for audio signal processing.
- **ReportLab** for dynamic PDF generation.
