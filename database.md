
# WEEK ONE DB
## 🖥️ Part 1: Using MySQL Workbench (a.k.a. Click & Code Mode 🖱️)

 🌀 **Step 1: Open Workbench & Connect:**
   - Open MySQL Workbench
   - Connect to your local database server

🧱 **Step 2: Create Your Database:**
  - Go to the SQL Editor
  - Paste this SQL command:
     
```sql
CREATE DATABASE <your_cool_database_name>;
```
- Click the ⚡ Execute button.

🔍 **Step 3: View Your Database:**
   - Refresh the Schemas section on the left
   - Find your database name there

💥 **Step 5: Drop a Database (Carefully):**
```bash
DROP DATABASE <your_cool_database_name>;
```
 _📣 Ask before running: Are you sure you want to delete it?_

## 💻 Part 2: Using the Terminal (a.k.a. Hacker Mode 😎)

🪄 **Step 1: Log in to MySQL:**
```bash
mysql -u root -p
```
_📌 Tip: type it in confidently_

🏗️ **Step 2: Create a New Database:**
```bash
CREATE DATABASE <your_cool_database_name>;
```
_🎉 Be creative with the name,Some fun ideas: school, journal, adventure._

👀 **Step 3: Check if It’s There:**
```bash
SHOW DATABASES;
```
_🕵️‍♂️ Can you find yours in the list?_

🎯 **Step 4: Start Using It:**
```bash
USE <your_cool_database_name>;
```
_💡 This tells MySQL, “Hey, I’m working on this one now."_

⚠️ **Step 5: Drop (Delete) a Database:**
```bash
DROP DATABASE <your_cool_database_name>;
```
_🚨 Warning: This command permanently deletes the database and everything inside it._



# WEEK 2 DB



## 🎯 Hands-on Class Activity: Let’s Build a Database Together
_Today’s mission: Create and explore a database, perform CRUD operations using both Terminal and MySQL Workbench._

#### CREATE TABLE Statement Example
```bash
CREATE TABLE tasks (
    id INT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    start_date DATE,
    due_date DATE
);
```
**another example.....**
```bash
CREATE TABLE contacts(
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(320) NOT NULL
);
```
**insert data**
```bash
INSERT INTO contacts(name, email)
VALUES('Jonte', 'john@mail.com');
```
**Fetch Data**

```bash
SELECT * FROM contacts;
```
### Defining a structured customer table with various data types.
```bash
CREATE TABLE customers (
    id CHAR(36) PRIMARY KEY DEFAULT (UUID()),
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(20),
    address TEXT,
    date_of_birth DATE,
    signup_timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
#### Viewing Table Structure
🔍 **Step 2: Inspect What You Created**

Let’s peek under the hood and see the table structure.
```bash
DESCRIBE customers;
```
**This helps you confirm all columns were created properly**
```bash
SHOW COLUMNS FROM customers;
```
**Inserting data**

Time to bring your table to life. Let’s add some sample customers, feel free to come up with your own names if you're feeling creative.

```bash
INSERT INTO customers (name, email, phone, address, date_of_birth)
VALUES
('Alice', 'alice.kimani@example.com', '+254723478', 'Nairobi', '1995-08-10');

INSERT INTO customers (name, email, phone, address, date_of_birth)
VALUES
('Brian', 'brian.otieno@example.com', '+2548765432', 'Kisumu', '1990-02-25');

INSERT INTO customers (name, email, phone, address, date_of_birth)
VALUES
('Carol', 'carol.wanjiku@example.com', '+25434567', 'Mombasa', '1988-12-15');

