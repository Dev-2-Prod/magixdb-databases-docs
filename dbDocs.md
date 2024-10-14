# Database Connection Documentation

## Overview

This documentation provides an overview of the database connection classes used in the backend of the application. Each class is responsible for connecting to a specific type of database and provides methods to interact with the database, such as querying data and retrieving the database schema.

## Files and Classes

### 1. `db_router.py`

This file contains the FastAPI router for handling database-related API endpoints. It includes endpoints for connecting to databases, querying data, generating reports, and managing dashboards.

#### Key Endpoints

- **`/connect/`**: Connects to a specified database using provided connection parameters.
- **`/query/`**: Executes a query on a connected database.
- **`/report/`**: Generates a report based on conversation history.
- **`/create_dashboard/`**: Creates a new dashboard for a user.
- **`/insert_dashboard/`**: Inserts a query into a specified dashboard.

### 2. `MariaChinook` (in `maria.py`)

This class handles connections to a MariaDB database.

#### Input Parameters

- `host`: The database server host (default: `"localhost"`).
- `username`: The username for database authentication (default: `"root"`).
- `password`: The password for database authentication (default: `"sanchay"`).
- `database`: The name of the database to connect to (default: `"Chinook"`).

### 3. `MSSQLConnection` (in `mssql.py`)

This class handles connections to a Microsoft SQL Server database.

#### Input Parameters

- `server`: The server address of the SQL Server.
- `database`: The name of the database to connect to.
- `username`: The username for database authentication.
- `password`: The password for database authentication.

### 4. `MySQLChinook` (in `Mysql.py`)

This class handles connections to a MySQL database.

#### Input Parameters

- `host`: The database server host.
- `username`: The username for database authentication.
- `password`: The password for database authentication.
- `database`: The name of the database to connect to.
- `port`: The port number for the database connection (default: `3306`).
- `isDummy`: A boolean indicating whether to set up a dummy database.

### 5. `oracle_db_connection` (in `oracle.py`)

This class handles connections to an Oracle database.

#### Input Parameters

- `username`: The username for database authentication (default: `"ADMIN"`).
- `password`: The password for database authentication (default: `"Culindadbmagix@28"`).
- `connection_string`: The connection string for the Oracle database.

### 6. `sqlite_chinook` (in `sqlite_chinook.py`)

This class handles connections to a SQLite database.

#### Input Parameters

- `db_file`: The path to the SQLite database file (default: `"sqlite_3_chinook.db"`).

## Usage

Each class provides methods to:

- **Connect** to the database.
- **Query** the database.
- **Retrieve** the database schema.
- **Verify** the setup of the database.
- **Close** the connection.

These classes are utilized in the `db_router.py` file to handle API requests related to database operations.

