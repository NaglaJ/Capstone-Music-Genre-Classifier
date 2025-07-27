### Capstone-Music-Genre-Classifier
Model that takes characteristics of songs and predicts the genre
https://github.com/NaglaJ/Capstone-Music-Genre-Classifier/blob/c44b518b3b5b2bac43a417041612f98e883017b7/Music%20Genre%20Classifier.ipynb

N. Elbassioni


## Executive Summary:
This notebook contains an analysis of data from Kaggle that includes a list of songs and a number of features for each song that has been gathered from other sources including Spotify and Last.fm.  This data is also available in KaggleHub. The objective of the model is to use characteristics of songs to predict the appropriate ‘genre’ of the music.

## Rationale:
How does a recording artist decide what genre to classify their music? This is important because as a listener, I generally find new music by searching a genre or listening to a genre-based mix (e.g., New Indie Rock Mix).  Music streaming companies categorize songs by genre.  Recording artists reach their audience by identifying or aligning with a specific genre.  
Research Question:
Since definitions and categories are loose, could using the characteristics of their songs help them define a better fit for ‘genre’ and allow them to reach their target audience?

## Data Sources
kagglehub.dataset_download("undefinenull/million-song-dataset-spotify-lastfm")
The data contained a number of null values that need to be addressed, specifically in the ‘genre’ and ‘tags’ column. Interestingly, ‘genre’ had the most null values by far, with 28,335 null values as compared to 1,127 for ‘tags’. This is mentioned because the model I developed can be used to identify genre for these null values with a 75% accuracy.

Genre values are one of the following:  'RnB' 'Rock' 'Pop' 'Metal' 'Electronic' 'Jazz' 'Punk' 'Country'
 'Folk' 'Reggae' 'Rap' 'Blues' 'New Age' 'Latin' 'World'

## Methodology
After cleaning the data, features were transformed using a standard scaler for numeric features and encoder for categorical features and for the y prediction, which is genre. This data was split into training and test sets.

A number of models were assessed using grid search functions.  Models included SVC, LogisticRegression, DecisionTree Classifier and K-nearest neighbors. Because SVC is so resource intensive, LogisticRegression can provide similar results with a slightly lower level of accuracy without requiring significant processing resources. 

The driving features used in the model are 
Tags
Year
Duration_ms
Danceability
Energy
Key
Loudness
Mode
Speechiness
Acousticsness
Instrumentalness
Liveness
Valence
Tempo
Time_signature

## Results:
The model achieved a test accuracy of 75%. The model is based on the SVC algorithm using svc_C value of 1 and kernel value of ‘rbf’.

## Next Steps:
Ultimately, the accuracy score is not great as a genre identifier.  However, it is good enough to use as a way to clean data by populating the Nan values for the ‘genre’ column in order to improve a data set.  The million song dataset included null values for over 28,000 rows.  The outcome of the model in predicting genre for these NaNs is provided in the notebook.
Why is it important to use the genre column at all?  Streaming services categorize their music by genre, as that is the common language with the listening audience.  Genre serves as a highest-level category in the categories and subcategories that appear in ‘tags’.  These sub-genres change regularly, so how to track them? How can a streaming executive understand what genres generate the most revenue? The genre provides a simple roll-up category for such an analysis without having to map tags to similar category groupings.
Another next step could also be to compare the models predictions to the genres listed in Spotify or a music streaming service for those songs.  Note that spotify uses a different list for genres that includes many more than those included in this model.  Spotify also allows for multiple values in the ‘genre’ field, unlike the dataset I used which only allowed 1 value. For this reason, the spotify genre would have to be updated to align terms and select a single value.

Finally, the list of features can be reduced significantly to include only ‘tags’, ‘instrumentalness’, ‘loudness’ and ‘duration_ms’, valence and danceability. Ensemble techniques could have more impact on this simpler model.
