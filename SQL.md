# SQL:

### JOINS: Joins data between two tables

```sql
SELECT * // select all columns
FROM martian // from what table (left table)
INNER JOIN base // defines the table to join to (right table)
ON martian.base_id = base.base_id // on what key are you joining
```

INNER: returns only records with matching rows in each column

LEFT: returns every row from the left table even if no match exists in the right table

RIGHT: returns every row from the right table even if there is no match in the left table

FULL (also called OUTER JOIN): returns every row from both tables regardless if they have a match in the other table

![https://i.redd.it/dyqnzpuddxk21.png](https://i.redd.it/dyqnzpuddxk21.png)

### INDEX:

- Creates an index reference to a column to speed up queries
- Takes quite a long time to create
- Indexes only affect queries which involve the indexed column
- Indexes are not free they requires storage and increase the time to insert records involving the indexed columns
- The order matters for multi-column indexes

```sql
// single column index
CREATE INDEX person_first_name_idx
ON person (first_name);

//multi-column index
CREATE INDEX person_firstname_lastname_idx
ON person (last_name, first_name);
```

### VIEWS:

Allow you to create a queryable subset of tables

easy way to summarize complex selects for reusability

```sql
CREATE VIEW martian_view AS
SELECT martian_id, first_name, last_name
FROM martian

Select * from martian_view // only returns columns included in the view not others
```

### **Primary Keys**

A primary is a single column value used to identify a database record uniquely.

It has following attributes

- A primary key cannot be NULL
- A primary key value must be unique
- The primary key values should rarely be changed
- The primary key must be given a value when a new record is inserted.

### Foreign Keys

Foreign Key references the primary key of another Table! It helps connect your Tables

- A foreign key can have a different name from its primary key
- It ensures rows in one table have corresponding rows in another
- Unlike the Primary key, they do not have to be unique. Most often they aren't
- Foreign keys can be null even though primary keys can not

### **Composite Keys**

- A composite key is a primary key composed of multiple columns used to identify a record uniquely
- In a database you could have two people with the same name Robert Phil, but they live in different places.
- It's better to have an id to identify individuals (see normalization below)
- Not recommended in NF2

### Cardinality:

the numerical relationship between rows of one table and row in the other

### **Normalization:**

A database design technique that reduces data redundancy and eliminates undesirable characteristics like Insertion, Update and Deletion Anomalies. Normalization rules divides larger tables into smaller tables and links them using relationships. The purpose of Normalization in SQL is to eliminate redundant (repetitive) data and ensure data is stored logically.

1NF (First Normal Form):

- Each Record should be unique
- Each cell should be atomic (indivisible)

2NF (Second Normal Form)

- 1NF + Single Column Primary keys (no composite)

3NF (Third Normal Form):

- 1NF + 2NF + Has no transitive functional dependencies

**What are transitive functional dependencies?**

A transitive functional dependency is when changing a non-key column, might cause any of the other non-key columns to change

### Other Commands:

```sql
create database Customer; // create database

use Customer; // switch to database

create table Customer
(
	FistName varchar(50),
	LastName varchar(50),
	Age int
); // create table

alter table Customer ADD city varchar(50); // add column to table

alter table Customer DROP COLUMN age; // remove column from table

INSERT INTO Customer (FistName, LastName) VALUES ('Peter', 'Little'); // insert record

SELECT * From Customer; // select all columns

Select FirstName From Customer; // select just firstname

Select FirstName From Customer ORDER BY Firstname; // sort result

Select FirstName From Customer ORDER BY Firstname DESC; // sort descending result

Update Customer SET FirstName = 'jimmy' Where FirstName = 'Peter'; // Update a record

Delete From Customer Where FirstName = 'jimmy'; // delete a record;

//Combine two queries
SELECT martian_id, 'Martian' AS status // AS to create your own field
FROM martian
	UNION
SELECT visitor_id, 'Visitor' AS status
FROM visitor

```