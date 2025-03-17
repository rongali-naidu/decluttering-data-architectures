
## **Understanding key terminology in Data Architecture**

---

### 0. **What is Framework?**
- **Definition**: 
  A pre-defined structure or model that guides development.
- **Example**:  
PyTorch for deep learning.

### 1. **What is Architecture?**
- **Definition**:  
  Architecture refers to the high-level design that defines how various system components interact and work together to deliver a solution. In **data architecture**, it governs how data is ingested, stored, processed, and accessed.

- **Example**:  
  **Lambda Architecture** is a hybrid approach to data processing that combines batch and real-time analytics, while **Data Mesh** is a decentralized data ownership model.

---

### 2. **What is a Platform?**
- **Definition**:  
  A platform is an integrated environment providing infrastructure, tools, and frameworks to build, deploy, and manage data and applications.

- **Example**:  
  **AWS** is a cloud platform offering services like S3 (storage), Redshift (data warehouse), and Glue (ETL) to implement data pipelines and analytics.

---

### 3. **What is Technology?**
- **Definition**:  
  Technology refers to the specific hardware, software, or methodologies that support and implement data platforms and architectures.

- **Example**:  
  **Apache Hadoop** is a technology used for distributed data storage and processing, often forming the backbone of on-premise data lakes.

---

### 4. **What is a Service?**
- **Definition**:  
  A service is a discrete offering that provides specific functionality, typically as part of a broader platform.

- **Example**:  
  **AWS Athena** is a serverless query service allowing SQL-based access to data stored in **S3**.

---

### 5. **What is a Data Pipeline?**
- **Definition**:  
  A data pipeline is a sequence of processes that move, transform, and store data from source systems to target environments.

- **Example**:  
  An **ETL pipeline** extracts customer data from databases, transforms it (e.g., anonymizing PII), and loads it into a data warehouse.

---

### 6. **What is Data Governance?**
- **Definition**:  
  Data governance is the framework for managing data quality, access, security, and compliance across an organization's data assets.

- **Example**:  
  **AWS Lake Formation** enforces fine-grained access control over S3 datasets.

---

### 7. **What is a Data Model?**
- **Definition**:  
  A data model defines how data is organized and structured within a system, including relationships and constraints.

- **Example**:  
  **Star Schema** is a dimensional model used in data warehouses, optimizing for analytical queries.

---

### 8. **What is a Data Lake?**
- **Definition**:  
  A data lake is a centralized repository that stores structured and unstructured data in its native format.

- **Example**:  
  **AWS S3** acts as the storage layer in modern data lake architectures.

---

### 9. **What is a Data Warehouse?**
- **Definition**:  
  A data warehouse is a system optimized for querying and analyzing large volumes of structured data.

- **Example**:  
  **Amazon Redshift** provides scalable, columnar storage for analytical workloads.

---

### 10. **What is a Data Lakehouse?**
- **Definition**:  
  A data lakehouse is a hybrid architecture combining the raw data storage capabilities of a data lake with the querying performance of a data warehouse.

- **Example**:  
  **Delta Lake** (built on **Apache Spark**) enables ACID transactions on data lakes, supporting a lakehouse model.

---

### 11. **What is Metadata?**
- **Definition**:  
  Metadata is "data about data," providing information on structure, source, and lineage.

- **Example**:  
  **AWS Glue Data Catalog** stores metadata about tables and schemas for querying with **Athena**.

---

### 12. **What is Data Ingestion?**
- **Definition**:  
  Data ingestion is the process of importing data from various sources into storage systems.

- **Example**:  
  **AWS Glue** is used to ingest batch data, while **Kinesis** handles real-time ingestion.

---

### 13. **What is Data Processing?**
- **Definition**:  
  Data processing transforms raw data into meaningful information through cleaning, filtering, and aggregation.

- **Example**:  
  **Apache Spark** is widely used for large-scale batch and streaming data processing.

---

### 14. **What is Data Access Control?**
- **Definition**:  
  Data access control ensures that only authorized users can interact with specific datasets.

- **Example**:  
  **AWS Lake Formation** applies fine-grained permissions on S3 data through **Glue**.



# Scalability, Availability, Reliability, and Performance Concepts

Following is my intrepreation of these terminology ... refer https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.concepts.wa-concepts.en.html

## Scalability
Scaling is growing an infrastructure (compute, storage, networking) larger so that the applications running on that infrastructure can serve more users at a time.

- **Vertical Scaling**: Replacing with high-processing capable hardware/software. It involves taking what you’ve got and replacing it with something more powerful.
- **Horizontal Scaling**: Adding more smaller units to increase capacity.
- **Scale-out / Scale-in**: Horizontal scaling. Adding/removing the smaller units.
- **Scale-up / Scale-down**: Vertical scaling. Replacing with more powerful hardware (scale-up) or with less powerful hardware (scale-down).
- **Auto Scaling**: A service feature for deciding on scale-out/scale-in/scale-up/scale-down depending on pre-configured conditions.
- **Scaling vs Upgrading**: In my opinion, scaling refers to hardware, while upgrading could involve either a software update or a hardware upgrade to newer versions.

## Availability
The percentage of time a service is operational and available for customer use. Higher availability means fewer service disruptions.

- **Example**: AWS S3 Standard storage class is designed for **99.99% availability**.

## Reliability
The likelihood that a service will be up and running (or available) within a specific time period. This is a key factor for users requiring uninterrupted service.

- **Example**: AWS S3 Standard storage class is designed for **99.99% availability**.

## Durability
Durability measures the period a product or service remains in a useful state.

- **Example**: Amazon S3 Standard, S3 Standard–IA, S3 One Zone-IA, and S3 Glacier are all designed to provide **99.999999999% durability** of objects over a year. This equates to an average annual loss of **0.000000001%** of objects. For instance, if you store **10 million** objects with Amazon S3, you can expect to lose a single object every **10,000 years** on average.

## Speed vs Bandwidth vs Throughput
These concepts can be better understood using the analogy of a freeway:

- **Speed**: The speed of a car in a lane represents the speed of data transmission.
- **Bandwidth**: The number of lanes on the freeway represents the amount of data that can be transmitted simultaneously.
- **Throughput**: The number of cars passing a point per second represents the total volume of data transmitted per unit of time.

### Analogy using Amazon Redshift:
- **Speed**: Each WLM queue can process **2 queries per second**.
- **Bandwidth**: Redshift can support a maximum of **5 WLM queues**.
- **Throughput**: Redshift can process up to **10 queries per second** (5 queues × 2 queries/second).

## Latency
The time it takes to serve a request from the moment it is received to when the response is delivered.

