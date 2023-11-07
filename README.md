sql workbench, mongoDB command prompt, server->bin -> sql sh login -> keyspaces -> command
# Database Types
The functionality is provided for the given databases only.

```
├── Databases
   ├── MySQL
   ├── SQLite
   ├── MongoDB
   ├── PostgreSQL
   ├── MariaDB (a MySQL fork)
   ├── Microsoft SQL Server
   ├── Oracle Database
   ├── Redis
   ├── Cassandra
   ├── CouchDB
   ├── Neo4j
   ├── Amazon DynamoDB
   └── Firebase Realtime Database

```
<!-- # 🚀 Installation

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
 -->

## 🏃‍♂️ Steps to extract Schema from different databases
<h2 align = 'center';"> Using Command Line</h2>

### Step 1 : Open the command line on your device.
For windows : Start -> Run -> Search cmd <br>
For macOS : Press Command + Space -> Type Terminal and Search <br>
For Linux : Press Ctrl + Alt + T <br>

<!-- ```cmd
pip install mysql-connector-python
```
#### Step 1 : Install the MySQL Connector
You need to install the mysql-connector library if you haven't already. You can do this using pip:
```cmd
pip install mysql-connector-python
``` -->

### Step 2: Run the command on your device for your particular database type.

#### 1. MySQL Database

To extract the schema of a MySQL database, you can use the mysqldump command with the --no-data option to generate a dump file containing only the database schema:
```bash
mysqldump -u username -p --no-data database_name > schema.sql
```
Replace username with your MySQL username, database_name with the name of the database, and provide the password when prompted. The schema will be saved in the schema.sql file.

#### 2. SQLite Database
SQLite databases store their schema in a file, so you can directly copy it:
```bash
sqlite3 database_name .schema > schema.sql
```
This command creates a copy of the SQLite database file, which contains the schema information.

#### 3. PostgreSQL Database
To extract the schema of a PostgreSQL database, you can use the pg_dump command with the --schema-only option:

```bash
pg_dump -U username -d database_name -s -f schema.sql
```
Replace username with your PostgreSQL username, database_name with the name of the database, and specify the output file using the -f option.

Make sure to install any required tools or database clients on macOS, such as MySQL, PostgreSQL, SQLite, jq, and libxml2 (for xmllint), if they are not already installed. 

This command will create a file called schema.sql that contains the schema (table structures, indexes, etc.) of the specified MySQL database.

#### 4. Oracle Database
To extract a schema from an Oracle database using shell commands, you can use the expdp (Data Pump Export) utility, which is provided by Oracle to export data and metadata from Oracle databases. Here's how you can use it to extract a schema:
* Open a terminal or command prompt on the server where Oracle Database is installed.
* Use the expdp command to export the schema to a dump file. Replace the placeholders with your specific values:

```bash
expdp username/password@hostname:port/service_name schemas=schema_name dumpfile=schema_dump.dmp directory=directory_name logfile=export_log.log
```
* username: Your Oracle username with the necessary privileges.
* password: Your Oracle password.
* hostname: The hostname or IP address of the Oracle database server.
* port: The port on which the Oracle listener is running (typically 1521).
* service_name: The Oracle service name or SID.
* schema_name: The name of the schema you want to extract.
* schema_dump.dmp: The name of the dump file where the schema will be exported.
* directory_name: The name of the Oracle directory where the dump file will be stored. You can create an Oracle directory using SQL commands.
* export_log.log: The name of the log file to record the export process.

Here is an example command : 
```bash
expdp hr/mypassword@localhost:1521/orcl schemas=HR dumpfile=hr_schema.dmp directory=DATA_PUMP_DIR logfile=export_hr.log

```
#### 5. MongoDB Database
Use the mongodump command to create a backup of your MongoDB database, specifying the --db option to target the specific database you want to extract the schema from:
```bash
mongodump --host hostname --port port --db your_database_name --out backup_directory
```
* hostname: The hostname or IP address where your MongoDB server is running.
* port: The port on which MongoDB is listening (default is 27017).
your_database_name: The name of the MongoDB database you want to extract the schema from.
* backup_directory: The directory where the backup files will be stored. A new directory with the same name as your database will be created in this location.