```
### 📦 Bonus: Check Your Data
```bash
SELECT * FROM customers;
```

> 💬 Challenge: Try inserting your own data with your name. Change the values be creative.


## ✅ Altering Tables
Modifying table after creation.

**Adding Columns**

Use the **ALTER TABLE** statement to add a new column to an existing table.
```bash
ALTER TABLE customers
ADD COLUMN paid BOOLEAN DEFAULT FALSE;
```
**Dropping Columns**

You can remove a column from a table using the **ALTER TABLE** statement.
```bash
ALTER TABLE customers
DROP COLUMN paid;
```

**Modifying Data Types**

Change the data type of an existing column with the ALTER TABLE statement.
```bash
ALTER TABLE customers
MODIFY COLUMN address VARCHAR(20);
```
**Renaming Columns**

You can rename a column using the **ALTER TABLE** statement.
```bash
ALTER TABLE customers
CHANGE COLUMN old_column_name new_column_name VARCHAR(50);
```
**Adding Constraints - Primary Key**

To add a primary key to an existing table, you can use the **ALTER TABLE** statement with the ADD PRIMARY KEY clause.
```bash
ALTER TABLE table_name
ADD PRIMARY KEY (column_name);
```
**Remove a Primary Key Constraint:**
```bash
ALTER TABLE your_table_name 
DROP PRIMARY KEY;
```
## RENAME a table

The **RENAME** command only applies to changing the table's name
```bash
RENAME TABLE old_table_name TO new_table_name;
```
## Delete all rows

Use the **TRUNCATE TABLE** statement to delete all rows from a table efficiently.
```bash
TRUNCATE TABLE customers;
```

## Deleting Tables
Use the **DROP TABLE** statement to delete an existing table and all its data.
```bash
DROP TABLE customers;  
```


### 🧪 Load a Sample Database
If you’ve downloaded a [sample SQL](https://drive.google.com/file/d/1ClfnXsCfg5OnB7aLsS3zjaPSBo66YApM/view?usp=sharing) file (e.g. salesDB.sql), here’s how to load it:
1. Make sure you know where the file is saved on your computer.
2. In your terminal, run:
```bash
mysql -u root -p < salesDB.sql
```
3. Then open MySQL and run:
```bash
USE salesDB;
SHOW TABLES;
```
_🔍 Voilà! You should see the tables loaded from the file._




## DML Commands
**UPDATE command**
You can modify data in an existing table using the UPDATE command

```bash
UPDATE employees 
SET 
    email = 'jane@mail.com'
WHERE
    employeeNumber = 1056;
```

**UPDATE to modify values in multiple columns**

To update values in the multiple columns, you need to specify the assignments in the SET clause. 

```bash
UPDATE employees 
SET 
    lastname = 'alice',
    email = 'jane@mail.com'
WHERE
    employeeNumber = 1056;
```
**Using UPDATE to replace string example**
```bash
UPDATE employees
SET email = REPLACE(email,'@classicmodelcars.com','@mycars.org')
WHERE
   jobTitle = 'Sales Rep' AND
   officeCode = 6;
```
**DELETE command**

DELETE allows you to remove data from your table.

**Basic Deletion**
```bash
-- Delete all records from the customers table
DELETE FROM customers;
```
**Conditional Deletion**
```bash
-- Delete records where email is 'alice@example.com'
DELETE FROM customers
WHERE email = 'alice@example.com';
```
## Order By
To sort the rows in the result set, you add the **ORDER BY** clause to the SELECT statement.

If you want to sort customers by the last name in descending order.

```bash
SELECT 
  contactLastname, 
  contactFirstname 
FROM 
  customers 
ORDER BY 
  contactLastname DESC;
```
**Selecting a random employee**
```bash
SELECT 
    employeeNumber
FROM
    employees
WHERE
    jobtitle = 'Sales Rep'
ORDER BY RAND()
LIMIT 1;
```



# WEEK 3 DB



## 🎯 Hands-on Class Activity

To Mark the beginning of a transaction
```sql
START TRANSACTION
```
Apply the changes of a transaction to the database.
```sql
COMMIT
```
Undo the changes of a transaction by reverting the database to the state before the transaction starts.
```sql
ROLLBACK
```
To instruct MySQL to not start a transaction implicitly and commit the changes automatically
```sql
SET autocommit = OFF;
```
### Transactions example
```sql
CREATE DATABASE stadium;
USE stadium;
CREATE TABLE users (
    id INT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    email VARCHAR(255)
);
```
### COMMIT Example
```sql
START TRANSACTION;

INSERT INTO users (id, username) 
VALUES (1, 'peter');

UPDATE users 
SET email = 'peter@mail.com' 
WHERE id = 1;
COMMIT;
```
Select data from the users table
```sql
SELECT * FROM users;
```
### ROLLBACK Example
```sql
START TRANSACTION;
INSERT INTO users (id, username) 
VALUES (2, 'sharon');

UPDATE users 
SET email = 'sharon@mail.com' 
WHERE id = 2;
ROLLBACK;
```
Select data from the users table
```sql
SELECT * FROM users;
```
### Aggregate Functions
**AVG() function** calculates the average value of a set of values
```sql
SELECT 
    AVG(buyPrice) avg_buy_price
FROM 
    products;
```
**COUNT() function** function returns the number of the values in a set.
```sql
SELECT 
    COUNT(*) AS total
