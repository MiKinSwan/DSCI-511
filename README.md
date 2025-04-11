#  10000 Movies Dataset 🎥
## 📚 Overview
This dataset collects movie data using The Movie Database (TMDB) API, which provides access to a comprehensive range of movie-related information. The dataset contains various attributes related to movies, categorized into four main sections:**movies**, **trailers**, **posters**, and **cast and crew**.

**Movies Dataset**: Contains essential details about each film, including title, release date, genres, revenue, budget, popularity,etc .
**Trailers Dataset**: Includes all trailer releases associated with each movie, providing video and metadata.
**Posters Dataset**: Holds various images, such as backdrops, logos, and posters, related to each movie.
**Cast and Crew Dataset**: Provides detailed information about the people involved in each production, such as actors, directors, producers, and other key crew members.
These datasets serve as a rich resource for exploring patterns and trends in the movie industry, helping to uncover correlations related to movie success factors like release dates, ratings, genres, and box office performance.

## ➕ Data Integration
All datasets can be merged based on a unique movie ID to facilitate further analysis. By using the unique movie ID, you can combine information from the movies, trailers, posters, and cast and crew datasets to create a more comprehensive view of each movie.

## 📩 Data Storage
Each dataset is saved as a separate JSON file, making it easy to handle and process while maintaining the structure provided by the TMDB API. This format ensures compatibility with various data analysis tools and makes it simple to load and analyze the data as needed.

## 📊 Column Descriptions & Summary Statistics

We describe only the important columns for each dataset in the following sections.

**Common Columns for Movies Data:**

| Column Name              | Description |
|-------------------------|-------------|
| `id`              | A unique code assigned to each individual movie |
| `release date`                  | The date on which the movie was officially released. |
| `title`                 | Movie name. |
| `overview`               | A brief summary outlining the plot or content of the movie. |
| `popularity`                 | A numerical value indicating the level of popularity of the movie. |
| `vote count`    | The total number of votes received for the movie. |
| `vote average`  | The average rating given to the movie. |
| `original_language`              | The language used in that movie. |
| `genres`           | The categories or types of the movie, such as Action, Comedy, Thriller, etc. |
| `budget`              | The budget of the movie. |
| `revenue`             | The revenue of the movie. |
| `poster_path`             | The poster image . |


**Common Columns for Cast and Crew Data:**

