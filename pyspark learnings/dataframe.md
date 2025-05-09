# Creating DataFrames from Filestores
```python
# Create a DataFrame from CSV
census_df = spark.read.csv('path/to/census.csv', header=True, inferSchema=True)
# header=True: Uses the first row as column headers
# inferSchema=True: Automatically detects data types (e.g., integer, string)
```
## Printing DataFrame Schema

```python
# Show the schema
census_df.printSchema()
```
root
 |-- age: integer (nullable = true)
 |-- education.num: integer (nullable = true)
 |-- marital.status: string (nullable = true)
 |-- occupation: string (nullable = true)
 |-- income: string (nullable = true)

 ## Basic Analytics on PySpark DataFrames

```python
# .count() will return the total row numbers in the DataFrame
row_count = census_df.count()
print(f'Number of rows: {row_count}')

# groupBy() allows the use of SQL-like aggregations
census_df.groupBy('gender').agg({'salary_range_usd': 'avg'}).show()
# sum(), min(), max()
```

## Key functions for Pyspark analytics
- .select(): Selects specific columns from the DataFrame
- .filter(): Filters rows based on specifc conditions
- .groupBy(): Groups row based on one or more columns
- .agg(): applies aggregate functions to grouped data

## Key Functions Example: `filter()` and `select()`

```python
# Using filter and select, we can narrow down our DataFrame
filtered_census_df = census_df.filter(df['age'] > 50).select('age', 'occupation')
filtered_census_df.show()
```