# Azure data fundamentals

## Module 1: explore core data concepts

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

## Module 2: Explore relational data in Azure

### Azure SQL DB
- highly scalable cloud database service with build in high availability and machine learning. Always encrypted,
- **Azure SQL DB Managed instance** combines leading security features with SQL server compability and business model designed for on-permises customers.
- Azure SQL Managed Instance Option
 - pre provision compute resources for migration, enables cost efficient migration, enables cost-efficient migration. *Instance pool?*
- Azure SQL Database resources sharing between multiple databases to price optimize, simplified performance management for multiple databases, fully managed service. *Elastic pool?*

PostgresSQL: is the most popular and wanted database for modern apps, relational and custom data types. Ability geo. PGSQL
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

## Module 3: Explore non-relational data in Azure
# Lesson 1

### Introduction to SQL
Statements types:

**DML** Data manipulation language: SELECT, INSERT, UPDATE, DELETE. Some dialects, PGSQL post gress SQL.

**DDL** CREATE, ALTER(modify structure), DROP, RENAME -  create modify and remove
DCL grant revoke deny

element of the SELECT statement:
```
1.  SELECT
2.  FROM
3.  WHERE
4.  GROUP BY
5.  ORDER BY

HAVING: 
```

Database based on server

### Query Tools
Azure portal
Sql management studio
Sql server data tools

### Query relational data in Azure SQL Database for PostgresSQL


Azure data studio 
SQLCMD
Azure CLI/Cloud Shell
