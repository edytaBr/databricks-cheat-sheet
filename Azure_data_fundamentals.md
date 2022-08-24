# Azure data fundamentals

## Explore core data concepts

#### Data types:
strudctured (tables), semistructures(JSON. not all fields), unstructured(pictures, sound, video).

#### Data stores
- file stores
- databases

#### Common formats
- Delimited text files
- JavaScript Object Notation (JSON)
- XML and it's tags
- Binary Large Object (BLOB)
- Optimized file formats that helps with compression, indexing, efficient storage and processing
 - AVRO -  row based format, good for compresing data and minimizing storage and network bandwidth 
 - ORC - organize data in columns rather rows, contains stripes
 - Parquet - row groups, , parquet files incuudes metadata that describes the set of rows found in each chunk.

# Explore databases
- Relational database - structured data data represents entity, PK, FK thus data can be normalized, 
- Non relational - dont apply relational schema to the data, 
 - key-value databases - each record consist of a unique key
 - document database -  form of key database in which the value is a JSON document
 - column family databases - store tabular data cinprising rows and columns, but we can divide columns into group columns - columns family - like data about customers, products they bought.
 - graph databases - entities as nodes with links to define relationships between them.


## Explore transactional data processing
- primary function of business computing
- transactions as small events, (moving money between two accounts) - transactional systems might have many milions of transactions. 
- Online Transactional Processing (OLTP) - work performed by transactional systems -  suport CRUD operations, - suport acud sematics
- 

# Module 1: explore core data concepts

- structured: schema, rows columns
- semi-structured, doent fit into rows, columns, but have fags and keys -> data stored in json. 
- unstructured no scheme or structred - video, audio img.

Data Stores
- Transactional data stores - primary function of business computing, 
 - High volumes, ONLTP, divided into pices, bank transfer
 - Normalization - spliting data into tables, can make query quite complex, usually we have to join data
- **Analytical data stores** : capturing row data and generating buisness decissions. 
- Data ingestion
- Data Storage
- Data processing
- Data visualization
 - data ignestion- capturing new data, recording, collection of data, 
 - store data in repository - doc. db, 
 - raw data, no suitable format -> anomalies, transformation, cleaning, we want to visualize
- Data processing: make something useful from your data, 
 - **streaming processing**: as it arrived straming, each new is processed as it has arrvied. in real time, handles data in real time, no waiting until new batch,data as it has come in. when we are dealing with new dynamical data.
 - **batch** processing new data are collecting into groups. large parts of data at conviniet time, , there is always time delay, between ingestion and processing. data need to be carefully checked. 

!!!!!!!!!! https://docs.microsoft.com/nb-no/learn/modules/explore-core-data-concepts/6-analytical-processing


# Lesson 2
roles in data:
- **data administrator**
 - manage data, implies security, user access, monitor performance
 - maintatining data performance, policies are implemented, backups. 
- **data engineer**: azure synapse studio, sql server managment studio, azure portal/cli
 -  pipelines and processes
 -  data ingestion and storade
 -  analytics preparation, prepare data 
 -  data performance as expected, cleaning, 
- **Data analyst** power BI desktop, power bi portal, power bi service, 
 - design

# Lesson 3
Relational data

- row, columns, data types, easy to store information.
- stored in tables
- *entity* thing
- columns defined by a datatype

### Normalization
- reduce storage
- avoid data duplication
- in normalized database schema
 - PK and FK are used to define relationships
 - no data duplication exists (3NF)
 - data is retrived by joining tables together in a query 
- 
### Indexes
- optimizes search queries for faster data retieval
- reduces the amount od data pages that need to be read 

### View
- virtual table based on the result of the query

### NoSQL
- non relational
 - **key-value stores**: read and write data quickly
 - **document based**: data stored as documents with ID
 - **column family databases**: organizez data in rows and columns: parquet files, seems like relationals: but can divided columns in groups: column families, apache casandra
 - **graph databases**: stores nodes and edges: example, all employes in organization: node -> employe, edges: reporting line. Fine all employe who reports to IT manager, who is in the same departamet. Gremlin API

