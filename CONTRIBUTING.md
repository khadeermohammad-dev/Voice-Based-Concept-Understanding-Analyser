# 🤝 Contributing to Voice-Based Concept Understanding Analyser

We welcome contributions to improve the **Voice-Based Concept Understanding Analyser (VBCUA)**! Please read the following guidelines before submitting pull requests or opening issues.

---

## 🛠️ How to Contribute

### 1. Fork & Clone
```bash
git clone https://github.com/YOUR_USERNAME/Voice-Based-Concept-Understanding-Analyser.git
cd Voice-Based-Concept-Understanding-Analyser
```

### 2. Create a Feature Branch
```bash
git checkout -b feature/amazing-new-feature
```

### 3. Set Up Local Environment & Install Dependencies
```bash
cd 05_Project_Development/backend
python -m venv venv
# On Windows:
venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate

pip install -r requirements.txt
```

### 4. Commit Your Changes
Keep commit messages clean, concise, and structured (e.g. `feat: add whisper multi-language support`).

### 5. Submit a Pull Request
Push your branch to GitHub and submit a Pull Request targeting the `main` branch.

---

## 🔒 Security Guidelines
- **NEVER** commit real API keys, passwords, or personal credentials.
- Test that `.env` files are ignored by git before submitting.