#### 6. MariaDB Database
To extract the schema of a MySQL database, you can use the mysqldump command with the --no-data option to generate a dump file containing only the database schema:
```bash
mysqldump -u username -p --no-data database_name > schema.sql
```
Replace username with your MySQL username, database_name with the name of the database, and provide the password when prompted. The schema will be saved in the schema.sql file.

































<!-- ```python
import mysql.connector
```

#### Step 2: Import the necessary libraries
You'll need to import the mysql.connector library to connect to the MySQL database.

```python
import mysql.connector
``` -->

<!-- #### Step 3: Create a MySQL connection
You should establish a connection to your MySQL database by providing the necessary connection details, such as the host, username, password, and database name.

```python
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

```
#### Step 4: Create a cursor object
A cursor is used to execute SQL queries and fetch results from the database. You can create a cursor like this:

```python
cursor = connection.cursor()
```

#### Step 5: Extract schema information
To extract the schema from the database, you can use SQL queries to retrieve information about tables, columns, and other database objects. Here's an example of how to retrieve a list of tables in the database:

```python
# Get the list of tables in the database
cursor.execute("SHOW TABLES")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])
```
#### Step 6: Close the cursor and connection
Make sure to close the cursor and the database connection when you're done with them to release resources.

```python
cursor.close()
connection.close()
```

### 2. SQLite

#### Step 1: Import the necessary libraries
You'll need to import the sqlite3 library to work with SQLite databases.

```python
import sqlite3
```
#### Step 2: Connect to the SQLite database
To connect to an SQLite database, provide the path to the database file or create a new one if it doesn't exist.

```python
# Replace 'your_database.db' with the path to your SQLite database file
connection = sqlite3.connect('your_database.db')
```
#### Step 3: Create a cursor object
Similar to working with MySQL, you need to create a cursor to execute SQL queries and fetch results.

```python
cursor = connection.cursor()
```

#### Step 4: Extract schema information
You can use SQL queries to retrieve schema information from the SQLite database. For example, to get a list of tables in the database:

```python
# Get the list of tables in the database
cursor.execute("SELECT name FROM sqlite_master WHERE type='table';")

# Fetch all table names
tables = cursor.fetchall()

# Print the list of tables
for table in tables:
    print(table[0])
```

#### Step 5: Close the cursor and connection
Don't forget to close the cursor and the database connection when you're done with them.

```python
cursor.close()
connection.close()
```

### 3. MongoDB

#### Step 1: Install the pymongo library
You need to install the pymongo library if you haven't already. You can do this using pip:

```cmd
pip install pymongo
```
#### Step 2: Import the necessary libraries
You'll need to import the pymongo library to work with MongoDB.

```python
import pymongo
```
#### Step 3: Connect to a MongoDB database
To connect to a MongoDB database, provide the connection details, such as the host and port. If authentication is required, you can also provide the username and password.

```python
# Replace these values with your MongoDB connection details
host = "your_host"
port = 27017  # Default MongoDB port

# Create a connection to the MongoDB server
client = pymongo.MongoClient(host, port)

# Access a specific database
database = client["your_database_name"]

# If authentication is required:
# database.authenticate("your_username", "your_password")
```
#### Step 4: Access a collection
In MongoDB, data is stored in collections. You can access a specific collection within the database.

```python
# Access a specific collection in the database
collection = database["your_collection_name"]
```
#### Step 5: Perform operations on the collection
You can perform various operations on the collection, such as inserting documents, querying data, and updating documents. Here's an example of inserting a document into the collection:

```python
# Insert a document into the collection
data = {"key": "value"}
insert_result = collection.insert_one(data)
print("Inserted document ID:", insert_result.inserted_id)

#Query Documents
result = collection.find({"field_name": "value"})
for document in result:
    print(document)
    
```

#### Step 6: Close the MongoDB connection
Close the MongoDB connection when you're done with it to release resources.

```python
client.close()
``` -->
