
# 🎬 Movie Recommendation System

A machine learning-powered **movie recommendation system** that combines content-based filtering, collaborative filtering, and a hybrid approach to deliver personalized movie suggestions based on user preferences.

---

## ✨ Features

- 🎯 **Content-Based Filtering** — recommends movies similar to the input based on genres, keywords, cast, crew, and overview
- 👥 **Collaborative Filtering** — uses ALS (Alternating Least Squares) to identify preference trends across movies
- 🔀 **Hybrid Model** — merges both approaches with tuned weights for balanced, diverse recommendations
- 🧹 **Robust Preprocessing** — handles nested JSON fields, stemming, stop word removal, and deduplication

---

## 🧠 Methodology

### 1. Data Preprocessing
- Merged TMDB Movies and Credits datasets on movie title
- Extracted genres, keywords, top 4 cast members, and director from nested dictionaries
- Applied stemming and created a unified `tags` column from all features

### 2. Content-Based Filtering
- Vectorized `tags` using `CountVectorizer` (top 5000 features, no stop words)
- Computed **cosine similarity** between all movie vectors
- Recommended movies ranked by similarity score

### 3. Collaborative Filtering
- Computed a **weighted score** per movie using vote average, vote count, and popularity
- Built a sparse user-item matrix with `scipy.sparse.csr_matrix`
- Applied **ALS (Alternating Least Squares)** via the `implicit` library for preference prediction

### 4. Hybrid Model
- Combined content-based and collaborative results with adjustable weights
- Filtered final recommendations by genre alignment with the input movie

---

## 📊 Results

| Approach | Input | Top Recommendations |
|----------|-------|-------------------|
| Content-Based | Avatar | Avatar: The Last Airbender, Guardians of the Galaxy, Interstellar, Gravity, The Martian |
| Collaborative | Batman | The Dark Knight, Batman Begins, Inception, Joker, The Prestige |
| Hybrid | Avatar | Avatar: The Last Airbender, Guardians of the Galaxy, Interstellar, Batman Begins, Joker |

---

## 🗂️ Dataset

**TMDB 5000 Movies & Credits** (via Kaggle)

| Dataset | Contents |
|---------|----------|
| `tmdb_5000_movies.csv` | Title, genres, keywords, popularity, ratings |
| `tmdb_5000_credits.csv` | Cast and crew details |

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| **Language** | Python 3 |
| **Data Processing** | Pandas, NumPy |
| **NLP** | NLTK (stemming), Scikit-learn (CountVectorizer, cosine similarity) |
| **Collaborative Filtering** | SciPy (sparse matrix), implicit (ALS) |
| **Visualization** | Matplotlib, Seaborn |

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/FatimaShakil/movie-recommender.git
cd movie-recommender
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Download from [Kaggle — TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) and place both CSV files in the `data/` folder.

### 4. Run the notebook
```bash
jupyter notebook MRSNotebook.ipynb
```

Or run as a script:
```bash
python MovieRecommenderSystem.py
```

---

## 📁 Project Structure

```
movie-recommender/
├── EDA.ipynb                                  # Exploratory data analysis
├── MRSNotebook.ipynb                          # Main recommendation system notebook
├── MRS.py                                     # Recommendation system script
├── MovieRecommenderSystem.py                  # Full pipeline script
├── Project Report - Movie Recommender System.docx
├── requirements.txt
└── README.md
```

---

## 🔮 Future Enhancements

- Incorporate user reviews and ratings for refined recommendations
- Expand dataset to include multilingual movies
- Real-time user interaction tracking for dynamic collaborative filtering
- Deploy as a web app with Streamlit or FastAPI

---

## 📄 License

This project is for academic purposes.