## Lesson 5

**Data analitics**
- geting data and getting picture how its going.
- strength and weaknesses in organization and make decisions.
- combine all data from mini sources to construct data warehouses.
1. **Data ingestion**: data could be ingested: stream/batch. Catch data. Might involve filtering, some transformation, convert to more standard format. Quick, not complex aggregation. 
2. **Data processing**: All data collected, raw format, clean it, more meaningful format, results can be used to visualiza and make query. Aim is to convert raw data into buisness model. Some agreggation, generate predictive. Automating, azure databricks. Stream oriented
 - **ETL**: extract, transform and load: continues pipeline, simple and basic models
 - **ELT**: extract, load, transform: stored before transform. then transform and complex processing. depend on multiple items, cloud workloads.
 
 ### Explore data visualization - power BI
 
 Azure Data Factory: cloud based data ignestion: create and schedule pipelines, that can ignest data from different data sources.
6. Data exploration:


## Lesson 4

### Non relational data
- multiple entities in the same collection or container with different fields
- have a different non-tabular schema
- are uften defined by labeling each field with the name it represents
- subfields []
- should have an unique id value `key value`
- semistructured data: contains fields. Format/file types include:
 - Json, avro, orc(strips of data. index, parquet (row groups, data are stored in row group, and metadata that described the chunks of data storing and processing nested data)

### Unstructured data
- does not naturally containg data: audio, video
- use azure blob storage
- often used to extract data from and categorize or identify structures, 

### Data analytics

- **descriptive**: what is happening, answer question what is going on, reports about financial data
- **diagnostics**: why is this happening, find out what the root cause it is: identify anomaly, collect data, and statistical method to discover the reason
- **predictive**: all about what is likely to happen in the future.
- **prescriptive**: what actions has to be taken to achieve the target
- **cognitive**: based on how the human brain works

# Module 2: Explore relational data in Azure

## Introduction
### Understand relational data

- *Realtional db* entities from real world as tables
- *Normalization* schema design process that minimizes data duplication and supports data integrity.
 - in involves separation of each entoty into tables, decomposition and then define each data type for proper column, separate atributtes into columns, define `PK` and `FK`

### SQL commands

1. **Data Definition Language** (DDL):  statements to create, modify, and remove tables and other objects in a database
 - `CREATE`
 - `ALTER`
 - `DROP`
 - `RENAME`
3. **Data Control Language (DCL)**: database administrators to manage access to objects
 - `GRANT`
 - `DENY`
 - `REVOKE`
 
 `GRANT SELECT, INSERT, UPDATE`\
 `ON` Product\
 `TO` user1
 
3. **Data Manipulation Language (DML)** to manipulate the rows in tables
 - `SELECT`
 - `INSERT`
 - `UPDATE`
 - `DELETE`
 - 

### Describe database objects

Database can store tables but additionally can contain other sturctures that help to optimize data organization.
- *views*: virtual table based on the result of a `SELECT` query, A virtual table based on the results of a query

- *stored procedures*: SQL statements that can be run on command `CREATE PRODECURE`, can be reused over and over again, runs with `EXEC`. A pre-defined SQL statement that modifies data

- *indexes*: help to search for data: like index in the book to find data faster, can improve performance when db is big. They are nor free, they consume some resources. A structure that enables queries to locate rows in a table quickly.

## Explore relational database services in Azure

### Describe Azure SQL services and capabilities

Azure SQL family - databases based services in Azure include:
- SQL server on Azure Virtual Machines (VMs) -  IaaS - running in azure with installation of SQL server. , virtuaøizes hardware infrastructure for compute, storage and networking. We manage all aspects of the server, including operating system and SQL Server, updates, configuration, backups, and other mainenance tasks. When customer still needs some administrative privillages. 
- 
- Azure SQl Managed Instance - PaaS - automated software update management, backups, maintenance tasks, recude administrative things. Fully automated updates, backups and recovery. 

- Azure SQL Database -  fully managed PaaS. Fully automated updates, backups and recovery.
 - Single Database
 - Elastic Pool -  resources reffered as pool, use resources available in the pool.
 - 
- Azure SQL Edge - optimized for IoT

### Describe Azure services for open-source databases

1. MySQL: simple. Community, Standard, Enterprise
 - Azure Database for MySQL: PaaS
 - Two deployment options: Single Server and Flexible Server

2. MariaDB: rewritten and optimized to improve performance
 - PaaS
3. PostgreSQL: can store and manipulate some  geometric data. Own language pgSQL 
 - PaaS
  - Single Server - similar to MySQL
  - Flexible Server - is fully managed database servise, with more control and server configuration, better costs optimatization controls.
  - Hyperscale (Citus) - database split across nodes, 


### Azure SQL DB
- highly scalable cloud database service with build in high availability and machine learning. Always encrypted,
- 
- **Azure SQL DB Managed instance** combines leading security features with SQL server compability and business model designed for on-permises customers.
- Azure SQL Managed Instance Option
 - pre provision compute resources for migration, enables cost efficient migration, enables cost-efficient migration. *Instance pool?*
- Azure SQL Database resources sharing between multiple databases to price optimize, simplified performance management for multiple databases, fully managed service. *Elastic pool?*

PostgresSQL: is the most popular and wanted database for modern apps, relational and custom data types. Ability geo. pgSQL
MariaDB: Engine is optimized, temporal data. 
MySQL:simple to use database management system. Community free, Standard, Enterprise.

Benefits of Azure Database for MySQL, PostgreSQL, MariaDB.
single server: postgres sql.  fully managed and secure, intelligent performance optimization, flexible and open
hyperscale: fully managed and secure, intelligent performance optimization, flexible and open, high performance scale out with hyperscale

## Lesson 2
Provisioning 

Configure relational data services
Provide provisioning parameters:
1. Basics: subscription (billing account), resource group, managed instance, server name, database name (null-creating new), admin login, password, region (data senter), opt in pools, compute and storage and backup configuration DTU. Pricing tiers, 3: Basic light computes, small scale, testing,. General purpose: balance computes: hosting web and mobile apps. servers that processes real time data.
2. Connectivity and Firewalls 1433, open data server to the world.

Connection Policy:
1. redirect connection policy: estabilish 
2. Proxy mode: all connection are proxied by azure sql gateways.outside from azure. while tcp is estabilished 
3. default

Network security - SQL Database

**Private endpoint**: use private IP address. Brings service to network.

Authentication and Access Controll
-single place to administrate uses and permissions to our db.
-MFA

## Access controll
RBAC: who and what can do with resources. Azure Role Based Access Control
- role: collection of permissions

Azure DB: Read replicas
- help improve performance and scale of read-intensive workloads such as BI and analytics. Replica new services, replica replaces the master in case of regional disasters. data storage replica servers grows automaticall without impacting workloads.h


### Module 4

#### Explore Azure Table Storage

#### Azure blob storage -  unstructured data

1. Block blobs 
consist of blocks
best for storing discrete large binary objects, each individual block can store up to 100MB of data

2. Page blobs fixed size 512 byte pages

3. Append blobs

rehadration - upgrade blob.

storing images, documents, searching directly in browser, vide and audio files, reduncandy for blobs - are stored in different regions
soft delete - able to recover
snapschot - version of blob in time, monitor changes

### Explore Azure File Store
create file shares - share up to 100 TB, share data, replicated within region and georeplicated, enable encryption, 

### Azure Cosmos DB - no relational data bases
all types of structures, noSQL data, manage data in partitions, json, data organized in containers, 
- document data base - 

container, table storage -> 

Cosmos DB APIs - can switch between cosmos api

- SQL API
- MongoDB API -> document database, to anable mongo db to run on cosmos DB (mongo on permises)
- Gremlin API -> graph db to azure cosmos db
- Table API
- Cassandra API - column dbms - on premises - cassandra like on cosmos db - document request - anable to quickly migrate cassandra api to cosmos db


##### Use cases for Azure Cosmos DB
1. Web and retail
2. Gaming - db tier is crucial, modern games performe graphical processing on mobile/console clients but rely on the cloud 
3. IoT systems - many data ingested, 

## Lesson 2 Explore provisioning - cosmos db

1. Azure portal - 
2. Azure CLI
3. Azure power shell
4. azure resource templates

Backup - cosmos - specify, 
Encryption - service managed or key encryption

Inside cosmos database we can create container.

#### Data migration tool
to import data - to container - target info - database to connect

#### Azure authentication

1. MFA 
2. configure storage accounts - 
3. geo redundancy 3 copies in your region and 3 in another one
4. 


## Module 3: Explore Azure Storage for non-relational data
 [Microsoft learn](https://docs.microsoft.com/nb-no/learn/modules/explore-provision-deploy-non-relational-data-services-azure/1-introduction)
 
 1. Azure storage - core service to store data in cloud
 
 1.1 Azure Blob storage
 - massive amoungt of unstructured data: binary or blobs.
  - blobs: blobs store **data files** in optimized in cloud. In azure storage account we store blobs in **containers** (easy way to group related blobs, and organize them into virtual folders) 
 - Blobs types:
  - **Block** - set of blocks (block is the smallest to read), *varry* in size up yo 50000 -  max size 4.7. Best to store discrete, large binary data that change infrequently. 
  - **Page** - *fixed* size pages, page can hold up 8 TB, used to implement virtual disk storage for virtual machines
  - **Append** - block to support append operations, only append: updating or deleting isnt't supported.
 - **3 tires in blob storage**
  - **Hot** - 
  - **Cold** - data accessed inrrequently
  - **Archive** - data we don't want to lost and have to be 

[Azure blob storage](/assets/azure-blob-storage.png)

1.2 Azure DataLake Storage Gen2
- structured, semi structured, unstructured daya sypred in **files**
- Gen2 is newer and: advantages - scalability if blob storage, cost conrtol of tiers, hierarchical file system capabilities, compability with major analytics system.
- to create use hierarchical namespace

![Azure blob storage](/assets/azure-data-lake.png)

1.3 Azure files
**File shares** - enables to store a file on one computer and give access to users on other computers - works on local areas, and not when users are distributed. 
Like files on local uni. On permises, shared between users. 100TB on single storage account, max size of 1 file is 1 TB, up to 2000 shared connections.
- we can upload file to azure file by using azure portal or azure file storage.
- Two performance tiers - based on medium: hard discs or ssd
- Two network file sharing protocols:
 - SMB  
 - NFS - premium tier
 
 
![Azure files](/assets/azure-files.png)


1.4 Azure tables
- noSQL
- tables with key/value data items
- not like relational databases - can have semi-structual data
- all rows must have unique key made of partition key and row key.
- when modified rows - time stamp is recorded
- no concept of foregin key, viewes, relationships, stored procedures, 
- normaly data are denormalized -  we dont have to split data into columns like in relational databases.
- Azure tables - to ensure fast access - data are split into partitions. 

**Partitioning** - mechanism for grouping related rows based on common property or partition key. The same partition key same storage. 


![Azure blob storage](/assets/azure-tables.png)


## Sandbox and knowledge check
Things you can put in the storage;\ for different data types:
- containers, with blobs
- file shares
- tables

Folders in blob storage are virtual, and only exist as part of the path of a blob. Since the products folder contained no blobs, it isn't really there! - we have to upload blob

Folders in a flat namespace blob container are virtual, and can’t be managed.

1. Azure data lake storage.
2. Azure Data Lake Store Gen2 support enables you to use hierarchical folders to organize and manage access to blobs. It also enables you to use Azure blob storage to host distributed file systems for common big data analytics platforms.
Data Lake Gen2 upgrade page -> upgrade your storage account to enable hierarchical namespace and support Azure Data Lake Storage Gen 2
3. Azure files
4. Azure Tables provide a key/value store for applications that need to store data values, but don't need the full functionality and structure of a relational database. In tables we add entity. Here we add keys. partition key and row key. Here we can manually enter values. 
5. Azure table storage key - partition key and row key
6. to support azure synapse analytics we should uograde the account to enable hierarchical namespace and create a blob container to an existing azure storage
7. azure file storage enables users at different sites to share files. 

## Explore fundamentals of Azure Cosmos DB
Azure Cosmos DB -  highly scalable database service for NoSQL data.
- supoorts many APIs
- highly scalable
- automatically allocates space in a container for partitions
- automated indexes
Usage:
- IOT and telematics - systems that ingest large amount of data, cosmos can accept data quickly, real time data process by using azure functions
- Retail and marketing .  
- Gaming 
- web and mobile applications - modeling social interactions

### Azure cosmos DB APIs

- by this we can migrate data from commonly  used NoSQL stores and apply their exisiting programming skills. When procisioning new Cosmos DB instance we can select API.

1. Core (SQL) API - can use SQL like language
2. MangoDB API -  data stored in binary json format (BJSON)
3. Table API - work with data in key-value tables -  similar to Azure Table Storage but Azure Cosmos offers greater scalability and performance than azure table storage
4. Cassandra API -  is compatibile - column-family storage structure -  similar to relational tables but not every row has to have the same columns. 
5. Fremalin API - data in graph structure, 

We can create additional Cosmos DB accounts across multiple regions. For Cosmos DB service region availability

## Explore data roles and services

1. Azure SQL - family of relational database solutions
 - Azure SQL Database PaaS
 - Azure SQL Managed Instance - more administrative responsibility than SQL Database
 - Azure SQL VM - virtuall machine with maximum configurability with full management responsibility
 - 
2. Azure Database for open source relational database
- MySQl
- MariaDB
- PostgreSQL

3. Azure Cosmos DB
- non-relational NoSQL
- supports many APIs: JSON documnets, key-value pairs, column families, graphs.

4. Azure Storage
- Blob containers binary files, cost efficient, scalable
- File shares - network file shares
- Tables - key-value storages when we need to read and write data quickly

Data enginieers use Azure Storage to host data lakes - blob storage with a hierarchical namespace that enables files to be organized in folders

5. Azure Data Factory
- allow to define and schedule data pipelines to transform and transfer, 
- data ingestion from the cloud
- used to build ETL 

6. Azure Synapse Analytics - comprehesive solutions: including: data ingestion pipelines, data warehouse storage and data lake storage throught one single service. 
- multiple analytics
 - pipelines as in Data Lake Factory
 - SQL - database engine
 - Apache Spark - distributed data base processing - multiple programming languages: Java, Scala, Python, SQL.
 - Azure Synapse Data Explorer  - real time querying
 
 7. Azure Databricks: zaure version of databricks, for large scale analytics
 8. Azure HDInsight - provides azure hosted clusters for popular apache open source big data processing. We use it to create clusters when we have workloads that depend on multiple open source technologies. 
 
  - Apache Spark
  - Apache Hadoop
  - Apache HBase
  - Apache Kafka
  - Apache Storm 
  
9. Azure Stream we can capture real data streamin into analytical data or for real-time visualization
10. Azure Data Explorer - query and analyze data with timestampsuch as is typically found in log files.
11. Microsoft Purview - enterprise wide data governance and discoverability
12. Microsoft Power BI - reporting and data modeling

