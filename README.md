# Movie-Recommender-System Final Output:
![Screenshot 2024-07-01 172856](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/884efd8d-1748-49f1-9940-f6704bbde845)

# Project Overview:
This project involves creating a movie recommendation system using Python for data processing and machine learning, and deploying the application using Streamlit. The project is divided into two main parts:
1. Data Processing and Model Building
2. Application Deployment using Streamlit
# 1. Data Processing and Model Building
### 1.1 Data Loading:
The datasets used are tmdb_5000_movies.csv and tmdb_5000_credits.csv. These datasets are loaded using pandas.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/623126b2-eae7-4e70-8c47-d2b6297300d9)
### 1.2 Data Merging
The two datasets are merged on the title column to combine movie details with their respective credits.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/cdcd1e15-5e57-4cf2-818b-f8604e439e29)
### 1.3 Data Cleaning and Preprocessing
- Columns Selection: Only relevant columns are selected for further processing.
- Handling Missing Values: Missing values are dropped.
- Removing Duplicates: Duplicate entries are removed.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/7b1bf860-376a-4db1-8a1e-d63694fa4341)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/78dc3135-bf85-4213-b4e7-cd00d8b3d6d4)
### 1.4 Feature Engineering
- Text Processing: The overview, genres, keywords, cast, and crew columns are processed to create a unified tags column.
- Tokenization and Stemming: Text data is tokenized and stemmed using NLTK's PorterStemmer.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/183876a2-e74a-4e12-a342-453b5eb180c2)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/65ba7709-f555-4cef-8ead-1336e82c952b)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/fb580255-1da3-48cc-9f2a-4636adebc6f5)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/74223b3a-2257-4f40-9f4e-6f93a2a427f4)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/e60f31a0-b795-4d1e-877b-9574d9eab361)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/bfe1f0b6-27d1-4505-8c50-9ae8e32988cc)
movies['genres'] = movies['genres'].apply(convert)
movies['keywords'] = movies['keywords'].apply(convert)
movies['cast'] = movies['cast'].apply(convert3)
movies['crew'] = movies['crew'].apply(fetch_director)

movies['overview'] = movies['overview'].apply(lambda x: x.split())
movies['genres'] = movies['genres'].apply(lambda x: [i.replace(" ", "") for i in x])
movies['keywords'] = movies['keywords'].apply(lambda x: [i.replace(" ", "") for i in x])
movies['cast'] = movies['cast'].apply(lambda x: [i.replace(" ", "") for i in x])
movies['crew'] = movies['crew'].apply(lambda x: [i.replace(" ", "") for i in x])

movies['tags'] = movies['overview'] + movies['genres'] + movies['keywords'] + movies['cast'] + movies['crew']
new_df = movies[['movie_id', 'title', 'tags']]
new_df['tags'] = new_df['tags'].apply(lambda x: " ".join(x))
new_df['tags'] = new_df['tags'].apply(lambda x: x.lower())
new_df['tags'] = new_df['tags'].apply(stem)

### 1.5 Vectorization and Similarity Calculation
- CountVectorizer: The tags column is vectorized using CountVectorizer.
- Cosine Similarity: Cosine similarity is calculated to find similar movies.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/a7476d4a-906d-4bac-a8c4-342bd7ce0469)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/58de8615-efb5-4cb4-8ec3-4de68b67a1e3)

### 1.6 Model Saving
The processed data and similarity matrix are saved using pickle.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/a35f389c-52bf-4356-b63c-9e60d3a440cf)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/44fa1f37-9de7-42d9-9119-46902a959598)
# 2. Application Deployment using Streamlit
### 2.1 Streamlit Setup
- Streamlit is used to create a web application for the movie recommendation system.
### 2.2 Loading the Model
- The saved model and similarity matrix are loaded.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/2d814f95-9e85-4873-9a78-0c9058459292)

### 2.3 Recommendation Function
- A function to recommend movies based on the cosine similarity.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/8202a2b2-b512-419e-8686-e20f8724153f)
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/f3bdd827-b2cd-47ad-b3c6-2d673daf45e1)

### 2.4 Streamlit Interface
- The Streamlit interface to input a movie and display recommendations.
![image](https://github.com/sivasankarseelam/Movie-Recommender-System/assets/133698242/e7981b3c-d3ea-4e14-95e0-dae861af03a4)


















