The project implements a comprehensive sentiment analysis pipeline designed to extract valuable insights from Yelp reviews, leveraging the power of managed services on the Google Cloud Platform (GCP). Below are the key technologies and GCP services employed in this end-to-end solution:

## Core Technologies:
1. **Apache Spark MLlib on Dataproc Spark Clusters:**
   - Utilized for distributed data processing, feature extraction, model training, and evaluation.
   - Specific libraries employed include SparkSQL, Dataframes, and Datasets for data manipulation.
   - Tokenization and Vectorization techniques are applied to convert text into numeric features.
   - Classification algorithms such as Logistic Regression, SVM, and Naive Bayes are employed for sentiment analysis.

2. **Google Cloud Pub/Sub:**
   - Facilitates real-time streaming ingestion of Yelp review data from the Yelp API into the pipeline.

3. **Google BigQuery:**
   - Serves as both a data warehouse for batch storage and a platform for serving ML model features.

4. **GCP Services:**
   - **Dataproc:** Fully managed Spark and Hadoop clusters used for data engineering and running PySpark jobs at scale.
   - **BigQuery:** Serverless enterprise data warehouse for BI and large-scale data analysis.
   - **PubSub:** Scalable, durable event streaming for ingesting real-time data into applications.
   - **Cloud Storage:** Geo-redundant object storage utilized for durable storage of batch datasets.
   - **Cloud Functions:** Serverless compute used for deploying ML models with autoscaling.

## Data Pipeline Stages:

1. **Ingestion:**
   - Yelp review JSON data is streamed in real-time from the Yelp API into a Pub/Sub topic.

2. **Streaming Data Pipeline:**
   - Pub/Sub topic streams data into a BigQuery table.
   - BigQuery triggers a Dataproc PySpark job for data preprocessing.
   - Cleaned data with sentiment predictions is loaded back into BigQuery.

3. **Batch Pipeline:**
   - Historical dataset is stored in Cloud Storage.
   - Dataproc PySpark job reads the dataset for Feature Engineering, Model Training/Tuning.
   - The best model is exported to Cloud Functions for real-time prediction.

4. **Analysis:**
   - Data Studio provides interactive dashboards off BigQuery.
   - Aggregate trends and compare sentiment across various dimensions.

5. **Retraining:**
   - Models are retrained periodically with new review data to maintain predictability.

Below is a rough sketch of the datapipeline used in the project

  ![image](https://github.com/AV-D/Yelp-Sentiment-Analysis-on-Google-Cloud-Platform/assets/148166848/b8719268-b143-4b29-b08a-269ca65afd64)

