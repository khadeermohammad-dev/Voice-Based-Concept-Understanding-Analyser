# 📋 Phase 2: Requirement Analysis

## 🎯 Functional Requirements (FR)

### FR-1: Speech-to-Text Processing
- **FR-1.1**: System shall accept audio files in `.wav`, `.mp3`, `.m4a`, or `.ogg` formats.
- **FR-1.2**: System shall transcribe audio into text using OpenAI Whisper / Web Speech API with minimum 90% word accuracy for clear speech.

### FR-2: Semantic Understanding Evaluation
- **FR-2.1**: System shall compare student transcript against reference concept definitions using Sentence-BERT embeddings.
- **FR-2.2**: System shall calculate cosine similarity score (range 0.0 to 1.0) and map to performance tiers (Excellent, Good, Needs Improvement, Poor).

### FR-3: Generative LLM Fact-Checking & Feedback
- **FR-3.1**: System shall integrate Google Gemini API to analyze factual correctness and concept accuracy.
- **FR-3.2**: System shall generate personalized natural language suggestions detailing missing sub-concepts.

### FR-4: Vocal Analytics & Signal Processing
- **FR-4.1**: System shall analyze audio waveforms using Librosa to calculate RMS energy and signal amplitude.
- **FR-4.2**: System shall identify acoustic pauses (>0.5 sec) and filler words ("um", "uh", "like") to score speech fluency.

### FR-5: Dashboard & PDF Export
- **FR-5.1**: System shall render interactive charts for score breakdowns and speech pace.
- **FR-5.2**: System shall generate downloadable PDF evaluation reports using ReportLab.

---

## ⚙️ Non-Functional Requirements (NFR)

### NFR-1: Performance & Latency
- Response time for audio transcription and semantic analysis shall be under 5 seconds for 60-second audio files.

### NFR-2: Security & Privacy
- API keys (e.g. `GEMINI_API_KEY`) must be stored in `.env` files and excluded from git tracking.
- Audio uploads shall be processed in-memory or stored temporarily without persistent exposure.

### NFR-3: Usability & Accessibility
- System user interface shall follow responsive web design standards across desktop and mobile screen sizes.

---

## 🛠️ Tech Stack Requirements

| Component | Technology Selected | Version / Details |
| :--- | :--- | :--- |
| **Language Core** | Python, JavaScript | Python 3.10+, Node.js 18+ |
| **Speech Recognition** | OpenAI Whisper | Base / Small Model |
| **Semantic NLP** | Sentence-Transformers | `all-MiniLM-L6-v2` |
| **LLM Reasoning** | Google Gemini API | `google-genai` SDK |
| **Signal Processing** | Librosa, SciPy | Librosa 0.10.1 |
| **Frontend UI** | React + Vite / Streamlit | React 18, Streamlit 1.30+ |
| **PDF Rendering** | ReportLab | ReportLab 4.0+ |
