## Exploring London's Travel Network

### Project Overview 
This project offers an excellent starting point for aspiring data engineers. It introduces you to working with real-world data from a major public transport network that handles over 1.5 million daily journeys. 
The project's strength lies in its use of industry-standard data warehouse solutions like Snowflake, Amazon Redshift, Google BigQuery, or Databricks. 
These platforms are crucial in modern data engineering, allowing you to efficiently process and analyze large datasets. 
By analyzing transport trends, popular methods, and usage patterns, you'll learn how to extract meaningful insights from large datasets - a core competency in data engineering.

### Background
Given the city's roads were originally designed for horse and cart, this area and population growth has required the development of an efficient public transport system! 
Since the year 2000, this has been through the local government body called Transport for London, or TfL, which is managed by the London Mayor's office. 
Their remit covers the London Underground, Overground, Docklands Light Railway (DLR), buses, trams, river services (clipper and Emirates Airline cable car), roads, and even taxis.

### Project
1. Download Dataset
2. Load the Dataset into Bigquery or postgresql or any other db of your choice

```
CREATE DATABASE TFL;

\c tfl

CREATE TABLE journeys (
    month INTEGER,
    year INTEGER,
    days INTEGER,
    report_date DATE,
    journey_type VARCHAR(100),
    journeys_millions NUMERIC
);
```

```
COPY journeys FROM 'tfl_journeys_final.csv' DELIMITER ',' CSV HEADER;
```

**Questions:**

1. What are the most popular transport types, measured by the total number of journeys?
   The output should contain two columns, 1) JOURNEY_TYPE and 2) TOTAL_JOURNEYS_MILLIONS, and be sorted by the second column in descending order.
   Save the query as most_popular_transport_types.

```
CREATE OR REPLACE FUNCTION most_popular_transport_types()
RETURNS TABLE (journey_type VARCHAR, tot_journey_mill NUMERIC) AS $$
BEGIN
  RETURN QUERY
    SELECT journey_type, SUM(journeys_millions) AS tot_journey_mill
    FROM journeys
    GROUP BY journey_type
    ORDER BY tot_journey_mill;
END;
$$ LANGUAGE plpgsql;
```

```SELECT * FROM most_popular_transport_types();```

|   journey_type    | tot_journey_mill  |
--------------------|------------------
| Emirates Airline  |    14.5837175749 |
| Tram              |   314.6898754821 |
| TfL Rail          |   411.3134209833 |
| Overground        |  1666.8456664279 |
| Underground & DLR |  15020.466543504 |
| Bus               |   24905.19394699 |

2. Which five months and years were the most popular for the Emirates Airline? Return an output containing MONTH, YEAR, and JOURNEYS_MILLIONS, with the latter rounded to two decimal places and aliased as ROUNDED_JOURNEYS_MILLIONS.
   Exclude null values and save the result as emirates_airline_popularity.

     ```
    CREATE OR REPLACE FUNCTION emirates_airline_popularity()
    RETURNS TABLE (month INTEGER, year INTEGER, tot_journey_mill NUMERIC) AS $$
    BEGIN
      RETURN QUERY
        SELECT month, year, ROUND(journeys_millions, 2) AS tot_journey_mill 
        FROM journeys 
        WHERE journey_type = 'Emirates Airline' 
          AND journeys_millions IS NOT NULL  
        ORDER BY tot_journey_mill DESC LIMIT 5;
    END;
    $$ LANGUAGE plpgsql;
    ```

| month | year | jour_millions |
|-------|------|---------------|
  |  5 | 2012 |          0.53 |
  |  6 | 2012 |          0.38 |
  |  4 | 2012 |          0.24 |
  |   5 | 2013 |          0.19 |
  |   5 | 2015 |          0.19 |

3. Find the five years with the lowest volume of Underground & DLR journeys, saving as least_popular_years_tube.
   The results should contain the columns YEAR, JOURNEY_TYPE, and TOTAL_JOURNEYS_MILLIONS.

     ```
    CREATE OR REPLACE FUNCTION least_popular_years_tube()
    RETURNS TABLE (year INTEGER, total_journeys_millions NUMERIC) AS $$
    BEGIN
      RETURN QUERY
        SELECT year, journey_type, SUM(journeys_millions) AS total_journeys_millions
        FROM journeys WHERE journey_type = 'Underground & DLR'
        GROUP BY year, journey_type
        ORDER BY total_journeys_millions
        LIMIT 5;
    END;
    $$ LANGUAGE plpgsql;
    ```

 | year |   journey_type    | total_journeys_millions |
|------|-------------------|-------------------------|
|  2020 | Underground & DLR |           310.179316314| 
|  2021 | Underground & DLR |            748.45254420| 
|  2022 | Underground & DLR |           1064.85900860| 
|  2010 | Underground & DLR |           1096.14558838| 
|  2011 | Underground & DLR |           1156.64765448| 