| Column Name              | Description |
|-------------------------|-------------|
| `adult`              | Indicates if the content is rated for adults (`True` or `False`). |
| `gender`                  | The gender of the individual (0 = Unknown, 1 = Female, 2 = Male). |
| `id`                 | Unique identifier for the individual in TMDb. |
| `known_for_department`               |The department the individual is primarily known for (e.g., \"Acting\"). |
| `name`                 | The full name of the individual. |
| `original_name`    | The original name of the individual (if different from the displayed name). |
| `popularity`  | Popularity score reflecting the individual's prominence in the industry. |
| `cast_id`              | Unique identifier for the cast/crew record in a specific movie or TV show. |
| `character`           | The name of the character portrayed (for cast) or role held (for crew). |
| `credit_id`              | Unique identifier for the credit record. |
| `order`             | The order in which the individual appears in the credits. |

**Common Columns for Poster Data:**

| Column Name              | Description |
|-------------------------|-------------|
| `aspect_ratio`              | The proportion of the image width to height. |
| `height`                  | Image height |
| `iso_639_1`                 | The language code of the image (e.g. en, or null) |
| `file_path`               |The image file path to see the image(e.g. /9nhjGaFLKtddDPtPaX5EmKqsWdH.jpg) . |
| `vote_average`                 | The average vote score for this image. |
| `vote_count`    | The total number of votes received for the image. |
| `width`  | Image width. |

**Common Columns for Trailer Data:**

| Column Name              | Description |
|-------------------------|-------------|
| `iso_639_1`              | The language code of the trailer (e.g. en, or null) |
| `iso_3166_1`                  | The country code where the trailer was released(eg "US means United States") |
| `name`                 | The title or name of the trailer |
| `key`               |A unique identifier used to access the trailer on its hosting platform.  |
| `site`                 | The platform where the trailer is hosted. |
| `type`    | The type of video, such as 'Teaser', 'Trailer', 'Clip', or 'Featurette'. |
| `official`  |  A Boolean value (True or False) indicating whether the trailer is an officially released video. |

If you want to open image such as (backdrops, logos, posters), you have to use a base_url, a file_size and a file_path.
```
base_url = https://image.tmdb.org/t/p/
file_size = "w500"  # Choose a desired image size (w500, original, etc.)
file_path = "/hP7eihpJolSy4LXgyNfghYgPztG.png"
For example, https://image.tmdb.org/t/p/w500/hP7eihpJolSy4LXgyNfghYgPztG.png
```
If you want to open videos from trailer dataset, you have to combine the key ( 'TaFK_ULWBTc') and the site url(which is YouTube) to form the full URL of the video.


```
site_url= https://www.youtube.com/watch?v={key}
For example,https://www.youtube.com/watch?v=TaFK_ULWBTc
```

## 🧮 Selected Summary Statistics
The dataset consists of 10,000 movies, updated as of February 2025, including the latest movie details. After removing duplicate entries based on movie ID in main_movie.json, the final dataset contains 9,979 unique movies.

## 🧩 Limitations of the Data
The process of collecting this data encounters several challenges.

Some movies lack important details such as revenue, budget, popularity, or cast information, and there are inconsistencies in formatting (e.g popularity values like 0.059000000000000004).
Some movies appear multiple times due to different editions, re-releases, or translations. Even when fetching data from the same pagination, merging detailed information—such as trailers and posters—can result in mismatched movies.

That is why, we chose not to merge the data and instead created separate JSON files for further analysis of specific topics like trailers and posters.
The cast and crew dataset is exceptionally large, which can slow down your notebook if you attempt to load all data for a single movie. To manage this, it is necessary to break the data into smaller sections when analyzing specific details.

Furthermore, vote count and vote average were more actively used in the past, whereas newer movies receive fewer votes. This inconsistency makes it difficult to analyze real voting trends accurately.


## 💡 Example Use Cases
In our analysis, we primarily focus on the movies dataset to examine box office revenues by visualizing movie popularity, exploring the relationship between vote count and vote averages, identifying the most common genres, and determining trends in movie releases by year and month.

The trailer dataset allows for multimedia analysis, such as sentiment analysis on trailer content, comparing engagement metrics across different genres, or studying the correlation between trailer views and a movie’s financial success. Researchers can also explore the impact of trailer release timing on audience anticipation and box office performance.

The poster dataset is valuable for visual and design-related studies. Image analysis techniques can be used to examine color schemes and design elements commonly associated with different genres. Typography analysis can reveal how fonts and layouts evolve over time. Additionally, sentiment analysis can assess how audiences react to different types of poster designs.

The cast and crew dataset enables studies on representation, diversity, and career trajectories in the film industry. Researchers can analyze gender and ethnicity distribution among actors and filmmakers, identify collaborations between directors and actors, and track career growth over time. This dataset also supports network analysis to visualize connections between cast and crew members across different productions.

Overall, this dataset is a versatile resource for exploring various aspects of the film industry, from financial success and audience engagement to visual storytelling and industry representation.


## ⚡ Usage and Terms
This dataset is provided by The Movie Database (TMDb) API. Please refer to their [Terms of Use](https://www.themoviedb.org/terms-of-use) for more information.

## Links
Google colab: https://colab.research.google.com/drive/1Uf4aWUj71M1tnrCHY_n58zvrtgmX5A55?usp=sharing
Kaggle: https://www.kaggle.com/datasets/fatmahaljohani/tmdb-data
GitHub: https://github.com/fatmah13/TMBd-data/tree/main

