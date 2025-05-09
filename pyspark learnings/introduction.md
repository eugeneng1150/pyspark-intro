# What is Pyspark
- Distributed data processing: Designed to handle large datasets across clusters
- Supports various data formats like CSV, Parquet, JSON
- SQL integration allows query of data using both Python and SQL Syntax

# Spark cluster
## Master Node
- Manages the cluster, coordinate tasks, and schedules jobs
## Worker Nodes
- Execute the tasks assigned by the master
- Responsible for executing the actual computations and storing data in memory or disk

# SparkSession
- allow you to acces your spark cluster
```python
# Import SparkSession
from pyspark.sql import SparkSession

# Initialize a SparkSession
spark = SparkSession.builder.appName("MyApp").getOrCreate()
# builder() sets up a session
# getOrCreate() creates or retrieves a session
# appName() helps manage multiple sessions
```

# PySpark DataFrames
- Similar to other DataFrames but
- Optimized for PySpark

```python
# Import and initialize a Spark session
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("MySparkApp").getOrCreate()

# Create a DataFrame
census_df = spark.read.csv("census.csv", 
    ["gender", "age", "zipcode", "salary_range_usd", "marriage_status"])

# Show the DataFrame
census_df.show()
```