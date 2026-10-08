# ScamShield AI – Intelligent Scam Detection Assistant

### Tagline
**Detect. Explain. Protect.**

---

## 1. Project Title & Overview
**ScamShield AI** is an intelligent, end-to-end AI cybersecurity product built for the **Generative AI & Intelligent Assistant Hackathon**.

It provides real-time fraud detection, social engineering analysis, explainable threat reasoning, multi-turn conversation intelligence, and grounded Generative AI safety guidance.

---

## 2. Problem Statement
Digital scams across SMS, WhatsApp, and Email leverage urgency, fear, authority impersonation, fake KYC notifications, and OTP theft. Traditional spam filters provide only binary "Spam / Not Spam" labels. ScamShield AI answers:
- *Is this suspicious?*
- *Why is it suspicious?*
- *What type of scam is this?*
- *What specific steps should I take next?*

---

## 3. Key Features
- **Single Message Analysis**: Detects fraud probability, risk level, scam category, and highlights suspicious phrases.
- **Multi-Turn Conversation Analysis**: Evaluates risk escalation across sequential chat turns.
- **Explainable AI (XAI)**: Visualizes threat indicators, extracted URLs, OTP requests, and rule highlights.
- **Grounded Generative AI Assistant**: Google Gemini API integration grounded on structured safety engine findings to prevent hallucinations, with offline fallback.
- **Incident Response Guidance**: Immediate emergency protocols if the user clicked a link or shared an OTP.
- **Cybersecurity Dashboard**: Interactive Chart.js trend charts, category distributions, KPI metrics, and audit history.
- **Multilingual Support**: Supports English, Tanglish (Tamil-English code-mixed), and Tamil.

---

## 4. Architecture
```text
User Input (Message / Conversation)
            ↓
  Language Detection Engine
            ↓
   NLP Preprocessing & Feature Extraction
      ↙                       ↘
  ML Classifiers           Rule Engine
 (Binary & Multi-class)    (Security Indicators)
      ↘                       ↙
        Risk Scoring Engine (0-100)
            ↓
     Explainable AI Highlights
            ↓
  Grounded Generative AI Assistant (Gemini API)
            ↓
   Actionable Safety Guidance & Incident Response
            ↓
    SQLite Database & Web Interface
```

---

## 5. Dataset & Benchmark Results
- **Dataset Size**: 22,000 raw synthetic records (10,452 clean deduplicated records across 20 scam categories).
- **Classifiers Evaluated**: Logistic Regression, Multinomial Naive Bayes, Linear SVM, Random Forest, Gradient Boosting, HistGradientBoosting, XGBoost.
- **Best Binary Model**: Logistic Regression (F1-Score: **1.0000**, Accuracy: **1.0000**, ROC-AUC: **1.0000**).
- **False Positive Rate (FPR)**: **0.0000**
- **False Negative Rate (FNR)**: **0.0000**
- **Challenge Benchmark Accuracy**: **1.0000** (14 adversarial test cases).

---

## 6. Project Directory Structure
```text
ScamShield_AI/
│
├── app/
│   ├── main.py                  # FastAPI Entrypoint & Web App Mounting
│   ├── api/                     # REST API Routers (Auth, Analyzer, Assistant, Dashboard, History, Feedback)
│   ├── core/                    # Config, Security (JWT/PBKDF2), Logging
│   ├── database/                # SQLAlchemy Models, Session, Pydantic Schemas
│   └── services/                # Master Analyzer, Risk Engine, XAI, Assistant Service
│
├── src/
│   ├── data/                    # Dataset Generator, Cleaner, Validator
│   ├── nlp/                     # Preprocessing, Entity Regex Tokenizers, Language Detection
│   ├── features/                # Custom NLP & Social Engineering Feature Extractors
│   ├── models/                  # ML Training, Evaluation, Prediction Engine
│   ├── rules/                   # Deterministic Cybersecurity Rule Engine
│   ├── conversation/            # Multi-Turn Conversation Thread Analyzer
│   └── safety/                  # Recommendation Engine & Emergency Incident Guidance
│
├── data/
│   ├── raw/                     # Raw Generated Datasets (scamshield_raw.csv/.json)
│   ├── cleaned/                 # Cleaned Datasets (scamshield_clean.csv/.json)
│   ├── processed/               # Train, Validation, Test, Challenge Splits
│   └── metadata/                # Data Dictionary & Statistics
│
├── models/                      # Joblib Artifacts (scam_classifier, category_classifier, tfidf_vectorizer)
├── notebooks/                   # Jupyter Notebooks (01 to 06)
├── reports/                     # Model Comparison CSV, Figures, Evaluation Report, Data Card, Model Card, Project Report
├── scripts/                     # Generator, Cleaner, Trainer, Evaluator, Seeder Scripts
├── tests/                       # Pytest Suite (19 Passing Unit Tests)
├── frontend/                    # Modern Cybersecurity SaaS Web Interface (HTML, CSS, JS)
├── .env.example
├── Dockerfile
├── docker-compose.yml
└── requirements.txt
```

---

## 7. Installation & Running Instructions

### Prerequisites
- Python 3.11+ installed.

### Setup & Run (Windows PowerShell)

1. **Environment & Dependencies**:
   ```powershell
   python -m pip install -r requirements.txt
   python -m pip install -r requirements-dev.txt
   ```

2. **Generate Dataset & Train Models**:
   ```powershell
   python scripts/generate_dataset.py
   python scripts/clean_dataset.py
   python scripts/train.py
   python scripts/evaluate.py
   python scripts/seed_database.py
   ```

3. **Launch Web Application & Backend**:
   ```powershell
   $env:PYTHONPATH="."
   python -m uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
   ```

4. **Access Applications**:
   - **Frontend SaaS Application**: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
   - **Swagger API Documentation**: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
   - **Health Endpoint**: [http://127.0.0.1:8000/health](http://127.0.0.1:8000/health)

---

## 8. Automated Testing
Run the complete Pytest suite (19 unit tests):
```powershell
$env:PYTHONPATH="."
pytest -v
```

---

## 9. Docker Deployment
```bash
docker-compose up --build
```

---

## 10. Privacy & Disclaimer
*ScamShield AI provides automated risk assessment and safety guidance based on pattern detection. It does not guarantee that a message is fraudulent or legitimate.*
