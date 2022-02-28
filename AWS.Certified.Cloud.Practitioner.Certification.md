# AWS Certification Cloud Practitioner

[AWS Certification Cloud Practitioner](https://aws.amazon.com/certification/certified-cloud-practitioner/) is a very macro-level overview of AWS services.

I've taken it as a learning process because even being familiar with specific AWS services from my work experience, there are so many AWS services and features that I don't know.

It is for sure the easiest AWS Certification because it doesn't go deep into subjects, but it is challenging if you are aiming to nail it and not just go for the 70% to get the badge.

To study for it, I've compiled a list of the services that are covered.
Some of these descriptions were sourced from AWS Glossary, but some have a personal touch, so take them with a grain of salt, and do your research.

For sure in only 65 questions, not every service will show up, but AWS says in the Exam Guide that all these services and features are a possibility of being covered, so probably it's a good idea of having a minimal understanding of each one of them.

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
  - Allows you to define scaling plans that automate how groups of resources respond to changes. You can use them to optimize availability while keeping the lowest possible cost.
- **AWS Budgets**
  - It allows you to monitor AWS spend and be alerted whe you exceed or are forecasted to exceed limits defined by you. You can also set allerts for when your metrics go below a define threshold, specially interesting if you buy reserved services.
- **AWS CloudFormation**
  - AWS own Infraestrucutre as Code (IaC) allows you to create JSON recepies and use them to create resources, update or destroy them. It's also possible to use them for 3rd party resources.
- **AWS CloudTrail**
  - CloudTrail helps governance, compliance and operational risk auditing, by logging 90 days of user / services activities either allowed or denied, and you can set alerts on top of it with CloudWatch or save this logs to S3.
- **Amazon CloudWatch**
  - Allows to collect logs, correlate them, query, set alarms or trigger automations. It is possible to use it for AWS resources or for on-premises applications and infraestrucutre.
- **AWS Config**
  - AWS Config let you manage configurations, and keep a record of past configurations. It's usefull to manage large infraestructure with multiple fleets of machines and services that share some codebase with different configurations. Ex.: a big eCommerce like Amazon with multiple configs for .com, .uk, .es, .de, etc..
- **AWS Cost and Usage Report**
  - It allows you to track AWS usage and do estimated charges for the account. You can drill down by service, tags, usage type, etc, understanding where are you spending money and how much.
- **Amazon EventBridge (Amazon CloudWatch Events)**
  - AWS EventBridge is a serverless event bus service. You can use it to generate time sensative events (Cron jobs) or create events with complex rules based on CloudWatch values or metrics.
- **AWS License Manager**
  - It let's to easly manage licences from multiple vendores like Microsoft, SAP, Oracle and IBM, for software on AWS or on-premises.
- **AWS Managed Services**
  - AWS Managed Services (MSP) is a program that validates AWS Partners with a proved track record and experience, and allows them to provide services to customers, like planning, designing, building or migrating to the cloud. It acellerates your cloud adoptions or allows you to outsource some of the monitoring/intervention on your cloud infraestructure.
- **AWS Organizations**
  - It let's you consolidate multiple AWS accounts into an organization, letting you do consolidated billing or apply rules to all your AWS accounts.
- **AWS Secrets Manager**
  - It allows you to easily rotate, manage and retrive credentials for Databases, APIs or other services. It helps you protect access to your applicatiosn or services by using a secrets management service.
- **AWS Systems Manager**
  - It allows you to view and manage infraestructure on AWS. It also allows you to automate operational taks on AWS resources.
- **AWS Systems Manager Parameter Store**
  - It allows yo automate common and repetitive IT operations and management tasks, by storing configuration data and secrets in a secure and hierarchical way. You can store passwords, database strings, license codes, and AMI (Amazon Machine Image).
- **AWS Trusted Advisor**
  - Provides recomendations that help you follow AWS best practices. Evaluate your account using checks to help you create an optimized AWS infraestructure, secure, performant and with reduced costs.

## Networking and Content Delivery:
- **Amazon API Gateway**
  - Fully managed service to help you develop, publish and monitor APIs at scale. It's the front door for applications to access data or business logic and a way to connect lambda functions to the outside world.
- **Amazon CloudFront**
  - AWS CDN that help you scale applications by levereging caching mecanisms on the edge, near yous costumers. It helps you provide more service with less costs.
- **AWS Direct Connect**
  - It's an alternative to the internet in order to connect your on-premises infraestructure to AWS, giving big bandwidth with low lattency between 2 infraestructures.
- **Amazon Route 53**
  - AWS DNS service, to manage domain resolutions. It's AWS Nameserver that you can use to manage domains.
- **Amazon VPC**
  - AWS Virtual Private Cloud (VPC) is a way of virtually isolate your resources inside AWS avoiding comunication with other services, other accounts of your own or other AWS clients. It let you manage IPs ranges and how they interconnect with each other like your own private Cloud.

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
  - Centrally manage and automate backups. It supports services like EC2 instances, EBS volumes, S3, RDS, DynamoDB, Document DB, EFS and others.
- **Amazon Elastic Block Store (Amazon EBS)**
  - EBS is a easy-to-scale block-storage designed for EC2, it can be attached to a machine and easly scaled or moved to another machine.
- **Amazon Elastic File System (Amazon EFS)**
  - It's a cloud storage solution that elasticly grow or shrinks as you add or remove files. It can be attached to multiple EC2 instances or ECS containers at the same time, beeing an option to share files in real time between resources, or store data without worrieing about scalability. It mounts  and share data on instances across regions using inter-region VPC peering 🤯 beeing a good way to syncronize data for disaster recovery.
- **Amazon S3**
  - AWS Simple Storage Service (S3) allows you to store files and share them across multiple services or publicly on the web. It have many features and multiple flavores of pricing depending on the way files are replicated across AZs or the expected patern of access. It proudly have 11 nines or availabiltiy. 99,999999999%.
- **Amazon S3 Glacier**
  - A special flavor of S3, made specially for data archiving with low prices but great data precistence, it have multiple options of data retrival from minues to days. You pay a lower value for keeping data there, but theres a fee when you need to retrive data.
- **AWS Snowball Edge**
  - A Petabyte-scale small container let you fastly store and move data to AWS. When you have a lot of data to lift and shift to a database or S3, this can be a good option to move data fast as internet connections can be a bottle neck.
- **AWS Storage Gateway**
  - Its a set of hybrid cloud storage services, that provide on-premises access to virtually unlimited cloud storage. Files are stored on S3, but available locally with old protocoles like SFTP, FTP, NFS, SMB, iSCSI and others. It can have a local hardware that bridge the cloud storage with local cache, both for fast access of files on the cloud that are tipicaly accessed locally or for fast copy to a local place and then slowlly copy to the cloud over internet.


# Conclusions
I found it useful to overview a vast amount of AWS services and features. For sure some of them I have never used and now I know they exist and more or less what value they add, in case I need to research further to check if they are a viable option for the project in hand.
