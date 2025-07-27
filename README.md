# Movie Recommender System

A content-based movie recommendation system implemented in Python using Jupyter Notebook. This project processes and analyzes movie metadata to suggest similar movies based on textual features such as genres, keywords, cast, crew, and overview.

## Project Overview

This project builds a movie recommendation system using content-based filtering. By leveraging metadata about movies, such as genres, plot keywords, cast, and crew, the system can recommend movies similar to a user-selected title.

## Features

- Loads and merges movie metadata from multiple datasets (`tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`).
- Cleans and preprocesses data to extract relevant information.
- Constructs textual "tags" for each movie combining overview, genres, keywords, cast, and crew.
- Vectorizes tags using `CountVectorizer` (Bag-of-Words model).
- Computes cosine similarity between movie vectors.
- Recommends the top similar movies for any given title.

## Data Sources

- **tmdb_5000_movies.csv**: Contains metadata about movies (title, overview, genres, keywords, etc.)
- **tmdb_5000_credits.csv**: Contains credits data (cast and crew) for each movie.

Both datasets should be available in the project directory.

## How It Works

1. **Data Loading and Merging**:
   - Read both the movies and credits datasets using pandas.
   - Merge datasets on the `title` column to unify movie metadata and credits.

2. **Feature Engineering**:
   - Select important columns: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, `crew`.
   - Parse and extract genre, keyword, cast, and director information using Python's `ast` module and list comprehensions.
   - Clean the text data and remove spaces for uniformity.

3. **Tag Generation**:
   - Combine the overview, genres, keywords, cast, and crew into a single string called "tags" for each movie.

4. **Vectorization**:
   - Use `CountVectorizer` from scikit-learn to transform the "tags" into a numerical feature matrix (`max_features=5000`, removing English stop words).

5. **Similarity Calculation**:
   - Calculate cosine similarity between all movie vectors to measure content similarity.

6. **Recommendation Function**:
   - Define a function `recommend(title)` that returns the top similar movies for a given movie title.

7. **Persistence**:
   - Save the processed data and similarity matrix using `pickle` for future use.

## Setup and Installation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/ritik-gupta001/Movie-recommend-system.git
   cd Movie-recommend-system
   ```

2. **Install dependencies:**
   Make sure you have Python 3.11+ and pip installed.
   ```bash
   pip install numpy pandas scikit-learn
   ```

3. **Download datasets:**
   Place `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` in the project root directory.

4. **Open the notebook:**
   Launch Jupyter Notebook.
   ```bash
   jupyter notebook Movie-recommendar-system.ipynb
   ```

## Usage

- Run all cells in `Movie-recommendar-system.ipynb` to process the data and build the recommender.
- To get recommendations for a movie:
  ```python
  recommend('Avatar')
  ```
  Example output:
  ```
  ['Titan A.E.', 'Small Soldiers', "Ender's Game", 'Aliens vs Predator: Requiem', 'Independence Day']
  ```

- The system will output the top 5 movies similar to the provided title.

## Requirements

- Python 3.11+
- pandas
- numpy
- scikit-learn
- Jupyter Notebook

## Results and Outputs

- The processed data and similarity matrix are saved as `movie_list.pkl` and `similarity.pkl` for efficient loading in future sessions.
- You can modify the `recommend` function to return more or fewer recommendations as needed.

## Contributing

Contributions, suggestions, and improvements are welcome! Please open an issue or submit a pull request.

## License

No license specified. Please contact the repository owner for usage permissions.

---

**Author**: [ritik-gupta001](https://github.com/ritik-gupta001)

