# 🏥 Disease Prediction System using Machine Learning

> Predict diseases from symptoms using a trained Random Forest model, served via a Flask web application.

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![Flask](https://img.shields.io/badge/Flask-2.x-black?style=flat-square&logo=flask)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?style=flat-square&logo=scikit-learn)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

**[🔗 Live Demo](https://your-app.onrender.com)** · **[📁 Repository](https://github.com/n-a-n-d-a-n/disease-prediction-system)**

---

## 📌 Overview

This system takes symptom inputs from a user and predicts the most likely disease using a machine learning model trained on a labeled symptom-disease dataset. It features a full-stack Flask web application with interactive HTML pages, a REST API for predictions, and an email notification system for user contact.

---

## ✨ Features

- **Symptom-based disease prediction** powered by a Random Forest classifier
- **Interactive web UI** with multiple pages (Home, Dashboard, About, Contact)
- **REST API** — `/predict` and `/symptoms` endpoints for programmatic access
- **CORS-enabled** for external frontend integration
- **Email notification system** — auto-acknowledgment to users + admin alerts on contact form submission
- **Multiple ML models benchmarked** — Random Forest, Decision Tree, SVM, Logistic Regression, XGBoost

---

## 🗂️ Project Structure

```
disease-prediction-system/
├── base_app.py               # Main Flask application entry point
├── endpoint.py               # API route definitions
├── predict_logic.py          # Core prediction logic
├── streamlit_app.py          # Standalone Streamlit version
├── requirements.txt          # Python dependencies
│
├── templates/                # Jinja2 HTML templates
│   ├── index.html
│   ├── dashboard.html
│   └── about.html
│
├── static/                   # CSS, JS, images
├── disease_prediction/       # Model training scripts & saved models
├── outputs/                  # Model output files
│
├── Training.csv              # Training dataset
├── Testing.csv               # Testing dataset
├── dataset.csv               # Raw dataset
├── Symptom-severity.csv      # Symptom severity scores
├── symptom_Description.csv   # Symptom descriptions
├── symptom_precaution.csv    # Recommended precautions per disease
│
├── main.ipynb                # Exploratory notebook & model training
└── models_comparison.md      # Benchmarking results across all models
```

---

## 🤖 Model

**Final model: Random Forest Classifier**

Selected over other models for the following reasons:

- **Robustness** — averages multiple decision trees, reducing overfitting
- **Feature Importance** — reveals which symptoms drive each prediction
- **Generalization** — reliable on unseen data, critical for healthcare use cases
- **Scalability** — handles large datasets with mixed feature types efficiently

### Benchmark Results

All models were evaluated on the symptom-disease dataset:

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Random Forest | 1.0 | 1.0 | 1.0 | 1.0 | 1.0 |
| Decision Tree | 1.0 | 1.0 | 1.0 | 1.0 | 1.0 |
| Logistic Regression | 1.0 | 1.0 | 1.0 | 1.0 | 1.0 |
| SVM | 1.0 | 1.0 | 1.0 | 1.0 | 1.0 |
| XGBoost | 1.0 | 1.0 | 1.0 | 1.0 | 1.0 |

> Perfect scores reflect a well-structured, clean symptom-disease dataset. Random Forest was chosen for its interpretability and robustness in production scenarios.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python, Flask |
| ML | scikit-learn, XGBoost, LightGBM |
| Data | pandas, numpy, scipy |
| Visualization | matplotlib, seaborn, plotly |
| Model Persistence | joblib, pickle |
| Frontend | HTML5, CSS3, JavaScript |
| Email | Gmail SMTP (App Password) |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- pip

### Installation

```bash
git clone https://github.com/n-a-n-d-a-n/disease-prediction-system.git
cd disease-prediction-system
pip install -r requirements.txt
```

### Running Locally

```bash
python base_app.py
```

Open `http://localhost:5000` in your browser.

### Email Configuration (optional)

To enable the contact form email feature, set these as environment variables:

```bash
SENDER_EMAIL=your_email@gmail.com
SENDER_PASSWORD=your_gmail_app_password
```

> Use a [Gmail App Password](https://support.google.com/accounts/answer/185833), not your actual Gmail password. Never hardcode credentials in source code.

---

## 🌐 API Reference

### `GET /symptoms`
Returns the list of all available symptoms.

```json
{
  "symptoms": ["itching", "skin_rash", "nodal_skin_eruptions", ...]
}
```

### `POST /predict`
Predicts a disease based on provided symptoms.

**Request body:**
```json
{
  "symptoms": ["fever", "cough", "fatigue"]
}
```

**Response:**
```json
{
  "disease": "Common Cold",
  "confidence": 0.94
}
```

---

## 📦 Deployment

This app is deployed on **Render** (free tier).

To deploy your own instance:

1. Push the repo to GitHub
2. Go to [render.com](https://render.com) → New → Web Service
3. Connect your repo
4. Set:
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `gunicorn base_app:app`
5. Add `SENDER_EMAIL` and `SENDER_PASSWORD` under Environment Variables
6. Deploy

---

## 📄 License

MIT License — feel free to use, modify, and distribute.
