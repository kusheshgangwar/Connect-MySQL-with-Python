# Python + MySQL Database Connection

A simple Python project that demonstrates how to connect a Python application with a MySQL database and perform basic database operations such as **INSERT, SELECT, UPDATE, and DELETE (CRUD)**.

## 📌 Project Overview

This project shows how Python can communicate with a MySQL database using the `mysql-connector-python` library.

### Technologies Used

- **Python**
- **MySQL**
- **MySQL Connector/Python**
- **SQL**

## 📂 Project Structure

```text
Python-MySQL-Project/
│
├── database.py
├── crud.py
├── requirements.txt
└── README.md
```

## ⚙️ Prerequisites

Before running the project, make sure you have:

1. Python installed
2. MySQL Server installed
3. MySQL database created
4. MySQL username and password available

## 📦 Installation

Install the required Python library:

```bash
pip install mysql-connector-python
```

Or install all dependencies using:

```bash
pip install -r requirements.txt
```

## 🗄️ Create Database

Open MySQL and execute:

```sql
CREATE DATABASE college;

USE college;
```

Create a student table:

```sql
CREATE TABLE student (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    age INT,
    city VARCHAR(100)
);
```

## 🔌 Database Connection

Create `database.py`:

```python
import mysql.connector

con = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="college"
)

if con.is_connected():
    print("Database connected successfully!")

con.close()
```

Replace:

```text
your_password
```

with your MySQL password.

## ➕ Insert Data

```python
import mysql.connector

con = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="college"
)

cursor = con.cursor()

sql = """
INSERT INTO student (name, age, city)
VALUES (%s, %s, %s)
"""

values = ("Rahul", 20, "Delhi")

cursor.execute(sql, values)
con.commit()

print("Data inserted successfully!")

cursor.close()
con.close()
```

## 📖 Read Data

```python
cursor.execute("SELECT * FROM student")

data = cursor.fetchall()

for row in data:
    print(row)
```

## ✏️ Update Data

```python
sql = "UPDATE student SET city = %s WHERE id = %s"

values = ("Mumbai", 1)

cursor.execute(sql, values)
con.commit()

print("Data updated successfully!")
```

## ❌ Delete Data

```python
sql = "DELETE FROM student WHERE id = %s"

values = (1,)

cursor.execute(sql, values)
con.commit()

print("Data deleted successfully!")
```

## 🔄 CRUD Operations

| Operation | SQL Command | Python Method |
|---|---|---|
| Create | `INSERT` | `cursor.execute()` |
| Read | `SELECT` | `fetchone()` / `fetchall()` |
| Update | `UPDATE` | `cursor.execute()` |
| Delete | `DELETE` | `cursor.execute()` |

## ▶️ How to Run

### Step 1: Clone or download the project

```bash
git clone <your-repository-url>
```

### Step 2: Open the project folder

```bash
cd Python-MySQL-Project
```

### Step 3: Install dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Configure MySQL

Update the following information in your Python file:

```python
host="localhost"
user="root"
password="your_password"
database="college"
```

### Step 5: Run the Python program

```bash
python database.py
```

## 📋 Example Output

```text
Database connected successfully!
Data inserted successfully!
Data updated successfully!
Data deleted successfully!
```

## 🔐 Security Note

Do not upload your actual MySQL password to GitHub.

For real projects, store sensitive information such as database credentials in environment variables instead of directly writing them in Python files.

## 🎯 Learning Outcomes

After completing this project, you will understand:

- How Python connects to MySQL
- How to create a database connection
- How to execute SQL queries from Python
- How to insert data
- How to retrieve data
- How to update records
- How to delete records
- How CRUD operations work
- How Python and databases communicate

## 👨‍💻 Author

**DeveloperWala**

Python & Data Analytics Project

---

⭐ If you found this project useful, consider giving it a star on GitHub.
