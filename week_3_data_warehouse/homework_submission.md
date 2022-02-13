## Question 1: What is count for fhv vehicles data for year 2019

```sql
SELECT
  COUNT(*)
FROM `chinwee-datatalkcamp.trips_data_all.nyc_fhv_2019` 
```


## Question 2: How many distinct dispatching_base_num we have in fhv for 2019

```sql
SELECT
  COUNT(DISTINCT dispatching_base_num)
FROM nyc_fhv_2019
```


## Question 4: What is the count, estimated and actual data processed for query which counts trip between 2019/01/01 and 2019/03/31 for dispatching_base_num B00987, B02060, B02279 *


```sql
CREATE OR REPLACE TABLE `chinwee-datatalkcamp.trips_data_all.nyc_fhv_2019_partitioned`
PARTITION BY DATE(dropoff_datetime)
CLUSTER BY dispatching_base_num AS (
  SELECT * FROM `chinwee-datatalkcamp.trips_data_all.nyc_fhv_2019`
);

SELECT count(*) FROM  `chinwee-datatalkcamp.trips_data_all.nyc_fhv_2019`
WHERE dropoff_datetime BETWEEN '2019-01-01' AND '2019-03-31' 
AND dispatching_base_num IN ('B00987', 'B02279', 'B02060');
```


## Question 5: What will be the best partitioning or clustering strategy when filtering on dispatching_base_num and SR_Flag

```sql
SELECT
  SR_FLAG,
  COUNT(*)
FROM `chinwee-datatalkcamp.trips_data_all.nyc_fhv_2019` 
GROUP BY 1
```