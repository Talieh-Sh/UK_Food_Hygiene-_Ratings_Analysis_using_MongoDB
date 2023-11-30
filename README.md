# NoSQL Challenge: UK Food Standards Analysis

## Project Overview

This project involves analyzing the UK Food Standards Agency's hygiene ratings data for various establishments across the United Kingdom. The data analysis is conducted to aid the food magazine "Eat Safe, Love" in focusing their future articles and critiques.
The analysis is performed using MongoDB, a NoSQL database, and Python, with data manipulation and exploratory analysis conducted within Jupyter Notebooks.


## Prerequisites
- MongoDB
- Python
- Jupyter Notebook
- Libraries: PyMongo, Pandas, pprint


## Instructions

### Part 1: Database and Jupyter Notebook Set Up

- Use `NoSQL_setup_starter.ipynb`.
- Import `establishments.json` into MongoDB.
  - Command: `mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`
- In the notebook, import necessary libraries.
- Create an instance of MongoClient.
- Confirm the database and collection setup.
- Assign the `establishments` collection to a variable.

### Part 2: Update the Database

- Add a new restaurant "Penang Flavours".
- Update "Penang Flavours" with the correct `BusinessTypeID`.
- Remove establishments within the Dover Local Authority.
- Convert certain string fields to numeric values using `update_many`.

### Part 3: Exploratory Analysis

- Use aggregation and querying techniques to extract insights.
- Convert results to Pandas DataFrames for easier analysis.

### For those interested in learning more about MongoDB and PyMongo, refer to the `Learn MongoDB & Pymongo.md` document. It provides additional resources and tutorials to deepen your understanding of these powerful tools.

