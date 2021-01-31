## Amazon Kinesis

Amazon Kinesis is the streaming data platform of AWS and has four distinct services under it: 
### 1. Kinesis Data Firehose 
    - Fully managed
    - used to ingest data into S3, Redshift or Elasticsearch
    - not much custom data processing going on
### 2. Kinesis Data Streams
    - Not fully managed
    - can do custom processing on data before ingesting to S3, Redshift, DynamoDB etc
    - can also push data streams to custom application for processing or analytics
### 3. Kinesis Video Streams
### 4. Amazon Kinesis Data Analytics

default retention - 24 hrs
max retention - 7 days

*******************************************