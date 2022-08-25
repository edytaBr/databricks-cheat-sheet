Exam questions:

1. *Entities*: Objects in which things about data should be captured and stored

- An entity is a thing in which information needs to be known or held. 
- A table is the object that stores a collection of entities. 
- A row represents a single instance of an entity.
- A column defines a specific property of an entity.

2. *Streaming data processing*: to process data that is generated continously and near real-time responses are required.

- **Streaming processing** - When data is generated on a continual basis and insights must you must be able see data insights immediately,
process data as it arrives rather than storing and processing data later as a group. 

- **Batch processing**, scheduled processing, and buffering all collect and store data for later processing.

3. ETL (Extract, Transform, Load)  
- Optimize data privacy
- filter sensitive data before transformation
- simple dara models without need of using Data Lake

4. ELT - (Extract, Load, Transform)
- Provide support for Data Lake
- Manage large volumes of data

5. Descriptive analytics - what has happend by looking at historical data

6. Diagnostic analytics - analyze results from descriptive

7. Predictive analytics - helps to forecast the future values using historical data

8. Prescriptive analytics - helps you define actions (prescription) that you should perform to achieve what you need (or overcome a problem).

9. `Tables`:  Store instances of entities as rows

10. `Indexes`: improve processing speed for data searches

11. `Views`: display data from predefined queries

12. `Keys`: create relationships

13. **Normalization**: process of splitting an entity into more than one table to reduce data redundancy.

14. **Deduplication** is the process of removing duplicate data from tables.

15. **Denormalization** is the process of combining tables. This process is often used to store data in databases which are used for data mining and reporting.

16. Optimization is the process of modifying fields and database structure to improve overall performance.

17. Azure SQL is an example of PaaS -  Platform as a service.

18. Infrastructure-as-a-service includes technologies such as virtual machines and virtual networks.

19. Software-as-a-service describes a method of software delivery in which users license software online by subscription. Microsoft offers subscriptions to license Office products like Microsoft Excel.

20. Application-as-a-service describes applications that are hosted in the cloud and offered to users by subscription. This is like software-as-a-service but often relates to custom line-of-business solutions.

21. There are no Azure data services that use the software-as-a-service or application-as-a-service model.
22. Azure Data Studio - query data located in a non-Microsoft Platform. Its cross platform database, that can be used on booth: on perms and cloud dataplatforms.
23. Azure Query Editor - query data from within the Azure Portal. Can be used to query data in Azure SQL databases.
24. SQL Server Datat Tools query data while working within a Visual Studio project. We can connect and then use it to query data on perms and in the cloud.
25. Scaling is the act of increasing or decreasing the resources used by a service. 
26. Computing is the act of processing data.
27. Provisioning is the act of running series of tasks to create and configure a service. 
28. Networking is the act of providing connectivity to a data resource.
29. `JOIN` Combine rows from multiple tables
30. `WHERE` filter records
31. `SUM` calculate the total value of numeric column
32. `COUNT` determine the number of rows retrieved
33. Non-relational data
  - flexible storage and ingested data
  - entities are self describing
  - entities may have different fields

34. Relational data
  - forced schemas
  - forced each rows to maintain the same columns 
35. Azure Cosmos DB is non relational document DB that supports high latency for both reading and writing. Only this one supports creating graph databases. It adds indexes automatically on elements. If we need to store in the azure environment that supports efficient non-key, field-based searching. 
36. Azure Table Storage is a NoSQL key-value storage that supports semi-structured data with dynamic column. This technique optimizes both data retrieval and writing but performance is not good when searching on non-partition key and non-key values.
37. Azure File Storage and Blob Storage are for files and BLOBs, not for searchable JSON documents.
38. Azure Table Storage is non-relational data store. To optimize data retrieval we should use partition key and row key. Azure Table storage does not support searching on properties.
39. To provision Azure Storage we should use Azure Resource Manager (ARM) templates. Azure portal, Azure CLI Azure PowerShell do not use text JSON files.
40. Data warehouse -  should be used to deploy and support analytical queries that involve high volume data and generating aggregated values. Thus perform sakes trend analyses.
41. Recording daily sales, printing reports, and searching sales orders are typical operations seen in online data processing (OLTP) databases and not in data warehouses.
42. Azure Synapse Analytics and Azure Databricks both support using Apache Spark clusters to process data. Azure Cosmos DB is for non-relational data. You can use Azure Data Factory for data integration and migration.
43. To get data from az Azure SQL database by using Azure Data Factory we should use: linked service and dataset.
  - To get data from a source, you need to create a linked service for Azure Data Factory. The linked service contains details about the data source including the server name and credentials. You must also define a dataset to describe the expected data structure. A dataset stores data retrieved from a data source.
  - You can use the Copy data activity for transferring data from one source to another (destination).
  - You can use an Azure Databricks notebook for processing data using spark clusters with given instructions.

44. Datasets: in this way we can present data we want to ingest.
45. A dataset represents the data that you want to ingest for processing. A dataset can also represent output data from a process.
46. pipeline to perform tasks and processes.
47. linked service to connect to a source or destination.
48. notebook can contain cells that read data, process data, and write the results out to a data store.
49. Power BI reports as paginated reports - case scenario
  - a report that has a table visual with an ability to print all the data in the table AND
  - report with a repeatable header and footer AND
  - a report that is formatted to fit well on a printed page
  - When a Power BI report that has a table visual contains multiple rows, printed, only records that can are displayed will be printed.
  - All records print if you design the report by using Report Builder as a paginated report, all records print.
  - Only paginated report supports repeatable headers and footers.
  - You cannot create paginated reports by using Power BI visuals. You must use Report Builder instead.





### References

https://docs.microsoft.com/learn/modules/describe-concepts-of-relational-data/2-explore-characteristics
https://docs.microsoft.com/learn/modules/explore-core-data-concepts/4-describe-difference
https://docs.microsoft.com/learn/modules/explore-concepts-of-data-analytics/2-describe-data-ingestion-process
