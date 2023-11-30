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
