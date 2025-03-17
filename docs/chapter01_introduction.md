### What is data architecture?

Reference : [AWS data-architecture](https://aws.amazon.com/what-is/data-architecture/)

Data architecture is the overarching framework that describes and governs an organization's data collection, management, and usage. Organizations today have vast data volumes coming in from various data sources and disparate teams wanting to access that data for analytics, machine learning, artificial intelligence, and other applications. Modern data architecture presents a cohesive system that makes data accessible and usable while ensuring data security and quality. It defines policies, data models, processes, and technologies that allow organizations to easily move data across departments and ensure it is available whenever needed—including real-time access—while fully supporting regulatory compliance.

### What are the components of any data architecture?
 Data architecture components represented visually

![Image](images/chapter_1_introduction/modern-data-architecture-components.png)

### The main data architecture components are given below.

#### Data sources
Data sources can be customer-facing applications, monitoring and telemetry systems, IoT devices and smart sensors, apps supporting business operations, internal knowledge stores, data archives, third-party data stores, and more. Both structured and unstructured data enter the organization at varying speeds, volumes, and frequencies.

#### Databases
Purpose-built database systems support modern applications and their different features. They can be relational or non-relational, some storing data as structured tables and others storing unstructured data types as documents or key-value pairs. Databases typically store domain-specific data related to a narrow use case. However, the data can be used beyond the current system. For example, data from a customer-facing app can be used for marketing analytics or planning and needs to be taken out of the database for processing. Similarly, processed data from elsewhere has to be reloaded into the database of an analytics or machine learning (ML) application.

#### Data lakes
A data lake is a centralized repository for raw data storage at scale. The data architecture describes how data moves from different databases to the data lake and back to different databases as needed for usage. The data lake stores data in a native or open format, allowing for formatting and cleaning before use. It supports data integration and breaks down data silos within an organization.

#### Data analytics
The data analytics component includes traditional data warehouses, batch reporting, and data streaming technology for real-time alerting and reporting. They can be used for one-time querying and advanced analytics use cases. Analytics are not constrained by data silos because the data architecture opens access and allows more freedom for everyone to use the organization's data assets.

#### Artificial intelligence
ML and AI are critical for a modern data strategy to help organizations predict future scenarios and build intelligence into applications. Data scientists use data from lakes to experiment, identify intelligence use cases, and train new models. Even after training, AI models require ongoing access to fresh data to generate relevant and useful output. Modern data architectures include all the technology and infrastructure that supports AI model training and inference.

#### Data governance
Data governance determines roles, responsibilities, and standards for data usage. It outlines who can take what action, upon what data, using what methods, and in what situations. It includes both data quality and data security management. Data architects define processes to audit and track data usage for ongoing regulatory compliance.

#### Metadata management is an integral part of data governance. Data architecture includes tools and policies to store and share metadata. It outlines mechanisms to provide a central metadata store where disparate systems can store and discover metadata and use it to further query and process data assets.

### How is data architecture implemented?
It is a best practice to implement your modern data architecture in layers. The layers group processes and technologies based on distinct objectives. Implementation details are flexible, but the layers guide technology choices and how they should integrate.


 

#### Staging layer
The staging layer is the entry point for data within the architecture. It handles raw data ingestion from various sources, including structured, semi-structured, and unstructured formats. You want this layer to be as flexible as possible.

If schema (data formats and types) are enforced rigidly in this layer, downstream use cases get limited. For example, enforcing all date values as a month, year format limits future use cases that require dd/mm/yyyy formatting. At the same time, you want some consistency. For example, if phone numbers are stored as strings and used as such, but some other data source starts generating the same data as numeric, it causes data pipelines to break.

Balancing flexibility with consistency requires you to divide this layer into two sub-layers.

Raw layer
The raw layer stores unaltered data exactly as it arrives, preserving the original format and structure without transformations. It is an enterprise-wide repository for data exploration, auditing, and reproducibility. Teams can revisit and analyze data in its original state when needed, ensuring transparency and traceability.

#### Standardized layer
The standardized layer prepares raw data for consumption by applying validation and transformations according to predefined standards. For example, in this layer, all telephone numbers would be converted to strings, all time values to specific formats, etc. It thus becomes the interface for all users within the organization to access structured, quality-assured data.

The standardized layer in data architecture is crucial for enabling self-service business intelligence (BI), routine analytics, and ML workflows. It enforces schema standards while minimizing disruptions caused by schema changes.

#### Conformed layer
Data integration from different sources is completed in the conformed layer. It creates a unified enterprise data model across domains. For example, customer data may have different details in different departments—order details are captured by sales, financial history is captured by accounts, and interests and online activity are captured by marketing. The conformed layer creates a shared understanding of such data across the organization. Key benefits include:

Consistent, unified definition of core entities across the organization.
Compliance with data security and privacy regulations.
Flexibility that balances enterprise-wide uniformity with domain-specific customization through centralized and distributed patterns.
It is not directly used for operational business intelligence but supports exploratory data analysis, self-service BI, and domain-specific data enrichment.

Enriched layer
This layer transforms data from the previous layer into datasets called data products tailored for specific use cases. Data products can range from operational dashboards used for daily decision-making to detailed customer profiles enriched with personalized recommendations or next-best-action insights. They are hosted in various databases or applications chosen based on the specific use case.

Organizations catalog the data products in centralized data management systems for discoverability and access by other teams. This reduces redundancy and ensures that high-quality, enriched data is easily accessible.

### What are the types of data architectures?
There are two different approaches to the conformed layer that create different data architecture types.

Centralized data architecture
In centralized data architectures, the conformed layer focuses on creating and managing common entities, like customer or product, that are universally used across the enterprise. The entities are defined with a limited set of generic attributes for easier data management and broad applicability. For example, a customer entity might include core attributes like name, age, profession, and address.

Such data architectures support centralized data governance, especially for sensitive information like personally identifiable information (PII) or payment card information (PCI). Centralized metadata management ensures that data is cataloged and governed effectively, with lineage tracking and lifecycle controls for transparency and security.

However, this model avoids including all possible attributes, as centrally managing complex data requirements slows down decision-making and innovation. Instead, domain-specific properties, such as customer campaign impressions(only required by marketing), are derived in the enriched layer by respective business units.

Data fabric technologies are useful in implementing centralized data architectures.

Distributed data architecture
Each domain creates and manages its own conformed layer in distributed data architectures. For example, marketing focuses on attributes like customer segments, campaign impressions, and conversions, while accounting prioritizes properties such as orders, revenue, and net income.

Distributed data architectures allow flexibility in defining entities and their properties but result in multiple datasets for common entities. Discoverability and governance of these distributed datasets are achieved through a central metadata catalog. Stakeholders can find and use the appropriate dataset while overseeing data exchange processes.

Data mesh technologies are useful in implementing distributed data architectures.

What is a data architecture framework?
A data architecture framework is a structured approach to designing data architecture. It provides a set of principles, standards, models, and tools that ensure efficient data management processes aligned with the organization's business objectives. You can think of it as a standard blueprint that a data architect uses to build high-quality and comprehensive data architectures.

Some examples of data architecture frameworks include

The DAMA-DMBOK framework
The Data Management Body of Knowledge (DAMA-DMBOK) framework outlines best practices, principles, and processes for effective data management across its lifecycle. It supports establishing consistent data management practices while ensuring alignment with business goals. By treating data assets as a strategic resource, DAMA-DMBOK provides actionable guidance for improving decision-making and operational efficiency.

The Zachman framework
The Zachman framework is an enterprise architecture framework that uses a matrix format to define the relationships between different perspectives (such as business owner, designer, and builder) and six key interrogatives (What, How, Where, Who, When, and Why). Organizations can visualize how data fits within their overall operations, ensuring that data-related processes align with business objectives and system requirements. The Zachman framework is widely recognized for its ability to bring clarity to enterprise-wide data and system dependencies.

TOGAF
The Open Group Architecture Framework (TOGAF) treats data architecture as a critical component of a broader system, emphasizing the creation of data models, data flows, and governance structures that support organizational needs. It establishes standardized data processes, ensuring system interoperability and efficient data management. It is particularly beneficial for large enterprises looking to align their IT and business strategies through a unified approach.

How does data architecture compare to other related terms?
Different data terminologies sound similar but have completely different meanings. We give some explanations below.

Data architecture vs. information architecture
Information architecture is the organization and presentation of information to end users. The term applies to user interfaces, websites, or content systems and relates to end-user information accessibility. Principles and tools in information architecture focus on navigation, categorization, and searchability—for example, within an online knowledge store or document database.

In contrast, data architecture focuses on designing and managing all organizational data. It deals with all backend technical data infrastructure, while information architecture only focuses on how end-users interact with and interpret information.

Data architecture vs. data engineering
Data engineering is the practical implementation of data architecture. Data architects provide a high-level plan for managing an organization’s data assets. They design scalable data systems aligned with business objectives and security policies. Data engineers implement the plan—building, maintaining, and optimizing data pipelines. They ensure data is ingested, cleaned, transformed, and delivered for analysis per the rules of data architecture.

Data architecture vs. data modeling
Data modeling is a process within data architecture that creates a visual representation of any data collection. It includes creating conceptual, logical, and physical data models that outline the data in the collection. A logical data model diagrammatically represents data constraints, entity names, and relationships for implementation in a platform-independent way. A physical data model further refines the logical model for implementation over specific data technology.

Data architecture has a much wider scope beyond data modeling. Beyond data attributes and relationships, it also defines a broader strategy for organization-wide data management. It includes infrastructure, policies, and technologies for data integration that align with organizational objectives.

**The Evolution of Data Architectures**

The need for data warehousing emerged as businesses began to recognize the value of collecting and analyzing data to drive decision-making. In the early days, operational databases, designed for transactional efficiency (OLTP), were ill-suited for complex analytical queries (OLAP). This led to the rise of data warehouses in the late 1980s and early 1990s—centralized repositories designed to store and analyze large volumes of structured data efficiently. Pioneered by people like Ralph Kimball and Bill Inmon , data warehouses enabled organizations to perform historical analysis, generate reports, and derive business insights that were previously impossible due to the limitations of transactional systems. [Reference: Ralph-Kimbhal](https://www.amazon.com/Books-Ralph-Kimball/s?rh=n%3A283155%2Cp_27%3ARalph%2BKimball), [Reference:Bill Inmon](https://www.amazon.com/s?k=Bill+Inmon+books&crid=GA2ZE2AP882D&sprefix=bill+inmon+books%2Caps%2C509&ref=nb_sb_noss)

### Data Volume: From Megabytes to Exabytes

Since then, the data landscape has undergone a profound transformation across multiple dimensions: the sheer size of data, the variety of data formats, advancements in database technologies, and the increasing sophistication of analytical and reporting requirements. Initially, data warehouses primarily handled megabytes to terabytes of structured data, but today, organizations contend with petabytes or even exabytes of structured, semi-structured, and unstructured data. This explosion in data volume, often referred to as the "data deluge," has been fueled by the proliferation of digital channels, IoT devices, social media, and other real-time data sources. [Reference: Hilbert, M., & López, P. (2011). The world’s technological capacity to store, communicate, and compute information. Science, 332(6025), 60-65.]

### Data Formats: Beyond Relational Models

The evolution of data formats also introduced new challenges. Traditional relational databases were designed to work with tabular data, but modern enterprises must process data in formats such as JSON, XML, Parquet, Avro, and multimedia content. This shift pushed database technology to evolve beyond relational models. Columnar storage, massively parallel processing (MPP), and schema-on-read approaches became essential to accommodate the diverse and dynamic nature of contemporary datasets. Technologies like NoSQL databases and distributed file systems gained prominence.

### Analytical and Reporting Requirements: From Static Reports to Real-Time Insights

Reporting and analytical requirements have similarly evolved. In the past, static, batch-based reports sufficed for business intelligence needs. However, as competition intensified, organizations demanded real-time insights, interactive dashboards, predictive analytics, and advanced machine-learning models. This shift drove the development of new architectures that could support both historical and real-time data analysis, leading to the emergence of concepts like data lakes and stream processing.

### The Big Data Era: Hadoop and Distributed Processing

The advent of Big Data in the early 2000s marked a paradigm shift. The Hadoop framework, introduced by projects like Google's MapReduce and the Apache Software Foundation, introduced distributed storage (HDFS) and parallel processing (MapReduce), making it feasible to store and process massive datasets affordably. While Hadoop addressed the scalability challenge, it introduced complexities in data management and governance. As a response, more flexible and efficient processing frameworks like Apache Spark emerged, offering in-memory computing and faster data transformation capabilities. [Reference: Dean, J., & Ghemawat, S. (2004). MapReduce: simplified data processing on large clusters. OSDI'04: Sixth Symposium on Operating System Design and Implementation, 137-150.]

### The Cloud Revolution: On-Demand Scalability and Managed Services

The shift to the cloud further revolutionized data architectures. Cloud platforms provided on-demand scalability, cost efficiency, and access to a wide array of managed data services. This allowed organizations to move beyond the limitations of on-premises infrastructure and adopt more agile, scalable data solutions. Data lakes became a popular choice for storing raw, unstructured data, offering a cost-effective way to capture vast amounts of information without imposing a predefined schema. Cloud-native data warehouses like Amazon Redshift and Snowflake offered improved performance and scalability.

### Machine Learning and AI: Driving Intelligent Insights

The rise of machine learning (ML) and artificial intelligence (AI) has further transformed data architectures. Organizations are leveraging advanced analytics and ML models to derive insights, automate decision-making, and enable predictive capabilities. Modern data platforms now integrate ML pipelines directly within their ecosystems, supporting tasks like feature engineering, model training, and inference at scale. This integration demands robust data governance, real-time data accessibility, and infrastructure that can manage both structured and unstructured datasets for AI applications.

### The Emergence of Lakehouses: Addressing Data Lake Limitations

Data lakes provided a solution for storing vast amounts of raw data, and queryin them with "schema-on-read" approach but lacked support for update/deletes. The Lakehouse architecture emerged as a response, combining the strengths of data warehouses and data lakes. 

### The Need for Decluttering Data Architectures

The rapid evolution of data architectures has resulted in a diverse range of solutions. Companies like **AWS**, **Databricks**, and **Snowflake**, each addressing the challenges of scale, variety, and velocity, have developed distinct approaches to data management, ranging from Lake Houses to cloud data platforms. While these architectures share core goals like efficient data processing and analysis, their underlying principles and implementation details can vary significantly. This book aims to declutter this complex landscape, providing a framework for understanding these architectures, identifying their commonalities and divergences, and ultimately guiding you in selecting the best approach for your specific needs.
