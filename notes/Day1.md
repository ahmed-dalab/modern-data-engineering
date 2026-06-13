# Day 1 Learning Journal — 13 June 2026

Today, 13 June 2026, I am starting a new learning journey, which I call **Modern Data Engineering + AI Systems**. My primary focus is on data, and I want to develop a deep understanding of data concepts so that it becomes easier for me to become a Data Analyst or Data Engineer. Later, this foundation will also make it easier for me to work with machine learning and AI systems in the next stage of my journey. This learning journey is expected to last more than six months.

Today, I learned the following concepts:

* What is Data Engineering?
* What is a Data Engineer?
* What is the Data Engineering Lifecycle?

When defining these terms, many experts provide different explanations. However, one of the most comprehensive definitions comes from the book **Fundamentals of Data Engineering**, which states:

> "Data engineering is the development, implementation, and maintenance of systems and processes that take in raw data and produce high-quality, consistent information that supports downstream use cases, such as analysis and machine learning. Data engineering is the intersection of security, data management, DataOps, data architecture, orchestration, and software engineering. A data engineer manages the data engineering lifecycle, beginning with getting data from source systems and ending with serving data for use cases, such as analysis or machine learning."

## Data Engineering

Data Engineering is the process of designing, building, and maintaining systems that enable organizations to collect, store, process, manage, and analyze data at scale.

## Data Engineer

A Data Engineer is a software engineer responsible for designing, implementing, scaling, and managing the data systems that organizations rely on for their operations.

## Core Responsibilities of a Data Engineer

* Pipeline Development
* System Architecture
* Data Optimization
* Data Governance and Security

## Data Engineering Lifecycle

The Data Engineering Lifecycle is a holistic framework that describes everything that happens to data, from the moment it is generated at the source to the moment it is consumed by an end user or downstream system.

The lifecycle does not operate in isolation. It is supported by several important "undercurrents," including:

* Security
* Data Governance
* Orchestration
* Software Engineering Best Practices

# The Five Main Stages of the Data Engineering Lifecycle

## 1. Generation (Source Systems)

This is where data is created. Data Engineers must understand the source systems where data originates.

Examples include:

* IoT devices
* Application databases (OLTP systems)
* APIs
* Log files
* Third-party systems

Data can exist in different formats, including:

* Structured data (SQL databases)
* Semi-structured data (JSON, XML)
* Unstructured data (documents, images, videos)

---

## 2. Ingestion

Once data is generated, it must be moved into the data environment.

There are two primary ingestion methods:

### Batch Ingestion

Data is collected and moved in batches at scheduled intervals.

### Streaming Ingestion

Data is captured and moved in real time as events occur.

---

## 3. Storage

Data Engineers select storage solutions based on the volume, variety, and access requirements of the data.

### Data Lakes

Large repositories designed to store raw, unstructured, or semi-structured data.

Example:

* Amazon S3

### Data Warehouses

Highly structured repositories optimized for analytical querying and reporting.

---

## 4. Transformation

Raw data is rarely ready for analysis. During this stage, data is cleaned, transformed, enriched, and combined.

Typical operations include:

* Removing duplicate records
* Handling missing values
* Converting data types
* Joining tables
* Aggregating metrics

### Common Approaches

#### ETL (Extract, Transform, Load)

Data is transformed before it is loaded into the target system.

#### ELT (Extract, Load, Transform)

Data is first loaded into the target system and transformed afterward.

Modern cloud-based workflows often favor ELT because cloud data warehouses provide powerful transformation capabilities.

---

## 5. Serving (Data Consumption)

This is the final stage of the lifecycle. Data is now clean, structured, and optimized for its intended use.

### Analytics

Feeding Business Intelligence (BI) dashboards and reports.

### Machine Learning

Providing clean datasets and features for AI and ML models.

### Reverse ETL

Sending processed data back into operational systems such as CRMs, marketing platforms, and customer engagement tools.

# PostgreSQL Refresher

Today, I also refreshed my database knowledge, including:

* Creating databases
* Creating tables
* Altering tables
* Schemas
* Data types
* UUIDs and their advantages

## Why UUIDs Are Useful

Traditionally, databases use auto-incrementing integers as primary keys.

For example:

```text
1
2
3
4
5
```

While simple, this approach has several limitations.

### 1. Global Uniqueness

UUIDs are globally unique, making them ideal for distributed systems.

### 2. Reduced Predictability

Integer IDs are predictable.

For example:

```text
/api/users/1
/api/users/2
/api/users/3
```

An attacker may attempt to enumerate records by guessing IDs.

UUIDs make this much more difficult because they are not sequential.

### 3. Easier Database Merging

Suppose:

* Tenant A has a user with ID = 5
* Tenant B also has a user with ID = 5

When merging databases, these IDs conflict and create primary key collisions.

UUIDs eliminate this problem because every identifier is designed to be unique across systems.

### 4. Better Support for Distributed Architectures

UUIDs can be generated independently by applications without first requesting the next available ID from the database.

This makes them particularly useful in modern cloud-native and distributed architectures.

# Reflection

Today I learned that Data Engineering is much broader than simply moving data from one place to another. It involves architecture, governance, security, software engineering, storage, transformation, and delivery. I also gained a clearer understanding of how data flows through its lifecycle and why database design decisions, such as choosing UUIDs over auto-incrementing integers, can have significant implications for scalability and system design.
