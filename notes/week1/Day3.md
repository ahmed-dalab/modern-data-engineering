# Day 3 Learning Journal — 15 June 2026

## Reading Progress

Today I continued reading Chapter 1 of *Fundamentals of Data Engineering*.

The main topics covered were:

* Data Engineering Skills and Activities
* Data Maturity
* The Role of Data Engineers
* Business Responsibilities
* Technical Responsibilities
* Programming Languages for Data Engineers
* The Importance of SQL
* Keeping Pace in a Fast-Moving Field

---

# Key Lessons Learned

## Data Engineering Is More Than Technology

One of the most important lessons I learned today is that Data Engineering is not only about building pipelines and moving data.

A Data Engineer must understand the undercurrents of Data Engineering:

* Security
* Data Management
* DataOps
* Data Architecture
* Software Engineering

These areas support the entire Data Engineering lifecycle.

---

## Data Engineering Is a Balancing Act

A Data Engineer constantly balances multiple factors:

* Cost
* Scalability
* Simplicity
* Agility
* Reusability
* Interoperability

The goal is not to build the most complex system but to build the right system for the business.

---

## What Data Engineers Usually Do Not Do

Although Data Engineers work closely with many stakeholders, they typically do not directly:

* Build Machine Learning models
* Create reports and dashboards
* Perform detailed data analysis
* Define business KPIs
* Build end-user applications

However, a Data Engineer should understand these areas well enough to support the people responsible for them.

---

# Data Maturity

Data maturity measures how effectively an organization uses data to create value.

The book introduces three stages of data maturity:

## Stage 1: Starting with Data

Characteristics:

* Small data teams
* Ad hoc reporting
* Limited data infrastructure
* Data Engineers often act as generalists

Main objective:

Build a strong data foundation before attempting advanced analytics or Machine Learning.

A key lesson from this stage is:

> Do not jump into Machine Learning before building reliable data systems.

---

## Stage 2: Scaling with Data

Characteristics:

* Formal data practices
* Growing data teams
* More specialized roles
* Scalable architectures

Main objective:

Create reliable and scalable data systems that support business growth.

---

## Stage 3: Leading with Data

Characteristics:

* Data-driven culture
* Automated pipelines
* Self-service analytics
* Mature governance processes

Main objective:

Use data as a competitive advantage while maintaining strong governance and quality controls.

---

# Background of Data Engineers

One thing I found interesting is that there is no single educational path to becoming a Data Engineer.

Many Data Engineers come from backgrounds such as:

* Software Engineering
* Database Administration
* Data Analysis
* Data Science
* ETL Development

Since I already have a Software Engineering background, I believe this gives me a strong foundation for transitioning into Data Engineering.

---

# Business Responsibilities of a Data Engineer

Technical skills alone are not enough.

A successful Data Engineer must also:

* Communicate effectively
* Gather business requirements
* Understand Agile, DevOps, and DataOps
* Control costs
* Continuously learn

One important lesson is that many data projects fail because of communication issues rather than technology issues.

---

# Technical Responsibilities of a Data Engineer

A Data Engineer is responsible for supporting the entire Data Engineering Lifecycle:

1. Generation
2. Ingestion
3. Storage
4. Transformation
5. Serving

While also considering:

* Security
* Data Management
* DataOps
* Data Architecture
* Orchestration
* Software Engineering

---

# Programming Languages for Data Engineers

The primary languages mentioned in the book are:

## SQL

The most important language for Data Engineering.

Used for:

* Databases
* Data Warehouses
* Data Lakes
* Analytics
* Data Transformation

### Personal Takeaway

SQL is not just a database language.

It is the primary language of modern data systems.

---

## Python

Used for:

* Data processing
* Automation
* Orchestration
* Data Science integration

Popular tools:

* Pandas
* NumPy
* Airflow
* PySpark

---

## Java / Scala

Useful for large-scale data frameworks such as:

* Spark
* Hive
* Druid

---

## Bash

Useful for:

* Linux administration
* Automation
* Scripting

---

# The Unreasonable Effectiveness of SQL

One of the strongest messages in today's reading is that SQL remains the most important language in Data Engineering.

Despite the rise of Big Data technologies, SQL continues to dominate modern data platforms because it is:

* Simple
* Expressive
* Productive
* Scalable

The book strongly suggests that every competent Data Engineer should become highly proficient in SQL.

---

# Keeping Pace with Technology

The data field changes rapidly.

The book's advice is:

> Focus on fundamentals while staying aware of new developments.

Technologies may change, but fundamental concepts such as:

* Data Modeling
* Data Architecture
* SQL
* Software Engineering
* Distributed Systems

remain valuable for many years.

---

# Personal Reflection

Today's reading reinforced my belief that starting with Data Engineering before Data Science and Machine Learning is the right path.

The book repeatedly emphasizes the importance of building strong data foundations before attempting advanced analytics or AI projects.

As someone coming from a Software Engineering background, I can see how many of my existing skills transfer directly into Data Engineering, particularly database design, system architecture, and software development.


# SQL Practice & Database Design

After completing the reading portion, I spent time practicing PostgreSQL fundamentals. The objective was to reinforce the concepts learned during Day 1 and Day 2 while becoming comfortable with the most common database operations.

## PostgreSQL Features Practiced

### UUID Generation

