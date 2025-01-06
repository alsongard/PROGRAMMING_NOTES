install Xampp server and start both MySQL and Apache.
Install the following in your python environment:
```
python3 -m venv folderName
cd foldername
source bin/activate
python3 -m pip install mysql-connector
```
preferred installer program : pip

**Python mysql connector modules:**
1. connect() : used to establish a connection with mysql server. It takes 3 or 4 arguments namely:
	   - database name: name of database. Example = books
	   - user :  root or name of user
	   - password : password associated with the username for authentication
2. Cursor(): The cursor is a system memory that is set aside when executing SQL commands. It is temporary and the cursor connection is bounded for the entire session.
3. Execute() : takes an sql query and executes it. A query is a command that is used to create, insert, delete, retrieve or update data from the database.

Python Database API(application program interface) is a database interface for python that supports various database management system.

Remember the first steps:
```
import mysql.connector

database = mysql.connector.connect(
	host = "localhost",
	user = "root",
	password = "",
)

# create cursor object
dbCursor = database.cursor()

dbCursor.execute("CREATE DATABASE software")
print("software database has been created")
```
Run file: ``python3 filename``

**Creating a table**
```
import mysql.connector

database = mysql.connector.connect(
	host = "localhost",
	user = "root",
	password = "",
	database = "software"
)

dbCursor = database.cursor()
tableQuery = """
		CREATE TABLE employee(
			id INT NOT NULL,
			fullname VARCHAR(255) NOT NULL,
			age INT NOT NULL,
			location VARCHAR(255), 
			phone_number INT NOT NULL
		)
	
"""
dbCursor.execute(tableQuery)
database.close()

```