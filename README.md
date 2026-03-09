# Analysis of Movie Review DataSet

The goal of this project is to analyze the MovieLens dataset to identify potential clusters amongst users, evolution of genre preference, and investigagte possible relation betwen number of reviews and numeric rating value for movie titles.

DataSet source: https://grouplens.org/datasets/movielens/
Name- MovieLens 32M
Scott Coleman
Team Name: Red Hot Data Scientists

# M2 Report
Since the completion of M1, I have made some updates to the overall plan for my project. First and foremost I have altered the discovery questions based on the feedback I was given on M1. The new questions are: "What distinct user segments exist based on viewing behavior?", "What genre co-occurence patterns exist in user viewing histories?", and "What anomalous rating patterns exist for highly-reviewd vs rarely-reviewed films?". These provide a better foundation to work with and have served me better in steering the direction of my investigation, thank you very much for the feedback.

EDA:
All of the tables contained the correct count of values and non contained erronious values. All outliers were accounted for either being users that are highly active, movies that share the same title, etc.. Significant findings from my EDA of each table included clear wide variety in user activity where some users review a handful of movies while other review thousands , a majority of movies belong to multiple categories, and user ratings were generally positive and clustered between 3.5 - 5.0. I conducted both bivariate as well as multivariate analysis involving features from all tables. For the genre's I split this features into the individual values so as to eliminate the overlap that occured in a majority of films. Through the use of a heatmap I found that there is some correlation between genres including Action and Adventure as well as Animation and Children's films. In the next milestone I plan to investigate this further to see if I can definitively determine whether there are co-occurences between genres that are meaningful. For the movie ratings I compared the count of ratings for each film against, the average rating for the film, std, avg against std.. These analysis demonstrated that movies that are more popular tend to converge towards average scores of around 3.0-4.0. In contrast less popular movies tend to have extreme averages whether they be high or low. This gives me hope that in the next module I will be able to find some meaningful information relating to question 3.

Preprocessing:
During preprocessing I found that all data types were consistent across tables. Only the tag variable contained missing values, to handle this I replaced them with a "None" value, so as to preserve the associated data entries. All outliers were found to be natural mainly presenting in the form of users with a high ratings count. The only duplicate records were caused by movies that share the same title name. As with the missing tags, these were kept so as to preserve the data quality. I converted the format of the timestamp feature in the tags and ratings columns from the given Unix time to date time format to allow for easier interpretation. I then split these into two new features 'year' and 'month'

Data Transformation & 1st Mining Technique:
For my first mining technique I decided to implement K-means clustering as a means of investigating question 1. To prepare the data for this I engineered a new table, 'User_features', containing count of ratings for each user, average rating given by each user, standard deviation for those averages, and genre counts for each user. After standarizing these features K-means clustering was applied using K = 3. The clusters identified related to three distinct user groups. These included, cluster 0, representing 'moderate users' that provided the second highest number of ratings. Cluster 1 which included 'intense users' who gave the highest number of ratings. And finally cluster 2 which are the 'causal users' as indicated by their low count of reviews. From this initial analysis alone it is clear that distinct groups are formed among the users and provides initial findings for question 1. I will expand upon this foundation in the next milestone.

Plans for M3:
In the next module I tend to investigate my discovery questions even further. Techniques I plan to implement include Apriori to investigate genre co-occurances, isolation forests for investigating anomalous ratings, and other clustering techniques for user segments including Hiearchical or DBSCAN.
