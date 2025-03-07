# Songalytics: Music Popularity Predictor

## Introduction

This study explores music trends through a detailed analysis of the Spotify dataset to uncover prevailing trends and predict song popularity using machine learning models. By examining a variety of genres and musical elements, this research aims to offer insights into listeners' preferences and the factors that contribute to a song's success. The findings are valuable for music creators, producers, and enthusiasts in understanding the elements that define the popularity of a track.

<img src="https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/intro.jpg" style="width: 750px;">

## Dataset

The dataset I used is a comprehensive compilation of Spotify tracks across 125 different genres, stored in a tabular CSV format. It offers a broad spectrum of audio features and metadata for each track, including the track's ID, artists, album name, popularity score, duration, explicitness, and numerous audio properties like danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, and time signature.

Link : https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset

## Cleaning the data set

Steps taken to clean the data:
1. Dropping irrelevant columns - Unnamed, track_id
2. Identifying columns with missing values and dropping null values
3. Checking for duplicate rows and dropping them
4. Checking the data type of columns - changing if required
5. Removing Outliers
6. Created a new column based  on popularity score - popularity category : Based on the popularity score, a new categorical column named ‘popularity category’ was created. The scores were divided into four categories: ‘emerging’ (0-25), ‘upandcoming’ (26-50), ‘mainstreamhits’ (51-75), and ‘charttoppers’ (76-100). Creating this new column is significant as it facilitates segmented analysis, allowing for a more nuanced understanding of the different popularity levels of the tracks

| Category  | Popularity Score Range |
| ------------- | ------------- |
| Emerging | 0-25 |
| Up and Coming  | 26-50  |
| Mainstream Hits  | 51-75 |
| Chart Toppers  | 76-100  |


## Explorartory Data Analysis

### Summary Statistics

Here are some fun ones!

| Feature | Analysis |
| ------------- | ------------- |
| artists  | There are 30,119 unique artists with "The Beatles" appearing most frequently (271 times).  |
| album_name  | 44,588 unique album names with "Alternative Christmas 2022" being the most frequent album name (185 times)  |
| track_name  | 9,477 unique track names with "Run Rudolph Run" appearing most frequently (151 times).  |
| track_genre  | 114 unique genres with "sad" being the most frequent genre (1,000 times).  |
| popularity_category  | 4 unique categories with "Emerging Artists" being the most frequent category (41,279 times). |

### Distribution of Numerical Features

![Distribution of Numerical Features](https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/images/distribution.png)

When interpreting the provided histograms, we are getting insights into the different characteristics of a collection of music tracks. Let’s break down these insights:

* Majority Low Popularity: Most of the tracks have popularity between 0 and 40.
* Some High Popularity: Few tracks exist with high popularity, extending up to 100.
* Mainstream Duration: Most tracks have a duration between 100,000 ms (1.67 minutes) and 300,000 ms (5 minutes).
* Extended Duration: Few tracks are longer than the typical range.
* Moderate to High Danceability: The majority of tracks score between 0.4 and 0.8 on danceability, indicating a general preference for danceable music.
* Balanced Distribution: Energy levels are evenly distributed, with a slight inclination towards higher energy levels.
* Uniform Distribution: Tracks are spread across different keys uniformly, indicating a varied musical scale presence.
* Predominantly Loud: The majority of the tracks are loud, falling between -10 and -5 dB, with fewer tracks being quieter.
* Predominantly Non-Speechy: Most tracks have low speechiness, indicating that they contain more music than spoken words.
* Varied Acousticness: Many tracks have low to moderate acousticness with fewer tracks having high acousticness.
* Predominantly Non-Instrumental: Most tracks are not instrumental.
* Variety: Few tracks exhibit moderate to high instrumentalness.
* Studio-like Quality: Most tracks have low liveness, meaning they probably are studio recordings with less audience noise.
* Few Live Recordings: Some tracks have high liveness, indicating potential live recordings.
* Balanced Mood: Tracks have a balanced distribution in terms of valence with a slight inclination towards happier or more positive music.
* Common Tempo: Most tracks lie in the common tempo range of 80 to 140 BPM (Beats Per Minute).
* Varied Tempo: Few tracks fall outside the common tempo range, suggesting variety in rhythm speed.
* Common Time: Most tracks have a 4/4 time signature, which is the most common time signature in modern music.

