# Learning Note 

## Intro
| Key Aspect             | Conventional Data Warehousing                                          | Big Data Processing Solutions                                                                                                                                                   |
| ---------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Data Handling Approach | Copying data from transactional data stores into a relational database | Handling large volumes of data in multiple formats, batch loaded or captured in real-time streams                                                                               |
| Data Storage           | Relational database with optimized schema                              | Data lake                                                                                                                                                                       |
| Data Types             | Structured data                                                        | Structured and unstructured data                                                                                                                                                |
| Use Cases              | Business intelligence, reporting                                       | Complex analytics, machine learning on large datasets                                                                                                                           |
| Querying               | SQL                                                                    | Distributed processing engines like Apache Spark                                                                                                                                |
| Tool/Platform          | Microsoft SQL Server, Oracle Database, IBM Db2, Teradata, Snowflake, Redshift               | Apache Hadoop, Apache Spark, Apache Kafka, Apache Flink, Google Cloud Dataflow, Databricks, Amazon EMR,Azure Synapse Analytics, Azure Data Lake Storage, Azure Stream Analytics |
|  |

## data warehousing architecture
### 1. Data Ingestion and Processing

![data ingestion pipelines](https://learn.microsoft.com/en-us/training/wwl-data-ai/examine-components-of-modern-data-warehouse/media/pipeline.png)
***
- Data is sourced from transactional data stores, files, real-time streams, etc.
- Extract, transform, and load (ETL/ELT) processes are used to clean, filter, and restructure the data.
- Ingestion includes batch processing of static data and real-time processing of streaming data.
- Distributed systems handle high volumes of data in parallel.
***

Azure Large-Scale Data Ingestion Instructions

    1.1. Choose the Pipeline Engine: Select either `Azure Data Factory` or `Azure Synapse Analytics` to create and run the pipelines.

    2.1. Define Activities: Construct pipelines with one or more activities that operate on data, starting with an input dataset and progressing through incremental manipulations.

    3.1. Utilize Linked Services: Use linked services in pipelines to load and process data, allowing for the use of appropriate technologies at each workflow step.

    4.1. Configure Data Sources: Ingest the input dataset using linked services like `Azure Blob Store`.

    5.1. Perform Data Processing: Apply transformations to the data using services such as `Azure SQL Database`, `Azure Databricks`, or `Azure HDInsight`.

    6.1. Implement Custom Logic: Optionally, incorporate custom logic using `Azure Functions`.

    7.1. Save Output Dataset: Store the resulting output dataset in a linked service like `Azure Synapse Analytics`.

    8.1. Leverage Built-in Activities: Take advantage of built-in activities within the pipelines, which do not require a linked service.

### 2. Analytical Data Store
- Relational data warehouses, file-system-based data lakes (sometimes called data lakehouses or lake databases), or hybrid architectures are used for large-scale analytics.
- These data stores optimize analytical queries and accommodate significant data volumes.

### 3. Analytical Data Model
- Data models (e.g., cubes) are created to pre-aggregate data for easier reporting and visualization.
- Numeric data is aggregated across dimensions to support drill-up/drill-down analysis.
- Models capture relationships between data values and dimensional entities.

### 4. Data Visualization
- Data analysts and non-technical users create reports, dashboards, and visualizations.
- Visualizations show trends, comparisons, and key performance indicators (KPIs).
- They can be presented in various formats, including printed reports, graphs/charts, web-based dashboards, and interactive environments.
