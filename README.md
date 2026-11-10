# Sentiment Analysis of Customer Reviews

A web application that analyzes customer reviews and classifies them as **positive**, **negative** or **neutral**. Users upload a CSV of reviews and explore the results on an interactive dashboard with charts, a review table and a one-click download of the analyzed data.

Developed by **Team Nexus** as part of the **IBM ICE** project (delivered with Phemesoft) at **Yenepoya (Deemed to be University)**, Bachelor of Computer Application, Big Data Analytics, 2024.

---

## Features

- **User authentication**: registration and login with Flask-Login, passwords hashed with bcrypt
- **CSV upload**: file validation and error handling with flash notifications
- **Text preprocessing**: tokenization, stop-word removal and lemmatization using spaCy
- **Sentiment analysis**: polarity scoring with TextBlob, plus classification with scikit-learn models
- **Model comparison**: Random Forest, SVM (Support Vector Machine) and Naïve Bayes
- **Interactive dashboard**:
  - Review counters (total, positive, negative, neutral)
  - Bar chart: sentiment overview
  - Pie chart: sentiment proportion
  - Line chart: sentiment trend
  - Review table with sentiment and detected emotion
  - Download button for the full analyzed dataset
- **Performance**: trained models serialized with pickle to reduce latency

## Tech Stack

| Area | Tools |
|---|---|
| Languages | Python, JavaScript |
| Backend | Flask, SQLAlchemy, WTForms, Flask-Login |
| NLP / ML | spaCy, TextBlob, scikit-learn, Pandas, NumPy |
| Visualization | Matplotlib, Seaborn, Power BI |
| Database | PostgreSQL / MySQL |
| Security | bcrypt, CSRF protection, Bandit |
| Version control | Git, GitHub |

## How It Works

```
CSV upload -> Preprocessing -> Feature extraction -> Sentiment classification -> Dashboard
              (spaCy)          (keywords, polarity)  (TextBlob + ML models)      (charts, table, download)
```

1. **Data collection**: reviews are uploaded as a CSV file (e.g. a Kaggle review dataset).
2. **Preprocessing**: remove irrelevant text, handle missing values, tokenize, remove stop words, lemmatize.
3. **Feature extraction**: convert text into features the models can learn from.
4. **Classification**: label each review as positive, negative or neutral.
5. **Training and testing**: train on one portion of the data and evaluate on another.
6. **Output**: display sentiment distribution and trends, with downloadable results.

## Getting Started

### Prerequisites

- Python 3.9 or later
- pip
- PostgreSQL or MySQL (or another database supported by SQLAlchemy)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Download the spaCy language model
python -m spacy download en_core_web_sm
```

### Configuration

Create a `.env` file in the project root. Never commit this file.

```env
SECRET_KEY=your-secure-random-value
DATABASE_URL=your-database-connection-string
FLASK_DEBUG=0
```

> The secret key and debug mode are read from environment variables. This addresses the Bandit findings for a hardcoded secret key (B105) and Flask debug mode (B201).

### Run the app

```bash
python app.py
```

Then open `http://127.0.0.1:5000` in your browser. If your entry file has a different name, use that instead of `app.py`.

## Usage

1. Register an account and log in.
2. Choose a CSV file containing customer reviews and upload it.
3. View the sentiment counters and charts on the dashboard.
4. Browse individual reviews with their sentiment and emotion.
5. Download the analyzed dataset.

## Testing

The project was tested across these areas:

- Unit tests for data preprocessing
- Integration tests for API endpoints
- Data entry and file-upload validation
- Security testing (SQL injection, XSS, CSRF)
- Performance, stress and volume testing with large datasets
- Recovery and system integration testing
- User acceptance testing with a feedback survey

## Security

- Passwords hashed with **bcrypt**
- **CSRF protection** enabled
- Static analysis with **Bandit**; all findings addressed:

| ID | Issue | Severity | Fix |
|---|---|---|---|
| B105 | Hardcoded password string | Low | Secret key moved to environment variables |
| B201 | Flask debug mode enabled | High | `debug=False` in production, controlled via environment configuration |
| B101 | Use of `assert` | Low | Replaced with explicit error handling |

## Future Improvements

- Deep learning models for better classification
- Support for reviews from multiple platforms and social media
- Real-time sentiment tracking



**Guided by:** Sumit Kumar Shukla

## Acknowledgements

- IBM Innovation Center for Education and Phemesoft
- Yenepoya (Deemed to be University)
- [Kaggle](https://www.kaggle.com) for datasets
- [scikit-learn](https://scikit-learn.org), [Flask](https://flask.palletsprojects.com), [spaCy](https://spacy.io) and [TextBlob](https://textblob.readthedocs.io) documentation

## License

Add a license of your choice (for example, MIT) before publishing.
