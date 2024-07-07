## Datatypes
**INT**
``INT(11)`` : Specifies the number of numbers given in this case eleven
**BIGINT**
``BIGINT``
Storing large numbers
**FLOAT**
``FLOAT``
Storing decimal numbers.
``DOUBLE``
Store large decimal numbers
**UNSIGNED**
takes only positive numbers

**VARCHAR**
``VARCHAR()``
By default it is given the default value of 1.
``VARCHAR(11)``
Accepts maximum of 11 characters
``VARCHAR(255)``
Accepts maximum characters of 255
the varchar is mostly used for usernames, password

**TEXT**
The text data type is used to insert a paragraph or several lines of statements such as recommendation, blogs.

**DATE**
**DATETIME**


## Creating a table
```
CREATE TABLE tableName(
	id INT(11) NOT NULL AUTO_INCREMENT,
);
```
To create a table select the database first, follow the above syntax.
**Creating columns**
for creating columns syntax identified is :
``columnName datatype limit <other options>``

```
CREATE TABLE usersdetails(
	id INT(11) NOT NULL AUTO_INCREMENT,
	username VARCHAR(50) NOT NULL, 
	email VARCHAR(100) NOT NULL, 
	pwd VARCHAR(255) NOT NULL,
	created_at DATETIME NOT NULL DEFAULT CURRENT_TIME
);
```

``created_at DATETIME NOT NULL DEFAULT "0000-00-00 00-00-00``
The above is used to assign the default time and date if the user does not enter the date and time the account is created.
``created_at DATETIME NOT NULL DEFAULT CURRENT_TIME, ``
Using the ``CURRENT_TIME`` enables the ``date [YYYY-MNTH-DAY] [HH:MIN:SEC]``

Using  the ``CURRENT TIME`` takes the current time of the server for the user.

**Primary key**
To declare a primary key, one can use either of the 2 options. 
*OPTION 1*
```
CREATE TABLE student(
	id INT(30) NOT NULL PRIMARY KEY
);
```

*OPTION 2*
```
CREATE TABLE student(
	id INT(30) NOT NULL, 
	PRIMARY KEY (id)
);
```

option 1 is preferred.


## INSERTING DATA INTO TABLES
Syntax
```
INSERT INTO TABLE_NAME("column_name") VALUES ("")
```

**inserting into ``usersdetails`` table**
```
INSERT  userdetails(username, email, pwd) VALUES ('mulati davidson', 'mulati@gmail.com', 'MUL123lati');
```

## UPDATING DATA INTO YOUR TABLE
```
UPDATE tableName SET columnName = 'value', columnName = 'value' WHERE id = value 
```

For updating multiple values and giving multiple specifications 
```
UPDATE tableName SET columnName = 'value', columnName = 'value' WHERE id = value 
```
Also one can specify several option for updating the value and also for the specific user.
```
UPDATE userdetails SET username = 'Polo g', email = 'Polog@gmail.com' WHERE id=1 AND username = 'mulati davidson';
```


## DELETING DATA FROM DATABASE
Syntax for deleting data from a database
```
DELETE FROM tableName WHERE id = value;
```

``ON DELETE CASCADE``

## FOREIGN KEY
To declare a foreign key :
```
CREATE TABLE comments (
	id INT (10) NOT NULL AUTO INCREMENT PRIMARY KEY,
	userdetails_id;
	FOREIGN KEY (userdetails_id) REFERENCES userdetails
);
```

## SELECTING DATA FROM TABLE
Syntax used in selecting data from a Table:
```
SELECT columnName, columnName FROM tableName WHERE id = value;
```

Example from ``userdetails`` table:
```
SELECT username, email FROM userdetails WHERE id = 1;
```

***to select everything use the following syntax***
```
SELECT * FROM userdetails WHERE id = 4;
```