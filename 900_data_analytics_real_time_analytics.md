# Understand batch and stream processing
## Batch Processing 
You can process data based on 
- a scheduled time interval, for example every hour 
- triggered the process when a certain amount of data has arrived 
- some other event 

**Advantages of batch processing**
- Large volumes of data can be processed at a convenient time.
- It can be scheduled to run at a time when computers or systems might otherwise be idle, such as overnight, or during off-peak hours.

**Disadvantages of batch processing**
- The time delay between ingesting the data and getting the results.
- All of a batch job's input data must be ready before a batch can be processed. This means data must be carefully checked. Problems with data, errors, and program crashes that occur during batch jobs bring the whole process to a halt. 

## Streaming Processing 
- In stream processing, each new piece of data is processed when it arrives

## Difference between batch and real time 
| Aspect           | Batch Processing                          | Stream Processing                              |
|------------------|--------------------------------------------|-------------------------------------------------|
| Data Scope       | Processes all data in the dataset.         | - Only has access to the most recent data received <br> - or rolling data (e.g. the last 30s data).   |
| Data Size        | Suitable for handling large datasets.       | Designed for individual records or micro batches.|
| Performance      | Latency is typically a few hours.           | Latency is in the order of seconds or milliseconds.|
| Analysis         | Used for complex analytics.                 | Used for simple response functions, aggregates, or calculations such as rolling averages.|

## Combine batch and stream processing
![batch and stream processing](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-fundamentals-stream-processing/media/lambda-architecture.png)
<details>
<summary>batch and stream processing in a large-scale data analytics architecture.</summary>

1. Data events from a streaming data source are captured in real-time.
2. Data from other sources is ingested into a data store (often a data lake) for batch processing.
3. If real-time analytics is not required, the captured streaming data is written to the data store for subsequent batch processing.
4. When real-time analytics is required, a stream processing technology is used to prepare the streaming data for real-time analysis or visualization; often by filtering or aggregating the data over temporal windows.
5. The non-streaming data is periodically batch processed to prepare it for analysis, and the results are persisted in an analytical data store (often referred to as a data warehouse) for historical analysis.
6. The results of stream processing may also be persisted in the analytical data store to support historical analysis.
7. Analytical and visualization tools are used to present and explore the real-time and historical data.
</details>

# Streaming processing architecture 
General Processing for stream processing 
1. Generating - An event generates some data. 
    - a social media post
    - a log file ..
2. Ingesting - The generated data is captured in `a streaming source` for processing. 
    - a cloud data store
    - a table in a database
    - a "queue" that encapsulates logic 
3. Processing - The event data is processed.
    - often by a perpetual query that operates on the event data to select data for specific types of events, project data values, or aggregate data values over temporal (time-based) periods (or windows) - for example, by counting the number of sensor emissions per minute.
4. Loading - streaming data results are written to an output/sink
    - a file 
    - a database table 
    - a real-time visual dashboard
    - another queue for further processing by a subsequent downstream query

## Ingestion - `Sources` for stream processing
- Azure Event Hubs
    - tool: A data ingestion service 
    - use case: manage queues of event data, ensuring that each event is processed in order, exactly once.
- Azure IoT Hub
    - tool: A data ingestion service
    - use case: optimized for managing event data from IoT devices.
- Azure Data Lake Store Gen 2
    - tool: A highly scalable storage service 
    - use case: 
        - used in batch processing scenarios
        - used as a source of streaming data
- Apache Kafka
    - An open-source data ingestion solution 
    - use case: commonly used together with Apache Spark. You can use Azure HDInsight to create a Kafka cluster.

## Output - `Sinks` for stream processing
- Azure Event Hubs: 
    - Store: as a queue 
    - use case: for further downstream processing.
- Azure Data Lake Store Gen 2
- Azure blob storage
    - Store: as a file.
- Azure SQL Database
- Azure Synapse Analytics
- Azure Databricks
    - Store: as a table in a database table 
    - use case: for querying and analysis.
- Power BI: 
    - Use case: to generate real time data visualizations in reports and dashboards.

# Azure Stream Analytics 
![](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-fundamentals-stream-processing/media/stream-analytics.png)

Stream Analytics is used to:
1. Ingest data from an [input](#ingestion---sources-for-stream-processing)
    - Azure event hub 
    - Azure IoT Hub
    - Azure Storage blob container
2. Process the data by using a query to `select`, `project`, and `aggregate data values`.
3. Write the results to an [output](#output---sinks-for-stream-processing)
    - Azure Data Lake Gen 2
    - Azure SQL Database
    - Azure Synapse Analytics
    - Azure Functions
    - Azure event hub
    - Microsoft Power BI, or others

# Aphache Spark on Azure 


# Azure Data Explorer
