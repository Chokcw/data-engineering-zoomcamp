Problem Statement

[This dataset from Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) provides information of 100k orders from 2016 to 2018 made at multiple marketplaces in Brazil. 

For this project, we want to find out the states with the most number of orders made and the daily volume of orders from these states.

We have used Airflow to orchestrate the ingestion of data to GCS and moving the data to Google Bigquery.

How to reproduce the project

- Set your bigquery project in the following
- Install kaggle using pip install kaggle, 
- create a folder call olist and cd olist
- Download the data
