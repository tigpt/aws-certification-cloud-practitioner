# AWS Certification Cloud Practitioner

AWS Certification Cloud Practitioner is a very macro level overview of AWS services.

It is for sure the esiest exame because it doesn't go deep into subjects, but it actualy is challenging if you are aming to nail it and not just go for the 70% to get the badge.

Because of that I've compiled a list of the services that are covered.
Some of this descriptions where sourced from AWS Glossary, but some have a personal touch, so take them with a graint of salt, and do your own research.

For sure in only 65 questions not every service will show up, but AWS say in the Exame Guide that all this services and features are covered, so probably it's a good idea of having a minimal understanding of each one of them.


#### There are 64 Services / Features to review, so grab your coffee and let's start!

## Analytics:
- **Amazon Athena**
  - AWS Athena is a serverless service that allows you to make queries using ANSI SQL in data stored on Amazon S3. It support a wide varity of data formats like CSV, TSV, JSON, or Textfiles. You pay for read data and you can read compressed data like Zip or Gzip, so if you have 10GB CSV but it is only 20Mb Ziped, you can just upload ziped vertion and query it while ziped, you will pay for 20Mb of read instead of 10Gb or read. Nothing to maintain, and super dupper fast, quering muliple GB of data in seconds.
- **Amazon Kinesis**
  - AWS Kinesis is a serverless service that allows you to collect, process, analyze video or data streams in real time. For example you can stream video from a security camera and do face detection or machine learning. You can also stream stock market data and act on it with real-time buy and sell actions. Have in mind that there could be a delay in data up to 1 second.
- **Amazon QuickSight**
  - AWS QuickSight is a serverless Business Inteligence service, it allows everyone in your organization to understand your data by asking questions in  natural language, explor dashboards and find patterns and outliers, using machine learning.

## Application Integration:
- **Amazon Simple Notification Service (Amazon SNS)**
  - AWS SNS is a serverless service that allows you to notify one or multiple services in a Publisher-Subscriber architecture (1-to-N). It can be used to send events from one server to multiple services (ex.: Lambda) or even to people (via e-mail or SMS). Messages are sent as arrive and if destinations are offline they don't have a mecanism to recover past messages (there's no guarantee of event to arrive to all destinations)
- **Amazon Simple Queue Service (Amazon SQS)**
  - AWS SQS is a serverless system that allows you to decouple systems on your architecture, by enabeling one system to send events to another even if they are offline. It implementes a Producer-Consumer architecture (1-to-1) and it buffers the information if not consumed imediatly or if there are a big burst of events produced. It's normally used to make services very scalable and reliable, and to protect slow backends from a big burst of requests. Information can be conssumed at a different rate that it's produced. Each event have a max size of 256Kb, so you will need to combine with other mecanism (ex.: S3) to send larger payloads.

## Compute and Serverless:
- **AWS Batch**
  - AWS Batch allows you to run hundreds of thousands of computing jobs on AWS. AWS Batch plans and schedule and execute batch jobs on AWS Fargate, EC2 or Spot Instances letting you focuse on the job and not on the orquestation of fleets to run the jobs.
- **Amazon EC2**
  - AWS EC2 it's a web service (API's) to launch and manage Linux or Windows Servers on AWS Data centeres, with a lot of flavores in terms of CPUs architectures and sizes, different amounts of RAM, GPU, Storages and Networking. It's the heart of AWS but could be seen as VPS on steroids. User need to patch and maintain APP software and OS on this machines.
- **AWS Elastic Beanstalk**
  - It's a PaaS (Platform as a Service), web server / backend run-time that allow you to deploy and scale without effort a web app. You can choose multiple platforms like PHP, Node.js, .NET, Python, etc.. to run your application without worry with loadballancing or server provisioning and maintnance, just focouse on your APP. It basicly creates EC2, Security Groups, Load balancers, etc. and configures them for you.
- **AWS Lambda**
  - AWS Lambda is a serverless, event-driven compute service that let's you run code without worry about infraestructure and scalability. You pay for what you use rounded to 1ms. You can chose different CPU and RAM sizes and different runtime environments, like Python Java or Ruby. Lambda funcitons will cold start if they are not used for long time (~15min) or they will warm start if theres an recent used instance available to recive new requests. You can setup reserved capacity but if so, you pay for int 24/7 even if you don't recive requests, or you can let AWS do the auto scaling to zero and not pay if you have no requests (ex.: during night while your clients or backend activities are inactive).
