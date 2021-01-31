# AWS-Solutions-Architect-Associate-Exam-Prep-Notes
AWS Solutions Architect Associate Exam Prep Notes

I took the test in early 2020 and used the following class from ACloudGuru to prep for the test
https://www.udemy.com/share/101WaCAEQfdVlUQHw=/

Then I used the mock test from Jon Bonso for practice
https://www.udemy.com/share/102DhnAEQfdVlUQHw=/

Here are some notes that I made for quick review of the material


## VPC Notes

Region
- Amazon EC2 is hosted in multiple locations worldwide. 
- These locations are composed of Regions and Availability Zones. 
- Each Region is a separate geographic area. 
- Each Region has multiple, isolated locations known as Availability Zones. 
- Amazon EC2 provides you the ability to place resources, such as instances, and data in multiple locations.

*******************************************
VPC
Based on this video - https://www.youtube.com/watch?v=LX5lHYGFcnA

!(https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/VPC%20Architecture.png)


Image Source: https://www.youtube.com/watch?v=LX5lHYGFcnA

VPC -> subnet -> EC2 or web server or DB server
Public subnet - traffic goes to internet via internet gateway
Private subnet - internal communication via VPN
When you create a custom VPC, a default Security Group, Access control list, and Route Table are created automatically.

*******************************************
When you create a VPC you have to assign the CIDR block.
e.g - say you create a VPC with 10.0.0.0/24 CIDR (meaning 256 ips) and need more now. You can not edit or modify the one you have.
Instead you can add a new VPC with CIDR with say 10.0.1.0/24 (meaning additional 256 ips)

*******************************************
￼

Amazon Virtual Private Cloud (VPC) 
- a logical data center or virtual data center in Cloud. 
- It provide an isolated section to host your machine. 
- VPC is a collection of the region, Internet Gateway(IG), Route table, NACL, Security group, Subnet, Instances. 
- VPC provides us a completely separate environment where we can place our machine in our own way. 
- Only one internet gateway per VPC.
 
Internet gateway 
- A horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet. 
- An internet gateway serves two purposes: to provide a target in your VPC route tables for internet-routable traffic and to perform network address translation (NAT) for instances that have been assigned public IPv4 addresses. 
- Route tables contain a set of rules, called routes, that are used to determine where network traffic is directed. 
- Each subnet in your VPC must be associated with a route table; the table controls the routing for the subnet. 
- A subnet can only be associated with one route table at a time, but you can associate multiple subnets with the same route table.
 
Network access control list (NACL)
- An optional layer of security for your VPC or subnet that acts as a firewall for controlling traffic in and out of one or more subnets. 
- You might set up network ACLs with rules similar to your security groups in order to add an additional layer of security to your VPC.
- VPC automatically comes with a modifiable default network ACL. By default, it allows all inbound and outbound IPv4 traffic and, if applicable, IPv6 traffic. 
- One subnet can only connect with a single ACL but a single ACL can have multiple subnets.

Security Groups
- A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. 
- When you launch an instance in a VPC, you can assign up to five security groups to the instance. 
- Security groups act at the instance level, not the subnet level. 
- Therefore, each instance in a subnet in your VPC could be assigned to a different set of security groups. 
- If you don't specify a particular group at launch time, the instance is automatically assigned to the default security group for the VPC. 

By default security group will allow outbound traffic. 
Security groups are always permissive; you can’t create rules that deny access. 
Security groups are stateful.

Security groups	NACLs
operates at instance/EC2 level	operates at VPC/subnets level
supports allow only rules	supports both allow and deny rules
is stateful: return traffic is allowed automatically	is stateless: return traffic must be explicitly allowed
evaluates all rules before deciding whether to allow traffic	evaluates rules from ascending order to decide whether to allow  traffic
applies to an instance only i.e. must specify security group while launching an instance or must apply later 	automatically applies to all instances in subnet

Subnet or Subnetwork
- A VPC spans all of the Availability Zones in the Region. 
- one subnet is mapped into one specific Availability Zone
- After creating a VPC, you can add one or more subnets in each Availability Zone. 
- When you create a subnet, you specify the CIDR block for the subnet, which is a subset of the VPC CIDR block. 
- Every subnet that you create is automatically associated with the main route table for the VPC.
- If a subnet's traffic is routed to an Internet gateway, the subnet is known as a public subnet. 

To enable access to or from the Internet for instances in a VPC subnet, you must do the following:
- Attach an internet gateway to your VPC.
- Ensure that your subnet's route table points to the Internet gateway.
- Ensure that instances in your subnet have a globally unique IP address (public IPv4 address, Elastic IP address, or IPv6 address).
- Ensure that your network access control lists and security groups allow the relevant traffic to flow to and from your instance.

