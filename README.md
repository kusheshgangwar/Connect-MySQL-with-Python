# Python MySQL Connection

This project demonstrates how to connect **Python with a MySQL database** using the `mysql-connector-python` library.

## 1. Install MySQL Connector

Open Command Prompt or Terminal and run:

```bash
pip install mysql-connector-python
```

## 2. Connect Python with MySQL

```python
import mysql.connector

con = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="college"
)

print("Database connected successfully!")

con.close()
```

Replace `your_password` with your MySQL password.

## 3. Read Data from MySQL

```python
import mysql.connector

con = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="college"
)

cursor = con.cursor()

cursor.execute("SELECT * FROM student")

data = cursor.fetchall()

for row in data:
    print(row)

cursor.close()
con.close()
```

## 4. Insert Data into MySQL

```python
import mysql.connector

con = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="college"
)

cursor = con.cursor()

sql = "INSERT INTO student (name, age, city) VALUES (%s, %s, %s)"
values = ("Rahul", 20, "Delhi")

cursor.execute(sql, values)
con.commit()

print("Data inserted successfully!")

cursor.close()
con.close()
```

## Basic Connection Flow

```text
Python
   ↓
mysql-connector-python
   ↓
MySQL Server
   ↓
Database
   ↓
Table
   ↓
SQL Queries
```

## Important Functions

| Function | Purpose |
|---|---|
| `mysql.connector.connect()` | Connect Python to MySQL |
| `cursor()` | Create a cursor |
| `execute()` | Execute SQL query |
| `fetchone()` | Get one record |
| `fetchall()` | Get all records |
| `commit()` | Save changes |
| `close()` | Close connection |