- **Amazon Lightsail**
  - AWS Lightsail is a simplified version of AWS EC2, it basicly is a VPS that is in direct competition with DigitalOcean or Linode, offering you a simple payment system with integrated backup solutions, Security Group management, Server status, Bandwith and much more, on a user friendly Grafical Web Interface. Probably a way to welcome VPS clients from other providers to AWS ecosystem.
- **Amazon WorkSpaces**
  - AWS WorkSpaces is a fully managed desktop virtualization service that enables you to acces data or applications remotly. Great to offer scalability or better performance machines to your organization colleagues. It Facilitate remote wokr or onboard contingent workers or even create powerfull AutoCad machines that can be accessed from cheap low speck laptops.

## Containers:
- **Amazon Elastic Container Service (Amazon ECS)**
  - AWS ECS is a fully managed container orchestration service built by Amazon. It makes it easy to deploy, manage and scale containerized applications. It supports Docker containers and you can run your containers on EC2 machines, Fargate (see below) or on-premises with (ECS Anywhere installed on your own machines). You just need to create a Cluster, Tasks-defenitions and run them either as Tasks (short lived / batch containers) or as Services (24/7 workloads like webservers). You can chose x86 or arm64 processors and linux or windows runtimes.
- **Amazon Elastic Kubernetes Service (Amazon EKS)**
  - AWS EKS is a managed and certified Kubernetes service, allowing you to run Kubernetes on AWS or on-premises with some abstraction from the clusters configuration and host machine maitnance, letting you focuse on conquering the world with your fleed of Pods.
- **AWS Fargate**
  - Amazon Fargate is a serverless pay-as-you-go compute engine that lets you focouse in building containers and not in running or manage servers that will run them. It is compatible with both ECS and EKS and amd64 (Intel/AMD) or arm64 (AWS Graviton). You can run all your containers on Fargate or mix and match between you EC2 / on-premise infraestructure, but user Fargate for fast scaling, or for batch process that requires a huge machine for a small amount of time. You pay per minute of computation and you chose the vCPU and RAM size, AWS will take care of the fleet of machines to give you that computation power to run you container without caring of the Host machine or OS.

## Database:
- **Amazon Aurora**
  - AWS Aurora is a fully managed MySQL-compatible (or PostgresSQL) relational database, on top of RDS, with high speed and availability (sometimes 5x faster then traditional MySQL). You can chose provisioned Aurora that manage the srevers instances sizes, or serverless (with a min and max resources) that can be scaled down to zero, allowing you to not pay 24/7 for that backend app that is only used once an month. The first query (cold start) can take a few seconds but then it will adapt to your needs.
- **Amazon DynamoDB**
  - AWS DynamoDB is a serverless NoSQL database, in reality it is a key-valued or wide column database with single digit milisecond response that scales to the moon. Some say it is a the KingDB because it's truelly created to scale to Terabytes of data, but each record can only store a max of 400kb. There are some limitations on the way you create it schema and how you query data, but when you unleash it's true power you understand why it exits.
- **Amazon ElastiCache**
  - AWS ElastiCache offeres managed caching service for Redis and Memcached, allowing you to unlock microseconds latency and scale with in-memory caching without focusing on servers. Acelerate applications performance, reduce backend database load.
- **Amazon RDS**
  - AWS RDS allows you easly setup and operate relational database in the cloud. Run Databases without focusing on adminstration tasks like hardware provisioning, database setup, patching and backups. It supports Aurora, MySQL, MariaDB, PostgreSQL, Oracle and Microsoft SQL Server.
- **Amazon Redshift**
  - AWS Redshift is a fully managed data warehouse service at pentabyte-scale. It uses SQL to analyze structured and semi-structured data across data warehouses, operational databases and data lakes. It leverate AWS custom designed hardware and machine learning to deliver the best performance at any scale.

## Developer Tools:
- **AWS CodeBuild**
  - Amazon Codebuild lets you create a CI/CD system. It is fully managed service that compiles source code, run tests and produce software packages ready to be deployed.
- **AWS CodeCommit**
  - AWS CodeCommit is a secure source control service to host private Git Repositories.
- **AWS CodeDeploy**
  - AWS CodeDeploy complements CodeBuild allowing you to automate software deployments to services like EC2, Fargate, Lambda or on-premises.
