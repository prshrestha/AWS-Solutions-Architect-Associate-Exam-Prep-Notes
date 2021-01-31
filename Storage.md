## Storage

### S3/Object Storage
- S3 and its types

### S3 Glacier Data Retrieval
- Standard retrieval
    - 3-5 hrs
- Bulk retrieval
    - 5-12 hrs
- Expedited retrieval
    - 1-5 min

### S3 Glacier Select
- run queries on data stored on S3 glacier

*******************************************
### Block Storage
- EBS
- Not a long term database type storage
- block level storage service for use with Amazon EC2
- For back up create a snapshot, store in S3 and use within the same AZ
- Can also copy snapshots to another region and use there
- Can use AWS Backup feature to automate backup scheduling, retention policies and monitor and restore activity

### Elastic Block Storage
- EBS Provisioned IOPS SSD provides sustained performance for mission-critical low-latency workloads.
- multi AZ enabled by default
- you will still be able to perform normal read and write operations on your EBS volume even while a snapshot is ongoing
- can encrypt while creating it
- after EBS is deleted data is lost
- can create snapshots to store in S3 as a back up
- then move to different AZ or region

### Types of EBS
- Provisioned IOPS SSD (io1) for smaller I/O
- Throughput Optimized HDD (st1) for larger I/O
- Cold HDD (sc1) for cost effective large I/O

When EC2 is deleted the instance volume is deleted

When EC2 is deleted EBS is also deleted

By default the DeleteOnTermination is true for EBS so it gets deleted
You can set DeleteOnTermination to false for EBS so that it doesn't get deleted
If you save the EBS (either by this method or by creating back up/snapshot) you can attach it to another EC2 instance later to retrieve the data

[Source](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html#preserving-volumes-on-termination)

***********************************
### Elastic File System
Shared File storage -> connect to EC2
- EFS - linux Elastic File System -> scalable file system
    - mountable file storage service for EC2
    - POSIX compliance
- FSx - windows

- multiple EC2 instances can share the same EFS
- Used for high workload, scalable storage and need output quickly. 
- EFS provides the scale and performance required for big data applications that require high throughput to compute nodes coupled with read-after-write consistency and low-latency file operations

- EFS lets you distribute your application code across multiple EC2 instances. This makes deployment of code very efficient. Instead of deploying the application code to multiple instances, you would need to push it to a single instance which has the EFS mounted on it. Moreover, installing themes and plugins can be done on a single instance and the changes get reflected across all other mount targets!

![VPC Endpoints](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/EC2%20instance.png)

*******************************************
### Storage Gateway
- primarily used for attaching infrastructure located in a Data center or office to the AWS Storage infrastructure.  
- is a storage service, but it is a hybrid
- storage service that enables on-premises applications to use cloud storage.
- To copy snapshots of your on premise data volumes to S3 for backup. You can create local volumes or EBS volumes from these snapshots.
- You can think of a file gateway as a file system mount on S3

| Cached Volume | Stored Volume |
|---------------|---------------|
| Store data in S3 and retain a copy of frequently accessed or sub set of data locally | Store data in S3 and also retain entire data set locally for low latency access |

### Direct connect

- for private dedicated connection from on premise resources to your VPC

![VPC Endpoints](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/Direct%20Connect.png)

![VPC Endpoints](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/Direct%20Connect%202.png)

[Source](https://www.youtube.com/watch?v=LX5lHYGFcnA)

### Data transfer

![VPC Endpoints](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/Connect.png)