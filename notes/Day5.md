# Day 5 Learning Journal — Storage and Ingestion (Chapter 2)

## Reading Progress

Today I continued Chapter 2 of *Fundamentals of Data Engineering* and studied two important stages of the Data Engineering Lifecycle:

* Storage
* Ingestion

Later today, I will practice SQL aggregation functions and build simple verification statistics.

---

# Storage

Storage is the foundation of the Data Engineering Lifecycle because data must be stored before it can be transformed, analyzed, or served to users.

One important lesson is that storage is not a single step in the lifecycle. Data may be stored multiple times as it moves through ingestion, transformation, and serving.

Examples of storage systems include:

* Databases
* Data Warehouses
* Data Lakes
* Object Storage

### Key Lesson

Choosing the right storage system depends on:

* Data volume
* Read speed requirements
* Write speed requirements
* Scalability
* Cost
* Query capabilities

There is no universal storage solution that works for every use case.

---

# Understanding Data Temperature

Not all data is accessed equally.

The book introduces the concept of data temperatures:

## Hot Data

Frequently accessed data.

Examples:

* User requests
* Live applications
* Operational systems

### Key Lesson

Hot data should be stored in systems optimized for fast retrieval.

---

## Warm Data

Occasionally accessed data.

Examples:

* Weekly reports
* Monthly analytics

---

## Cold Data

Rarely accessed data.

Examples:

* Historical archives
* Compliance records
* Backup data

### Key Lesson

Cold data is usually stored in cheaper storage systems because access speed is less important.

---

# Ingestion

Ingestion is the process of collecting data from source systems and moving it into the data platform.

Examples of source systems:

* Application Databases
* APIs
* IoT Devices
* Log Files
* Event Streams

### Key Lesson

The source system and ingestion layer are often the biggest bottlenecks in a data pipeline because they are frequently outside the Data Engineer's control.

---

# Batch vs Streaming

The book introduces two major ingestion approaches.

## Batch Ingestion

Data is collected and processed in chunks.

Examples:

* Daily reports
* Weekly analytics
* Model training datasets

### Advantages

* Simpler
* Cheaper
* Easier to maintain

### Personal Takeaway

Batch processing is still suitable for many business use cases.

---

## Streaming Ingestion

Data is processed continuously as events occur.

Examples:

* Financial transactions
* IoT sensor data
* Real-time notifications

### Advantages

* Low latency
* Near real-time processing

### Challenges

* More complex
* Higher operational costs
* Increased maintenance requirements

### Personal Takeaway

Streaming should only be used when there is a clear business need for real-time data.

---

# Push vs Pull

The book also introduces two ingestion models.

## Push Model

The source system sends data to a destination.

Examples:

* Event streams
* Message queues
* Webhooks

---

## Pull Model

The ingestion system retrieves data from the source.

Examples:

* Scheduled ETL jobs
* Database queries
* API polling

### Personal Takeaway

Both models are common in modern data architectures, and many systems use a combination of push and pull approaches.

---

# Biggest Lessons Learned

The most important lessons from today's reading are:

1. Storage decisions affect every stage of the Data Engineering Lifecycle.
2. Data has different temperatures (hot, warm, and cold) that influence storage choices.
3. Ingestion is often one of the most challenging stages of a data pipeline.
4. Batch processing remains useful despite the popularity of streaming systems.
5. Real-time streaming should be driven by business requirements rather than technology trends.

---

# Personal Reflection

Today's reading helped me understand that Data Engineering is not only about moving data but also about making thoughtful decisions regarding where data is stored, how it is ingested, and how quickly it needs to be accessed.

I also learned that many modern systems combine multiple storage technologies and ingestion patterns rather than relying on a single solution. The best architecture depends on business needs, scale, and operational requirements.

---

# SQL Practice (To Be Completed)

Today's SQL topics:

* COUNT()
* AVG()
* SUM()
* MIN()
* MAX()

### Build

