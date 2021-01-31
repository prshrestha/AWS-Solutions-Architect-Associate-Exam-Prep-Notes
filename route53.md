## Route 53

### Route 53 - DNS resolution
- Can use route 53 to route to multiple AZs
- Can also use route 53 to route to multiple regions

![VPC Endpoints](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/route53a.png)

### Routing Policies
![VPC Endpoints](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/routing_policy.png)

### CloudFront - Signed URLs vs Signed Cookies
| Signed URLs   | Signed Cookies |
|---------------|---------------|
| primarily for providing access to a single file | for providing access to multiple files |
| will change existing URL | won’t change existing URL |

### Origin Access Identity
To restrict access to content that you serve from Amazon S3 buckets, you create CloudFront signed URLs or signed cookies to limit access to files in your Amazon S3 bucket, and then you create a special CloudFront user called an Origin Access Identity (OAI) and associate it with your distribution. Then you configure permissions so that CloudFront can use the OAI to access and serve files to your users, but users can't use a direct URL to the S3 bucket to access a file there. Taking these steps help you maintain secure access to the files that you serve through CloudFront.

### Lambda@Edge 
- a feature of Amazon CloudFront that lets you run code closer to users of your application, which improves performance and reduces latency. 
- With Lambda@Edge, you don't have to provision or manage infrastructure in multiple locations around the world. You pay only for the compute time you consume - there is no charge when your code is not running

![VPC Endpoints](https://github.com/prshrestha/AWS-Solutions-Architect-Associate-Exam-Prep-Notes/blob/main/images/lambda_at_edge_kinesis.png.png)

### CNAME
Maps your domain example.com to cloudfront domain like [d111111abcdef8.cloudfront.net](d111111abcdef8.cloudfront.net) 
or like example.com and also you can add your own URL like 
[example.com/images/image.jpeg](example.com/images/image.jpeg)

### Alias records/ANAME
Unlike a CNAME record, you can create an alias record at the top node of a 
DNS namespace, also known as the zone apex. For example, if you register 
the DNS name [example.com](example.com), the zone apex is [example.com](example.com). 
You can't create a CNAME record for [example.com](example.com), but you can create an 
alias record for [example.com](example.com) that routes traffic to [example.com](example.com). 
It means I can have another site (say [test.com](test.com) route to [example.com](example.com))

### Customer Gateway
When connecting a VPN between AWS and a third party site, the Customer 
Gateway is created for the customer site but it contains information 
about the third party site e.g. the external IP address and type of routing.

### Virtual Private Gateway
The Virtual Private Gateway has the information regarding the AWS 
side of the VPN and connects a specified VPC to the VPN.

## CNAME vs. Alias Records

| CNAME  | Alias Records |
|---------------|---------------|
| A CNAME record can redirect DNS queries to any DNS record. For example, you can create a CNAME record that redirects queries from acme.example.com to zenith.example.com or to acme.example.org. You don't need to use Route 53 as the DNS service for the domain that you're redirecting queries to.| n alias record can only redirect queries to selected AWS resources, such as the following: (1) Amazon S3 buckets, (2) CloudFront distributions, (3) Another record in the Route 53 hosted zone that you're creating the alias record in. For example, you can create an alias record named acme.example.com that redirects queries to an Amazon S3 bucket that is also named acme.example.com. You can also create an acme.example.com alias record that redirects queries to a record named zenith.example.com in the example.com hosted zone. |
| CNAME can only be created for subdomain |Alias record can be created for both root domain and subdomain |
| Route 53 charges for CNAME queries.| Route 53 doesn't charge for alias queries to AWS resources. For more information, see Amazon [Route 53 Pricing.](https://aws.amazon.com/route53/pricing/)|
| A CNAME record redirects DNS queries for a record name regardless of record type, such as A or AAAA. | Route 53 responds to a DNS query only when the name of the alias record (such as acme.example.com) and the type of the alias record (such as A or AAAA) match the name and type in the DNS query. |
| A CNAME record appears as a CNAME record in response to dig or noslookup queries. | An alias record appears as the record type that you specified when you created the record, such as A or AAAA. The alias property is visible only in the Route 53 console or in the response to a programmatic request, such as an AWS CLI list-resource-record-sets command. |