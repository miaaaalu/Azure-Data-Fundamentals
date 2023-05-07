# Learning Notes

## Blob Storage (Binary large object)

| Aspect    | Details                                                                            |
| --------- | ---------------------------------------------------------------------------------- |
| Purpose   | Store unstructured data as blobs in the cloud                                      |
| Access    | Data files can be read and written using the Azure blob storage API                |
| Container | Blobs are stored in containers                                                     |
| Hierarchy | Blobs can be organized into a hierarchy of virtual folders using the "/" character |
| Use Cases | Serving images or documents to a browser                                           |
|           | storing files for distributed access, streaming video and audio                    |
|           | storing data for backup and restore, disaster recovery, and archiving              |
|           | storing data for analysis by an on-premises or Azure-hosted service                |


## Azure Blob Type
![IMAGE](https://miro.medium.com/v2/resize:fit:720/format:webp/0*PYSS__o2sYQBYgKd.png)

**Block blobs**
|              | Block Blob                                |
| ------------ | --------------------------------------- | 
| Handling     | Collection of blocks that form a file    |
| Maximum Size | Over 4.7 TB (up to 50,000 blocks)         |
| Block Size   | Up to 100 MB per block                    |
| Usage        | Best for very large, binary files         |
|              | Suitable for videos, high-resolution     |
|              | images, backups, and archives             |
|              | that change infrequently                  |


**Page blobs**

| Aspect | Details |
| ------ | ------- |
| Organization | Collection of fixed-size 512-byte pages |
| Purpose | Optimized for random read and write operations |
| Page-level Access | Fetch and store data for a single page |
| Maximum Size | Up to 8 TB of data |
| Usage | Implement virtual disk storage for virtual machines |


**Append blobs**

| Aspect | Details |
| ------ | ------- |
| Optimization | Optimized for append operations |
| Update and Deletion | Updating or deleting existing blocks is not supported |
| Block Size | up to 4 MB per block |
| Maximum size | just over 195 GB |

## Blob Storage Access Tiers 

|             | Hot tier                 | Cool tier                                                                                         | Archive tier                                                             |
| ----------- | ------------------------ | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Default     | Yes                      | No                                                                                                | No                                                                       |
| Use Cases   | Frequently accessed data | Infrequently accessed data                                                                        | Rarely accessed data                                                     |
|             |                          | It's common for newly created blobs to be accessed frequently initially, but less so as time pass | intended for historical data that mustn't be lost                        |
| Performance | High                     | Lower than Hot tier                                                                               | Lowest                                                                   |
| Latency     | Low (ms)                 | Low (ms)                                                                                          | High (hours)                                                             |
| Storage     | High-performance media   | Lower-performance media                                                                           | Offline state                                                            |
| Cost        | Highest                  | Lower than Hot                                                                                    | Lowest                                                                   |
| Retrieval   | Immediate                | Immediate                                                                                         | Hours                                                                    |
|             |                          |                                                                                                   | Requires access tier change and rehydration                              |
| Migration   | Not need                 | Optional, Can migrate to/from Hot tier                                                            | Required. Can migrate to/from Cool tier, requires rehydration for access |
| Rehydration | Not required             | Not required                                                                                      | Required                                                                 |



You can create lifecycle management policies for blobs in a storage account. A lifecycle management policy can automatically move a blob from Hot to Cool, and then to the Archive tier, as it ages and is used less frequently (policy is based on the number of days since modification). A lifecycle management policy can also arrange to delete outdated blobs.



Referenec

1. [What Is a BLOB?](https://medium.com/geekculture/what-is-a-blob-83e65f590694)

2. [Explore Azure blob storage
](https://learn.microsoft.com/en-us/training/modules/explore-provision-deploy-non-relational-data-services-azure/2-azure-blob-storage)

3. [Azure 基础：Blob Storage](https://www.cnblogs.com/sparkdev/p/6441421.html#:~:text=Blob%20Storage%20%E6%98%AF%E4%BB%80%E4%B9%88%EF%BC%9F,%E8%BF%99%E4%B8%AAURL%20%E6%9D%A5%E8%AE%BF%E9%97%AE%E6%96%87%E4%BB%B6%E3%80%82)