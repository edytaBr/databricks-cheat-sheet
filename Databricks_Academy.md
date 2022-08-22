# I. Databricks lakehouse platform

- data warehousing
- data engineering
- data streaming
- data science and ML
- 

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

migration 1.3.
