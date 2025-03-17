
## **Lambda Architecture**

NOTE : This seems to be related to problem i observed with Kinesis Firehose : when i reduced  buffer time from 10 mins to 1 mins, i could reduce the data refresh latency to 1 mins. But it resulted in another issue...smaller files issue . for one day data query,  provided the table is partitioned by snapshot day, SQL worked fine but when queried for the data accross the days, SQL performance went bad. due to  1 mins buffer , it resulted in around 60 files minimum...depending on the input data size, firehose could generate more than 60 files (for ex: in 1 min, it recieved 10 GB, we set 1 GB as buffer limit). One alternative, i thought aboyt this problem is 1) Developer lambda to merge small files into big files for previous day's files 2) Use this table for only recent data and separate table for historical data ...note that , not able to reduce the latency below 1 mins since that is the minum bufer time, Firehose provided.

Reference 1 : https://medium.com/%40vinciabhinav7/lambda-architecture-a-big-data-processing-framework-introduction-74a47bc88bd3

- **Overview**: Lambda Architecture is a **hybrid data processing model** that handles **real-time (stream)** and **batch** data processing simultaneously. It was popularized by **Nathan Marz** (author of "Big Data: Principles and Best Practices of Scalable Real-Time Data Systems").

- **How It Works**:
  It consists of **three layers**:

  1. **Batch Layer**:
     - Stores a **master dataset** (immutable raw data) in a **data lake**.
     - Processes large volumes of data in **batches**.
     - Generates **precomputed views** (e.g., daily reports).

  2. **Speed Layer**:
     - Handles **real-time streaming** data for low-latency queries.
     - Provides immediate insights while waiting for batch updates.

  3. **Serving Layer**:
     - Merges the outputs from both batch and speed layers.
     - Exposes data to consumers through **APIs** or **queries**.

---

### 🛠️ **Lambda Architecture in AWS Data Lake**
In an AWS environment, you can implement Lambda Architecture using a combination of services:

| **Layer**          | **AWS Service**                         |
|--------------------|----------------------------------------|
| **Batch Layer**    | Amazon S3 (Data Lake), AWS Glue (ETL)   |
| **Speed Layer**    | Amazon Kinesis, AWS Lambda, MSK (Kafka) |
| **Serving Layer**  | Amazon Athena, Amazon Redshift Spectrum |

✅ **Example Workflow**:
1. **Batch**: Store raw data in **S3**, process it with **AWS Glue**.
2. **Speed**: Use **Kinesis** to capture and analyze streaming data in real time.
3. **Serve**: Query both layers using **Athena** or **Redshift Spectrum**.

---

### 📊 **Why Use Lambda Architecture with a Data Lake?**
- **Fault Tolerance**: Batch data ensures a complete historical record.
- **Low Latency**: Speed layer delivers real-time insights.
- **Scalability**: Works well with massive datasets in AWS S3.

---

### **Lambda vs. Other Architectures**:

| Feature               | Lambda Architecture                  | Kappa Architecture                | Data Lakehouse                       |
|-----------------------|--------------------------------------|-----------------------------------|--------------------------------------|
| **Processing Layers**  | Batch + Speed + Serving              | Speed Layer Only                  | Unified Processing (Batch + Stream)  |
| **Complexity**         | High (maintaining two pipelines)     | Lower (single pipeline)           | Moderate (simplified architecture)   |
| **Use Case**           | Large-scale data + Real-time insights | Continuous real-time processing   | Unified analytics + ACID transactions|
| **AWS Example**        | S3 + Kinesis + Athena                | Kinesis + Lambda + Athena         | S3 + Glue + Lake Formation + Athena  |

