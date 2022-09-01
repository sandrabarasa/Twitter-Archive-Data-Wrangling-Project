# Twitter-Archive-Data-Wrangling-Project

## Introduction
This project involves data wrangling of the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog.

The data wrangling process involves three key steps, i.e.
1) Gathering data
2) Assessing data and,
3) Cleaning data

Python libraries required: pandas, numpy, requests, tweepy, json, seaborn, matplotlib, plotly and IPython.display.

## Gathering Data
The project has 3 datasets, i.e.
1) Enhanced Twitter Archive (df1) – Provided by Udacity in csv format and is loaded into the notebook using the read_csv function
2) Image Predictions File (df2) – Provided by Udacity and is loaded using the requests library.
3) Additional Data via the Twitter API (df3).

**NB:** Accessing dataset 3 (df3) required first requesting access to the Twitter API via a developer account that would allow access to token keys required in gathering of the data. I then used the tweet IDs in the Twitter archive dataset to query the Twitter API for each tweet's JSON data and stored each tweet's entire set of JSON data in a file called tweet_json.txt. After which I read the json file into a pandas data frame.

## Assessing Data
Assessing was done both visually and programatically to identify any quality and/or tidiness issues within the datasets.

**Quality Issues:**

> Dataset 1:
1) Incorrect data type for column 'timestamp' - should be datetime
2) Incorrect data type for column 'tweet ids' - should be string as this is an identifier
3) Remove rows that have retweet status ID as these are not original ratings
4) Irrelevant columns: 'in_reply_to_status_id', 'in_reply_to_user_id', 'retweeted_status_id', 'retweeted_status_user_id', 'retweeted_status_timestamp', 'expanded_urls'
5) Rows with text that contains "We only rate dogs" in the 'text' column are not dogs.
6) Values with 'None' instead of 'NaN' in the columns: 'doggo', 'fluffer', 'pupper' and 'puppo'
7) Incorrect extraction of some rating_numerator values
8) Incorrect data type for column 'rating_numerator' - should be float

> Dataset 2:
1) Incorrect data type for column 'tweet ids'- should be string as this is an identifier.
2) Rows where the number one predictions (i.e. column 'p1_dog' is false) are not dogs.

>Dataset 3:
1) Incorrect data type for column 'tweet ids'- should be string as this is an identifier
2) Inconsistency in column name to identify tweet ids. Change 'id' to tweet_id'
3) Irrelevant columns not needed in my analysis

**Tidiness Issues:**
1) 1 variable(dog type) in 4 columns i.e. doggo, fluffer, pupper, puppo
2) Combine all three datasets

## Cleaning Data
After creating copies of the datasets, I used the define-code-test method in my cleaning process, where I defined the issues raised, wrote code to correct the issue, then performed a test to confirm that the issue was indeed corrected.

After the cleaning process, I stored my data in csv format in a file named: ‘twitter_archive_master.csv’ which I then used to generate insights and perform visualisations.

## Findings
Insights generated included:
1) The most common dog stage is the pupper, followed by the doggo and puppo, each with 224, 75 and 24 dogs respectively. Under the pupper dog stage, the Golden retriever, the Pembroke and Labrador retriever were the most common, with 16, 10 and 8 dogs respectively.
2) On average, the standard poodle dogbreed received the most retweets when compared to other breeds under the first prediction (p1). On the other hand, the black-and-tan coonhound dogbreed received the most likes.
3) On average, the pupper dog stage received the least likes and retweets, despite being the most common dog stage.
4) The dog with the highest retweets is an Eskimo dog with 52,724 retweets. Photo shown below:
![image](https://user-images.githubusercontent.com/104767434/188016374-65ee72cb-8f64-4cdb-b577-52668df1306b.png)
5) The dog with the highest likes is a Lakeland terrier with 123,717 likes. Photo shown below:
![image](https://user-images.githubusercontent.com/104767434/188016535-d2e24314-b610-499a-b60b-87d3afe1f73a.png)
6) There is a positive correlation between the retweet count and favorite count of 0.965.