Conclusion:

This collection seems to contain a diverse range of music tracks but leans more towards mainstream preferences, such as moderate to high danceability, higher energy levels, louder volumes, and common time signatures. There are also instances of less common musical elements, providing a variety, such as tracks with high instrumentalness, varied tempo, and live recordings. The uniform distribution in keys also ensures a wide range of musical scales.

### Distribution of Categorical Features

![Distribution of Categorical Features](https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/images/Cat%20features.png)

* Explicit: The majority of the tracks are not explicit, with a smaller number of tracks being explicit.
* Mode: Most tracks are in Mode 1, with fewer tracks in Mode 0.
* Track Genre: The dataset has a diverse set of genres, with "sad", "upbeat", and "chill" being the most frequent ones.
* Popularity Category: The majority of the tracks fall under the "Emerging Artists" category, followed by "Mainstream Hits", "Underground Hits", and "Chart-Toppers".

### Correlation Matrix

![](https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/images/corr%20matrix.png)

Observations:

* Energy and Loudness have a strong positive correlation of 0.78, which is expected as louder songs are usually perceived as more energetic.
* Valence and Danceability have a moderate positive correlation of 0.54, indicating that tracks perceived as more positive or happier tend to be more danceable.
* Energy and Acousticness have a strong negative correlation of -0.71, suggesting that more energetic songs tend to have lower acousticness.
* Loudness and Acousticness have a moderate negative correlation of -0.56, indicating that louder songs tend to have lower acousticness.
* Energy and Valence have a moderate positive correlation of 0.39, suggesting that more energetic songs tend to be more positive or happier.
* Danceability and Speechiness have a moderate positive correlation of 0.22, indicating that more danceable songs tend to have more spoken words.

###  Box plots for numerical features against popularity_category

![](https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/images/box%20plots%20by%20popularity%20category.png)

* Popularity: As expected, "Chart-Toppers" have the highest median popularity, followed by "Mainstream Hits," "Emerging Artists," and "Underground Hits."
* Danceability: "Mainstream Hits" and "Chart-Toppers" tend to have higher median danceability compared to "Emerging Artists" and "Underground Hits."
* Energy: "Chart-Toppers" have a higher median energy level compared to other categories.
* Loudness: "Chart-Toppers" and "Mainstream Hits" tend to be louder compared to "Emerging Artists" and "Underground Hits."

### Top 10 genres based on their frequencies

```
sad            1000
rockabilly      999
rock-n-roll     999
study           998
mandopop        997
electro         997
chill           997
house           997
sertanejo       996
cantopop        996
```

### Artists with most Chart Toppers

![](https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/images/Screenshot%202023-09-22%20at%201.36.55%20PM.png)

### Average Dancebility for Top 10 Frequent Genres

## What constitutes a popular song ?

### Comparing mean values of each popularity category
```
# Grouping by 'popularity_category' and getting the mean of each feature per category
category_mean = df.groupby('popularity_category').mean()

# Sorting the resulting DataFrame by 'popularity' in descending order for better readability
category_mean.sort_values(by='popularity', ascending=False)
```

* Chart-Toppers tend to have higher energy, danceability, and valence compared to the other categories.
* Explicit Content: A higher percentage of Chart-Toppers have explicit content compared to the other categories.
* Acousticness: Chart-Toppers tend to have lower acousticness, implying that they might have more electronic elements.
* Instrumentalness: Chart-Toppers tend to have lower instrumentalness, implying they are likely to have more vocal content.
* Liveness: Up-and-Coming and Emerging Artists categories tend to have higher liveness compared to Chart-Toppers and Mainstream Hits.
* Speechiness: Emerging Artists category has slightly higher speechiness compared to the other categories.

