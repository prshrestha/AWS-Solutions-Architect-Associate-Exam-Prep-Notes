## General Knowledge

### Stateful vs. Stateless
#### Security groups are stateful
- This means any changes applied to an incoming rule will be automatically applied to the outgoing rule. 
- e.g. If you allow an incoming port 80, the outgoing port 80 will be automatically opened.

#### Network ACLs are stateless
- This means any changes applied to an incoming rule will not be applied to the outgoing rule. 
- e.g. If you allow an incoming port 80, you would also need to apply the rule for outgoing traffic.

*******************************************
### Recovery Point Objective/RPO
- acceptable amount of data loss measured in hours before disaster occurs

### Recovery Time Objective/RTO 
- how long do you want to be offline after recovery process has started or how long the recovery 
  process will take to finish after the disaster recovery process has been 
  kicked off.

For example, an RTO of 2 hours and an RPO of 15 minutes would mean all systems 
would be recovered in two hours or less and consistent to within 15 minutes of 
the failure

*******************************************
### Placement Groups

#### Cluster
- Put EC2s in the same AZ for low network latency, high throughput
- uses same underlying hardware

#### Spread
- Spreads EC2s across different AZs to separate critical instances from concurrent failure
- uses distinct underlying hardware
- limited to set up 7 instance per AZ

#### Partitioned 
- grouping where instances don’t share same underlying hardware
- instances are evenly distributed across underlying partition during launch
- for HDFS, HBase, Cassandra, Kafka or any other fault tolerant systems

*******************************************
### Metadata and User data

#### Metadata
- tells data about instance
- who am I?
- key/value pair

#### User data
- user supplied data during bootstrapping instances
- e.g. a script to certain task
- tells instances what to do
- string

*******************************************