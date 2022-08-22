# I. Databricks lakehouse platform

- data warehousing
- data engineering
- data streaming
- data science and ML


## Data lake
- analytics and data scientists quickly find insights and share models on an open platform. 
- **Databricks Lakehouse** single unified system.
- Open source data platforms.

### Datawarehousing on data lake
bronze-> silver -> gold

### Databricks Platform Security

Keepind data safe access control, code isolation, control plane and control plane, secure cluster connectivity 
define data access control over organization, 
compilance and certification regulations

### Knowledge test 1

*1. The three primary services that comprise the Databricks Lakehouse Platform include Databricks Data Science & Engineering Workspace, Databricks SQL, and *
- Databricks Machine Learning

*2. Which of the following is true about Databricks?*
- It provides organizations with a collaborative platform to work with big data, and is primarily aimed at data engineers, data scientists, data analysts, and machine learning practitioners

*3. Which of the following is a problem with the data warehouse model that is resolved by the Databricks Lakehouse Platform?*
- Poor support for data science, AI, and streaming

*4. Which of the following is a common problem faced by data practitioners?*
- Difficult to develop a consolidated data policy
- Siloed functional roles for individuals on data science teams
- Hard to translate proprietary data formats from one tool to another

*5. Which of the following is a common problem with data lakes*
- data reliability

*6. Which of the following security features come built-in with the Databricks Lakehouse Platform?*
- ACID transactions and Unity Catalog

*7. Which of the following compliances does Databricks support security controls for?*
- HIPAA, GDPR, CCPA

*8. The Lakehouse was created by combining the most useful elements of data lakes and ______.*
- Data warehouses



## Databricks SQL

## Databricks workspace Data Science and Engineering

#### Datascience and engineering workspace assets**
- noteboks
-  folders
-  repos
-  secrets
-  jobs
-  pipelines 
-  clusters
-  pools


### Knowledge test 2

*1. A data practitioner would most likely use the Databricks Data Science and Engineering Workspace to:*
 - Use Databricks Notebooks to collaborate with team members in a variety of programming languages.

*2. The Databricks Databricks Data Science and Engineering Workspace allow data practitioners to:*
- Integrate Databricks notebooks into a CI/CD workflow

*3. How do you view a job run’s details in the Databricks Data Science and Engineering Workspace?*
- Navigate to the Workflows page, and access the job run details from the “Runs” tab for the job.

*4. Which of the following assets automatically runs tasks in the Databricks Data Science and Engineering Workspace?*
- Jobs

*5. Which of the following Data Science and Engineering Workspace assets provide key-value storage for sensitive information, allowing you to easily decouple such material from code?*
- Secrets

*6. Which of the following Data Science and Engineering Workspace assets reduce cluster start and auto-scaling times by maintaining a set of idle, ready-to-use virtual machine instances?*
- Pools

*7. Which of the following Data Science and Engineering Workspace assets provide the ability to sync Notebooks and files to a remote Git repository?*
- Databricks Repos

## Databricks Machine Learning

### Security
**Unity Catalog** is a fine-grained governance solution for data and AI on the Lakehouse. Unity Catalog helps simplify security and governance of your data with the following key features:
 
###  MLFlow Components
- **Tracking**: track models and results
- **Models** manage and deploy
- **Projects** reusable code
- **Model Registry** full lifecycle stage transitions
- **Model Serving** real time serving

### Knowledge test 3
*1. Where does Databricks Machine Learning fit into the Databricks Lakehouse Platform?*
- It is one of the core services of the Lakehouse Platform, tailored towards data practitioners building and managing models

*2. Which of the following scenarios would be best tackled using Databricks Machine Learning?*
Tracking and cimparing the results of data science experiments

*3. Which of the following two Databricks Machine Learning features, when used together, enforce governance and security for machine learning projects?*
- ACLs and Unity Catalog

*4. Which of the following are MLflow components?*
- Model Serving, Projects, Tracking

*5. Which of the following machine learning libraries are included in Databricks Runtime ML?*
- TensorFlow, XGBoost, NLTS

