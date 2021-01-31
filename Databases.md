## Databases

### RDS
- when RDS have multi-AZ replication the DBs are synced synchronously and the replicated DBs are kept in standby for immediate use in case the primary DB fails
Multi-AZ deployments
- can’t use the DBs for read or write operations while primary is in use 
- this is meant to serve as a back up
- automatic failover when primary fails

### Read Replicas
- can use them as back up for read operations only
- no automatic failover; need to be manually upgraded to use


| Multi-AZ Deployments                                                                                          | Read Replicas                                                                  	|
|--------------------------------------------------------------------------------------------------------------	|-------------------------------------------------------------------------	|
| Synchronous replication – highly durable	                                                                            | Asynchronous replication – highly scalable                                           	|
| Only database engine on primary instance is active                                                                                    	| All read replicas are accessible and can be used for read scaling                                     	|
| Automated backups are taken from standby                                                         	| No backups configured by default                	|
| Always span two Availability Zones within a single Region                                                 	| Can be within an Availability Zone, Cross-AZ, or Cross-Region 	|
| Database engine version upgrades happen on primary 	| Database engine version upgrade is independent from source instance                        	|
| Automatic failover to standby when a problem is detected  | Can be manually promoted to a standalone database instance |

### DynamoDB
- Non relational
- schema less
- fully managed service 
- has autoscale enabled by default

### Amazon DynamoDB Accelerator (DAX)
a fully managed, highly available, in-memory cache that can reduce Amazon DynamoDB read times from milliseconds to microseconds, even at millions of requests per second.

![](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/Read-Through%20Cache.png)

### Amazon Aurora
- relational database that will automatically scale to accommodate data growth
- fully managed

### Amazon Redshift
- for OLAP
- Amazon Redshift is mainly used for data warehousing making it simple and cost-effective to analyze your data across your data warehouse and data lake
- Amazon Redshift does not support read replicas and will not automatically scale
- think of 100TB or Petabyte scale storage

*******************************************
OLAP - Redshift

OLTP - RDS and/or DynamoDB

*******************************************
### Elasticache
- In memory data storage for fast/realtime/low latency query
- NoSql DB
- AWS support Redis and Memcached
- Elasticache is used to increase the performance, speed and redundancy with which applications can retrieve data by providing an in-memory database caching system, and not for database analytical processes.

Memcached is designed for simplicity
Redis offers a rich set of features that make it effective for a wide range of use cases. Understand your requirements and what each engine offers to decide which solution better meets your needs.

![](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/Relational%20Databases.png)