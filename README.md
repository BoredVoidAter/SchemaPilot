# SchemaPilot

SchemaPilot is a command-line utility designed to streamline interaction with local development databases. It enables developers to easily explore database schemas, view table structures, inspect sample data, and generate basic SQL migration scripts directly from the terminal. The tool supports popular relational databases like SQLite, PostgreSQL, and MySQL. It aims to simplify database exploration and basic schema management, reducing the need for heavy GUI clients during development workflows.

## Usage

To use SchemaPilot, navigate to the project root directory and run the `main.py` script. Below are the basic commands:

### 1. Add a new database connection profile

```bash
python src/schemapilot/main.py add --name <profile_name> --type <db_type> --host <host> --port <port> --user <user> --password <password> --db_name <db_name>
```

Example:
```bash
python src/schemapilot/main.py add --name my_local_db --type postgresql --host localhost --port 5432 --user admin --password secret --db_name dev_db
```

### 2. Use an existing database connection profile

```bash
python src/schemapilot/main.py use --name <profile_name>
```

Example:
```bash
python src/schemapilot/main.py use --name my_local_db
```

### 3. Show database schema

```bash
python src/schemapilot/main.py schema
```

### 4. Inspect table data

```bash
python src/schemapilot/main.py inspect --table <table_name> [--limit <number_of_rows>] [--filter <json_filters>]
```

Example:
```bash
python src/schemapilot/main.py inspect --table users --limit 5 --filter '{"status": "active"}'
```

### 5. Suggest migration script

```bash
python src/schemapilot/main.py migrate --operation <operation_type> --table <table_name> [--column_details <json_column_details>]
```

Example (add column):
```bash
python src/schemapilot/main.py migrate --operation add_column --table products --column_details '{"name": "price", "type": "DECIMAL(10, 2)"}'
```