The following diagram shows a VPC that has been configured with subnets in multiple Availability Zones. 1A, 1B, 2A, and 3A are instances in your VPC. An IPv6 CIDR block is associated with the VPC, and an IPv6 CIDR block is associated with subnet 1. An internet gateway enables communication over the internet, and a virtual private network (VPN) connection enables communication with your corporate network.

￼

From <https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html#vpc-subnet-basics>
 
Auto scaling group 
cool down period
    - setting for ASG which ensures that it doesn’t launch or terminate additional instances before the previous scaling activity takes full effect

Instance 
a virtual server in the AWS cloud. With Amazon EC2, you can set up and configure the operating system and applications that run on your instance.

Elastic IP address
An Elastic IP address is a static, public IPv4 address designed for dynamic cloud computing. You can associate an Elastic IP address with any instance or network interface for any VPC in your account. 

The IPs are assigned to Elastic Network Interfaces and not to EC2s. The ENIs are then assigned to EC2s.

With an Elastic IP address, you can mask the failure of an instance by rapidly remapping the address to another instance in your VPC. Note that the advantage of associating the Elastic IP address with the network interface instead of directly with the instance is that you can move all the attributes of the network interface from one instance to another in a single step.

From <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-eips.html

Elastic Network Interfaces
An elastic network interface is a logical networking component in a VPC that represents a virtual network card.

From <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html>

VPC Peering
- Connect two VPCs
- You can connect VPCs within the same region or across different regions
- to connect to VPCs in same account or different account or same region or different region
- one VPC is the provider and another VPC is the receiver VPC 
    - this doesn’t matter if the VPCs are in same region
    - this matters if the VPCs are in different regions
- need to configure the route table after you peer in both VPCs

VPC Endpoints
- Allows connection to AWS services privately within a VPC
- Say EC2 wants to communicate to S3. EC2 doesn’t need to go out via public internet and connect to S3 via public interface. 
- With VPC endpoints EC2 can directly connect to S3 internally within your VPC (doesn’t go out via public internet)

￼

AWS PrivateLink 
- simplifies the security of data shared with cloud-based applications by eliminating the exposure of data to the public Internet. 
- AWS PrivateLink provides private connectivity between VPCs, AWS services, and on-premises applications, securely on the Amazon network. 
- AWS PrivateLink makes it easy to connect services across different accounts and VPCs to significantly simplify the network architecture.

VPC Interface Endpoints
- enables you to connect to services powered by AWS PrivateLink. 
- These services include some AWS services, services hosted by other AWS customers and Partners in their own VPCs (referred to as endpoint services), and supported AWS Marketplace Partner services. 
- The owner of the service is the service provider, and you, as the principal creating the interface endpoint, are the service consumer.

￼

VPN 
- to connect on premise resources to AWS

Connection to On-Premises Data Centers
You can use the following types of connections for a connection between an interface endpoint and your on-premises data center:
- AWS Direct Connect
- AWS Site-to-Site VPN

NAT Gateway
- Helps private subnet talk to internet or other AWS services via outbound connection (does NAT translation of private subnets)
- Private subnet talks to NAT Gateway in public subnet and then the response on the same connection is provided back to the private subnet.
- Connection from outside/public internet is not allowed.
- You can use a NAT device to enable instances in a private subnet to connect to the internet (for example, for software updates) or other AWS services, but prevent the internet from initiating connections with the instances. A NAT device forwards traffic from the instances in the private subnet to the internet or other AWS services, and then sends the response back to the instances. When traffic goes to the internet, the source IPv4 address is replaced with the NAT device’s address and similarly, when the response traffic goes to those instances, the NAT device translates the address back to those instances’ private IPv4 addresses.
￼

NAT devices are not supported for IPv6 traffic—use an egress-only Internet gateway instead. For more information, see Egress-Only Internet Gateways.

AWS offers two kinds of NAT devices—a NAT gateway or a NAT instance. We recommend NAT gateways, as they provide better availability and bandwidth over NAT instances. The NAT Gateway service is also a managed service that does not require your administration efforts. A NAT instance is launched from a NAT AMI. You can choose to use a NAT instance for special purposes.
- NAT Gateways
- NAT Instances
- Comparison of NAT Instances and NAT Gateways

*******************************************
VPC Flow Logs
- VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC
- Flow log data can be published to Amazon CloudWatch Logs and Amazon S3
- After you've created a flow log, you can retrieve and view its data in the chosen destination
- VPC Flow Logs can be created at the VPC, subnet, and network interface levels

*******************************************
Subnets and Routing

￼

￼

*******************************************
￼

*******************************************

 



 

