# Recommendation System: IBM Community

This project builds a recommendation system using real user-article interaction data from the IBM Watson Studio platform. The goal is to recommend articles to users based on article popularity, similar users, article content, and matrix factorization.

The project is part of the Udacity Data Science Nanodegree and demonstrates several recommendation techniques, including rank-based recommendations, user-user collaborative filtering, content-based recommendations, and SVD-based article similarity.

## Project Overview

The dataset contains interactions between users and articles on the IBM Watson Studio platform. Since the dataset does not include explicit ratings, each interaction is treated as evidence that a user engaged with an article.

The project is divided into the following sections:

1. Exploratory Data Analysis
2. Rank-Based Recommendations
3. User-User Based Collaborative Filtering
4. Content-Based Recommendations
5. Matrix Factorization using SVD
6. Conclusions and Recommendations

## Files in This Repository

```text
.
├── Recommendations_with_IBM.ipynb
├── Recommendations_with_IBM.html
├── project_tests.py
├── data/
│   └── user-item-interactions.csv
└── README.md
```

## Getting Started

To run this project locally, clone the repository and install the required Python libraries.

```bash
git clone https://github.com/LayanAlrashoud/Udacity-DataScience4.git
cd Udacity-DataScience4
```

If the notebook is inside a `starter` folder, move into that folder:

```bash
cd starter
```

## Dependencies

This project uses Python and the following libraries:

```text
pandas
numpy
matplotlib
scikit-learn
jupyter
nbconvert
```

## Installation

Create and activate a virtual environment:

```bash
python -m venv env
```

On Windows CMD:

```bash
env\Scripts\activate
```

On Windows PowerShell:

```bash
.\env\Scripts\Activate.ps1
```

Install the required packages:

```bash
pip install pandas numpy matplotlib scikit-learn jupyter nbconvert
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Recommendations_with_IBM.ipynb
```

## Project Instructions

### Part I: Exploratory Data Analysis

In this section, the dataset is explored to understand:

- The number of users
- The number of articles
- The number of user-article interactions
- The distribution of user interactions
- The most viewed article
- Missing values in the user identifier column

### Part II: Rank-Based Recommendations

Since the dataset does not contain article ratings, article popularity is measured by the number of interactions. The most popular articles are recommended to users, especially new users who do not have any previous interaction history.

### Part III: User-User Based Collaborative Filtering

A user-item matrix is created where:

- Rows represent users
- Columns represent articles
- A value of 1 means the user interacted with the article
- A value of 0 means the user did not interact with the article

Similar users are found using the dot product between user vectors. Recommendations are generated from articles read by similar users but not yet read by the target user.

An improved version ranks similar users by:

1. Similarity score
2. Number of total interactions

Articles are also ranked by popularity before being recommended.

### Part IV: Content-Based Recommendations

A content-based recommendation system is created using article titles. Since the article title is the only available text content, TF-IDF is used to convert titles into numerical features.

The steps include:

1. Extracting unique article titles
2. Applying TF-IDF vectorization
3. Reducing dimensionality using TruncatedSVD
4. Clustering article titles using KMeans
5. Recommending articles from the same title cluster
6. Ranking similar articles by popularity

This method is useful when recommending articles similar to a specific article.

### Part V: Matrix Factorization

TruncatedSVD is applied to the user-item matrix to learn latent relationships between users and articles.

Using 200 latent features, the project finds articles that are similar to a selected article based on their latent feature representations. Cosine similarity is used to identify the most similar article vectors.

## Testing

The notebook includes tests from the provided `project_tests.py` file. These tests validate:

- Data exploration results
- Rank-based recommendation functions
- User-item matrix creation
- User-user collaborative filtering functions
- Content-based recommendation functions

To run the tests, execute the notebook cells in order.

## Results

The project successfully implements multiple recommendation methods:

| Method | Best Used For | Limitation |
|---|---|---|
| Rank-Based Recommendations | New users with no history | Not personalized |
| User-User Collaborative Filtering | Users with interaction history | Does not work well for new users |
| Content-Based Recommendations | Similar article recommendations | Limited by short article titles |
| SVD / Matrix Factorization | Users or articles with enough interaction data | Less interpretable |

## Recommendation Strategy

For new users with no interaction history, rank-based recommendations are the best starting point because they recommend the most popular articles.

For users with a small amount of history, content-based recommendations can help suggest articles related to what they have already viewed.

For users with a lot of history, collaborative filtering and SVD-based recommendations are more useful because they can learn personalized patterns from user behavior.

## Future Improvements

Possible improvements include:

- Using full article text instead of only article titles
- Adding article tags, categories, descriptions, or keywords
- Building a hybrid recommender system
- Testing recommendations using A/B testing
- Tracking online metrics such as click-through rate, reading time, and return visits
- Building a Flask or Streamlit app to serve recommendations

## Built With

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## Author

Layan Alrashoud

## License

This project is for educational purposes as part of the Udacity Data Science Nanodegree.

