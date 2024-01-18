# Yelp-Sentiment-Analysis-on-Google-Cloud-Platform

This project implements an end-to-end sentiment analysis pipeline for extracting insights from Yelp reviews leveraging managed services on Google Cloud Platform.

# Technologies Used: 

## Core Technologies:
- Apache Spark MLlib on Dataproc Spark clusters for distributed data processing, feature extraction, model training and evaluation. 
## - Specific libraries used:
                            * SparkSQL, Dataframes and Datasets for data manipulation
                            * Tokenization and Vectorization for converting text to numeric features
                            * Classification algorithms: Logistic Regression, SVM, Naive Bayes
                            * Google Cloud Pub/Sub for real-time streaming ingestion of review data from Yelp API into the pipeline.
                            * Google BigQuery as data warehouse for batch storage as well as serving ML model features.
## GCP Services: 
                            * Dataproc: Fully managed Spark and Hadoop clusters used for data engineering and running PySpark jobs at scale.
                            * BigQuery: Serverless enterprise data warehouse for BI and large-scale data analysis.
                            * PubSub: Scalable, durable event streaming to ingest real-time data into applications.
                            * Cloud Storage: Geo-redundant object storage for durable storage of batch dataset.
                            * Cloud Functions: Serverless compute to deploy ML models with autoscaling.

## Data Pipeline Stages
1. Ingestion: Yelp review JSON data streamed in real-time from Yelp API into Pub/Sub topic.
2. Streaming Data Pipeline
* PubSub topic streams data into BigQuery table
* BigQuery triggers Dataproc PySpark job for data preprocessing
*Cleaned data with sentiment predictions loaded back into BigQuery
3. Batch Pipeline
* Historical dataset stored in Cloud Storage
* Dataproc PySpark job reads dataset for Feature Engineering, Model Training/Tuning
* Best Model exported to Cloud Functions for real-time prediction
4. Analysis:
* Data Studio provides interactive dashboards off BigQuery
* Aggregate trends, compare sentiment across dimensions
5. Retraining: Models retrained periodically with new review data to maintain predictability.

Below is a pipeline used in the project

  ![image](https://github.com/AV-D/Yelp-Sentiment-Analysis-on-Google-Cloud-Platform/assets/148166848/b8719268-b143-4b29-b08a-269ca65afd64)
