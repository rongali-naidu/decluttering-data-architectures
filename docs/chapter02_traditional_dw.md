# Traditional Data Warehouse (DW) Architecture

## **1. Data Warehouse (DW) and Enterprise Data Warehouse (EDW)**

### **Data Warehouse (DW):**

A Data Warehouse (DW) is a centralized repository that stores structured data from multiple sources. It is designed to support decision-making and analytical reporting. DW systems consolidate historical and current data for business intelligence (BI) and reporting purposes.

**Key Characteristics of DW:**

- Centralized storage for structured data.
- Supports analytical queries and reporting.
- Optimized for read-intensive operations.
- Contains historical and current data for trend analysis.

### **Enterprise Data Warehouse (EDW):**

Note: When companies start, they will start with single DW for entire company..this is referred as EDW. When company grows big, they may decide to have department specific DW teams, DW clusrers. EDW is just a differentiator whether company has centrailized DW team, DW Infrasture or Department specific DW team and DW Infrastrcuture.

An Enterprise Data Warehouse (EDW) is a large-scale, centralized repository that aggregates data from various business units across an entire organization. EDWs are designed to provide a unified view of organizational data for enterprise-wide reporting and analytics.

**Key Characteristics of EDW:**

- Enterprise-wide integration of data.
- Single version of truth for organizational decision-making.
- Scalable to handle large volumes of data.
- Supports advanced analytics and complex queries.

## **2. Data Marts**

A Data Mart is a subset of a data warehouse focused on a specific business line or department (e.g., finance, sales, marketing). It provides tailored data access for particular user groups, improving query performance by limiting the dataset.

**Key Characteristics of Data Marts:**

- Department-specific datasets.
- Faster query performance due to smaller data scope.
- Can be independent (stand-alone) or dependent (sourced from EDW).
- Supports specific analytical needs.

## **3. Operational Data Store (ODS)**

An Operational Data Store (ODS) is a database designed to integrate and store real-time or near-real-time operational data from transactional systems. It serves as an intermediary layer between operational systems and the data warehouse.

**Key Characteristics of ODS:**

- Real-time or near-real-time data updates.
- Supports operational reporting and analysis.
- Temporary storage before data moves to DW.
- Ideal for tactical decision-making.

## **4. ETL vs. ELT**

Note : I still cant figure out the real difference. I think, someone made an assumption that "Data is transsformed outside Datawarehouse in ETL" which is not true.

### **ETL (Extract, Transform, Load):**

ETL is a traditional approach where data is extracted from source systems, transformed into the desired format, and then loaded into the data warehouse.

**ETL Process Flow:**

1. **Extract**: Collect data from multiple sources (databases, APIs, files).
2. **Transform**: Cleanse, enrich, and standardize the data.
3. **Load**: Populate the transformed data into the data warehouse.

**Advantages of ETL:**

- Data quality and consistency ensured before loading.
- Supports complex transformations outside the data warehouse.
- Well-suited for legacy systems and on-premise environments.

**Disadvantages of ETL:**

- Time-consuming for large datasets.
- Requires robust infrastructure for processing before loading.

### **ELT (Extract, Load, Transform):**

ELT is a modern approach where raw data is extracted and loaded into the warehouse first, and transformations occur within the data warehouse using its processing power.

**ELT Process Flow:**

1. **Extract**: Collect raw data from source systems.
2. **Load**: Load raw data into the data warehouse.
3. **Transform**: Perform transformations using in-warehouse SQL or other tools.

**Advantages of ELT:**

- Faster data ingestion by loading raw data first.
- Utilizes the scalability of modern cloud-based data warehouses.
- Better suited for large-scale and unstructured data.

**Disadvantages of ELT:**

- Requires advanced data governance to manage raw data.
- Transformation complexity is shifted to the data warehouse environment.

**Key Difference:**

The primary difference lies in where the transformation occurs:
- **ETL**: Transformation happens **before** loading into the warehouse.
- **ELT**: Transformation happens **after** loading into the warehouse.

While both approaches serve similar goals, ETL is typically preferred in traditional on-premise systems, while ELT is more efficient for modern, cloud-native architectures.

## **5. Standard Layers in Data Warehouse Architecture**

### **a. Staging Layer**

The staging layer is an intermediate storage area where raw data from source systems is initially collected. It is used for data cleansing, validation, and preparing for transformation.

**Functions of Staging Layer:**

- Temporary data storage.
- Data extraction from various sources.
- Initial data cleansing and validation.
- Audit and error logging.

### **b. Processing Layer**

The processing layer is where data transformation occurs. Data from the staging layer is cleaned, integrated, and organized into the desired format before loading into the data warehouse.

**Functions of Processing Layer:**

- Data transformation (e.g., deduplication, normalization).
- Data enrichment and integration.
- Implementing business rules.
- Handling metadata and lineage tracking.

### **c. Presentation Layer**

The presentation layer provides end-users with access to processed data for reporting and analytics. This layer structures the data for easy querying and visualization.

**Functions of Presentation Layer:**

- Supports BI and analytical reporting.
- Provides data access through SQL or APIs.
- Structures data in star or snowflake schemas.
- Delivers dashboards, reports, and data extracts.

## **6. Metadata Management**

Metadata management involves the administration and governance of data about data. It provides context, structure, and meaning to the data stored within the warehouse.

**Types of Metadata:**

- **Technical Metadata**: Includes schema definitions, data types, and lineage.
- **Business Metadata**: Provides business context like definitions, owners, and usage.
- **Operational Metadata**: Tracks data processes, job logs, and data quality metrics.

**Functions of Metadata Management:**

- Ensures data traceability and lineage.
- Facilitates data discovery and cataloging.
- Enhances data governance and compliance.
- Supports impact analysis for schema changes.



