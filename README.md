# Spotify Music Genre Popularity Analysis and Prediction

## Overview
This project focuses on predicting song genres using data from Spotify’s music streaming platform. It examines how features such as release year, speechiness, danceability, and tempo influence genre classification. The project also addresses the following research questions:

- **RQ1**: How does song popularity differ across genres?
- **RQ2**: Is there a significant difference in speechiness between genres?
- **RQ3**: How has track popularity changed over time?

To build the genre prediction model, three classification algorithms were compared: Linear Discriminant Analysis (LDA), K-Nearest Neighbors (KNN), and Random Forest. After cleaning and preprocessing the dataset, the models were evaluated using metrics such as AUC, sensitivity, and specificity. The best-performing model was identified and tested to enhance Spotify’s recommendation system and playlist management capabilities.

## Key Methods Utilised

### Prediction Model
The methods and evaluation metrics utilised in the development of the prediciton models were:

Methods:
1. **Random Forest**: A machine learning algorithm that constructs multiple decision trees and averages their predictions. It was tuned with 100 trees, adjusting the number of predictors and data points in each node across 5 levels.
2. **Linear Discriminant Analysis (LDA)**: A linear classification model that reduces the number of variables by finding the best separation between classes. It did not require tuning, only normalization of numerical variables.
3. **K-Nearest Neighbours (KNN)**: A classification algorithm that compares data points to their k nearest neighbours and classifies based on the majority class. The number of neighbours was tuned over 20 levels, ranging from 1 to 100.

Evaluation Metrics:
- **AUC (Area Under the ROC Curve)**: Measures the model's ability to distinguish between classes, with values closer to 1 indicating better performance.
- **Sensitivity**: The proportion of true positives predicted by the model, representing the model’s ability to correctly identify a given genre.
- **Specificity**: The proportion of true negatives predicted by the model, indicating how well the model can exclude incorrect genre classifications.

### Research Questions
The methods used to analyse the song genres and answer the research questions were:
- **Visualizations**: Histograms and bar charts were used to explore the shape, location, spread, and outliers of each variable across genres.
- **Summary Statistics**: For each variable, the range, interquartile range (IQR), mean, and median were calculated to assess central tendency and variability.
- **Class Comparisons**: Variables were analyzed both overall and stratified by genre, allowing comparison of distribution patterns between genres.
- **Outlier Detection**: Outliers were identified in several variables, particularly for different genres, based on visual inspection of distributions and spread.
- **Trend Analysis**: Linear regression models were used to examine the relationship between time (year) and song popularity, providing insights into long-term trends across genres.

## Data
The dataset used in this project was sourced from the **spotifyr** package and contained **32,833 songs** with features like **energy, loudness, danceability, tempo, acousticness**, and **track release date**. After selecting 16 key variables for genre prediction, the data was cleaned, downsampled to **6,000 songs** (1,000 per genre), and split into **training (75%)** and **testing (25%)** sets.

Data preprocessing included normalization, removal of zero-variance and highly correlated variables, and cross-validation for model tuning. Exploratory Data Analysis (EDA) was performed to assess variable relationships and ensure data suitability for model building.

## Results

For the full analysis of the results please refer to the EDA, Founder Questions and Discussion sections of the written report in `Music_Genre_Analysis_Report.pdf`.

### Prediction Model
The comparative analysis of three machine learning models—Random Forest, K-Nearest Neighbors (KNN), and Linear Discriminant Analysis (LDA)—revealed that the **Random Forest model** performed the best in predicting music genres, achieving the highest **AUC** (85.02%) and demonstrating strong **specificity** (91.11%). It excelled in identifying genres like **rock, edm, and rap**, but showed weaker sensitivity for **pop, latin, and r&b** genres, likely due to limited variability in these categories. The **KNN model** had moderate performance with an AUC of 80.77%, showing a particular strength in predicting edm, though it, too, struggled with pop and r&b. The **LDA model**, while the weakest overall with an AUC of 80.97%, showed the most consistency across genres, though its sensitivity remained low. 

The primary challenge across all models was differentiating between pop, latin, and r&b genres, indicating potential issues with the dataset's representation of these genres. Despite these limitations, **Random Forest** emerged as the most reliable model for predicting song genres, particularly for rock and edm, while all models showed room for improvement in overall accuracy and sensitivity.

### Research Questions
1. **How does song popularity differ across genres?**: The popularity of songs varies between genres. Latin and pop genres had the highest average popularity, with mean values of 47.74 and 48.49, respectively. EDM had the lowest mean popularity at 35.76. The range and interquartile range (IQR) were similar across genres, with some variations in popularity distribution, but EDM was consistently the least popular genre.

2. **Is there a significant difference in speechiness between genres?**: Speechiness varied significantly across genres. Rap had the highest mean and median speechiness (0.193 and 0.168), with a wide IQR, indicating high variability. Genres like EDM, pop, and rock had lower average speechiness and less variance. Outliers were present in most genres, but rap stood out with higher overall speechiness compared to others.

3. **How has track popularity changed over time?**: Overall, track popularity decreased over time for all genres, except Latin, which showed a slight increase. Despite long-term declining trends, there was evidence of a short-term increase in popularity, particularly between 2010 and 2020 for genres like EDM, Latin, R&B, and rap. Latin was the only genre showing consistent growth in popularity over time.

## Technologies Used
The following R libraries and packages were used in this project:
- tidyverse
- lubridate
- stringr
- tidyr
- skimr
- recipes
- inspectdf
- dplyr
- rsample
- themis
- ranger
- vip
- parsnip
- dials
- discrim
- tune
- pROC
- kknn