- **AWS CodePipeline**
  - AWS CodePipeline is a managed service that makes it easy to model, visualize and automate continuous delivery by defining workflows.
- **AWS CodeStar**
  - AWS CodeStart agregate multiple of other AWS services, allowing you to create project templates and create source repos, build and deployment pipelines, virtual servers or serverless resources. It basicly helps you create build environments from templates like Go, PHP Laravel or other from dozens to chose.

## Customer Engagement:
- **Amazon Connect**
  - It's a easy-to- use omnichannel cloud based contact center service. You can respond to phone calls or chat inquiries from end customers, and create automations with other AWS services like Lambda, voice to text (Amazon Transcribe) or text to voice (Amazon Polly) and many others.

## Management, Monitoring, and Governance:
- **AWS Auto Scaling**
- **AWS Budgets**
- **AWS CloudFormation**
- **AWS CloudTrail**
- **Amazon CloudWatch**
- **AWS Config**
- **AWS Cost and Usage Report**
- **Amazon EventBridge (Amazon CloudWatch Events)**
- **AWS License Manager**
- **AWS Managed Services**
- **AWS Organizations**
- **AWS Secrets Manager**
- **AWS Systems Manager**
- **AWS Systems Manager Parameter Store**
- **AWS Trusted Advisor**

## Networking and Content Delivery:
- **Amazon API Gateway**
- **Amazon CloudFront**
- **AWS Direct Connect**
- **Amazon Route 53**
- **Amazon VPC**

## Security, Identity, and Compliance:
- **AWS Artifact**
  - AWS Artifact Provides on-demand access to AWS security and compliance reports and agreements.
- **AWS Certificate Manager (ACM)**
  - AWS ACM let you create, manage and deploy public or private certificates like SSL/TLS
- **AWS CloudHSM**
  - It allows to Manage hardware security module (HSM) for aplications running on EC2.
- **Amazon Cognito**
  - Cognito is a serverless service that provides control access to your Apps. You can create roles and map them to users, offloading user autentication and login from you. It can save user's data loaclly on devices to keep working when devices are offline. It can extend this users permissions to AWS services like AWS API Gateway.
- **Amazon Detective**
  - Amazon Dtective allows you to visualize security data to rapidly get root cause of potential security issues. It automatically collects data logs from your AWS resources (like VPC Flow Logs, AWS CloudTrail, AWS GuardDuty), and uses machine learning, statistical analysis and graph theory to build a linked set of data to enable you to faster and eficiently do security investigation.
- **Amazon GuardDuty**
  - AWS GuardDuty helps you protects AWS accounts, by stoping unauthorized activity, continuasly monitoring the account and workloads for malicious actions, delivering security findings.
- **AWS Identity and Access Management (IAM)**
  - AWS IAM provides very granual access controll to all AWS account, you can specify what users can access witch services and what operations are allowed or denied. You can also create roles that can be aplied to enteties (services, instances or users, both internal or externals).
- **Amazon Inspector**
  - Enables EC2 and ECR automated vunerability scans in order to identify security flaws. It also reveale unintend network exposures.
- **AWS License Manager**
  - It let's to easly manage licences from multiple vendores like Microsoft, SAP, Oracle and IBM, for software on AWS or on-premises.
- **Amazon Macie**
  - AWS Macie allows you to do data security and privacy check on AWS S3. It uses machine learning and pattern matching to discover and protect sensitive data like ID cards that are exposed inadvertently to the world. It also look for unfamiliar IP activity or downloads of large amount of sensitive data.
- **AWS Shield**
  - AWS Shield is a managed DDoS (Distributed Denial of Service) protection service to protect your applications runing on AWS.
- **AWS WAF**
  - AWS WAF (Web Application Firewall) helps you protect Web Applications or APIs against common web exploits and bots granting better availability.

## Storage:
- **AWS Backup**
- **Amazon Elastic Block Store (Amazon EBS)**
- **Amazon Elastic File System (Amazon EFS)**
- **Amazon S3**
- **Amazon S3 Glacier**
- **AWS Snowball Edge**
- **AWS Storage Gateway**


# Conclusions
I found it usefull to know a vast amount of AWS capabilities, for sure some of them I have never used them before and now I know they exist in case I need to research them further in orther to use them.
