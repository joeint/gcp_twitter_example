# Google Cloud Streaming Twitter Example
This examples shows how to listen to a Twitter hashtag (via the streaming API), process the tweet's sentiment and store the results all within Google Cloud Platform.

When a tweet is received, the application will run a sentiment analysis using Google's Natural Language Processing and then store the results within BigQuery.


## Prerequisites
* git installed - https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
* node installed - https://nodejs.org/en/
* If running within Google Cloud Compute Engine make sure to enable API scopes when creating the VM


## Setup 
1. ``git clone https://github.com/joeint/gcp_twitter_example.git``
2. ``npm install``
3. Generate Twitter keys from https://apps.twitter.com/
    * input keys into the .env file
4. Create the Big Query dataset and table
    * ``bq mk twitter``
    * ``bq mk --schema HashTag:STRING,Tweet:STRING,SentimentScore:FLOAT,SentimentMagnitude:FLOAT,InsertDate:STRING -t twitter.twitter_stream``
5. Update .env file with the GCP project id that contains the BQ Twitter table
6. (optional) update the hashtag in ``app.js`` 

## Running the application
You can run the application as on a virtual machine or within app engine
### VM Option
``node app.js``
### App Engine
``gcloud app deploy``
