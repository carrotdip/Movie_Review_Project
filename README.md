# Movie_Review_Project
## Overview
The purpose of this analysis is to predict the IMDb rating/score based on several parameters, including genre, rating, release date, director, and much more. Each year, hundreds of films are produced worldwide, and some are exceptionally successful, and others are surprisingly not. The goal of this project is to predict the success, measured by their IMDb rating, of upcoming films by first analyzing which features contribute heavily to the outcome of the movie, then creating a supervised machine learning model that will predict the IMDb rating. In addition to the supervised machine learning model that we intend to create to predict a movie rating, we are also focusing on several attributes and exploring if there is a correlation between those attributes and the final rating of movies.
The data source for this project was this [dataset](https://www.kaggle.com/danielgrijalvas/movies), which is a compiled tabular dataset of the budget, company, country of origin, director, genre, gross revenue, title, rating, release date, runtime, score, number of votes, stars, and writer, which was all scraped from the IMDb website. We hope to accurately predict the success of prospective movies, as well as determine the main contributing factors of a successful film.

## Outline
What affects movie ratings? How can we predict a movie rating?
In todays world we have so many different ways of watching movies, which also amplifies our choices on what movie to watch. Whether it is in the comfort of our own homes or going to the theater, the decision of what to commit our limited time to is an important one. So how do you narrow down your choices to the movies worth seeing? As a group we will attempt to answer the following questions along with a predictive model for determining movie rating:
* Which studio produces the highest rated movies?
* What genre is the most popular? (the highest rated)
* Does the actor affect the rating of the movie?
* Does the director affect the rating of the movie?

In our project we will present our machine learning model and outcome, describe and show the findings related to the questions above through statistical analysis and data presentation in Tableau.

## Summary of Data Preparation
Once we found the data through [dataset](https://www.kaggle.com/danielgrijalvas/movies) our next step was to prep the data set to ensure it was usable and complete. This was completed utilizing Python and Jupyter Notebook. Through this process we found that the dataset had missing information throughout. The largest portion of the incomplete dataset came from the budget information for each of the movie titles, there were over 2,000 movies that were missing budget information. Through various conversation and additional research, we decided that this attribute or feature was not entirely necessary as budget was found to have a weak correlation with the outcome of a film. Instead of removing the movie titles with the incomplete budget information, which would result in removing over 2,000 data points, we decided to remove the attribute all together, for all titles. This preserved a lot of data that we originally started with and resulted in a ~7,000 title dataset. We did have to delete some titles that had missing variables; however, those eliminations were very limited and it did not compromise our initial dataset.
There was a gross revenue feature of the dataset that dates back to the 1980s. These prices were adjusted for inflation following this [guide](https://towardsdatascience.com/adjusting-prices-for-inflation-in-pandas-daaaa782cd89).
 
## Statistical Analysis
 
## Machine Learning Model
Three preliminary supervised machine learning models: Linear Regression, Random Forest, and Gradient Boost were prepared to determine the best algorithm for the prediction of IMDb film ratings. The three models were created without any additional data processing to evaluate the metrics and noise of each individual system. The Random Forest model produced the highest r^2 score, which evaluates the performance of a regression-based machine learning model. The r^2 score measures the amount of variance in the predictions explained by the dataset.
To further improve the models, feature engineering was utilized on all three models. As much of the variance, and outliers, is due to most of the directors, writers, and stars only appearing once in the dataset, we set out to bin or group these names. It was found that grouping the directors, writers, and stars with one appearance into a separate category only made the model metrics worse. In the end, although we lost approximately 30% of the data, dropping these names improved each algorithm, but the random forest model produced the best results. Imputation was unfortunately not an option for these features.
Attempts to bin or group the other categorical variables, such as genre, MPAA rating, and company did not come to fruition, as the model metrics did not vary much after tweaking these features.
After binning and grouping data, it became apparent that the linear regression model was not as accurate as the two others. Therefore, the linear regression model was dismissed.
One-hot encoding, a form of feature engineering, was also utilized to convert the many categorical variables into a new binary variable to impute into the machine learning models. The data was then split into training and testing sets, and a standard scaler was used to scale the data.
To prevent overfitting, grid search with cross validation was utilized to determine the best hyperparameters for the remaining models. Several iterations of the grid search were performed, and it was found that the Random Forest model was the most robust, so we secured it as the final model.
 
## Results
### Machine Learning Model
The preliminary r^2 score for the linear regression, random forest, and gradient boost models were -2.55, 0.41, and 0.37, respectively. Further feature engineering of the linear regression machine learning model did not improve the metrics. The best metrics for the linear regression model was an r^2 score of 0.35, which was lower than the preliminary models of the random forest and gradient boost regression models, so the linear regression model was ultimately discarded.
After feature engineering of the remaining models as described above, the model metrics r^2, root mean square error (RMSE) and mean absolute error (MAE) came out to be 0.43, 0.81, and 0.47 for the random forest model and 0.37, 0.88, and 0.59 for the gradient boost model. After the grid search with cross validation, the random forest was determined to be the most robust supervised machine learning model for our prediction with an r^2 score of 0.43, RMSE of 0.77, and MAE of 0.45. This means that with our random forest supervised machine learning model, 43% of the variance can be explained by the original dataset, there is an average squared error of 0.77, and an average of 0.45 difference between the expected and actual IMDb ratings.
Although the r^2 score appears to be on the low side, it is actually expected. Due to the arduous nature of the dataset and our analysis, we did not expect to find a great linear relationship between the features and the predicted IMDb score. Additionally, the other model metrics, RMSE and MAE were fairly low, indicating low bias and an accurate model. Furthermore, overfitting the data was not a large concern as we took steps to prevent this. 
 
## Further Research
INCLUDE A FEATURE THAT LISTS COSTARS OR CODIRECTORS