Verification Statistics System

Examples:

* Total Users
* Total Organizations
* Active Organizations
* Average Verifications per User
* Maximum Verifications Processed
* Minimum Verifications Processed

(Practice section will be completed after SQL exercises.)


# SQL Practice

After completing today's reading, I practiced SQL aggregation functions by building a simple verification statistics system for the Xaqiiji platform.

Unlike previous exercises that focused on retrieving records, today's exercises focused on summarizing data and extracting insights from multiple rows.

---

# Verification Statistics System

To simulate a real-world identity verification platform, I created a new table called `verifications`.

The table stores:

* Verification Request ID
* User ID
* Verification Type
* Verification Status
* Processing Time
* Creation Date

This allowed me to generate verification statistics similar to what would appear on an administrative dashboard.

---

# COUNT()

The COUNT() function is used to determine the number of records matching a condition.

### Total Approved Verifications

```sql
SELECT COUNT(*)
FROM identity.verifications
WHERE status = 'Approved';
```

### Result

```text
15
```

### Lesson Learned

COUNT() is commonly used in dashboards and reports to calculate totals and monitor system activity.

---

# COUNT() with Filtering

### Total Rejected Verifications

```sql
SELECT COUNT(*)
FROM identity.verifications
WHERE status = 'Rejected';
```

### Result

```text
5
```

### Lesson Learned

COUNT() combined with WHERE clauses enables filtering and reporting on specific categories of data.

---

# AVG()

The AVG() function calculates the average value of a numeric column.

### Average Verification Processing Time

```sql
SELECT AVG(processing_time_seconds)
FROM identity.verifications;
```

### Result

```text
12.10 seconds
```

### Lesson Learned

Average values provide useful performance metrics and help measure overall system efficiency.

---

# SUM()

The SUM() function calculates the total value of a numeric column.

### Total Processing Time

```sql
SELECT SUM(processing_time_seconds)
FROM identity.verifications;
```

### Result

```text
242 seconds
```

### Lesson Learned

SUM() is useful for calculating cumulative metrics such as total processing time, revenue, costs, or transactions.

---

# MIN()

The MIN() function returns the smallest value in a column.

### Fastest Verification

```sql
SELECT MIN(processing_time_seconds)
FROM identity.verifications;
```

### Result

```text
8 seconds
```

### Lesson Learned

MIN() helps identify the best-case scenario or lowest recorded value.

---

# MAX()

The MAX() function returns the largest value in a column.

### Slowest Verification

```sql
SELECT MAX(processing_time_seconds)
FROM identity.verifications;
```

### Result

```text
15 seconds
```

### Lesson Learned

MAX() helps identify peak values, bottlenecks, and worst-case scenarios.

---

# Verification Statistics Summary

Based on the sample data:

| Metric                  | Value         |
| ----------------------- | ------------- |
| Total Verifications     | 20            |
| Approved Verifications  | 15            |
| Rejected Verifications  | 5             |
| Average Processing Time | 12.10 Seconds |
| Total Processing Time   | 242 Seconds   |
| Fastest Verification    | 8 Seconds     |
| Slowest Verification    | 15 Seconds    |

---

# Biggest Lesson Learned

Today I learned that SQL is not only used to retrieve records but also to generate meaningful business insights.

Using aggregation functions allows Data Engineers and Analysts to answer questions such as:

* How many verifications were processed?
* What percentage were approved?
* How long does verification typically take?
* What is the fastest and slowest processing time?

These types of queries form the foundation of dashboards, reporting systems, business intelligence platforms, and data analytics workflows.

---

# Personal Reflection

Today's exercises felt closer to real Data Engineering and Data Analysis work than previous SQL exercises.

Rather than focusing on individual rows, I began analyzing data at a higher level and extracting information that could support business decisions.

I can now see how aggregation functions are used to build metrics, KPIs, operational dashboards, and performance monitoring systems in real-world applications such as Xaqiiji.
