# Learning Note 

| Aspect                           | Details                                                                                                                                                                         |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Capacity                         | Share up to 100 TB of data in a single storage account                                                                                                                          |
| File Share Size Limit            | - Maximum size of a single file is 1 TB; <br>- quotas can be set to limit share size below 1 TB                                                                                 |
| Concurrent Connections           | supports up to 2000 concurrent connections per shared file                                                                                                                      |
| Uploading Files                  | - using the Azure portal or tools like AzCopy utility. <br>- File Sync Service, allows synchronization of locally cached copies of shared files with data in Azure File Storage |
| Performance Tiers                | - Standard Tier: Uses hard disk-based hardware, suitable for general-purpose file storage<br>- Premium Tier: Uses solid-state disks, offers higher throughput but higher cost   |
| Supported File Sharing Protocols | - Server Message Block (SMB): Commonly used across multiple operating systems (Windows, Linux, macOS)<br>- Network File System (NFS): Used by some Linux and macOS versions     |
| Pricing                          | - Standard Tier: Lower cost<br>- Premium Tier: Higher cost due to improved performance                                                                                          |


## Table Storage 

| Aspect                       | Details                                                                                                                                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Data Model                   | NoSQL storage solution that uses tables with *key/value* data items                                                                                                                                              |
| Table Structure              | Each row represents an item and contains columns for data fields                                                                                                                                               |
| Unique Key                   | Each row must have a unique key composed of a partition key and a row key                                                                                                                                      |
| Semi-Structured Data         | Azure Tables store semi-structured data with varying columns in each row                                                                                                                                       |
| Denormalization              | Data is denormalized, with each row holding the entire data for a logical entity                                                                                                                               |
| No Foreign Keys or Relations | Azure Tables do not support foreign keys, relationships, stored procedures, views, or other objects found in relational databases                                                                              |
| Partitioning                 | Tables are split into partitions based on a common property or partition key                                                                                                                                   |
| Benefits of Partitioning     | - Groups related rows together<br>- Improves scalability and performance<br>- Independent growth or shrinkage of partitions<br>- Helps narrow down data searches by including partition key in search criteria |
| Key Structure                | Key comprises a partition key that identifies the partition and a row key that is unique within the partition                                                                                                  |
| Ordering within Partitions   | Items within the same partition are stored in row key order                                                                                                                                                    |
| Point Queries                | Enables quick point queries to identify a single row                                                                                                                                                           |
| Range Queries                | Supports range queries to fetch a contiguous block of rows in a partition                                                                                                                                      |