I learned how PostgreSQL can automatically generate UUIDs using the `pgcrypto` extension.

```sql
CREATE EXTENSION IF NOT EXISTS pgcrypto;
```

This allows tables to automatically generate globally unique identifiers using:

```sql
gen_random_uuid()
```

instead of manually creating IDs.

### Schema Creation

I created a dedicated schema called `identity`:

```sql
CREATE SCHEMA IF NOT EXISTS identity;
```

This helped me understand that schemas act as logical namespaces for organizing database objects.

Example:

```text
xaqiiji_db
 └── identity
      ├── organizations
      └── users
```

---

## Database Design

### Organizations Table

I designed an `organizations` table containing:

* UUID Primary Key
* Organization Name
* Registration Number
* Email Address
* Active Status
* Creation Timestamp

Concepts reinforced:

* Primary Keys
* Unique Constraints
* NOT NULL Constraints
* Default Values

---

### Users Table

I designed a `users` table containing:

* UUID Primary Key
* Foreign Key to Organizations
* User Details
* Email Address
* Phone Number
* Creation Timestamp

Concepts reinforced:

* One-to-Many Relationships
* Foreign Keys
* Data Integrity
* Referential Integrity

Relationship:

```text
Organization
      │
      ├── User 1
      ├── User 2
      ├── User 3
      └── User N
```

One organization can have many users, while each user belongs to exactly one organization.

---

# CRUD Operations

Today I practiced the four fundamental database operations:

## Create

Using `INSERT` statements to add new organizations and users.

Example:

```sql
INSERT INTO identity.organizations (...)
VALUES (...);
```

Key lesson:

Before data can be analyzed or processed, it must first be created and stored correctly.

---

## Read

Using `SELECT` statements to retrieve records.

Examples:

```sql
SELECT * FROM identity.organizations;

SELECT id, name
FROM identity.organizations;
```

Key lesson:

Reading data is the foundation of reporting, analytics, and business intelligence.

---

## Update

Using `UPDATE` statements to modify existing records.

Example:

```sql
UPDATE identity.users
SET first_name = 'Jaamac'
WHERE id = '...';
```

Key lesson:

Always use a `WHERE` clause when performing updates.

Without a `WHERE` clause:

```sql
UPDATE identity.users
SET first_name = 'Jaamac';
```

every record in the table would be modified.

---

## Delete

Using `DELETE` statements to remove records.

Example:

```sql
DELETE FROM identity.users
WHERE email = 'ahmed@gmail.com';
```

Key lesson:

Always verify records using a `SELECT` statement before executing a delete operation.

Recommended workflow:

```sql
SELECT *
FROM identity.users
WHERE email = 'ahmed@gmail.com';
```

then:

```sql
DELETE FROM identity.users
WHERE email = 'ahmed@gmail.com';
```

---

# ALTER TABLE Operations

I practiced modifying table structures using `ALTER TABLE`.

Operations performed:

### Add Column

```sql
ALTER TABLE identity.users
ADD COLUMN role VARCHAR(50);
```

### Rename Column

```sql
ALTER TABLE identity.users
RENAME COLUMN role TO user_role;
```

### Change Data Type

```sql
ALTER TABLE identity.users
ALTER COLUMN user_role TYPE VARCHAR(100);
```

Key lesson:

Database structures evolve over time as business requirements change.

---

# Data Integrity Testing

One of the most valuable exercises today was testing database constraints.

### Foreign Key Validation

I intentionally attempted to insert a user using an organization ID that did not exist.

The database rejected the operation.

This demonstrated how Foreign Keys protect data integrity and prevent orphaned records.

Without this protection, a user could exist without belonging to a valid organization.

---

### Unique Constraints

I also observed how PostgreSQL prevents duplicate values when fields are marked as `UNIQUE`.

Examples:

* Email Addresses
* Registration Numbers

This ensures important business identifiers remain unique across the system.

---

# Table Maintenance Operations

I practiced several administrative commands:

### TRUNCATE

```sql
TRUNCATE TABLE identity.users;
```

Purpose:

Remove all rows while keeping the table structure intact.

---

### DROP TABLE

```sql
DROP TABLE identity.users;
```

Purpose:

Completely remove a table and its data.

---

### DROP SCHEMA

```sql
DROP SCHEMA identity CASCADE;
```

Purpose:

Remove the schema and all dependent objects.

I learned that `CASCADE` also removes:

* Tables
* Views
* Constraints
* Other dependent objects

Therefore, it should be used carefully.

---

# Key Lessons Learned

Today's practical exercises helped me understand that relational databases are not just collections of tables.

They enforce rules that maintain data quality and consistency through:

* Primary Keys
* Foreign Keys
* Unique Constraints
* NOT NULL Constraints

I also learned that operations such as `UPDATE`, `DELETE`, `TRUNCATE`, and `DROP` can be dangerous if used incorrectly.

As a future Data Engineer, it is important to understand not only how to create database structures but also how to protect and maintain data integrity throughout the system lifecycle.

---

# Personal Reflection

Today's practice reinforced the idea that SQL is much more than a query language. It is the primary interface through which data is created, managed, protected, and transformed.

The combination of database design, constraints, and CRUD operations gave me a clearer understanding of how modern applications manage data behind the scenes.

I now feel more confident designing relational databases and understanding the role they play within the broader Data Engineering lifecycle.
