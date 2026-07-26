# 📜 Changelog

All notable changes to the **Voice-Based Concept Understanding Analyser (VBCUA)** project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2026-07-26

### 🚀 Added
- **OpenAI Whisper Speech-to-Text Integration**: Automated conversion of user audio explanations to text transcripts.
- **Sentence-BERT Semantic Matching**: Cosine similarity computation between student transcript embeddings and reference concepts using `all-MiniLM-L6-v2`.
- **Google Gemini API Fact Checker**: Automated AI reasoning for factual accuracy validation and missing sub-concept suggestions.
- **Librosa Acoustic Analytics**: Acoustic feature extraction for RMS energy, unnatural silence pauses, and filler word frequency ("um", "uh", "like").
- **ReportLab PDF Generator**: Automated generation of formatted evaluation reports and certificates.
- **Dual Frontends**: Interactive Streamlit web application and React + Vite modern dashboard.
- **Project Structure**: Organized project layout into standard phase folders (`01_Brainstorming` through `08_Project_Demonstration`).
