<h2 align= "center">Using Python</h2>
# 🚀 Installation

## Install latest version of Python3

MagixDB is tested and supported on 64-bit systems with:

- Python 3.8, 3.9, and 3.10
- *
- *

## For Linux:
Python 3 is often pre-installed on Linux distributions. However, if it's not, you can typically install it using your package manager. For example, on Ubuntu, you can use the following command:

```bash
sudo apt-get update
sudo apt-get install python3
```
## For macOS:
macOS comes with Python 2 pre-installed, but you can install Python 3 alongside it. You can use Homebrew or download the installer from the Python website.

### Using Homebrew:

Install Homebrew (if not already installed):
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
Install Python 3:
```bash
brew install python@3
```

## For Windows:
You can download the Python installer for Windows from the Python website.

1. Visit the Python download page at https://www.python.org/downloads/windows/.
2. Download the latest Python 3 installer for Windows.
3. Run the installer and make sure to check the box that says "Add Python to PATH" during installation.

Check for the python version using : 
```cmd
python 
```
## Steps to extract the schema for databases
### 1. MySQL Database
#### Step 1 : Install the MySQL Connector
You need to install the mysql-connector library if you haven't already. You can do this using pip:
```bash
pip install mysql-connector-python

```

#### Step 2: Import, Connect and Extract the schema step-wise.
* You'll need to import the mysql.connector library to connect to the MySQL database.
* You should establish a connection to your MySQL database by providing the necessary connection details, such as the host, username, password, and database name.
* A cursor is used to execute SQL queries and fetch results from the database. 
*To extract the schema from the database, you can use SQL queries to retrieve information about tables, columns, and other database objects. 
*Make sure to close the cursor and the database connection when you're done with them to release resources.

```python
import mysql.connector
# Replace these values with your database connection details
host = "your_host"
user = "your_username"
password = "your_password"
database = "your_database_name"

# Create a connection to the MySQL database
connection = mysql.connector.connect(
    host=host,
    user=user,
    password=password,
    database=database
)

cursor = connection.cursor()
# Get the list of tables in the database
cursor.execute("SHOW TABLES")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])

cursor.close()
connection.close()
``` 

#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 2. SQLite

#### Step 1: Import, Connect and Extract the schema step-wise.
* You'll need to import the sqlite3 library to work with SQLite databases.
* To connect to an SQLite database, provide the path to the database file or create a new one if it doesn't exist.
* Similar to working with MySQL, you need to create a cursor to execute SQL queries and fetch results.
* You can use SQL queries to retrieve schema information from the SQLite database. 
* Don't forget to close the cursor and the database connection when you're done with them.
```python
import sqlite3
# Replace 'your_database.db' with the path to your SQLite database file
connection = sqlite3.connect('your_database.db')
cursor = connection.cursor()

# Get the list of tables in the database
cursor.execute("SELECT name FROM sqlite_master WHERE type='table';")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])

cursor.close()
connection.close()
```
#### Step 2: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.



### 3. MongoDB Database

#### Step 1: Install the pymongo library
You need to install the pymongo library if you haven't already. You can do this using pip:

```cmd
pip install pymongo
```
#### Step 2: Import libraries, connect and extract the schema.
* You'll need to import the pymongo library to work with MongoDB.
* To connect to a MongoDB database, provide the connection details, such as the host and port. If authentication is required, you can also provide the username and password.
* In MongoDB, data is stored in collections. You can access a specific collection within the database.
* You can perform various operations on the collection, such as inserting documents, querying data, and updating documents. 
* Close the MongoDB connection when you're done with it to release resources.
```python
import pymongo
# Replace these values with your MongoDB connection details
host = "your_host"
port = 27017  # Default MongoDB port

# Create a connection to the MongoDB server
client = pymongo.MongoClient(host, port)

# Access a specific database
database = client["your_database_name"]

# If authentication is required:
# database.authenticate("your_username", "your_password")

# Access a specific collection in the database
collection = database["your_collection_name"]
# Insert a document into the collection
data = {"key": "value"}
insert_result = collection.insert_one(data)
print("Inserted document ID:", insert_result.inserted_id)

#Query Documents
result = collection.find({"field_name": "value"})
for document in result:
    print(document)

client.close()
```
#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 4. Oracle Database

