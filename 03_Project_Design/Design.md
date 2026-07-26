# 📐 Phase 3: Project Design & System Architecture

## 🏗️ System Architecture Overview
The Voice-Based Concept Understanding Analyser (VBCUA) utilizes a modular microservices-oriented application architecture separating audio signal intake, transcription, semantic embedding calculation, generative LLM reasoning, scoring aggregation, and frontend presentation.

```mermaid
graph TB
    subgraph Frontend Layer
        ReactApp[React + Vite Web App]
        StreamlitApp[Streamlit Interactive App]
    end

    subgraph API & Controller Layer
        FastAPI[FastAPI / App Controller app.py]
    end

    subgraph AI Engine & Processing Core
        STTModule[Speech-to-Text Module\nspeech_to_text.py]
        SemEval[Semantic Evaluator\nsemantic_eval.py]
        FactCheck[LLM Fact Checker\nfact_checker.py & gemini_utils.py]
        AudioUtil[Acoustic Audio Utils\naudio_utils.py]
        ScoreEngine[Scoring Engine\nscoring_engine.py]
        PDFGen[PDF Report Generator\nreport_generator.py]
    end

    ReactApp -->|REST / Form Data| FastAPI
    StreamlitApp -->|Direct Import| API
    FastAPI --> STTModule
    FastAPI --> SemEval
    FastAPI --> FactCheck
    FastAPI --> AudioUtil
    STTModule --> ScoreEngine
    SemEval --> ScoreEngine
    FactCheck --> ScoreEngine
    AudioUtil --> ScoreEngine
    ScoreEngine --> PDFGen
    ScoreEngine --> ReactApp
    ScoreEngine --> StreamlitApp
```

---

## 🔁 Sequence Diagram: Evaluation Flow

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant Dashboard as Web Dashboard
    participant STT as Whisper STT Engine
    participant SBERT as Sentence-BERT Engine
    participant Gemini as Google Gemini API
    participant Acoustic as Librosa Audio Analyzer
    participant PDF as ReportLab PDF Engine

    Student->>Dashboard: Select Reference Concept & Upload Audio
    Dashboard->>STT: Send Audio File
    STT-->>Dashboard: Return Transcript String
    Dashboard->>SBERT: Compare Transcript vs Reference Concept
    SBERT-->>Dashboard: Return Cosine Similarity Score
    Dashboard->>Gemini: Prompt Fact-Checking Analysis
    Gemini-->>Dashboard: Return Fact Accuracy & Suggestions
    Dashboard->>Acoustic: Analyze Waveform & Energy
    Acoustic-->>Dashboard: Return Filler Count, Pauses, RMS
    Dashboard->>PDF: Compile All Metrics into PDF
    PDF-->>Dashboard: Generated Evaluation Report PDF
    Dashboard-->>Student: Display Comprehensive Scorecard & PDF Download
```

---

## 🗄️ Database & Schema Design

| Table / Entity | Field | Type | Description |
| :--- | :--- | :--- | :--- |
| `EvaluationSession` | `session_id` | `UUID` | Primary Key |
| | `student_name` | `VARCHAR(100)` | Name of student |
| | `concept_name` | `VARCHAR(200)` | Evaluated concept title |
| | `transcript` | `TEXT` | Generated speech transcript |
| | `similarity_score` | `FLOAT` | Cosine similarity score (0-1) |
| | `factual_score` | `FLOAT` | LLM factual accuracy score |
| | `fluency_score` | `FLOAT` | Acoustic fluency rating |
| | `filler_count` | `INTEGER` | Detected filler word count |
| | `created_at` | `TIMESTAMP` | Timestamp of evaluation |

```mermaid
erDiagram
    EVALUATION_SESSION {
        string session_id PK
        string student_name
        string concept_name
        string transcript
        float similarity_score
        float factual_score
        float fluency_score
        int filler_count
        datetime created_at
    }
```
