# Day 2 Learning Journal — 14 June 2026

## Topics Covered

Today I continued reading **Fundamentals of Data Engineering** and studied the topic:

**Evolution of Data Engineering**

I also revised several PostgreSQL concepts, including:

* Databases
* Schemas
* Tables
* Data Types
* Primary Keys
* Foreign Keys
* Unique Constraints
* NOT NULL Constraints
* SQL Command Categories

---

# Evolution of Data Engineering

One of the key lessons from today's reading is that Data Engineering did not emerge overnight. The role evolved alongside the growth of data systems and business needs.

## 1. Data Warehousing Era (1980s–1990s)

The roots of Data Engineering can be traced back to the rise of data warehouses and business intelligence systems.

Organizations began collecting large amounts of business data and needed dedicated systems for:

* Reporting
* Analytics
* Business Intelligence (BI)

During this period, roles such as:

* ETL Developer
* BI Engineer
* Data Warehouse Engineer

began to emerge.

These roles laid the foundation for what we now call Data Engineering.

---

## 2. Big Data Era (2000s–2010s)

As internet companies such as Google, Yahoo, and Amazon experienced explosive growth, traditional databases struggled to handle increasing volumes of data.

New technologies emerged, including:

* Hadoop
* MapReduce
* Spark
* Cassandra
* HBase

This period introduced the concept of **Big Data**, characterized by:

* Volume
* Velocity
* Variety

Data Engineers were responsible for managing large-scale distributed systems and processing massive datasets.

---

## 3. Modern Data Engineering Era (2020s–Present)

Modern Data Engineering focuses less on managing complex infrastructure and more on managing the entire data lifecycle.

Today's Data Engineer is often described as a **Data Lifecycle Engineer**.

Modern responsibilities include:

* Data Architecture
* Data Governance
* Security
* Data Quality
* Orchestration
* DataOps
* Data Lifecycle Management

The goal is no longer simply storing large amounts of data but ensuring that data is reliable, accessible, secure, and valuable to the business.

---

# PostgreSQL Revision

Today I refreshed several PostgreSQL concepts that are fundamental to database design.

## Database

A database is a collection of related data organized for efficient storage, retrieval, and management.

Example:

```text
xaqiiji_db
```

---

## Schema

A schema is a logical namespace inside a database used to organize database objects.

Example:

```sql
CREATE SCHEMA identity;
```

Instead of placing everything inside the default `public` schema, schemas help organize related tables.

Example:

```text
identity.users
identity.organizations
```

---

## Primary Key

A Primary Key uniquely identifies each row in a table.

Example:

```sql
id UUID PRIMARY KEY
```

Characteristics:

* Unique
* Cannot be NULL
* One primary key per table

Purpose:

Allows records to be uniquely identified and referenced.

---

## Foreign Key

A Foreign Key creates a relationship between two tables.

Example:

```sql
organization_id UUID NOT NULL,

FOREIGN KEY (organization_id)
REFERENCES organizations(id)
```

Purpose:

Ensures that a user can only belong to an organization that already exists.

This helps maintain data integrity.

---

## Unique Constraint

The UNIQUE constraint prevents duplicate values.

Example:

```sql
email VARCHAR(255) UNIQUE
```

Purpose:

Ensures that no two records can share the same email address.

Common use cases:

* Email addresses
* Phone numbers
* Registration numbers
* National IDs

---

## NOT NULL Constraint

The NOT NULL constraint makes a field mandatory.

Example:

```sql
first_name VARCHAR(100) NOT NULL
```

Purpose:

Prevents records from being created without required information.

---

# SQL Command Categories

SQL commands are grouped into categories based on their purpose.

## 1. DDL — Data Definition Language

DDL is used to define and modify the structure of database objects.

Commands:

```sql
CREATE
ALTER
DROP
TRUNCATE
```

Examples:

```sql
CREATE TABLE users (...);

ALTER TABLE users ADD COLUMN phone VARCHAR(20);

DROP TABLE users;

TRUNCATE TABLE users;
```

### Note

`TRUNCATE` removes all rows from a table but keeps the table structure intact.

---

## 2. DML — Data Manipulation Language

DML is used to modify data stored inside tables.

Commands:

```sql
INSERT
UPDATE
DELETE
```

Examples:

```sql
INSERT INTO users (...);

UPDATE users
SET first_name = 'Ahmed';

DELETE FROM users
WHERE id = '123';
```

---

## 3. DQL — Data Query Language

DQL is used to retrieve data from the database.

Command:

```sql
SELECT
```

Example:

```sql
SELECT *
FROM users;
```

Joins are commonly used in DQL because they help retrieve data from multiple related tables.

---

## 4. DCL — Data Control Language

DCL manages user permissions and access control.

Commands:

```sql
GRANT
REVOKE
```

Examples:

```sql
GRANT SELECT ON users TO analyst;

REVOKE SELECT ON users FROM analyst;
```

Purpose:

Controls who can access and modify database resources.

---

## 5. TCL — Transaction Control Language

TCL manages database transactions and ensures data consistency.

Commands:

```sql
BEGIN
COMMIT
ROLLBACK
SAVEPOINT
```

Purpose:

Ensures that a group of related operations either:

* All succeed
* Or all fail

This is critical for maintaining data integrity.

Example:

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 100
WHERE id = 1;

UPDATE accounts
SET balance = balance + 100
WHERE id = 2;

COMMIT;
```

If any operation fails:

```sql
ROLLBACK;
```

The database returns to its previous state.

---

# Key Takeaways

Today I learned that Data Engineering has evolved from traditional data warehouses to modern data lifecycle management.

I also strengthened my understanding of relational database design and SQL command categories.

The most important concepts I reviewed today were:

* Primary Keys
* Foreign Keys
* Unique Constraints
* NOT NULL Constraints
* SQL Command Categories (DDL, DML, DQL, DCL, TCL)

These concepts form the foundation for building reliable and scalable data systems.
