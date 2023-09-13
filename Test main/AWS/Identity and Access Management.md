![[Screenshot from 2023-09-08 11-37-25 1.png]]
## Network Boundary

**VPC** (Isolated private network for security)
## Custom infrastructure

**DNS** 
- Route53

**API Gateway**

**Cognito** (Create user pools)

**Load Balancer**
- Elastic Load Balancer

**Web Backend Layer**
- EC2 (VM)
- Lambda (code)
- ECS (Elastic service - manage your containers)
- EKS(Elastic kubernetis service)

**Application Layer**
- EC2
- Lambda
- ECS
	**Cache**
	- Elastic Cache
	**Relational Database**
	- Aurora (AWS based)
	- RDS (Custom db)
	**NoSQL Database**
	- DynamoDB
	- DocumentDB (You can use MongoDB)
	- OpenSearch (Elastic search)

**Search Query Submition**

**Event Coordination**
- SNS {Simple notification service} (Publisher)
- SQS {Simple Queue service} (Subscriber)
- EventBridge (Provide tird-party integration with shopify for example)
- Step Functions (Define workflows)

**General Object Storage**
- S3 {Simple storage service, Bucked} *Very cheep*

**Cached Content** (images, scripts etc.)
- CloudFront (Replicate Storage in different geo-locations) *Better performance*

**Analytical Processing**
- EMR
- Athena

**Data Warehouse**
- Redshift (Meant for big queries )

**Dashboarding**
- QuickSight

**Deployment Orchestration**
- Code Commit (Store your code)
- Code Build (build artifacts)
- Code Deploy (Deploy artifacts)
- Code Pipeline (CI/CD)

**Monitoring**
- CloudWatch (for monitoring stability of the infrastructure)
- CloudTrail (for auditing) *Who is doing what and when*

**Rapid Development**
- Amplify (Do things behind the scenes)
- SAM (Local testing)

**Infrastructure as code IaC**
- Cloud Formation (Service for writing JSON, YAML etc. configuration files)
- CDK {Cloud Development Kit} (Prefered way!) *You can use loops, functions etc.*
## Packaged Infrastructure

**Elastic Beanstalk** (Create custom infrastructure automatically) *Still need to maintain the components*

**App Runner** (All you mange is your application the infrastructure is managed by AWS)

**Lightsail** (Beginner friendly option for smaller applications)

**AppSync** (GraphQL alternative)
