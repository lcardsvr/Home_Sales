# Home_Sales
Module 22 Challenge

## Requirements

- A Spark DataFrame is created from the dataset. (5 points)



|                  id|               date|date_built| price|bedrooms|bathrooms|sqft_living|sqft_lot|floors|waterfront|view|
|--------------------|-------------------|----------|------|--------|---------|-----------|--------|------|----------|----|
|f8a53099-ba1c-47d...|2022-04-08 00:00:00|      2016|936923|       4|        3|       3167|   11733|     2|         1|  76|
|7530a2d8-1ae3-451...|2021-06-13 00:00:00|      2013|379628|       2|        2|       2235|   14384|     1|         0|  23|
|43de979c-0bf0-4c9...|2019-04-12 00:00:00|      2014|417866|       2|        2|       2127|   10575|     2|         0|   0|
|b672c137-b88c-48b...|2019-10-16 00:00:00|      2016|239895|       2|        2|       1631|   11149|     2|         0|   0|
|e0726d4d-d595-407...|2022-01-08 00:00:00|      2017|424418|       3|        2|       2249|   13878|     2|         0|   4|
|5aa00529-0533-46b...|2019-01-30 00:00:00|      2017|218712|       2|        3|       1965|   14375|     2|         0|   7|
|131492a1-72e2-4a8...|2020-02-08 00:00:00|      2017|419199|       2|        3|       2062|    8876|     2|         0|   6|
|8d54a71b-c520-44e...|2019-07-21 00:00:00|      2010|323956|       2|        3|       1506|   11816|     1|         0|  25|
|e81aacfe-17fe-46b...|2020-06-16 00:00:00|      2016|181925|       3|        3|       2137|   11709|     2|         0|  22|
|2ed8d509-7372-46d...|2021-08-06 00:00:00|      2015|258710|       3|        3|       1918|    9666|     1|         0|  25|
|f876d86f-3c9f-42b...|2019-02-27 00:00:00|      2011|167864|       3|        3|       2471|   13924|     2|         0|  15|
|0a2bd445-8508-4d8...|2021-12-30 00:00:00|      2014|337527|       2|        3|       1926|   12556|     1|         0|  23|
|941bad30-eb49-4a7...|2020-05-09 00:00:00|      2015|229896|       3|        3|       2197|    8641|     1|         0|   3|
|dd61eb34-6589-4c0...|2021-07-25 00:00:00|      2016|210247|       3|        2|       1672|   11986|     2|         0|  28|
|f1e4cef7-d151-439...|2019-02-01 00:00:00|      2011|398667|       2|        3|       2331|   11356|     1|         0|   7|
|ea620c7b-c2f7-4c6...|2021-05-31 00:00:00|      2011|437958|       3|        3|       2356|   11052|     1|         0|  26|
|f233cb41-6f33-4b0...|2021-07-18 00:00:00|      2016|437375|       4|        3|       1704|   11721|     2|         0|  34|
|c797ca12-52cd-4b1...|2019-06-08 00:00:00|      2015|288650|       2|        3|       2100|   10419|     2|         0|   7|
|0cfe57f3-28c2-472...|2019-10-04 00:00:00|      2015|308313|       3|        3|       1960|    9453|     2|         0|   2|
|4566cd2a-ac6e-435...|2019-07-15 00:00:00|      2016|177541|       3|        3|       2130|   10517|     2|         0|  25|
|--------------------|-------------------|----------|------|--------|---------|-----------|--------|------|----------|----|
only showing top 20 rows


- A temporary table of the original DataFrame is created. (10 points)

Done

- A query is written that returns the average price, rounded to two decimal places, for a four-bedroom house that was sold in each year. (5 points)

SELECT date_built, round(avg (price),2)
AS Average_Price
FROM home_sales 
WHERE bedrooms==4 
group By date_built
order by date_built

|date_built|Average_Price|
|----------|-------------|
|      2010|    296800.75|
|      2011|     302141.9|
|      2012|    298233.42|
|      2013|    299999.39|
|      2014|    299073.89|
|      2015|    307908.86|
|      2016|    296050.24|
|      2017|    296576.69|

- A query is written that returns the average price, rounded to two decimal places, of a home that has three bedrooms and three bathrooms. (5 points)

SELECT date_built, round(avg (price),2) 
AS Average_Price
FROM home_sales 
WHERE bedrooms==3 
AND bathrooms==3 
group By date_built
order by date_built

|date_built|Average_Price|
|----------|-------------|
|      2010|    292859.62|
|      2011|    291117.47|
|      2012|    293683.19|
|      2013|    295962.27|
|      2014|    290852.27|
|      2015|     288770.3|
|      2016|    290555.07|
|      2017|    292676.79|


- A query is written that returns the average price of a home with three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet for each year built rounded to two decimal places. (5 points)

SELECT date_built, round(avg (price),2) 
AS Average_Price
FROM home_sales 
WHERE bedrooms==3 
AND bathrooms==3 
AND floors==2
AND sqft_lot >= 2000
group By date_built
order by date_built

|date_built|Average_Price|
|----------|-------------|
|      2010|    280447.23|
|      2011|    281413.45|
|      2012|    295858.68|
|      2013|    295142.13|
|      2014|    294195.13|
|      2015|    291788.36|
|      2016|     287812.6|
|      2017|    282026.59|

- A query is written that returns the view rating for the average price for homes that are greater than or equal to $350,000, rounded to two decimal places. (The output shows the run time for this query.) (10 points)

SELECT round(avg (view),2) 
AS Average_View_Rating
FROM home_sales 
WHERE price >=350000 

|Average_View_Rating|
|-------------------|
|              32.26|


--- 0.48814916610717773 seconds ---

- A cache of the temporary "home_sales" table is created and validated. (10 points)

Done

- The query from step 6 is run on the cached temporary table, and the run time is computed. (10 points)

SELECT round(avg (view),2) 
AS Average_View_Rating
FROM home_sales 
WHERE price >=350000 

|Average_View_Rating|
|-------------------|
|              32.26|


--- 0.23134303092956543 seconds ---

- A partition of the home sales dataset by the "date_built" field is created, and the formatted parquet data is read. (10 points)

Done

- A temporary table of the parquet data is created. (10 points)

Done

- The query from step 6 is run on the parquet temporary table, and the run time is computed. (10 points)

|Average_View_Rating|
|-------------------|
|              32.26|


--- 0.3357667922973633 seconds ---

- The "home_sales" temporary table is uncached and verified. (10 points)

Done


## Submission

1. Jupyter notebook submitted and available in GitHub under https://github.com/lcardsvr/Home_Sales/blob/main/Home_Sales_colab.ipynb

2. Requirements for the challenge fulfilled and shown above.