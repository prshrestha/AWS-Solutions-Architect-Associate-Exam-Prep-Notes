## EC2 Pricing

### Pricing
- On demand EC2 instances are priced by either seconds (min 60 seconds) or by hours.
 
### EC2 termination
1. Determine which Availability Zones have the most instances, and at least one instance that is not protected from scale in.
2. Determine which instances to terminate so as to align the remaining instances to the allocation strategy for the On-Demand or Spot Instance that is terminating.
3. Determine whether any of the instances use the oldest launch configuration: 
    - Check if scaled using launch config or launch template.  AWS terminates EC2 from launch configuration before the one from launch template
    - AWS terminates oldest launch configuration first
    - AWS terminates oldest launch template first
4. After applying all of the above criteria, if there are multiple unprotected instances to terminate, determine which instances are closest to the next billing hour. If there are multiple unprotected instances closest to the next billing hour, terminate one of these instances at random. 
Note that terminating the instance closest to the next billing hour helps you maximize the use of your instances that have an hourly charge. Alternatively, if your Auto Scaling group uses Amazon Linux or Ubuntu, your EC2 usage is billed in one-second increments. For more information, see [Amazon EC2 Pricing.](https://aws.amazon.com/ec2/pricing/)
 

![Pricing](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/pricing.png)

[Source](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-termination.html#default-termination-policy)

￼
 
