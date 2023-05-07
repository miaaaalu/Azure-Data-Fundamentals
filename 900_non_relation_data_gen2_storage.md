# Learning Note

> ADLS Gen2 = Azure Blob Storage + ADLS Gen1

## Blob Storage vs.  ADLS Gen2
| Use Cases | Blob storage | Gen2 |
| --- | --- | --- |
| Serving images or documents directly to a browser | ✔️ |  |
| Storing files for distributed access, such as installation | ✔️ |  |
| Streaming video and audio | ✔️ |  |
| Storing data for backup and restore, disaster recovery, and archiving | ✔️ |  |
| Writing to log files | ✔️ |  |
| Any type of text or binary data, such as application backend, backup data, and general-purpose data | ✔️ |  |
| Creating a modern data warehouse |  | ✔️ |
| Advanced analytics against big data |  | ✔️ |
| Creating a real-time analytical solution |  | ✔️ |
| Hadoop compatible access (HDFS, ABFS) is required. Access it through compute technologies including Azure Databricks, Azure HDInsight, and Azure Synapse Analytics without moving the data between environments |  | ✔️ |
| ACL and POSIX permissions along with some extra granularity support is required |  | ✔️ |
| Batch, interactive, streaming analytics, and machine learning data |  | ✔️ |


## Reference
1. [Ashish Pate- Azure — Difference between Azure Blob Storage and Azure Data Lake Storage (ADLS)
](https://medium.com/awesome-azure/azure-difference-between-azure-blob-storage-and-azure-data-lake-storage-comparison-azure-blob-vs-adls-gen2-81af5ef2a6e1)
2. [Azure Data Lake Storage Gen2 简介
](https://learn.microsoft.com/zh-cn/azure/storage/blobs/data-lake-storage-introduction)