### Correlation Matrix: Popularity Score

![](https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/images/corr%20matrix%20focus%20popularity.png)

The correlation matrix (focused on popularity) and the correlation values show the relationship between the features and the popularity score.
Observations:
* Explicit Content (r=0.0424r=0.0424): Songs with explicit content tend to have a slight positive correlation with popularity.
* Duration (r=0.0380r=0.0380): There is a slight positive correlation between the duration of a song and its popularity.
* Danceability (r=0.0357r=0.0357): There is a slight positive correlation between danceability and popularity.
* Loudness (r=0.0354r=0.0354): Loudness also has a slight positive correlation with popularity.
* Instrumentalness (r=−0.0768r=−0.0768): There is a slight negative correlation between instrumentalness and popularity, suggesting that songs with more vocals tend to be more popular.
* Valence (r=−0.0483r=−0.0483): There is a slight negative correlation between valence and popularity.
* Speechiness (r=−0.0451r=−0.0451): There is a slight negative correlation between speechiness and popularity.

### ANOVA
```
import scipy.stats as stats

# Initialising a dictionary to hold p-values for each feature
p_values = {}

# List of features to perform ANOVA on
features = ['explicit', 'duration_ms', 'danceability', 'loudness', 'instrumentalness', 'valence', 'speechiness']

# Performing ANOVA for each feature
for feature in features:
    # Extracting the groups
    group1 = df[df['popularity_category'] == 'charttoppers'][feature]
    group2 = df[df['popularity_category'] == 'mainstreamhits'][feature]
    group3 = df[df['popularity_category'] == 'upandcoming'][feature]
    group4 = df[df['popularity_category'] == 'emerging'][feature]

    # Performing ANOVA and storing the p-value
    f_stat, p_value = stats.f_oneway(group1, group2, group3, group4)
    p_values[feature] = p_value

p_values
```
The p-values obtained from the ANOVA tests for the features across different popularity categories are as follows:
```
{'explicit': 6.454145319575757e-131,
 'duration_ms': 1.7746465932399508e-56,
 'danceability': 4.994958051619132e-127,
 'loudness': 2.2979291269703185e-84,
 'instrumentalness': 3.0203410777439953e-282,
 'valence': 2.169545891776659e-87,
 'speechiness': 2.105664599560184e-155}
 ```
All the p-values are extremely close to zero, much less than the commonly used significance level of 0.05. This indicates that there are statistically significant differences in the means of these features across different popularity categories.

## Machine Learning Algos

| Algorithm | RMSE |
| ------------- | ------------- |
| Linear Regression  | 22.134  |
| Random Forest Regressor  | 14.334  |
| Support Vector Regressor  | 21.108  |
| XGBoost  | 15.115  |
| Neural Network Regressor (MLPRegressor)  | 20.086  |

We can see that the least RMSE acquired is by using Random Forest Regressor. 

## Feature Importance 

Lastly let's observe feature importance with help of Random Forest Regressor model we created since it gives the least RMSE. 

![](https://github.com/adiimated/Songalytics-Spotify-Data-Analysis/blob/main/images/feature%20importance.png)

As we can see album name, track genre, track name, artist and its acousticness hold the most importance while deciding whether a song will be a hit or not.

## Conclusion

In conclusion, the analysis of the Spotify dataset revealed significant trends in music tracks and listeners' preferences. This project successfully linked musical elements like energy and danceability to a song’s popularity and highlighted the variety in musical genres available on Spotify. The predictive models, especially the Random Forest Regressor, showed the capability of machine learning in predicting song popularity. This study serves as a stepping stone to further, more in-depth research into music analytics and user preferences.

