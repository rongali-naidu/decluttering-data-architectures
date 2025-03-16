| **Category**             | **AWS**                                | **Databricks**                      | **Microsoft Azure**                       | **Google Cloud**                           |
|--------------------------|----------------------------------------|-------------------------------------|-------------------------------------------|--------------------------------------------|
| **Data Warehouse**       | Amazon Redshift                       | Databricks SQL Warehouses (with Photon) | Azure Synapse Analytics (Dedicated SQL)  | BigQuery                                   |
| **Big Data Processing**  | EMR (Spark, Hive, Presto), Athena, Redshift, Spectrum | Databricks (Spark)                  | Azure HDInsight (Spark, Hadoop)           | Dataproc (Spark, Hadoop)                   |
| **Batch Processing**     | AWS Batch (with Glue ETL, EMR, Lambda) | Databricks Jobs                     | Azure Batch, Azure Data Factory (ADF)     | Dataflow (for batch), Cloud Composer (Airflow) |
| **ETL/ELT**              | AWS Glue (ETL)                         | Databricks Delta Live Tables        | Azure Data Factory, Synapse Pipelines     | Cloud Dataflow, Dataform                   |
| **Serverless Compute**   | AWS Lambda                             | Databricks Serverless               | Azure Functions                           | Cloud Functions                            |
| **Streaming (Low Latency)** | Kinesis Data Streams                  | Structured Streaming (in Databricks) | Azure Event Hubs, Azure Stream Analytics  | Pub/Sub, Dataflow                          |
| **High-Volume Streaming**| Kafka on EMR                           | Kafka on Databricks (with Delta)    | Azure Event Hubs (Kafka API)             | Pub/Sub, Kafka on GKE (Google Kubernetes)  |
| **Streaming to Data Lake**| Kinesis Data Firehose                  | Autoloader (in Databricks)          | Azure Event Hubs Capture, Synapse Link   | Pub/Sub to BigQuery, Dataflow              |
| **DynamoDB to Streaming**| DynamoDB Streams + Kinesis Firehose    | Change Data Feed + Auto Loader      | Cosmos DB Change Feed + Event Hubs       | Firestore Change Streams + Pub/Sub         |
| **Ad-hoc Querying**      | Amazon Athena , Amazon Redshift                        | Databricks SQL                      | Azure Synapse Analytics (serverless SQL) | BigQuery                                   |
| **BI/Visualization**     | Amazon QuickSight                     | Databricks SQL Dashboards           | Power BI                                 | Looker (or Looker Studio)                  |
| **Metadata Management**  | AWS Glue Data Catalog                  | Unity Catalog                       | Azure Purview, Synapse Data Catalog      | Data Catalog (within BigQuery)             |
| **Permissions Management**| AWS Lake Formation                    | Unity Catalog (fine-grained ACLs)   | Azure RBAC + Purview                     | IAM + BigLake Tables                       |
| **Orchestration**        | Managed Workflows for Apache Airflow  | Databricks Workflows (Task Orchestration) | Azure Data Factory, Azure Logic Apps      | Cloud Composer (Managed Airflow)           |
| **Data Science & ML**    | Amazon SageMaker                      | Databricks ML (with MLflow)         | Azure Machine Learning                   | Vertex AI                                  |

