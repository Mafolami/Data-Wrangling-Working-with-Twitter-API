# Data-Wrangling-Working-with-Twitter-API
This project explores Twitter's WeRateDog's tweet archives and draws insights from analyses.

Introduction
The goal of the project is to carry out data wrangling for the WeRateDogs Twitter data and be able to draw insightful conclusions through quality assessment, analysis and visualizations. To achieve this goal, the Twitter archive data was made available. Nonetheless, the data provided only has few tweet details. It became necessary to obtain more tweet informatin from the archives, and using several approaches, assess and clean the newly gleaned information while also making it ready and usable for further analyses. Some of the additional information retrieved included: retweet and favorite counts, and the image predicction data. The additinal image prediciton data provided information as to whether the animal is or not a dog.

For the project, I used three dataframes containing the provided twitter_archive csv file, a json .txt file, and a tsv file.

The twitter_archive_enhanced csv file provided basic information about each WeRateDog tweet such as the name of dog, dog rating numerator and denominator, and the source of each tweet. The json file obtained using tweepy gave more relevant information about each WeRateDog tweet, making analysing the data much better. The third dataframe is the tsv file containing the prediction of each image including their classification into two buckets of whether they are dog or not dog.

Wrangling Efforts
The following were the steps taken to wrangle my data:
I imported the necessary libraries and read the dataframes as required

I visually and programmatically assessed my data using head(), sample(), info(), describe(), shape(), isnull() and others.

Using requests, I downloaded the tweet image predictions tsv file and assessed it.

I queried the twitter API using tweepy to obtain additional tweet information

I retained the rows containing tweets with only original ratings and dropped tweets without images

Quality issues identified and solution:
The following quality issues were identified and solution provided to each of them accordingly:

Some 'expanded_urls' have their urls duplicated in the same observation. One unique url should be retained
The 'name' column in 'original_tweet' contains names that are not of the dogs in the tweet: eg a, unacceptable etc
Columns 'p1, p2 and p3' in 'true_image_pred' consists of upper and lower cases, and hyphen and underscore characters
p1, p2 and p3 colummns in 'true_image_pred' contain 'false' values which appear irrelevant in the table.
Almost all the values of 'retweeted_status_id', 'retweeted_status_user_id' and 'retweeted_status_timestamp' in 'original_tweet' are missing
'timestamp' in 'original_tweet' has a wrong data type
The 'in_reply_to_status_id' & 'in_reply_to_user_id' in 'original_tweet' have over 90% of its value missing
Some of the 'doggo', 'floofer', 'pupper' and 'puppo'columns have none as their values
Tidiness:
Tidiness issues identified were:

The three variables in the file_df data can be merged with the original_tweet dataset because it is part of the same observational unit as the data in the original_tweet data.

The columns "doggo, floofer, pupper and puppo" should be merged because they do not each represent a unique observational unit.

Final steps
As last steps after assessing and cleaning identified quality and tidiness issues,the cleaned dataframes were merged and stored into a csv file. The csv file, which became the master file, was used to conduct further analysis and visualization.
