Question 1: What is the count of records in the model fact_trips after running all models with the test run variable disabled and filtering for 2019 and 2020 data only (pickup datetime) 

```sql
SELECT COUNT(*) 
FROM `chinwee-datatalkcamp.dbt_cchok.fact_trips`
WHERE EXTRACT(YEAR FROM pickup_datetime) IN (2019, 2020)
```

Question 2: What is the distribution between service type filtering by years 2019 and 2020 data as done in the videos . (Yellow/Green)
```sql
SELECT service_type, COUNT(*) 
FROM `chinwee-datatalkcamp.dbt_cchok.fact_trips`
WHERE EXTRACT(YEAR FROM pickup_datetime) IN (2019, 2020)
GROUP BY 1
```

Question 3: What is the count of records in the model stg_fhv_tripdata after running all models with the test run variable disabled
```sql
SELECT COUNT(*) FROM `chinwee-datatalkcamp.dbt_cchok.stg_fhv_tripdata` -- 42084899
```

Question 4: What is the count of records in the model fact_fhv_trips after running all dependencies with the test run variable disabled
```sql
SELECT COUNT(*) FROM `chinwee-datatalkcamp.dbt_cchok.fact_fhv_trips` -- 22676253
```


Question 5: What is the month with the biggest amount of rides after building a tile for the fact_fhv_trips table
```sql
SELECT 
  EXTRACT(MONTH FROM pickup_datetime),
  COUNT(*) 
FROM `chinwee-datatalkcamp.dbt_cchok.fact_fhv_trips` -- 22676253
GROUP BY 1
ORDER BY 2 DESC -- January
```
