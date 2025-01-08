# Home_Sales

## Home Sales Data Analysis with PySpark

  This project demonstrates data processing and analysis of home sales data using FindSpark, PySpark, Google Colab, and Google Drive. The data includes information about homes, such as price, bedrooms, bathrooms, view rating, and the year built. The goal is to perform various analyses and data manipulations, including partitioning, caching, querying, and exporting results.

## Table of Contents

**1.** Project Overview

**2.** Technologies Used

**3.** Setup Instructions

**4.** Key Tasks

**5.** Output Files

**6.** Results

**7.** References

##  Project Overview

This project involves:

- Analyzing home sales data using FindSpark & PySpark.
- Caching and partitioning data for optimized querying.
- Querying data to extract insights, such as the average home price based on specific criteria.
- Storing processed data in Parquet format and compressing it for storage and sharing.

## Technologies Used

- FindSpark & PySpark: For big data processing and analysis.
- Google Colab: As the script development environment.
- Google Drive: For data storage and sharing.
- Parquet: For efficient data storage.
- Python: Core programming language.

## Setup Instructions
**1.** Mount Google Drive in Colab:

  `from google.colab import drive
drive.mount('/content/drive')`

**2.** Install Necessary Libraries (if not already installed):

  `!pip install findspark`

**3.** Load and Explore Data:

- Data can be stored in your Google Drive and accessed using its path ( /content/drive/MyDrive/Home_Sales.csv ).

**4.** Run the Notebook:

- Execute the steps in the notebook sequentially to process and analyze the data.

## Key Tasks

**1.** Data Loading:

- Load the home sales data from Google Drive.
  
**2.** Data Partitioning:

- Partition the data by the date_built field and save it in Parquet format:

  `output_path = "/content/drive/MyDrive/Home_Sales_Partitioned"
  df.write.mode("overwrite").partitionBy("date_built").parquet(output_path)`

**3.** Caching and Querying:

- Cache temporary tables for performance optimization:

  `spark.sql("CACHE TABLE home_sales")`
  
**4.** Queries:

- Calculate the average price of homes per "view" rating:

  `SELECT view, ROUND(AVG(price), 2) AS avg_price
  FROM home_sales
  GROUP BY view
  HAVING AVG(price) >= 350000
  ORDER BY view DESC;`
  
**5.** Exporting Data:

- Zip the partitioned data for download:

  `!zip -r home_sales_partitioned.zip /content/drive/MyDrive/Home_Sales_Partitioned`

**6.** Push to GitHub

## Output Files

- Partitioned Data: Saved in Parquet format in the folder /content/drive/MyDrive/Home_Sales_Partitioned.
- Zipped Data: A compressed version of the partitioned data for easy download.
- Analysis Results: Results from SQL queries for insights like average home prices.

## Results

- The analysis provided insights into:
  - Average home prices by view rating.
  - Trends in prices based on the year built.
  - Filtering and aggregating data based on specific criteria (e.g., bedrooms, bathrooms, square footage).
    
## References

ChatGPT and Xpert Learning Assistant were used for analysis reference and troubleshooting errors for this project assignment.

- OpenAI. (January, 2025). ChatGPT (GPT-4) [Large language model]. https://chat.openai.com/ Xpert Learning Assistant was used for troubleshooting errors for this project assignment.

- Xpert Learning Assistant. (2025). Retrieved from https://bootcampspot.instructure.com/