FROM 
    products;
```
**SUM() function** returns the sum of values in a set.
```sql
SELECT 
    productCode, 
    SUM(priceEach * quantityOrdered) total
FROM
    orderDetails
GROUP BY productCode
ORDER BY total DESC;
```
**MAX() function** returns the maximum value in a set.
```sql
SELECT 
     MAX(buyPrice) highest_price
FROM 
     products;
```
**MIN() function** returns the minimum value in a set of values
```sql
SELECT 
    MIN(buyPrice) lowest_price
FROM 
    products;
```
### GROUP BY Examples
To group the order statuses:
```sql
SELECT 
  status 
FROM 
  orders 
GROUP BY 
  status;
```
To obtain the number of orders in each status:
```sql
SELECT 
  status, 
  COUNT(*) 
FROM 
  orders 
GROUP BY 
  status;
```
To get total amount of each order:
```sql
SELECT 
  orderNumber, 
  SUM(quantityOrdered * priceEach) AS total 
FROM 
  orderdetails 
GROUP BY 
  orderNumber;
```
#### HAVING Clause
Allows you to apply a condition to the groups returned by the GROUP BY clause and only include groups that meet the specified condition.
To find which order has total sales greater than 1000:
```sql
SELECT 
  ordernumber, 
  SUM(quantityOrdered) AS itemsCount, 
  SUM(priceeach * quantityOrdered) AS total 
FROM 
  orderdetails 
GROUP BY 
  ordernumber 
HAVING 
  total > 1000;
```
# WEEK 4 DB



## 🎯 Hands-on Class Activity
### 🚀 Speeding up Queries with Indexes
First, try running this query without an index:
```sql
SELECT 
    employeeNumber, 
    lastName, 
    firstName
FROM
    employees
WHERE
    jobTitle = 'Sales Rep';
```
Use the **CREATE INDEX** statement to create a new index for a table.

Now create an index to make the search faster:
```sql
CREATE INDEX idxTitle ON employees(jobTitle);
```
Check if the index was created:
```sql
SHOW INDEXES FROM employees;
```
Test the performance plan:
```sql
EXPLAIN SELECT 
    employeeNumber, 
    lastName, 
    firstName
FROM
    employees
WHERE
    jobTitle = 'Sales Rep';
```
### 🗑️ MySQL DROP INDEX statement
Use the **DROP INDEX** statement to remove an existing index.
```sql
DROP INDEX idxTitle ON employees;
```

### 👤 MySQL CREATE USER statement
To create a new user in the MySQL database, you use the **CREATE USER** statement.

Let’s create a new user:
```sql
CREATE USER jontefresh@localhost IDENTIFIED BY '1234';
```
To show the users on the current MySQL Server:
```sql
SELECT user FROM mysql.user;
```
### 🔑 Change MySQL User Password
To change the password of the a user use the **ALTER** … IDENTIFIED BY statement
```sql
ALTER USER jontefresh@localhost IDENTIFIED BY 'abcd'; -- new password
```
### ✏️ MySQL RENAME USER statement
The **RENAME USER** statement allows you to rename one or more existing user accounts.
```sql
RENAME USER 'jontefresh'@'localhost' TO 'john'@'localhost';
```
### 🗑️ MySQL DROP USER statement
To remove a user account from the MySQL Server, you use the **DROP USER** statement as follows:
```sql
DROP USER john@localhost;
```
### 🛡️ MySQL GRANT statement
You use the **GRANT** statement to assign one or more privileges to a user account.

**Global Privileges**

To grant all privileges in all databases in the current database server
```sql
GRANT ALL ON *.* TO jontefresh@localhost;
```
To show the privileges assigned to jontefresh
```sql
SHOW GRANTS FOR jontefresh@localhost;
```
**Database Privileges**

Apply to all objects within a specific database (all tables, views, etc. in that database).
```sql
-- create a new user
CREATE USER mercy@localhost IDENTIFIED BY '1234';
-- giving access to one database only
GRANT SELECT, INSERT, UPDATE, DELETE ON salesdb.* TO 'mercy'@'localhost';
```
**Table Privileges**

Apply to specific tables within a database.
```sql
-- create a new user
CREATE USER gerald@localhost IDENTIFIED BY '1234';
-- giving access to only one table inside the database.
GRANT SELECT, INSERT ON salesdb.customers TO 'gerald'@'localhost';
```
### 🎭 MySQL Roles

MySQL database server may have multiple users with the same set of privileges.

A **role** is essentially a named collection of privileges.
#### Roles in the Coffeehouse
Your coffeehouse has different teams:
- 👩‍💻 Developers (dev)
- 📊 Accounts team (accounts)
- ☕ Baristas (barista)
```sql
CREATE DATABASE coffeehouse;
USE coffeehouse;
CREATE TABLE customers(
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(255) NOT NULL, 
    last_name VARCHAR(255) NOT NULL, 
    phone VARCHAR(15) NOT NULL,
    email VARCHAR(255) UNIQUE,
    amount DECIMAL(10,2) CHECK(amount>0)
);
INSERT INTO customers(first_name,last_name,phone,email,amount)
VALUES
('James','brown','123456','james@mail.com',300),
('Michael','white','123789','white@mail.com',150),
('Mary','smith','123789','smith@mail.com',150),
('Louis','peters','123789','peters@mail.com',1100),
('Brenda','audrey','123789','audrey@mail.com',1200);
SELECT * FROM customers;
```
**Let’s create roles:**
```sql
CREATE ROLE dev, accounts, barista,interns;
```
**Grant privileges to each role:**

The following statement grants all privileges to dev role:
```sql
GRANT ALL ON coffeehouse.* TO dev;
```
The following statement grants **INSERT**, **UPDATE**, and **DELETE** privileges to accounts role
```sql
GRANT INSERT, UPDATE, DELETE ON coffeehouse.* TO accounts;
```
The following statement grants **SELECT** privilege to barista role
```sql
GRANT SELECT ON cofeehouse.* TO barista;
```
### Assigning roles to user accounts
```sql
-- developer user 
CREATE USER henry@localhost IDENTIFIED BY 'pass';

