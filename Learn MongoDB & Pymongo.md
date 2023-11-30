# MongoDB and PyMongo

## Overview
This project uses NoSQL databases, mainly MongoDB, with Python. We use PyMongo to connect Python with MongoDB. It's great for handling lots of data, works fast, and can adapt to changes in data.

- **Use SQL** for structured data, complex queries, ACID compliance, data integrity, and advanced reporting. (**ACID Compliance**: Essential when atomicity, consistency, isolation, and durability are critical for transactions.)
- **Use NoSQL** for unstructured data, scalability, flexible schema, high-speed operations, and real-time applications.
  
## Why NoSQL?
We use NoSQL because it's great for different kinds of data, can grow with our needs, and is really fast. It's perfect for big projects and apps that need to work in real-time.

## MongoDB
MongoDB is a leading NoSQL database that uses a document-oriented approach for storing data in JSON-like documents. It's known for its:

- **Document-Oriented Storage**: Intuitive storage model, allowing for varied data structures.
- **Scalability and Performance**: Efficient handling of large data volumes and complex queries.
- **Rich Query Language**: Extensive querying capabilities, including text search and geospatial queries.
- **High Availability**: ReplicaSets provide automatic failover and data redundancy.

## Using PyMongo
PyMongo is the Python driver for MongoDB. It allows easy interaction with MongoDB from Python applications. Key features include:

- **Easy for Python Users**: Simple for Python coders to use.
- **Works with Python Stuff**: Fits right in with Python tools and libraries.
- **Full MongoDB Experience**: Lets you do everything MongoDB can do.

## Installation

To set up this project, you need to install MongoDB and PyMongo. You can do this via:

```bash
# Install MongoDB (follow MongoDB's official documentation for installation)
# Install PyMongo
pip install pymongo
```

## Importing the Dataset
To import your dataset into MongoDB, use the following command:
```
mongoimport --type json -d data_base_name -c collection_name --drop --jsonArray json_file_name.json
mongoimport --type csv -d data_base_name -c collection_name --drop --headerline --file csv_file_name.csv

```



## Usage

Here is a basic example of how to use PyMongo to connect to a MongoDB database:

```python
from pymongo import MongoClient

# Create a MongoDB client
client = MongoClient("mongodb://localhost:27017/")

# Connect to your database
db = client.your_database_name
```


## Find Documents with Specific Criteria

To find and display documents in your collection that match certain criteria:

```python
# Define your search criteria
search_criteria = {'FieldName': 'Value'}

# Find documents matching the criteria
matching_documents = db.collection_name.find(search_criteria)

# Print each matching document
for document in matching_documents:
    print(document)
```


## Update and Delete Data
To update a specific restaurant's data and delete certain records:

```# Update data
db.collection_name.update_one({'FieldName': 'Value'}, {'$set': {'OtherFieldName': NewValue}})

# Delete records
db.collection_name.delete_many({'FieldName': 'Value'})

```

## Data Type Conversion
To convert data types within your documents:
```
# Convert data types for specific fields
db.collection_name.update_many({}, [{'$set': {'field1': {'$toType': 'newType'}, 'field2': {'$toType': 'newType'}}}])
```


## Convert MongoDB Results to a Pandas DataFrame

To convert the results of a MongoDB query to a Pandas DataFrame, you can use the `pd.json_normalize` function. This is particularly useful for further data manipulation and analysis in Python.

```python
import pandas as pd

# Assuming 'results_list' is your list of documents from a MongoDB query
results_list = [...]  # replace with your data

# Convert the list of MongoDB documents to a Pandas DataFrame
df = pd.json_normalize(results_list, sep='_')

```

## Constructing and executing a MongoDB query with sorting and limiting results using PyMongo
### Construct the query to find documents within the latitude and longitude range
```
query = {
    'field': {'$gte': ... , '$lte': ... },
    'field2': {'$gte': ... , '$lte': ... }
}

# Define sorting criteria and result limit
sort_criteria = [('your_sorting_field', 1)]  # Replace 'your_sorting_field' with the field name
limit = 5  # Limit the number of results returned

# Execute the query, apply sorting, and limit the results
result_list = list(collection.find(query).sort(sort_criteria).limit(limit))

# Print the query results
pprint(result_list)
```


## MongoDB Aggregation Pipeline

This section explains how to create an aggregation pipeline in MongoDB to match certain documents, group them by a specific field, and then sort the results.

```
# Step 1: Match documents based on a condition
match_query = {'$match': {'your_field_name': your_match_condition}}  # Replace with your field and condition

# Step 2: Group the matched documents by a specific field
group_query = {'$group': {
                          '_id': '$your_group_field',  # Replace with the field you want to group by
                          'count': {'$sum': 1}
                         }}

# Step 3: Sort the grouped results
sort_values = {'$sort': {'count': -1}}  # -1 for descending order

# Combine steps into a pipeline
pipeline = [match_query, group_query, sort_values]

# Execute the pipeline
results = list(collection.aggregate(pipeline))

# Print the number of documents in the result
print(len(results))

# Print the first 10 results
for i, result in enumerate(results[:10]):
    print(result)
```


## Understanding Aggregation vs. Basic Query in MongoDB

### Aggregation vs. Basic Query
This aggregation pipeline is more complex than a basic query. While a basic query simply retrieves documents that match certain criteria, an aggregation pipeline allows for multiple steps of data processing like matching, grouping, and sorting.

### Grouping and Summarizing
The pipeline includes a `$group` stage, which groups data by a specified field and calculates aggregate values (like count). This type of data processing is not achievable through a basic query.

### Order of Execution
In the aggregation pipeline, data flows through each stage sequentially. This allows for complex data transformations and analysis that are beyond the capabilities of a simple query.

### Use Case
Aggregation pipelines are particularly useful for more complex data analysis tasks. They are ideal for summarizing data, performing calculations across multiple documents, or reshaping data output for more in-depth analysis.

