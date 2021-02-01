## EC2 and ECS

### TL; DR
- EC2 - is simply a remote (virtual) machine.
- ECS stands for Elastic Container Service - as per basic definition of [computer cluster](https://en.wikipedia.org/wiki/Computer_cluster), ECS is basically a logical grouping of EC2 machines/instances. Technically speaking ECS is a mere configuration for an efficient use and management of your EC2 instance(s) resources i.e. storage, memory, CPU, etc.

### EC2
- is like your computer on cloud. You can install docker on it or some RDS or noSQL db
- is simply a remote (virtual) machine.
- EC2 is a different thing that you can use with the various OS
 
### Container service - ECS
- can run docker inside 
- manage EC2s inside it
- can have EC2 instances it and pay for each EC2
- We don't pay for ECS
 
*******************************************
ECS, Elastic Beanstalk and Fargate allows docker container to run natively.

In EC2 docker has to be installed separately.

### Elastic Beanstalk
- Fully managed
- Elastic Beanstalk handles an application's deployment details of capacity provisioning, load balancing, auto-scaling, and application health monitoring

*******************************************
### Elastic Container Service (ECS)
- As per basic definition of computer cluster, ECS is basically a logical grouping of EC2 machines/instances.
- Technically speaking ECS is a mere configuration for an efficient use and management of your EC2 instance(s) 
  resources i.e. storage, memory, CPU, etc.
 
In simple words, ECS is a manager while EC2 instances are just like employees. All the employees (EC2) 
  under this manager(ECS) can perform "Docker" tasks and the manager also understands "docker" pretty well. 
  So, whenever you need "docker" resources, you show up to the Manager. Manager already has status from 
  every employee(EC2) decides which one should perform the task. Now, coming back to your question, 
  a manager without an "employee" does not make sense.
  

## [What is the difference between Amazon ECS and Amazon EC2? - Stack Overflow](https://stackoverflow.com/questions/40575584/what-is-the-difference-between-amazon-ecs-and-amazon-ec2)

AWS ECS is just a logical grouping (cluster) of EC2 instances, and all the EC2 instances part of an 
ECS act as Docker host i.e. ECS can send command to launch a container on them (EC2). 
If you already have an EC2, and then launch ECS, you'll still have a single instance. 
If you add/register (by installing the AWS ECS Container Agent) the EC2 to ECS it'll 
become the part of the cluster, but still a single instance of EC2.
An Amazon ECS without any EC2 registered (added to the cluster) is good for nothing.

To simplify it further, if you have launched an Amazon ECS with no EC2 instances added to it, 
it's good for nothing i.e. you can't do anything about it. ECS makes sense only once one (or more) 
EC2 instances are added to it.
The next confusing thing here is the container term - which is not fully virtualized machine instances, 
and Docker is one technology we can use to create container instances. Docker is a utility you can 
install on our machine, which makes it a Docker host, and on this host you can create containers 
(same as virtual machines - but much more light-weight). To sum up, ECS is just about clustering of 
EC2 instances, and uses Docker to instantiate containers/instances/virtual machines on these (EC2) hosts.

All you need to do is launch an ECS, and register/add as much EC2 instances to it as you need. 
You can add/register EC2 instances, all you need is Amazon ECS Container Agent running on your 
EC2 instance/machine, which can be done manually or directly using the special AMI (Amazon Machine Image) i.e. 
Amazon ECS-optimized AMI, which already has the Amazon ECS Container Agent. During the launch of a 
new EC2 instance the Agent automatically registers it to the default ECS cluster.

The container agent running on each of the instances (EC2 instances) within an Amazon 
ECS cluster sends information about the instance's current running tasks and resource 
utilization to Amazon ECS, and starts and stops tasks whenever it receives a request from Amazon ECS. 
For more information, see [Amazon ECS Container Agent](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_agent.html). Once set, each of the created container instances 
(of whatever EC2 machine/node) will be an instance in Amazon ECS's swarm.

*******************************************

![EC2 and ECS](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/ec2_ecs.png)