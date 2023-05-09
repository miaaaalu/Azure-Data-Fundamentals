- [Intro](#intro)
- [data warehousing architecture](#data-warehousing-architecture)
  - [1. Data Ingestion and Processing](#1-data-ingestion-and-processing)
  - [2. Analytical Data Store](#2-analytical-data-store)
  - [(1). Data Warehouse](#1-data-warehouse)
  - [**(2). Data Lake**](#2-data-lake)
  - [**Hybrid approaches**](#hybrid-approaches)
  - [Azure services for analytical stores](#azure-services-for-analytical-stores)
    - [Synapse Analytics](#synapse-analytics)
    - [Databricks](#databricks)
  - [3. Analytical Data Model](#3-analytical-data-model)
  - [4. Data Visualization](#4-data-visualization)

# Intro
| Key Aspect             | Conventional Data Warehousing                                          | Big Data Processing Solutions                                                                     |
| ---------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Data Handling Approach | Copying data from transactional data stores into a relational database | Handling large volumes of data in multiple formats, batch loaded or captured in real-time streams |
| Data Storage           | Relational database with optimized schema                              | Data lake                                                                                         |
| Data Types             | Structured data                                                        | Structured and unstructured data                                                                  |
| Use Cases              | Business intelligence, reporting                                       | Complex analytics, machine learning on large datasets                                             |
| Querying               | SQL                                                                    | Distributed processing engines like Apache Spark                                                  |

# data warehousing architecture
## 1. Data Ingestion and Processing

![data ingestion pipelines](https://learn.microsoft.com/en-us/training/wwl-data-ai/examine-components-of-modern-data-warehouse/media/pipeline.png)
- Data is sourced from transactional data stores, files, real-time streams, etc.
- Extract, transform, and load (ETL/ELT) processes are used to clean, filter, and restructure the data.
- Ingestion includes batch processing of static data and real-time processing of streaming data.
- Distributed systems handle high volumes of data in parallel.



<details>
  <summary>Azure Large-Scale Data Ingestion Instructions
</summary>

1.1. Choose the Pipeline Engine: Select either `Azure Data Factory` or `Azure Synapse Analytics` to create and run the pipelines.

2.1. Define Activities: Construct pipelines with one or more activities that operate on data, starting with an input dataset and progressing through incremental manipulations.

3.1. Utilize Linked Services: Use linked services in pipelines to load and process data, allowing for the use of appropriate technologies at each workflow step.

4.1. Configure Data Sources: Ingest the input dataset using linked services like `Azure Blob Store`.

5.1. Perform Data Processing: Apply transformations to the data using services such as `Azure SQL Database`, `Azure Databricks`, or `Azure HDInsight`.

6.1. Implement Custom Logic: Optionally, incorporate custom logic using `Azure Functions`.

7.1. Save Output Dataset: Store the resulting output dataset in a linked service like `Azure Synapse Analytics`.

8.1. Leverage Built-in Activities: Take advantage of built-in activities within the pipelines, which do not require a linked service.
</details>

## 2. Analytical Data Store
- Relational data warehouses, file-system-based data lakes (sometimes called data lakehouses or lake databases), or hybrid architectures are used for large-scale analytics.
- These data stores optimize analytical queries and accommodate significant data volumes.

There are two common types of analytical data store.

## (1). Data Warehouse

A data warehouse is a relational database in which the data is stored in a schema that is optimized for data analytics rather than transactional workloads. 

A data warehouse is a great choice when you have transactional data that can be organized into a structured schema of tables, and you want to use SQL to query them.

<details>
  <summary>Schema</summary>

**Star Schema Elements**
- fact table, which are related to one or more dimension tables that represent entities by which the data can be aggregated. E.g. sales order data fact table
- dim table, e.g. customer, product, store, and time dimensions 
- purpose: enable you to easily find monthly total sales revenue by product for each store. 

**Snowflake Schema**

star schema is often extended into a snowflake schema, by adding additional tables related to the dimension tables to represent dimensional hierarchies. 

For example, product might be related to product categories. 
</details>

## **(2). Data Lake**

A data lake is a file store, usually on a distributed file system for high performance data access. 

Technologies: like Spark or Hadoop are often used to process queries on the stored files and return data for reporting and analytics. These systems often apply a schema-on-read approach to define tabular schemas on semi-structured data files at the point where the data is read for analysis, without applying constraints when it's stored. 

Usecase: supporting a mix of structured, semi-structured, and even unstructured data that you want to analyze, without the need for schema enforcement when the data is written to the store.

## **Hybrid approaches**

- Hybrid Approach: This approach combines features of `data lakes` and `datawarehouses`.
- Raw Data in Data Lake: The raw data is stored as files in a `data lake`.
- Relational Storage Layer: A relational storage layer abstracts the underlying files and exposes them as tables.
- SQL Queries: The tables in the relational storage layer can be queried using SQL.
- PolyBase in Azure Synapse Analytics: SQL pools in Azure Synapse Analytics include PolyBase, which allows defining external tables based on files in a `data lake` (and other sources) and querying them using SQL.
- Lake Database Approach: Azure Synapse Analytics also supports a Lake Database approach. It involves using database templates to define the relational schema of a data warehouse while storing the underlying data in data lake storage. This approach separates the storage and compute for the data warehousing solution.
- Data Lakehouses: Data lakehouses are a relatively new approach in Spark-based systems. They leverage technologies like Delta Lake, which adds relational storage capabilities to Spark. With data lakehouses, you can define tables that enforce schemas and transactional consistency, support batch-loaded and streaming data sources, and provide a SQL API for querying.


## Azure services for analytical stores

### Synapse Analytics 

**Scalable Data Warehousing:**
   - Synapse Analytics enables you to build and manage a scalable, high-performance SQL Server-based relational data warehouse.

**Data Lake Integration:**
   - It supports integration with a data lake, allowing you to store and analyze large volumes of structured and unstructured data.

**Apache Spark Integration:**
   - Synapse Analytics seamlessly integrates with Apache Spark, an open-source distributed processing framework, providing powerful capabilities for big data processing and analytics.

**Log and Telemetry Analytics:**
   - Native support for log and telemetry analytics through Azure Synapse Data Explorer pools, enabling analysis and insights from log and telemetry data.

**Data Ingestion and Transformation:**
   - Built-in data pipelines facilitate efficient data ingestion and transformation, simplifying the process of getting data into the analytics environment and preparing it for analysis.

**Azure Synapse Studio:**
   - All Azure Synapse Analytics services can be managed through Azure Synapse Studio, a comprehensive user interface. It provides a unified management experience, allowing you to manage, monitor, and develop analytics solutions. It also supports the creation of interactive notebooks for collaboration and documentation, combining Spark code and markdown content.

### Databricks 

- **Comprehensive Data Analytics Solution**: built on Apache Spark

- **Native SQL Capabilities**: enabling the use of SQL queries for data analysis and exploration.

- **Workload-Optimized Spark Clusters**: esigned for data analytics and data science workloads.

- **Interactive User Interface**: allows you to manage the system and explore data using interactive notebooks.

- **Existing Expertise and Multi-Cloud Support**

## 3. Analytical Data Model
- Data models (e.g., cubes) are created to pre-aggregate data for easier reporting and visualization.
- Numeric data is aggregated across dimensions to support drill-up/drill-down analysis.
- Models capture relationships between data values and dimensional entities.

## 4. Data Visualization
- Data analysts and non-technical users create reports, dashboards, and visualizations.
- Visualizations show trends, comparisons, and key performance indicators (KPIs).
- They can be presented in various formats, including printed reports, graphs/charts, web-based dashboards, and interactive environments.