#### Step 1: Install the cx_Oracle library
```bash
pip install cx_Oracle
```

#### Step 2 :Import libraries, connect and extract the schema.
* You'll need to import the cx_Oracle library to work with Oracle databases.
* To connect to an Oracle database, provide the necessary connection details, including the username, password, host, and SID (Service Identifier) or TNS (Transparent Network Substrate) entry.
* A cursor is used to execute SQL queries and fetch results from the database.
* You can use SQL queries to retrieve schema information from the Oracle database.
* Remember to close the cursor and the database connection when you're done to release resources

```python
import cx_Oracle
# Replace these values with your Oracle database connection details
username = "your_username"
password = "your_password"
dsn = "your_dsn"

# Create a connection to the Oracle database
connection = cx_Oracle.connect(username, password, dsn)

cursor = connection.cursor()

# Get the list of tables in the schema
cursor.execute("SELECT table_name FROM user_tables")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])

cursor.close()
connection.close()
```
#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 5. PostgreSQL Database

#### Step 1: Install the psycopg2 library 
```bash
pip install psycopg2
```

#### Step 2 :Import libraries, connect and extract the schema.
* You'll need to import the psycopg2 library to work with PostgreSQL databases.
* To connect to a PostgreSQL database, provide the necessary connection details, including the host, database name, username, and password.
* A cursor is used to execute SQL queries and fetch results from the database.
* You can use SQL queries to retrieve schema information from the PostgreSQL database.
* Make sure to close the cursor and the database connection when you're done with them

```bash
import psycopg2

# Replace these values with your PostgreSQL database connection details
host = "your_host"
database = "your_database"
user = "your_username"
password = "your_password"

# Create a connection to the PostgreSQL database
connection = psycopg2.connect(
    host=host,
    database=database,
    user=user,
    password=password
)

cursor = connection.cursor()

# Get the list of tables in the public schema
cursor.execute("SELECT table_name FROM information_schema.tables WHERE table_schema = 'public'")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])

cursor.close()
connection.close()
```
#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 6. MariaDB Database
#### Step 1 : Install the MySQL Connector
You need to install the mysql-connector library if you haven't already. You can do this using pip:
```bash
pip install mysql-connector-python

```

#### Step 2: Import, Connect and Extract the schema step-wise.
* You'll need to import the mysql.connector library to connect to the MySQL database.
* You should establish a connection to your MySQL database by providing the necessary connection details, such as the host, username, password, and database name.
* A cursor is used to execute SQL queries and fetch results from the database. 
*To extract the schema from the database, you can use SQL queries to retrieve information about tables, columns, and other database objects. 
*Make sure to close the cursor and the database connection when you're done with them to release resources.

```python
import mysql.connector
# Replace these values with your database connection details
host = "your_host"
user = "your_username"
password = "your_password"
database = "your_database_name"

# Create a connection to the MySQL database
connection = mysql.connector.connect(
    host=host,
    user=user,
    password=password,
    database=database
)

cursor = connection.cursor()
# Get the list of tables in the database
cursor.execute("SHOW TABLES")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])

cursor.close()
connection.close()
``` 

#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 7. Microsoft SQL Server Database
#### Step 1 : Install the pyodbc library
```bash
pip install pyodbc

```

#### Step 2: Import, Connect and Extract the schema step-wise.
* You'll need to import the pyodbc library to work with Microsoft SQL Server databases.
* To connect to a Microsoft SQL Server database, provide the necessary connection details, such as the server name, database name, username, and password.
* A cursor is used to execute SQL queries and fetch results from the database.
* You can use SQL queries to retrieve schema information from the SQL Server database.
* Make sure to close the cursor and the database connection when you're done with them