-- read access user
CREATE USER wayne@localhost IDENTIFIED BY 'pass';
CREATE USER testuser@localhost IDENTIFIED BY 'pass';     

-- read/write users
CREATE USER brenda@localhost IDENTIFIED BY '1234';   
CREATE USER ann@localhost IDENTIFIED BY '1234';
```
To verify the role assignments:
```sql
SHOW GRANTS FOR henry@localhost;
```
**Assigning Permission to users using ROLES**
```sql
GRANT dev TO henry@localhost;
GRANT  accounts TO brenda@localhost;
GRANT barista TO wayne@localhost;
```
**Setting default roles**

To specify which roles should be active each time a user account connects to the database server, you can use the SET DEFAULT ROLE statement.
```sql
SET DEFAULT ROLE ALL TO testuser@localhost;
```
**Revoking privileges from roles**
```sql
REVOKE INSERT, UPDATE, DELETE  ON crm.* FROM accounts;
```
**Removing roles**
To delete one or more roles, you use the DROP ROLE statement:
```sql
DROP ROLE barista;
```
### ❌ MySQL REVOKE statement

The **REVOKE** statement revokes one or more privileges from a user account.
```sql
REVOKE ALL, GRANT OPTION FROM jontefresh@localhost;
```
#### revoke privileges from a user
```sql
-- create a new user 
CREATE USER tamara@localhost IDENTIFIED BY '1234';
-- grant privilege
GRANT SELECT, UPDATE, INSERT ON salesdb.* TO tamara@localhost;
-- display the granted privileges
SHOW GRANTS FOR tamara@localhost;
-- revoke privilege
REVOKE INSERT, UPDATE ON salesdb.* FROM  tamara@localhost;
```
# WEEK 5 DB


## 🎯 Hands-on Class Activity
_Your mission today as a junior database administrator is to explore how employees, projects, and addresses are connected._

You’ll use different types of **JOINs** to uncover hidden stories inside the database.
### 🚀 Joins and Relationships
#### 📚 Relationships in MySQL
In databases, relationships describe how tables are connected.
##### 1️⃣ One-to-One
One row in Table A is linked to exactly one row in Table B.
```sql
USE salesdb;
-- Staff table
CREATE TABLE staff (
  staffId INT PRIMARY KEY,
  FullName VARCHAR(100) NOT NULL
);

-- IDCard table (1:1 with Staff)
CREATE TABLE IDCard (
  CardId INT PRIMARY KEY,
  staffId INT UNIQUE, -- ensures only one card per employee
  IssueDate DATE,
  FOREIGN KEY (staffId) REFERENCES staff(staffId)
);

