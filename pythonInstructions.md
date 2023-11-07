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