```python
import pyodbc

# Replace these values with your SQL Server database connection details
server = "your_server_name"
database = "your_database_name"
username = "your_username"
password = "your_password"

# Create a connection to the SQL Server database
connection = pyodbc.connect(
    f"DRIVER={{SQL Server}};SERVER={server};DATABASE={database};UID={username};PWD={password}"
)

cursor = connection.cursor()

# Get the list of tables in the database
cursor.execute("SELECT table_name FROM information_schema.tables WHERE table_type = 'BASE TABLE'")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])

cursor.close()
connection.close()
``` 

#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 8. Redis Database
#### Step 1 : Install the redis-py library
```bash
pip install redis

```

#### Step 2: Import, Connect and Extract the schema step-wise.
* You'll need to import the redis library to work with Redis
* To connect to a Redis server, you typically provide the host and port where Redis is running
* In Redis, you can use the KEYS command to list all keys matching a pattern. Here's how you can use the keys method from redis-py to retrieve all keys. Please note that the KEYS command can be resource-intensive and should be used with caution in a production environment.
* You can close the connection when you're done


```python
import redis

# Replace these values with your Redis server connection details
host = "your_redis_host"
port = 6379  # Default Redis port

# Create a connection to the Redis server
redis_client = redis.Redis(host=host, port=port, db=0)

# Retrieve all keys in the Redis database
keys = redis_client.keys("*")

# Print the list of keys
for key in keys:
    print(key.decode("utf-8"))

redis_client.close()
``` 

#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```python
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 9. Cassandra Database
#### Step 1 : Install the cassandra-driver library
```bash
pip install cassandra-driver
```

#### Step 2: Import, Connect and Extract the schema step-wise.
* You'll need to import the cassandra library to work with Cassandra:
* To connect to a Cassandra cluster, provide the necessary connection details, including the contact points (hostnames or IP addresses) of the cluster nodes.
* A session is used to execute CQL (Cassandra Query Language) statements.
* In Cassandra, schema information is typically related to keyspaces and column families (similar to tables in relational databases). You can list keyspaces and column families using CQL queries. 
* Don't forget to close the session and cluster when you're done with them


```python
from cassandra.cluster import Cluster

# Replace these values with your Cassandra cluster connection details
contact_points = ['node1', 'node2', 'node3']  # List of Cassandra cluster nodes

# Create a connection to the Cassandra cluster
cluster = Cluster(contact_points=contact_points)

session = cluster.connect()

# Get the list of keyspaces in the Cassandra cluster
keyspaces = session.execute("SELECT keyspace_name FROM system_schema.keyspaces")

# Print the list of keyspaces
for keyspace in keyspaces:
    print(keyspace.keyspace_name)

session.shutdown()
cluster.shutdown()
``` 

#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```bash
python your_file_name.py
```
You can also copy the script and run it on your IDE.

### 10. CouchDB Database
#### Step 1 : Install the couchdb library
```bash
pip install couchdb
```

#### Step 2: Import, Connect and Extract the schema step-wise.
* You'll need to import the couchdb library to work with CouchDB
* To connect to a CouchDB server, provide the server URL.
* In CouchDB, data is organized into databases, similar to collections in other NoSQL databases. 
* Documents in CouchDB are stored in databases. You need to list them.
* You can close the connection when you're done


```python
import couchdb

# Replace this URL with your CouchDB server URL
server_url = "http://localhost:5984"

# Create a connection to the CouchDB server
server = couchdb.Server(server_url)

# List all existing databases on the CouchDB server
databases = server.list()
for database in databases:
    print(database)

# Replace 'your_database_name' with the name of the CouchDB database you want to inspect
database_name = 'your_database_name'
db = server[database_name]

# List all documents in the specified database
for doc_id in db:
    print(doc_id)

server.close()
``` 

#### Step 3: Run this file on your device.
To run a Python file from the shell (command prompt or terminal), you can use the python command followed by the name of the Python script you want to execute. Here's the basic syntax: 
```bash
python your_file_name.py
```
You can also copy the script and run it on your IDE.



