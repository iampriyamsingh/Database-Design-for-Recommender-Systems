# Database Performance Evaluation for Recommender Systems

This repository contains a Jupyter Notebook that measures and compares the performance of five different database types: PostgreSQL, MongoDB, Cassandra, Redis, and Neo4j. The performance metrics are evaluated using two datasets: Retail Rocket (`events.csv`) and Diginetica (`train_clicks`).

Additionally, a Neo4j Graph-Based Recommender System is developed using the MovieLens dataset to demonstrate creating nodes and relationships, computing similarities, and generating recommendations.

## Table of Contents
1. [Introduction](#introduction)
2. [Setup Instructions](#setup-instructions)
3. [Database Configuration](#database-configuration)
4. [Usage](#usage)
5. [Performance Metrics](#performance-metrics)
6. [Neo4j Graph-Based Recommender System](#neo4j-graph-based-recommender-system)
7. [Results Visualization](#results-visualization)
8. [Saving Results](#saving-results)
9. [Dependencies](#dependencies)
10. [License](#license)

## Introduction

The notebook performs the following operations to measure database performance:

1. **Creation of Database based on Dataset Features**
2. **Insertion of Records into Created Database** (Bulk Insertion & Batch Insertion)
3. **Reading Records**
4. **Updating Records**
5. **Deleting Records**

The performance metrics for these operations are captured for five different databases: PostgreSQL, MongoDB, Cassandra, Redis, and Neo4j.

Additionally, a Neo4j Graph-Based Recommender System is developed using the MovieLens dataset, performing operations such as:

1. Creating Nodes and Relationships
2. Calculating Movie-Movie Similarity
3. Computing Jaccard Similarity
4. Generating Recommendations

The MovieLens dataset files `users.dat` and `movies.dat` are used to create nodes, while `ratings.dat` is used to create relationships.

## Setup Instructions

To run the notebook, you need to set up the following databases:

- PostgreSQL
- MongoDB
- Cassandra
- Redis
- Neo4j

Make sure you have the datasets (`events.csv` and `train_clicks`) available in the appropriate directory.

## Database Configuration

For each database, ensure the correct configuration and connection parameters in the notebook code.

### PostgreSQL

```python
db_params = {
    'dbname': 'your_db',
    'user': 'your_user',
    'password': 'your_password',
    'host': 'localhost',
    'port': 5432
}
```

### MongoDB

```python
client = pymongo.MongoClient('mongodb://localhost:27017/')
db = client['your_db']
collection = db['your_collection']
```

### Cassandra

```python
auth_provider = PlainTextAuthProvider(username='your_user', password='your_password')
cluster = Cluster(['localhost'], auth_provider=auth_provider)
session = cluster.connect()
```

### Redis

```python
redis_client = redis.StrictRedis(host='localhost', port=6379, db=0)
```

### Neo4j

```python
uri = "bolt://localhost:7687"
driver = GraphDatabase.driver(uri, auth=("your_user", "your_password"))
```

## Usage

1. **Import Libraries**

    The notebook begins by importing necessary libraries such as `psycopg2`, `pymongo`, `redis`, `neo4j`, `cassandra-driver`, `matplotlib`, `pandas`, `psutil`, and others.

2. **Monitoring Resource Utilization**

    Functions to monitor CPU and memory usage are defined and utilized to measure the resource consumption during database operations.

3. **Database Operations**

    Each database operation (create, insert, read, update, delete) is implemented with functions specific to the database type.

## Performance Metrics

Performance metrics such as execution time, CPU usage, and memory usage are captured for each operation on the datasets.

## Neo4j Graph-Based Recommender System

A separate section in the notebook is dedicated to creating a recommender system using Neo4j. This includes:

- Creating nodes from `users.dat` and `movies.dat` files.
- Creating relationships from `ratings.dat` file.
- Computing similarities between movies.
- Generating movie recommendations based on similarities.

## Results Visualization

The notebook includes code to visualize the results:

- **Execution Time vs Number of Records**
- **Memory Usage vs Number of Records**
- **Total RAM Comparison**

These visualizations help compare the performance of the different databases.

## Saving Results

The performance results are saved to a general results file (e.g., `results.csv`) for further analysis.

## Dependencies

The following Python libraries are required to run the notebook:

- `psycopg2`
- `pymongo`
- `redis`
- `neo4j`
- `cassandra-driver`
- `matplotlib`
- `pandas`
- `psutil`
- `numpy`

Install the dependencies using pip:

```
pip install psycopg2 pymongo redis neo4j cassandra-driver matplotlib pandas psutil numpy
```

## License

This project is licensed under the MIT License. See the LICENSE file for details.
