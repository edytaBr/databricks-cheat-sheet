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

## 3. Relational entities and Vievs

### 3.1 Databases and Viewvs
Creating table with default or defined location
hive variables  in `{}`


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

#### ZORDER optimatization

#### Reviewing Delta Lake Transactions - 

We can `RESTORE` our data - `RESTORE TABLE` table `TO VERSION OF 8`
`VACUUM`To clean old data we can clean our data, vacumm on delta table makes -  no travel back in the time. By default prevent to vacumm data younger than 7 days. Retention perdiod: how old they can be.
`DRY RUN` -  show what will be deleted

### 2.3L Delta Lake Versioning, Optimatization and Vaccuming Lab
- `DESCRIBE HISTORY beans` -  describes the history of the table
- tables are changing - thus we can take which version we will use - (read version) - `SELECT * FROM` beans `VERSION AS OF` 1
- RESTORE A PREVIOUS VERSION - 
`spark.databricks.delta.vacuum.logging.enabled`** to **`true`** to ensure that the **`VACUUM`** operation is recorded in the transaction log.
- `DRY RUN`
- Run the command again without **`DRY RUN`** to permanently delete these files.
- define schema if there are no data in the databae which can be inferred into

```
CREATE TABLE table
USING CVS OPTIONS (
path = '${da.paths.datasets}/flights/departuredelays.csv',
  header = "true",
  mode = "FAILFAST"
);

```
### 2.3L Views and CTEs

CTEs - common table expressions

#### Types of views

1. Normal view `CREATE VIEW`
2. Temporary view `CREATE TEMPORARY VIEW` - show tables is showing us column with summary about tables, thus `isTemporary` is set to `true` in the case of temporary view
4. Global Temp View `CREATE GLOBAL TEMPORARY VIEW` this one is missing in the `SHOW TABLES`. glonbal views can be shown in `global _temp`

1. TEMP CREATE GLOBAL TEMPORARY VIEWS are tight to the spark session. so restarting the cluster, detactching/attaching, installing the python package that can restart the interpreter
6. GLOBAL TEMP VIEWS - are attached to global_temp in cluster as long as the cluster is running we are ok, they are lost when the cluster is restarted

#### CTEs

DROP TABLE CASCADE - drop all associated tables and functions, restrict will not drop non empty

DESCRIBE EXTENDED sales csv

external data sources will not quarantee performance, and qualities associated with data lake and lakehouse (delta lake sources). For example while querying delta lake we will get the most recent version, but table registrated against other data sources may represent older cached versions. So here we can use RESRESH - refresch the cache of our data by running `REFRESH TABLE`

## Extracting data from SQL Database

## 4.3 Creating Delta Tables

By CTAS we can define `Delta Tables`- creating tables as SELECR: `CREATE TABLE AS SELECT` - infer schema from query, usefull to use when using data that at source has well defined schema
- from temporary view we can create delta table
- CREATE OR REPLACE TABLE - here we define data types to define specific columns, 
- CREATE OR REPLACE VIEW - no data type definition
- Delta Lake no need to refresh, always up to date

### Table constraints

Delta lake enforces schema on write thus we can add standard SQL constraint management clauses: NOT NULL and CHECK

### Add constraint

ALLTER TABLE table ADD CONSTRAINTS valid_date CHECK (date > '2020-02-01') -  check constraints in tblproperties

### Delta Lake Table cloning

- `DEEP CLONE` - all data plus metadata
- `SHALLOW CLONE` - data doesnt move, just copy of transaction log

## 4.4 Writing to delta table

#### OVERWRITE 
- CREATE OR REPLACE TABLE, can define schema
- INSERT OVERWRITE - only replace no overwrite, overwrite only new records, can overwrite individual partitions, can't enforce schema

#### APPEND ROWS
- INSERT INTO - without overwriting, can cause overwrite

#### MERGE UPDATES
- update, inserts, deletes as completed single transaction, multiple conditions, custom logic
- matched and not matched conditions
- can be used for matched and not matched
```
MERGE INTO users a
USING users_update b
ON a.user_id = b.user_id
WHEN MATCHED AND a.email IS NULL AND b.email IS NOT NULL THEN
  UPDATE SET email = b.email, updated = b.updated
WHEN NOT MATCHED THEN INSERT *
```
#### Load incrementally

`COPY INTO`
- ingest data from external systems (requires consistent schema), 
- better to overwrite data in the table -  faster, can retrive data using time travel, acid so in the case of failure - previous version in in


## 4.5 Extract Lad Data Lab


1. Extract raw data from JSON
```
CREATE TABLE IF NOT EXISTS events_json
  (key BINARY, offset BIGINT, partition INT, timestamp BIGINT, topic STRING, value BINARY)
USING JSON
OPTIONS (path = "${da.paths.datasets}/ecommerce/raw/events-kafka/")
```
NOTE: remeber that LONG == BIGINT

2. Create empty table

```
CREATE TABLE IF NOT EXISTS events_raw
  (key BINARY, offset BIGINT, partition INT, timestamp BIGINT, topic STRING, value BINARY)
```
3. Insert data from 1 to 2
```
INSERT INTO events_raw
SELECT * FROM events_json
```
4. Create Delta Table from a Query

```
CREATE OR REPLACE TABLE item_lookup
AS SELECT * FROM parquet. .`${da.paths.datasets}/ecommerce/raw/item-lookup`
```

## 4.6 CLEANING DATA

- `COUNT` (column) - skips null values
- `COUNT(*)` -  counts `NULL` as well  
- `COUNT_IF(user_id is NULL AS missing_user` 

- `DISTINCT` - may be affected by NULL  

WHERE, DISTINCT

## 4.7 Advanced SQL Transformation

### `:` and `,` notation

- `:` possible to get some JSON attributes
-  json* unpack json

### Data Structures

- traverse in JSON by `.` ecommerence.purchase_revenue_in_usd
- `explode(idem)` put each element in own array arrays in JSON

### Collect array

- collect set - unique values
- flatten - combine arrows
- array_distinct - remove duplicates

### JOINS
. inner, outer, left, right, anti, cross, semi

### SET OPERATIONS
- UNION
- MINUS
- INTERSECT

### Pivot tables

### Higher order functions - Ccomplex data
- FILTER
 -  `SELECT filter(array(1, 2, 3), x -> x % 2 == 1);`
 [1,3] 
- EXIST
 - `SELECT exists(array(1, 2, 3), x -> x % 2 == 0);`
 - true 
- TRANSFORM - existing build in function on eisting array
-  `SELECT transform(array(1, 2,3), x -> x+1);`
 - [2, 3, 4] 
- 
- REDUCE

### FILTER - WITH LAMBDA EXPRESSIONS
- FILTER (items, i -> i.item_id LIKE "%K") AS king_items
