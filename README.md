# Sentiment-Based Movie Recommendation System

A content-based movie recommendation engine that combines **cosine similarity** with **NLP sentiment analysis** to deliver personalized recommendations. Built using the TMDB dataset and deployed as an interactive web app via Streamlit.

> Associated research paper: *"Enhancing User Experience Through Sentiment-Based Recommendation"*
> Published — Reva University, School of Computer Science and IT

---

## Live Demo

```bash
streamlit run app.py
```

---

## Project Overview

| Attribute | Detail |
|-----------|--------|
| Type | Machine Learning + NLP |
| Domain | Recommendation Systems |
| Dataset | TMDB 5000 Movies Dataset |
| Stack | Python, Scikit-learn, Pandas, Streamlit, TMDB API |
| Status | Complete |
| Research | Published paper — Reva University (2024) |

---

## Problem Statement

Traditional movie recommendation systems rely purely on ratings or watch history, ignoring how users *feel* about movies. A user who rates a film 4/5 despite disliking its ending has a fundamentally different preference signal than one who loved every minute. This project integrates sentiment analysis into the recommendation pipeline to capture that nuance.

---

## Approach

### 1. Content-Based Filtering
- Extracted features: genre, cast, keywords, crew, movie overview
- Applied text vectorization to build movie feature vectors
- Computed **cosine similarity** between all movie pairs
- Recommended top-5 most similar movies for any given title

### 2. Sentiment Analysis
- Scraped user reviews from IMDB for selected movies
- Classified review sentiment using **Naive Bayes** (primary) and **SVM** (comparison)
- Sentiment scores were used to weight and re-rank recommendations

### 3. Architecture

```
User Input (Movie Title)
        │
        ▼
  Flask/Streamlit App
        │
   ┌────┴────┐
   │         │
   ▼         ▼
Cosine     IMDB Review
Similarity  Scraper
(TMDB data) │
   │         ▼
   │    Naive Bayes
   │    Sentiment Model
   │         │
   └────┬────┘
        ▼
  Ranked Recommendations
  + Sentiment Labels
        │
        ▼
   TMDB API (posters)
        │
        ▼
  Final UI Output
```

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Data processing | Python, Pandas, NumPy |
| Feature extraction | Scikit-learn (CountVectorizer) |
| Similarity computation | Cosine Similarity (sklearn) |
| Sentiment classification | Naive Bayes, SVM (sklearn) |
| Web scraping (reviews) | BeautifulSoup, Requests |
| Frontend | Streamlit |
| Movie metadata + posters | TMDB API |
| Model serialization | Pickle |

---

## Dataset

- **TMDB 5000 Movies Dataset** — 5,000 movies with metadata (genres, cast, crew, keywords, overview)
- Source: [Kaggle — TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
- IMDB reviews scraped dynamically at runtime for sentiment classification

---

## How to Run

### Prerequisites
```bash
pip install streamlit pandas numpy scikit-learn requests pickle5
```

### Steps
```bash
# 1. Clone the repository
git clone https://github.com/Athish24/sentiment-movie-recommender
cd sentiment-movie-recommender

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the Jupyter notebook to generate model files
jupyter notebook notebook86c26b4f17.ipynb
# This generates: model/movie_list.pkl and model/similarity.pkl

# 4. Launch the Streamlit app
streamlit run app.py
```

### Note on API Key
The app uses the TMDB API to fetch movie posters. The key in `app.py` is a public demo key — if it stops working, get a free key at [themoviedb.org](https://www.themoviedb.org/settings/api) and replace it in `app.py`:
```python
url = "https://api.themoviedb.org/3/movie/{}?api_key=YOUR_KEY&language=en-US"
```

---

## File Structure

```
sentiment-movie-recommender/
├── app.py                          → Streamlit web application
├── notebook86c26b4f17.ipynb        → Data preprocessing + model building notebook
├── model/
│   ├── movie_list.pkl              → Serialized movie dataframe (generated)
│   └── similarity.pkl              → Precomputed cosine similarity matrix (generated)
├── requirements.txt
└── README.md
```

---

## Key Results

- Recommendation engine returns top-5 semantically similar movies with poster images
- Cosine similarity on combined feature vectors (genre + cast + keywords + overview) outperforms genre-only filtering
- Naive Bayes classifier achieves reliable sentiment classification on IMDB review text
- System successfully differentiates between similarly-rated movies with opposite sentiment profiles

---

## Research Paper

**Title:** Enhancing User Experience Through Sentiment-Based Recommendation

**Authors:** Dr. Yashavnth TR, Dr. Lithin Kumble, Dr. Mallikarjun Kodabagi, Ms. Indhuja, Athish Sabarish JS

**Institution:** Reva University, School of Computer Science and IT, Bengaluru

**Key contributions:**
- Proposed integration of aspect-based sentiment analysis with cosine similarity for personalized movie recommendations
- Benchmarked SVM vs Naive Bayes for sentiment classification on movie review data
- Demonstrated that sentiment-weighted recommendations improve relevance over content-only approaches

---

## Limitations & Future Work

- Real-time IMDB scraping adds latency — pre-computed sentiment scores would improve performance
- Popular movies dominate recommendations due to data imbalance
- Future: integrate aspect-based sentiment analysis for scene/character-level preference modeling
- Future: hybrid approach combining collaborative + content-based + sentiment filtering

---

## Author

**Athish Sabarish JS**
B.Tech CSE — Reva University, Bengaluru
[LinkedIn](https://linkedin.com/in/athish-sabarishjs) | [GitHub](https://github.com/Athish24)
"# Enhancing-User-Experience-Through-Sentiment-based-Recommendation-System" 
