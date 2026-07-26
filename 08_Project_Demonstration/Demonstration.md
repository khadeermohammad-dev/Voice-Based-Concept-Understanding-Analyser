# 🎬 Phase 8: Project Demonstration & Video Guide

## 📺 Demonstration Overview
This document guides users and evaluators through demonstrating the Voice-Based Concept Understanding Analyser application step by step.

---

## ⚡ Quick Demonstration Steps

### Step 1: Launch Application Stack
Run the convenience launch script inside `05_Project_Development/`:

```cmd
cd 05_Project_Development
start_project.bat
```

This launches both the Python Streamlit web dashboard at `http://localhost:8501` and the React + Vite frontend application at `http://localhost:5173`.

### Step 2: Select a Reference Concept
In the web interface:
1. Choose a pre-configured concept (e.g., *Machine Learning*, *Supervised vs Unsupervised Learning*, *Overfitting & Underfitting*) or type a custom reference concept.

### Step 3: Upload or Record Spoken Explanation
1. Upload an audio recording file (`.wav` or `.mp3`) of a student explaining the concept.
2. Click **Analyze Voice Concept**.

### Step 4: Review Assessment Dashboard
1. Inspect the generated **Transcript**.
2. View the **Semantic Similarity Score Gauge** (e.g., `85% Match - Good Understanding`).
3. Check the **LLM Factual Feedback** section powered by Google Gemini.
4. Review the **Acoustic Fluency Breakdown** (Filler words count, average pause duration).

### Step 5: Export PDF Evaluation Report
1. Click **Download Evaluation PDF Report**.
2. Open the downloaded PDF to view the compiled evaluation certificate.

---

## 📹 Video Demo Information
- **Video Title**: Voice-Based Concept Understanding Analyser Complete Walkthrough
- **Location**: Refer to `video_demo/README.md` for video demo download links and preview notes.