-- Insert sample data
INSERT INTO staff VALUES (1, 'Brian Otieno'), (2, 'Faith Wanjiru');
INSERT INTO IDCard VALUES (101, 1, '2025-01-01'), (102, 2, '2025-01-10');
```
Example join
```sql
-- Inner join
-- Join to see the relationship
SELECT S.FullName, C.CardId, C.IssueDate
FROM staff S
INNER JOIN IDCard C ON S.staffId = C.staffId;
```
##### 2️⃣ One-to-Many

One row in Table A can be linked to many rows in Table B.

Example: One department has many employees.
```sql
-- Department table
CREATE TABLE Department (
  deptId INT PRIMARY KEY,
  deptName VARCHAR(100) NOT NULL
);
-- Employee table (Many employees can belong to one department)
CREATE TABLE Employee (
  empId INT PRIMARY KEY,
  empName VARCHAR(100) NOT NULL,
  deptId INT,
  FOREIGN KEY (deptId) REFERENCES Department(deptId)
);
-- Insert sample data
INSERT INTO Department(deptId,deptName) VALUES (1, 'Finance'), (2, 'IT'),(3,'Marketing');

INSERT INTO Employee(empId,empName,deptid) VALUES 
(101, 'Alice Akinyi', 1),
(102, 'James Kariuki', 1),
(103, 'Kevin Mwangi', 2),
(104,'Mercy James',NULL),
(105,'Alice sanele', NULL);
```
Example join
```sql
-- Join to see the relationship
-- Inner join 
SELECT D.deptName, E.empName
FROM Department D
INNER JOIN Employee E ON D.deptId = E.deptId;
-- Left Join
SELECT E.empName, D.deptName
FROM Employee E
LEFT JOIN Department D ON E.deptId = D.deptId;
-- Right join
SELECT D.deptName, E.empName
FROM Employee E
RIGHT JOIN Department D ON E.deptId = D.deptId;
```
##### 3️⃣ Many-to-Many

One row in Table A can be linked to many rows in Table B, and vice versa.

Example: A book can have many authors, and an author can write many books.

_To implement this, we use a junction table (also called a bridge or linking table)._
```sql
-- Author table
CREATE TABLE Author (
  authorId INT PRIMARY KEY,
  authorName VARCHAR(100) NOT NULL
);

-- Book table
CREATE TABLE Book (
  bookId INT PRIMARY KEY,
  title VARCHAR(100) NOT NULL
);

-- Junction table to represent Many-to-Many
CREATE TABLE BookAuthor (
  bookId INT,
  authorId INT,
  PRIMARY KEY (bookId, authorId),
  FOREIGN KEY (bookId) REFERENCES Book(bookId),
  FOREIGN KEY (authorId) REFERENCES Author(authorId)
);

-- Insert sample data
INSERT INTO Author(authorId,authorName) VALUES (1, 'Ngugi wa Thiong\'o'), (2, 'Chimamanda Adichie'),(3,'Damilare Kuku');
INSERT INTO Book(bookId,title) VALUES (101, 'The River Between'), (102, 'Half of a Yellow Sun'),(103,'Nearly all men in Lagos are Mad');
select * from book;
-- Link authors to books
INSERT INTO BookAuthor(bookId,authorId) VALUES 
(101, 1), -- Ngugi wrote The River Between
(102, 2), -- Chimamanda wrote Half of a Yellow Sun
(102, 1), -- Ngugi also contributed to Half of a Yellow Sun
(103,3); -- Damilare Kuku book
```
Example join
```sql
-- Join to see the relationship
SELECT B.title, A.authorName
FROM Book B
INNER JOIN BookAuthor BA ON B.bookId = BA.bookId
INNER JOIN Author A ON BA.authorId = A.authorId;
```
## Joins
#### 🏗️ Database Setup
We’ve created a simple system with employees, their projects, and where they live.
```sql
CREATE DATABASE safari;
USE safari;

-- Employees table
CREATE TABLE Employee (
  EmployeeId INT PRIMARY KEY,
  FullName VARCHAR(45) NOT NULL,
  Department VARCHAR(45) NOT NULL,
  Salary DECIMAL(10,2) NOT NULL,
  Gender VARCHAR(45) NOT NULL,
  Age INT NOT NULL
);

