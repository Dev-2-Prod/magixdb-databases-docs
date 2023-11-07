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


# 🏃‍♂️ Steps to extract Schema from different databases
<h2 align = 'center';"> Using Command Line</h2>

## Step 1 : Open the command line on your device.
For windows : Start -> Run -> Search cmd <br>
For macOS : Press Command + Space -> Type Terminal and Search <br>
For Linux : Press Ctrl + Alt + T <br>


## Step 2: Run the command on your device for your particular database type.

### 1. MySQL Database

To extract the schema of a MySQL database, you can use the mysqldump command with the --no-data option to generate a dump file containing only the database schema:
```bash
mysqldump -u username -p --no-data database_name > schema.sql
```
Replace username with your MySQL username, database_name with the name of the database, and provide the password when prompted. The schema will be saved in the schema.sql file.

### 2. SQLite Database
SQLite databases store their schema in a file, so you can directly copy it:
```bash
sqlite3 database_name .schema > schema.sql
```
This command creates a copy of the SQLite database file, which contains the schema information.

### 3. PostgreSQL Database
To extract the schema of a PostgreSQL database, you can use the pg_dump command with the --schema-only option:

```bash
pg_dump -U username -d database_name -s -f schema.sql
```
Replace username with your PostgreSQL username, database_name with the name of the database, and specify the output file using the -f option.

Make sure to install any required tools or database clients on macOS, such as MySQL, PostgreSQL, SQLite, jq, and libxml2 (for xmllint), if they are not already installed. 

This command will create a file called schema.sql that contains the schema (table structures, indexes, etc.) of the specified MySQL database.

### 4. Oracle Database
To extract a schema from an Oracle database using shell commands, you can use the expdp (Data Pump Export) utility, which is provided by Oracle to export data and metadata from Oracle databases. Here's how you can use it to extract a schema:
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
### 5. MongoDB Database
Use the mongodump command to create a backup of your MongoDB database, specifying the --db option to target the specific database you want to extract the schema from:
```bash
mongodump --host hostname --port port --db your_database_name --out backup_directory
```
* hostname: The hostname or IP address where your MongoDB server is running.
* port: The port on which MongoDB is listening (default is 27017).
your_database_name: The name of the MongoDB database you want to extract the schema from.
* backup_directory: The directory where the backup files will be stored. A new directory with the same name as your database will be created in this location.

### 6. MariaDB Database
To extract the schema of a MySQL database, you can use the mysqldump command with the --no-data option to generate a dump file containing only the database schema:
```bash
mysqldump -u username -p --no-data database_name > schema.sql
```
Replace username with your MySQL username, database_name with the name of the database, and provide the password when prompted. The schema will be saved in the schema.sql file.

### 7. Microsoft SQL Server
To extract a schema from a Microsoft SQL Server database using shell commands, you can use the sqlcmd utility along with the bcp (Bulk Copy Program) utility. Follow these steps to extract the schema:

* Use the sqlcmd utility to generate SQL scripts for the schema. Replace the placeholders with your specific values:
```bash
sqlcmd -S server_name -d database_name -U username -P password -Q "EXEC sp_helpfile" -o schema.sql
```
* server_name: The name or IP address of your SQL Server.
* database_name: The name of the SQL Server database from which you want to extract the schema.
* username: Your SQL Server username with appropriate privileges.
* password: Your SQL Server password.
* schema.sql: The output file where the schema information will be saved.

### 8. Redis
If you want to retrieve information about the keys and data types in your Redis database, you can use the SCAN command. You can interact with Redis using its command-line client, redis-cli.

* Start the redis-cli tool to connect to your Redis server. Replace hostname and port with your Redis server's hostname and port (usually 6379):
```bash
redis-cli -h hostname -p port
```

* To list all keys in the Redis database, you can use the SCAN command as follows: 
```bash
SCAN 0
```
This command will return a cursor and a list of keys. If the cursor is non-zero, you should run the SCAN command again with the new cursor to retrieve the next batch of keys until the cursor becomes 0.

* To get the data type of a specific key, you can use the TYPE command. Replace your_key with the key you want to inspect:
```bash
TYPE your_key
```

### 9. Cassandra
Start the cqlsh tool to connect to your Cassandra cluster. Use the following command, replacing the placeholders with your specific values:
```bash
cqlsh -u username -p password -k keyspace_name -h hostname -C port
```
* username: Your Cassandra username with appropriate privileges.
* password: Your Cassandra password.
* keyspace_name: The name of the Cassandra keyspace containing the table you want to inspect.
* hostname: The hostname or IP address of your Cassandra cluster node.
* port: The CQL native transport port (default is 9042).

Once you are in the cqlsh shell, use the DESCRIBE TABLE command to inspect the table, and simultaneously save the output to a file using the tee command:
```bash
DESCRIBE TABLE table_name; | tee output.txt
```
This command will save the output of the DESCRIBE TABLE command to a file named output.txt in the current working directory.

### 10. CouchDB
Use the cURL command to make an HTTP GET request to CouchDB to retrieve a document. Replace the placeholders with your specific values:
```bash
curl -X GET http://username:password@hostname:port/database_name/document_id
```
* username: Your CouchDB username with appropriate privileges.
* password: Your CouchDB password.
* hostname: The hostname or IP address where your CouchDB server is running.
* port: The port on which CouchDB is listening (default is 5984).
* database_name: The name of the CouchDB database you want to inspect.
* document_id: The unique identifier of the document you want to inspect.




























