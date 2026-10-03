# 🎬 TMDB Movie Recommendation System

> **Why did the system recommend that movie?**

You watch one movie.  
A few moments later, another one appears.

But what makes that recommendation relevant?

This project explores that question by building a **Content-Based Movie Recommendation System** using the **TMDB 5000 dataset**.

The goal is not only to generate recommendations, but to understand **what makes two movies similar** and how that similarity can be used to recommend movies.

---

##  Project Overview

Recommendation systems are widely used by platforms such as Netflix, YouTube, Spotify, and e-commerce applications to help users discover relevant content.

Two fundamental approaches are:

###  Content-Based Filtering

Recommends items based on their characteristics.

> **"You liked this movie → here are movies with similar characteristics."**

###  Collaborative Filtering

Recommends items based on user behaviour and preferences.

> **"People with preferences similar to yours → also liked these movies."**

For this project, I focus on **Content-Based Recommendation**.

---

##  Objective

The main objective of this project is to understand:

**What makes two movies similar?**

The system analyzes movie information, processes textual descriptions using NLP, converts them into numerical representations using **TF-IDF**, calculates similarity, and generates movie recommendations.

---

##  Recommendation Pipeline

```text
TMDB Movie Data
       ↓
Data Preprocessing
       ↓
Movie Feature Analysis
       ↓
Rating & Popularity Analysis
       ↓
Feature Scaling
       ↓
Hybrid Movie Scoring
       ↓
NLP — Movie Overview
       ↓
TF-IDF Vectorization
       ↓
Similarity Calculation
       ↓
Top Similar Movies
````

---

##  How the System Works

### 1. Data Collection

The project uses the **TMDB 5000 Movie Dataset**, consisting of:

* `tmdb_5000_movies.csv`
* `tmdb_5000_credits.csv`

The datasets are merged using the movie `id`.

The final dataset contains approximately **4,800 movies** after preprocessing.

---

### 2. Data Preprocessing

The movie data is explored and cleaned to prepare it for analysis and recommendation.

This includes examining:

* Movie titles
* Movie overviews
* Ratings
* Vote counts
* Popularity
* Other movie-related attributes

Unnecessary columns are removed during preprocessing.

---

### 3. Weighted Rating

A weighted rating is calculated using:

* Vote average
* Vote count
* Overall average rating

This helps avoid relying only on the average rating of movies with very few votes.

The idea is to balance a movie's rating with the amount of voting information available.

---

### 4. Popularity Analysis

Movie popularity is analyzed separately to understand which movies receive higher popularity scores within the dataset.

This provides another signal that can contribute to movie ranking.

---

### 5. Feature Scaling

The rating-based score and popularity score are scaled using **MinMaxScaler**.

This puts the values on a comparable scale before combining them.

---

### 6. Hybrid Movie Score

The scaled rating and popularity scores are combined to create a **hybrid movie score**.

This allows the ranking to consider both:

* Movie ratings
* Movie popularity

---

##  7. NLP & TF-IDF

The movie **overview** is one of the most important features for the content-based recommendation system.

Natural Language Processing is used to convert movie descriptions into numerical representations.

The project uses:

```python
TfidfVectorizer(
    min_df=3,
    ngram_range=(1,3),
    stop_words="english"
)
```

TF-IDF helps identify words and phrases that are important for describing a movie.

The system considers:

* Individual words
* Two-word combinations
* Three-word combinations

This creates a numerical representation of each movie's overview.

---

##  8. Similarity Calculation

After converting movie overviews into TF-IDF vectors, the system calculates similarity between movies.

A kernel-based similarity method is used to compare the movie representations.

The resulting similarity matrix allows the system to identify movies whose descriptions are similar to a selected movie.

---

##  9. Movie Recommendation

When a user selects a movie:

```text
Selected Movie
      ↓
Find Movie Index
      ↓
Retrieve Similarity Scores
      ↓
Sort Similar Movies
      ↓
Remove Selected Movie
      ↓
Return Top Recommendations
```

The system then returns the most similar movies.

---

##  Example

If a user selects:

**John Carter**

the system analyzes its movie representation and compares it with other movies in the dataset.

The movies with the highest similarity scores are then returned as recommendations.

---

##  Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Natural Language Processing**
* **TF-IDF**
* **MinMaxScaler**
* **Similarity-based Recommendation**
* **Jupyter Notebook**

---

##  Key Concepts Demonstrated

This project demonstrates practical understanding of:

* Data Cleaning
* Data Exploration
* Feature Engineering
* Statistical Rating
* Popularity Analysis
* Feature Scaling
* Natural Language Processing
* TF-IDF Vectorization
* Similarity Calculation
* Content-Based Recommendation
* Ranking and Recommendation

---

## Project Structure

```text
TMDB-Movie-Recommendation-System/
│
├── TMDB Movie Recommendation.ipynb
│
├── tmdb_5000_movies.csv
│
├── tmdb_5000_credits.csv
│
└── README.md
```

---

##  What I Learned

Through this project, I explored how a recommendation system can be built from raw movie data.

More importantly, I learned that a recommendation is not simply about producing a result.

It is about understanding the **features, representations, similarity measures, and ranking logic** that lead to that result.

The central idea of this project is:

> **Don't just ask what the system recommends. Ask why.**

---


##  About Me

 **Divya Upadhyay**