*6. MLflow __________ is a format for packaging data science code to streamline machine learning operations.**
- Projects

*7. An MLFlow run tracks which of the following?*
- Any parameters and values of the parameters from the run


*8. How does Feature Store solve one of the most common problems on data science teams?*
- It provides a Registry that keeps track of all features that have been created and facilitates reuse across different models.

# II. Databricks module

## Module 1: Databricks Workspaces and Services

Data Lakehouse: one platform to unify all of data, analytics and AI workloads
- Data Lake poor support for BI
- Data Warehouse good BI but poor machine learning

Heart of Data warehouses: Data lake, reliability with ACID transactions, time travel, utilized advanced caching and indexing, support for fine grained access control, can decide who can access data.

Lakehouse is build on the top of it and its:
- simple, data exists only once one common platform
- open source projects: redash, ml flow, delta lake, spark, koalas
- colloborative: share across all workloads: models, dashboards, notebooks, datasets

Lakehouse, data are in Data lake data dont have to be copied to different platforms, 

## Databricks architecture and services
- *contol plane*: back end architecture, majority of data does not live here.
- *data plane*: all data are processed, reside in cloud account.


#### Databricks Services_
- ML
- data science and enginniering 
- sql

#### Clusters, computations resources, clusters live in data plane, set of one of more VM, driver node, and worker nodes
 - **drivers** coordinates activities 
 - **executors** run tasks composing a Spark job
 
 ##### All purpose clusters
 - analyze data collaborativiely 
 - best for performing ad-hoc analysis, data exploration or development 
 
 ##### Job Clusters
 - can't restart
 - up to 30 clusters
 - databricks job scheduler creates job clusters when running jobs

##### Assets
Things we can create in workspace
- notebook, table, clusterm job, pipeline, repo


# Git version with databricks repos

## Databricks repos: clone pull, add, commit, push, branching
[CI/CD workflows with Databricks Repos and Git integrationk](#https://docs.databricks.com/repos/ci-cd-best-practices-with-repos.html)

- migration 1.3.

- pull regulary


# 1.3 L: Getting started with Databricks Platform

%run : run notebooks from different locations 
- `%run` 
 - example `%run ./Notebook_B` if notebook are merged together
 - `display` will display as data frame
 - metadata = `dbutils.fs.ls`
 - SELECT * FROM delta .`${DA.paths.datasets}/nyctaxi-with-zipcodes/data`

## Module 2: Data Lake


### 2.0 What is Delta Lake

Open source project. optimized for cloud object storage, ACID for object storage transaction guarantees, A: success or fail, C:varies the most, I: D, changes are permanemt

solved issues:
how append data: consistency by atomic actions, modification, changes are not commited until data jobs are done, real time operation, 
- Delta lake is default

### 2.1 Managing Delta Tables
**Atomic operations work independently**

- `Delta lake` default format for all tables created in databricks
- empty table `CREATE TABLE` students (id `INT`, name `STRING`, value `DOUBLE`) -> dont use `delta` because delta is default in databricks.  
 - `CREATE TABLE IF NOT EXISTS` students 
- can insert separately or can insert as one single transaction: INSERT INTO students VALUE (4, "Ted". 4.7)
- views temporary: `CREATE OR REPLACE TEMPORARY VIEW`
- `UPDATE` -> `SET` -> `WHERE`
- `MERGE INTO` students b USING students c `ON` "matching columns" WHERE MATCHED AND` u.type = "update" `THEN UPDATE SET *`

### 2.2 Manipulation Tables with Delata Lake Lab

```
MERGE INTO beans a
USING new_beans b
ON a.name=b.name AND a.color = b.color
WHEN MATCHED THEN
  UPDATE SET grams = a.grams + b.grams
WHEN NOT MATCHED AND b.delicious = true THEN
  INSERT *
```

### 2.3 Advanced Delta Lake Features

Temporary view usually are mainly to update tables.

**Hive** metastore to register databases, tables, views

- `DESCRIBE EXTENDED`: shows metadata about tables
 - explore files from above: `dbutils.fs.ls`  
- Transaction saved in _delta_log

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