INSERT INTO Employee (EmployeeId, FullName, Department, Salary, Gender, Age) VALUES 
(1001, 'Brian Otieno', 'IT', 65000, 'Male', 25),
(1002, 'Faith Wanjiru', 'HR', 75000, 'Female', 27),
(1003, 'Peter Mwangi', 'Finance', 80000, 'Male', 28),
(1004, 'Michael Oduor', 'Finance', 82000, 'Male', 29),
(1005, 'Lilian Njeri', 'HR', 90000, 'Female', 26),
(1006, 'Kevin Kimani', 'IT', 67000, 'Male', 24),
(1007, 'Grace Achieng', 'HR', 76000, 'Female', 27),
(1008, 'Samuel Kiptoo', 'IT', 72000, 'Male', 28),
(1009, 'David Abdi', 'IT', 70000, 'Male', 28),
(1010, 'Halima Yusuf', 'HR', 88000, 'Female', 26);

-- Projects table
CREATE TABLE Projects (
 ProjectId INT PRIMARY KEY AUTO_INCREMENT,
 ProjectName VARCHAR(200) NOT NULL,
 EmployeeId INT,
 StartDate DATETIME,
 EndDate DATETIME,
 FOREIGN KEY (EmployeeId) REFERENCES Employee(EmployeeId)
);

INSERT INTO Projects (ProjectName, EmployeeId, StartDate, EndDate) VALUES 
('Develop Mobile App for M-Pesa Agents', 1003, NOW(), DATE_ADD(NOW(), INTERVAL 30 DAY)),
('Build HR Portal for Nairobi County', 1002, NOW(), DATE_ADD(NOW(), INTERVAL 45 DAY)),
('Set Up Servers at Konza Tech City', 1007, NOW(), DATE_ADD(NOW(), INTERVAL 45 DAY)),
('Fix Safaricom Data Center Issues', 1009, NOW(), DATE_ADD(NOW(), INTERVAL 7 DAY)),
('Design Database for County Hospital', 1010, NOW(), DATE_ADD(NOW(), INTERVAL 15 DAY)),
('Develop eCitizen Chatbot', NULL, NOW(), DATE_ADD(NOW(), INTERVAL 10 DAY)),
('Migrate Banking System to Cloud', NULL, NOW(), DATE_ADD(NOW(), INTERVAL 5 DAY)),
('Create E-learning App for Schools', 1004, NOW(), DATE_ADD(NOW(), INTERVAL 30 DAY)),
('Fix Jambojet Online Booking System', 1001, NOW(), DATE_ADD(NOW(), INTERVAL 7 DAY)),
('Build SACCO Loan Management System', 1008, NOW(), DATE_ADD(NOW(), INTERVAL 15 DAY)),
('Develop a Plugin for Local SME', NULL, NOW(), DATE_ADD(NOW(), INTERVAL 10 DAY));

-- Address table
CREATE TABLE Address (
 AddressId INT PRIMARY KEY AUTO_INCREMENT,
 EmployeeId INT,
 Country VARCHAR(50),
 County VARCHAR(50),
 City VARCHAR(50),
 FOREIGN KEY (EmployeeId) REFERENCES Employee(EmployeeId)
);

INSERT INTO Address (EmployeeId, Country, County, City) VALUES 
(1001, 'Kenya', 'Kisumu', 'Kisumu City'),
(1002, 'Kenya', 'Nairobi', 'Westlands'),
(1003, 'Kenya', 'Kiambu', 'Thika'),
(1004, 'Kenya', 'Mombasa', 'Nyali'),
(1005, 'Kenya', 'Nakuru', 'Nakuru Town'),
(1006, 'Kenya', 'Kakamega', 'Kakamega Town');

```
**INNER JOIN clause**

The **INNER JOIN** matches each row in one table with every row in other tables and allows you to query rows that contain columns from both tables.


```sql
-- Write a query to show which employees are currently assigned to projects.
SELECT E.EmployeeId, E.FullName, E.Department, P.ProjectName
FROM Employee E
INNER JOIN Projects P ON E.EmployeeId = P.EmployeeId;
```

**LEFT JOIN clause**

Returns all rows from the left table, irrespective of whether a matching row from the right table exists or not.

```sql
-- Write a query to show who which employee is still waiting for a project assignment.
SELECT E.EmployeeId, E.FullName, E.Department, P.ProjectName
FROM Employee E
LEFT JOIN Projects P ON E.EmployeeId = P.EmployeeId;
```

**RIGHT JOIN clause**

Returns all rows from the right table regardless of having matching rows from the left table or not.

```sql
-- Write a query to find which projects are waiting for staff allocation.
SELECT P.ProjectId, P.ProjectName, E.FullName, E.Department
FROM Employee E
RIGHT JOIN Projects P ON E.EmployeeId = P.EmployeeId;
```

# WEEK 6 DB


