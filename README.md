# SQL README & Cheat Sheet

## Introduction
SQL (Structured Query Language) is used to interact with relational databases. It allows users to create, read, update, and delete (CRUD) data efficiently. 

## Installation
To use SQL, install a database management system (DBMS) such as:
- MySQL
- PostgreSQL
- SQLite
- Microsoft SQL Server

Use a command-line interface (CLI) or a GUI tool like MySQL Workbench, pgAdmin, or DBeaver.

## Cheat Sheet

### Database Operations
```sql
CREATE DATABASE db_name;   -- Create a new database
DROP DATABASE db_name;     -- Delete a database
USE db_name;              -- Select a database to use
SHOW DATABASES;           -- List all databases
```

### Table Operations
```sql
CREATE TABLE table_name (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);                          -- Create a table
DROP TABLE table_name;      -- Delete a table
ALTER TABLE table_name ADD column_name DATATYPE; -- Add a new column
ALTER TABLE table_name DROP COLUMN column_name; -- Remove a column
SHOW TABLES;               -- List all tables
DESCRIBE table_name;       -- Show table structure
```

### Data Manipulation (CRUD)
```sql
INSERT INTO table_name (id, name, age) VALUES (1, 'Alice', 25); -- Insert data
SELECT * FROM table_name;       -- Retrieve all data
UPDATE table_name SET age = 26 WHERE id = 1; -- Update data
DELETE FROM table_name WHERE id = 1; -- Delete data
SELECT COUNT(*) FROM table_name; -- Count rows in a table
```

### Querying Data
```sql
SELECT name, age FROM table_name WHERE age > 20; -- Filter records
SELECT DISTINCT name FROM table_name;  -- Get unique values
SELECT * FROM table_name ORDER BY age DESC; -- Sort records
SELECT * FROM table_name LIMIT 10; -- Limit the number of records
SELECT * FROM table_name WHERE name LIKE 'A%'; -- Pattern matching
```

### Joins
```sql
SELECT A.name, B.salary FROM employees A
JOIN salaries B ON A.id = B.employee_id;  -- Inner Join
SELECT A.name, B.salary FROM employees A
LEFT JOIN salaries B ON A.id = B.employee_id; -- Left Join
SELECT A.name, B.salary FROM employees A
RIGHT JOIN salaries B ON A.id = B.employee_id; -- Right Join
SELECT A.name, B.salary FROM employees A
FULL JOIN salaries B ON A.id = B.employee_id; -- Full Join
```

### Aggregate Functions
```sql
SELECT COUNT(*) FROM table_name;  -- Count rows
SELECT AVG(age) FROM table_name;  -- Average value
SELECT SUM(salary) FROM table_name; -- Sum of values
SELECT MIN(age), MAX(age) FROM table_name; -- Min and Max
```

### Grouping and Filtering
```sql
SELECT age, COUNT(*) FROM table_name GROUP BY age;  -- Group by age
SELECT age, COUNT(*) FROM table_name GROUP BY age HAVING COUNT(*) > 2; -- Filter groups
```

### Indexing
```sql
CREATE INDEX idx_name ON table_name(name);  -- Create an index
DROP INDEX idx_name ON table_name; -- Remove an index
SHOW INDEX FROM table_name; -- Show indexes
```

### Transactions
```sql
START TRANSACTION;  -- Start transaction
UPDATE table_name SET age = 30 WHERE id = 1;
COMMIT;  -- Save changes
ROLLBACK;  -- Undo changes
SAVEPOINT sp1; -- Create a savepoint
ROLLBACK TO sp1; -- Rollback to savepoint
```

### User Management
```sql
CREATE USER 'user1'@'localhost' IDENTIFIED BY 'password';  -- Create a user
GRANT ALL PRIVILEGES ON db_name.* TO 'user1'@'localhost';  -- Grant permissions
REVOKE ALL PRIVILEGES ON db_name.* FROM 'user1'@'localhost';  -- Revoke permissions
DROP USER 'user1'@'localhost'; -- Delete a user
SHOW GRANTS FOR 'user1'@'localhost'; -- Show user privileges
```

### Backup and Restore
```sql
mysqldump -u user -p db_name > backup.sql  -- Backup database
mysql -u user -p db_name < backup.sql  -- Restore database
```

### System Queries
```sql
SHOW VARIABLES LIKE 'version'; -- Check database version
SHOW PROCESSLIST; -- Show active queries
SHOW STATUS; -- Show database status
```

