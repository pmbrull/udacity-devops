# Cloud DevOps Engineer - Fundamentals

## Introduction

Welcome to Udacity Cloud DevOps Nanodegree Program

Companies, big and small, are rapidly adopting cloud computing to enable their digital transformation. According to the latest Gartner report, the cloud tech services market is projected to grow 17.3% in 2019, totaling $206 billion. This growth is due to the desirability of cloud computing, as it allows companies to innovate at a faster pace and reduce operational costs.
IT organizations that adopt DevOps perform better

    They experience 1/60th of the service failures
    They recover from failure 168 times faster than their lower-performing peers
    They deploy 30 times more frequently with 1/200th of the lead time


Change model ELSA: Event - Language - Structure - Agency. Push for an Event that shows what can actually happen so that the Language changes: from No we cant do that, to maybe it is possible. Find a small area of improvement in the organization, do it, and share back the result. Take actions so that when you are pushing for change, the attitude goes from permission seeking to value seeking. Match the solution that you see to the desire that they are seeking.
A silo is just a closed community for decision making and where a problem gets discussed. To break the silos, the first step is bringing that people to your people. For example, a DBA does not need a database. It's rather the opposite, there were some software developers that needed to store data but did not want to fight against the runtime part, so they created the figure of DBA out of a conversation, so a knowledge / tech silo is born. This is an exclusive approach. With DevOps you follow an inclusive approach, where everyone is co-responsible for a solution to run correctly in Production, so bring in all the necessary knowledge, but we are not forcing anyone into a small box to develop themselves. How can we work together to make something that is better than what we have today.

Do not fight agains "best practices", as there is no such thing. What we have are good practices that were born inside a frame. Instead, ask yourself what events brought to those best practices and how you can shape from that, how can we recapture the things that are actually valuable.

Metrics for the solution are important: at the end of a period, measure the effectiveness of the solution or re-think the metrics if they are not good enough. Critical and data driven approach to test the execution of a process.

## Lesson 1 - Cloud Computing


This lesson will cover how to host a website in the cloud, with all secutiry, computing and storage benefits it involves.

### Cloud Computing is the delivery of IT resources over the Internet. The cloud is like a virtual data center accessible via the Internet that allows you to manage:

    Storage services likes databases
    Servers, compute power, networking
    Analytics, artificial intelligence, augmented reality
    Security services for data and applications

Characteristics of Cloud Computing

    Pay as you go - You pay only for what you use and only when your code runs.
    Autoscaling - The number of active servers can grow or shrink based on demand.
    Serverless - Allows you to write and deploy code without having to worry about the underlying infrastructure, which is managed by the cloud provider. Therefore, as a developer, you just need to focus on writing code.

### Types of Cloud Computing

* Infrastructure-as-a-Service (IaaS): The provider supplies virtual server instances, storage, and mechanisms for you to manage servers.

* Platform-as-a-Service (PaaS): A platform of development tools hosted on a provider's infrastructure. You just focus on developing and deploying applications.

* Software-as-a-Service (SaaS): A software application that runs over the Internet and is managed by the service provider.

### Cloud Deployment Models

* Public Cloud: A public cloud makes resources available over the Internet to the general public.

* Private Cloud: A private cloud is a proprietary network that supplies services to a limited number of people. (on-premise)

* Hybrid Cloud: A hybrid model contains a combination of both a public and a private cloud.

The hybrid model is a growing trend in the industry for those organizations that have been slow to adopt the cloud due to being in a heavily regulated industry. The hybrid model gives organizations the flexibility to slowly migrate to the cloud.

### Benefits

There are several benefits to the cloud.

    Stop guessing about capacity.
    Avoid huge capital investments up front.
    Pay for only what you use.
    Scale globally in minutes.
    Deliver faster.
    No huge capital investment upfront.

### Cloud Based Products
Amazon Web Services offers a broad set of global cloud-based products.

Analytics

    Quick Sight
    Athena
    Redshift

Application integration

    Simple Queue Service (SQS)
    Simple Notification Service (SNS)

Cost management

    AWS Budgets

Compute services

    Elastic Cloud Compute (EC2)
    Lambda
    Elastic Beanstalk

Database management services

    MySQL
    Oracle
    SQLServer
    DynamoDB
    MongoDB

Developer tools

    Cloud 9
    Code Pipeline

Security services

    Key Management Service (KMS)
    Shield
    Identity and Access Management (IAM)

Additional Services

    Blockchain
    Machine Learning
    Computer Vision
    Internet of Things (IoT)
    AR/VR

### Global Infrastructure

* Region: A region is considered a geographic location or an area on a map. You choose a region to reduce latency and costs. If you are developing a tool for China, don't use the East Coast region, as it will have a lot of latency.

OBS: Resources do not replicate accross regions!

* Availability Zone: An availability zone is an isolated location within a geographic region and is a physical data center within a specific region.

* Edge Location: An edge location is as a mini-data center used solely to cache large data files closer to a user's location. Used to serve content as quick as possible - content delivery network.

Additional Information

    There are more Availability Zones (AZs) than there are Regions.
    There should be at least two AZs per Region.
    Each region is located in a separate geographic area.
    AZs are distinct locations that are engineered to be isolated from failures.

### Shared Responbility Model

AWS is responsible for security OF the cloud, we are responsible for security IN the cloud.

Examples

AWS is responsible for:

    Securing edge locations
    Monitoring physical device security
    Providing physical access control to hardware/software
    Database patching
    Discarding physical storage devices

You are responsible for:

    Managing AWS Identity and Access Management (IAM)
    Encrypting data
    Preventing or detecting when an AWS account has been compromised
    Restricting access to AWS services to only those users who need it

AWS provides many powerful security controls but when and how you apply them is your responsibility. 

### S3 & CloudFront

In this hands-on exercise, you will create a S3 bucket with a Cloud Front distribution.
Prerequisites:

    AWS Account

Topics Covered:

By the end of this lab, you will be able to:

    Create and configure a bucket
    Upload an object to a bucket
    Create distribution

Steps:

    Create S3 Bucket
        On the AWS Management Console page, type S3 in the Find Services box and then select S3.
        Click Create bucket
        Enter a Bucket name.
            Note: Bucket names must be globally unique.
        Click the Create button.
        Once the bucket is created, click on the name of the bucket to open the bucket to the contents.
    Upload Object to Bucket
        Once the bucket is open to its contents, click the Upload button.
        Click the Add Files button.
        Select a file from your local computer to upload.
        Click Open.
        Click Upload.
    Create CloudFront Distribution
        Select Services from the top left corner.
        Enter cloud front in the Find a service by name or feature text box and select Cloud Front.
        Click Create Distribution.
        Under the Web delivery method, select Get Started.
        Under Origin Settings:
        Under Origin Domain Name, select the S3 bucket that you just created.
        Under Origin Path, enter / to indicate the root level.
        Leave the defaults for the rest of the options.
        Click Create Distribution.
            Note: It may take up to 10 minutes for the CloudFront Distribution to be created.
    Delete Bucket and Distribution
        To delete the Cloud Front distribution, click on the radio button next to the Delivery Method for the distribution. Click Disable and then Yes, Disable. Click Close.
        Once the distribution is disabled, you can delete it by selecting the radio button next to the Delivery Method and clicking the Delete button.
        To delete the S3 bucket, navigate to S3, but clicking on Services and typing S3 in the Find Services box and then select S3.
        Select the radio button next to the name of the bucket you want to delete.
        Click Delete.
        Type the name of the bucket to confirm deletion.
        Click the Confirm button.

## Lesson 2 - Foundational and Compute Service

### Elastic Cloud Compute

Elastic Cloud Compute or EC2 is a foundational piece of AWS' cloud computing platform and is a service that provides servers for rent in the cloud.

Pricing Options
There are several pricing options for EC2.

    On Demand - Pay as you go, no contract.
    Dedicated Hosts - You have your own dedicated hardware and don't share it with others.
    Spot - You place a bid on an instance price. If there is extra capacity that falls below your bid, an EC2 instance is provisioned. If the price goes above your bid while the instance is running, the instance is terminated.
    Reserved Instances - You earn huge discounts if you pay up front and sign a 1-year or 3-year contract.

Tips

    EC2 is found under the Compute section of the AWS Management Console.

    Spot instances can save you up to 90% off the on-demand pricing.

    There are several instance types that provide varying combinations of CPU, memory, storage, and networking capacity.


### Elastic Block Store

Elastic Block Store (EBS) is a storage solution for EC2 instances and is a physical hard drive that is attached to the EC2 instance to increase storage.

Tips

    EBS is found on the EC2 Dashboard.
    There are several EBS volume types that fall under the categories of Solid State Drives (SSD) and Hard Disk Drives (HDD).

The advantage of using EBS instead of in memory (or instance store) is that you are able to persist the data after EC2 is terminated, so any data stored in the volume is still accessible. Moreover, any EBS is automatically replicated in its AZ => ofers high availability, durability and disaster recovery.

In the volume page > Actions, you can easily change both size and volume type.

### Security

Security in the cloud allows you to have complete control over your virtual networking environment.

    Configure your virtual network with public or private facing subnets
    Launch your servers in the selected network to secure access


### Virtual Private Cloud (VPC)

Virtual Private Cloud or VPC allows you to create your own private network in the cloud, in contraposition of Flat Networks, where all users, i.e., all EC2 instances, are connected to the same switch. You can launch services, like EC2, inside of that private network. A VPC spans all the Availability Zones in the region.

VPC allows you to control your virtual networking environment, which includes:

    IP address ranges
    subnets
    route tables
    network gateways

Tips

    VPC is found under Networking & Content Delivery section of the AWS Management Console.
    The default limit is 5 VPCs per Region. You can request an increase for these limits.
    Your AWS resources are automatically provisioned in a default VPC.
    There are no additional charges for creating and using the VPC.
    You can store data in Amazon S3 and restrict access so that it’s only accessible from instances in your VPC.


A VPC can protect, for example:  EC2 Instances can be launched in a VPC, and you can store data in Amazon S3 and restrict access so that it’s only accessible from instances in your VPC.

### Virtual Servers in the Cloud

In this hands-on exercise, you will launch a virtual server in the cloud within a secure network. You will also manage additional storage options for your server.
Prerequisites:

    AWS Account

Topics Covered:

By the end of this lab, you will be able to:

    Launch a secure EC2 (Elastic Cloud Compute) instance within a VPC (Virtual Private Cloud)
    Manage an EBS volume

Steps:

    Access VPC service from AWS Management Console
        On the AWS Management Console page, type vpc in the Find Services box and then select VPC.
        Click the Launch VPC Wizard button and select VPC with a Single Public Subnet. Important: In the VPC Name text box, enter a name for the VPC, and then select the first AZ from the Availability Zone dropdown. Leave everything else as the defaults.
        Select Create VPC button.
        You should see the VPC Successfully Created page, click the OK button in the far right. Important: You should see a table that lists all of the VPCs, make a note of the one just created.
    Launch an EC2 instance
        Navigate to the EC2 console page, by clicking on Services in the upper left-hand menu. Type EC2 in the text box and click on EC2 found in the search results.
        On the EC2 Dashboard page, click on Instances in the left-hand navigation.
        Click Launch Instance.
        Select the Amazon Linux 2 AMI (HVM), SSD Volume Type Amazon Machine Image (AMI). Important: You are free to choose a different AMI, but to avoid excessive charges, pick one that says, Free Tier Eligible.
        For the Instance Type, select the free-tier instance type of t2.micro.
        Click on Next: Configure Instance Details.
        Enter the 1 for the Number of Instances.
        For Purchasing option, leave unchecked.
        For Network, select the VPC that was created in the previous step, and then select the subnet in to which to launch the instance.
        Keep the other default settings on this page as is.
    Attach an EBS volume
        Click on Next: Add Storage to attach an EBS volume. Important: Here we already see there is a root volume (or device) attached to your instance, this is an EBS volume. We are going to add additional storage.
        To attach additional storage, click on Add New Volume.
        Select Delete on Termination and keep the other default settings.
        Click Review and Launch.
        Click Launch Instances.
        Generate and download a new key pair and then launch the instance. Important: This will allow you to SSH into your instance from your local machine. This is a one-time process, so generate and download the new key pair now.
        The launch will take a couple of minutes, select View Instances during the wait.
        Check the instance state, it should say running.

Congratulations! You’ve launched your first virtual server in the cloud.

    Cleanup & Disable EC2 Instance To avoid recurring charges for leaving an instance running, let’s disable the EC2 instance and terminate the VPC
        From the EC2 Dashboard, select the instance just created, click Actions, then Instance State, and then select Terminate.
        From the VPC Dashboard, select the VPC just created, click Actions, then Delete VPC.

### Lambda - Serverless Computing Power
AWS Lambda provides you with computing power in the cloud by allowing you to execute code without standing up or managing servers.

Tips

    Lambda is found under the Compute section on the AWS Management Console.
    Lambdas have a time limit of 15 minutes.
    The code you run on AWS Lambda is called a “Lambda function.”
    Lambda code can be triggered by other AWS services - Lambda is event-driven, so you can run your code based on certain events happening, like a file upload, or a record being inserted in a database, etc. 
    AWS Lambda supports Java, Go, PowerShell, Node.js, C#/.NET, Python, and Ruby. There is a Runtime API that allows you to use other programming languages to author your functions.
    Lambda code can be authored via the console.

### Compute Power in the Cloud

In this hands-on exercise, you will write your first Lambda function using Node.js.
Prerequisites:

    AWS account

Topics Covered:

By the end of this lab, you will be able to:

    Author a Lambda function using Node.js via the console
    Test a Lambda function via the console

Steps:

    Create a Lambda Function
        On the AWS Management Console page, type lambda in the Find Services box and then select Lambda.
        Click the “Create function” button and select Author from scratch.
        Enter a Function name and select Node.js 8.10 as the runtime.
        For Permission, click Choose or create an execution role, and select Create a new role with basic Lambda permissions.
        Click Create function.
    Modify a Lambda Function
        Scroll down to the code for the Lambda function.
        Replace the code on Line 5 with the statement below:

        body: JSON.stringify('Hello ' + event.key1 + ' from Lambda!'),

        Click the Save button in the upper right-hand corner.
        Scroll down to the Basic Settings section.
            For the Description, enter Udacity Function.
            Change the Timeout from 3 seconds to 10 minutes.
            Click the Savebutton in the upper right-hand corner.

    Test a Lambda Function
        Click on the Test button in the upper right-hand corner.
        Ensure the Event template is Hello World.
        For the Event name enter TestEvent Important: The name cannot contain spaces.
        Update the JSON to the statement below, replacing the statement with your name.

        {
        "key1": "Place your name here"
        }

    Click Create.
    Click the Test button in the upper right-hand corner again.
    Scroll up to see the output in the Execution Results pane.
    Review your results in the window.

Congratulations on writing your first Lambda function!

### Elastic Beanstalk

Elastic Beanstalks is an orchestration service that allows you to deploy a web application at the touch of a button by spinning up (or provisioning) all of the services that you need to run your application: EC2, auto-scaling, elastic load balancer. We can also administrate all the services separatedly. It can also spin up databases, VPCs and security groups.

Tips

    Elastic Beanstalk is found under the Compute section of the AWS Management Console.
    Elastic Beanstalk can be used to deployed web applications developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker.
    You can run your applications in a VPC.

Steps:

    Access Elastic Beanstalk service from AWS Management Console
        On the AWS Management Console page, type elastic beanstalk in the Find Services box and then select Elastic Beanstalk.
        If this is your first time accessing Elastic Beanstalk, click the Get started button.
        Enter an Application name.
        Under Platform, click the dropdown for Choose a platform. Select Tomcat.
        Under Application code, select Upload your code. Click the Upload button.
        Under Upload your code, make sure Local file is selected for Source code origin.
        Click Choose File and upload the downloaded WAR file (link above in pre-requisites), udacity.war.
        Click the Upload button.
        Click the Create application button. Important: It will take about 10 minutes for your application to be created. There are several resources that need to be spun up to support your application. Your application is created once you see a green check mark and the Health of your application is Ok.
        After the application is created, copy the application’s URL. Important: The URL can be found on the top of the page, to the right of your application’s name.
    Test the deployed web application in a browser
        Navigate to a web browser like Chrome or Safari.
        Paste the application URL and append /message on the end of the URL.
        Upon successfully accessing that URL, you will see the text Hello World in your browser window.
    Inspect the EC2 instance created for you
        Navigate to the EC2 console and inspect the instance that was created for you. The instance has the same name as your application. You can administer and manage this EC2 as if you created it yourself.
    Cleanup and delete resources
        To clean up the resources to avoid recurring charges, navigate back to the Elastic Beankstalk console.
        Select your application.
        Select the Actions button in the upper-right hand corner.
        Select Terminate environment.
        Enter the name of the application to be deleted.
        Click the Terminate button.
        After the application is terminated, you will be brought to the main page for the application.
        Click on the Actions button in the upper right-hand corner.
        Select Delete application.
        Enter the name of your application.
        Click the Delete button.

## Storage and Content Delivery

### Storage in the Cloud

Storage and database services in the cloud provide a place for companies to collect, store, and analyze the data they've collected over the years at a massive scale.

Storage & Database Services

    Amazon Simple Storage Service (Amazon S3)
    Amazon Simple Storage Service (Amazon S3) Glacier
    DynamoDB
    Relational Database Service (RDS)
    Redshift
    ElastiCache
    Neptune
    Amazon DocumentDB


* Durability: no data loss.
* Availability: how quickly you can access your data - fast and reliable.
* Scalability: meet demand seamlessly by adding or removing the resources necessary to mantain a steady state and fast response time. Vertical, horizontal or diagonal.

### S3 & S3 Glacier
Amazon Simple Storage Service (or S3) is an object storage system in the cloud.

Storage Classes
S3 offers several storage classes, which are different data access levels for your data at certain price points.

    S3 Standard
    S3 Glacier
    S3 Glacier Deep Archive
    S3 Intelligent-Tiering
    S3 Standard Infrequent Access
    S3 One Zone-Infrequent Access

A file stored in S3 gets a unique URL that then can be used to access it. All objects are stored in a bucket, which live in a region. However, bucket name must be globally unique. It is designed focusing on durability and availability 99'99999%. The use cases are: static websites, content delivery, backup and recovery, archival and big data, application data and hybrid cloud storage.

There are different storage classes, which are simply different access levels for your data. For example, in S3 Glacier you should store archival data that is not intended to be accesses frequently. It is cheaper than S3 Standard, but data retrieval can take from minutes to a few hours. It would be useful for audit logs. S3 Glacier is a secure, durable, and low-cost storage class for data archiving.
 
Tips

    S3 is found under the Storage section on the AWS Management Console.
    A single object can be up to 5 terabytes in size.
    You can enable Multi-Factor Authentication (MFA) Delete on an S3 bucket to prevent accidental deletions.
    S3 Acceleration can be used to enable fast, easy, and secure transfers of files over long distances between your data source and your S3 bucket. 

### DynamoDB

DynamoDB is a NoSQL document database service that is fully managed. Unlike traditional databases, NoSQL databases, are schema-less. Schema-less simply means that the database doesn't contain a fixed (or rigid) data structure. It can quickly scale and handle large amounts of data. Schema-less + no fixed structure = high flexibility.

DynamoDB is a fully managed service, so you don't need to worry about servers, patches or upgrades. Companies such as Lyft, Airbnb or Netflix relies on DynamoDB to support their mission critical workloads.

Data is stored under tables in JSON format.

Tips

    DynamoDB is found under the Database section on the AWS Management Console.
    DynamoDB can handle more than 10 trillion requests per day.
    DynamoDB is serverless as there are no servers to provision, patch, or manage.
    DynamoDB supports key-value and document data models.
    DynamoDB synchronously replicates data across three AZs in an AWS Region.
    DynamoDB supports GET/PUT operations using a primary key.

We could also set up a Global Table - it can exist in multiple AWS Regions with automatic replication! Moreover, we can add Triggers, i.e., a Lambda function to run anytime a record is inserted into the table.

In this hands-on exercise, you will create a NoSQL database in the cloud.
Prerequisites:

    AWS Account

Topics Covered:

By the end of this lab, you will be able to:

    Create a table
    Add data to a table
    Query data in a table

Steps:

    Access the DynamoDB service from AWS Management Console
        On the AWS Management Console page, type "dynamo" in the Find Services box and then select DynamoDB.
        On the DynamoDB Console, click Create table.
        Enter Course as the Table name.
        Enter Name in for the Partition key and ensure String is selected. Note: The partition key spreads data against partitions for scalability.
        Keep the remainder of the defaults, and click the “Create” button.
    Add Data to the Table
        Once the table is created, click on the Items tab.
        Click Create item.
            In the data entry window, type the following:
                For name, enter, Course 1 and click Save
                Click the +icon to add additional fields:
                    Select Insert
                    Select String
                    For the field name, enter Teacher
                    For the value, enter Kesha Williams
                    Click Save
        Follow the same process to add 5 more documents.
    Query Data in a Table
        In the dropdown that contains Scan, change it to Query.
        Where it says Enter value, in the row next to the name Partition key, enter Course 1 and click Start Search.
        You should see your search results appear in the window.
    Cleanup and delete resources
        To clean up the resources to avoid recurring charges, ensure the table name is selected.
        Click on the Delete table button.
        Ensure Delete all CloudWatch alarms for this table is selected and click Delete. 

### Relational Database Service (RDS)

RDS (or Relational Database Service) is a service that aids in the administration and management of databases. RDS assists with database administrative tasks that include upgrades, patching, installs, backups, monitoring, performance checks, security, etc.

Database Engine Support

    Oracle
    PostgreSQL
    MySQL
    MariaDB
    SQL Server
    Aurora (AWS)

Features

    failover
    backups
    restore
    encryption
    security
    monitoring
    data replication
    scalability

However, Database Administration is hard and time consuming and requires specialized skills. Or, if your time does not have any specialist of that sort, it takes time away from your developers. DBA tasks include updgrades, patching, installs, backups, monitoring and performance checks and security, etc.

The point of RDS is that it aids in the database administration. It sits on top of your database and automates time consuming tasks. To deliver a managed service experience, Amazon RDS doesn't provide shell access to DB instances.

From RDS, it is easy to check any configuration from all created databases.

### Redshift

Redshift is a cloud data warehousing service to help companies manage big data. Redshift allows you to run fast queries against your data using SQL, ETL, and BI tools. Redshift stores data in a column format to aid in fast querying. It also automates mantainance and administration tasks.

Features: fast query and analysis, not transaction processing and usually stored historical data (archival), while more recent transactions are more suitable in a relational database, where you can query them regularly.

Data is stored in columnar format, rather than row store. This aids in fast query and analysis.

Tips

    Redshift can be found under the Database section on the AWS Management Console.
    Redshift delivers great performance by using machine learning.
    Redshift Spectrum is a feature that enables you to run queries against data in Amazon S3.
    Redshift encrypts and keeps your data secure in transit and at rest.
    Redshift clusters can be isolated using Amazon Virtual Private Cloud (VPC).

### RDS Lab

In this hands-on exercise, you will create a MySQL database instance using RDS.
Prerequisites:

    AWS Account

Topics Covered:

By the end of this lab, you will be able to:

    Launch a MySQL database

Steps:

    Launch MySQL Database
        On the AWS Management Console page, type rds in the Find Services box and then select RDS.
        On the left-hand side, click Databases.
        Click Create database.
        Under engines option, select MySQL and click the Next button
        Under Instance specifications, leave the defaults.

        Under the Settings section:
            Enter a name for the instance under DB instance identifier

        Note: This will not be the database name.
        Enter a Master username
        Enter a Master password and confirm the password.
        Click Next
        For Virtual Private Cloud (VPC), select Create new VPC.
        Ensure Create new DB Subnet Group is selected.
        Leave the defaults for Subnet group, Public accessibility, Availability zone, and VPC security groups.
        Under Database options, enter a Database name and leave the rest as defaults.
        Under Deletion protection, uncheck Enable deletion protection. Important: In a real production scenario, you would leave this option checked.
        Click Create database`.
    View Instance Details
        Once your database is created, open it by clicking on View DB Instance details.
        Make sure the DB instance status shows available.
        Scroll through and observe how the instance is configured.
    Delete Database Instance Clean up the resources to avoid recurring charges.
        From the RDS Dashboard homepage, select Databases from the left-hand navigation pane.
        Select your newly created database by clicking on the name radio button next to the name.
        From the Actions menu, select Delete.
        In the confirmation popup:
            Uncheck Create final snapshot
            Select I acknowledge that upon instance deletion, automated backups, including system snapshots and point-in-time recovery, will no longer be available.
            Enter the requested confirmation for deletion.
            Click the Delete button

### Content Delivery Network (CDN)

Why do we need CDN? It speeds up the delivery of static and dynamic web content, such as Web pages, cascading style sheets, JavaScript and images.

Usually, content is cached from a period of time and when a user asks for some content, it is pulled from cache, which speeds up the delivery of the content to the end users.

CDN reduces latency and decreases the load on the servers, which provides better end-user experience. Latency: the time it takes to respond to a request, website access + website load.

### Cloud Front

CloudFront is used as a global content delivery network (CDN). Cloud Front speeds up the delivery of your content through Amazon's worldwide network of mini-data centers called Edge Locations. Content is cached for a certain period of time in an edge location that is close to the user. If the user asks for some content, it is first checked in the edge location. If it's not there, then it's pulled from the origin, cached in the edge location, and sent from there to the user.

You can configure how long an element remains cached before you refresh and you can even manually remove some contant from the cached, should it be changed.

CloudFront works with other AWS services, as shown below, as an origin source for your application:

    Amazon S3
    Elastic Load Balancing
    Amazon EC2
    Lambda@Edge
    AWS Shield

Tips

    CloudFront is found under the Networking & Content Delivery section on the AWS Management Console.
    Amazon countinously adds new Edge Locations.
    CloudFront ensures that end-user requests are served from the closest edge location.
    CloudFront works with non-AWS origin sources.
    You can use GeoIP blocking to serve content (or not serve content) to specific countries.
    Cache control headers determine how frequently CloudFront needs to check the origin for an updated version your file.
    The maximum size of a single file that can be delivered through Amazon CloudFront is 20 GB.

Summary: Cloud Front is used to stream content more efficiently.

Moreover, in cloudfront we can enable geographic restriction - disable connections from certain IP adresses. Therefore, it also can be used as a security mechanism.

### S3 & CloudFront

In this hands-on exercise, you will create a S3 bucket with a Cloud Front distribution.
Prerequisites:

    AWS Account

Topics Covered:

By the end of this lab, you will be able to:

    Create and configure a bucket
    Upload an object to a bucket
    Create distribution

Steps:

    Create S3 Bucket
        On the AWS Management Console page, type S3 in the Find Services box and then select S3.
        Click Create bucket
        Enter a Bucket name.
            Note: Bucket names must be globally unique.
        Click the Create button.
        Once the bucket is created, click on the name of the bucket to open the bucket to the contents.
    Upload Object to Bucket
        Once the bucket is open to its contents, click the Upload button.
        Click the Add Files button.
        Select a file from your local computer to upload.
        Click Open.
        Click Upload.
    Create CloudFront Distribution
        Select Services from the top left corner.
        Enter cloud front in the Find a service by name or feature text box and select Cloud Front.
        Click Create Distribution.
        Under the Web delivery method, select Get Started.
        Under Origin Settings:
        Under Origin Domain Name, select the S3 bucket that you just created.
        Under Origin Path, enter / to indicate the root level.
        Leave the defaults for the rest of the options.
        Click Create Distribution.
            Note: It may take up to 10 minutes for the CloudFront Distribution to be created.
    Delete Bucket and Distribution
        To delete the Cloud Front distribution, click on the radio button next to the Delivery Method for the distribution. Click Disable and then Yes, Disable. Click Close.
        Once the distribution is disabled, you can delete it by selecting the radio button next to the Delivery Method and clicking the Delete button.
        To delete the S3 bucket, navigate to S3, but clicking on Services and typing S3 in the Find Services box and then select S3.
        Select the radio button next to the name of the bucket you want to delete.
        Click Delete.
        Type the name of the bucket to confirm deletion.
        Click the Confirm button.

## Lesson 4 - Security

Why do we need security for cloud applications? It is important to secure data, even more that considered PII - personally identifiable information. The important access of cloud security is not only securing data but also the applications that access that data, and even the infrastructure, like the servers.

### AWS Shield

AWS Shield is a managed DDoS (or Distributed Denial of Service) protection service that safeguards web applications running on AWS.

> A DDoS attack is based on overwhelming an application or website with traffic using multiple sources so that the service becomes unavailable.

AWS Shield is a service that you get "out of the box", it is always running (automatically) and is a part of the free standard tier. If you want to use some of the more advanced features, you'll have to utilize the paid tier.

Tips

    AWS Shield can be found under the Security, Identity, & Compliance section on the AWS Management Console.
    AWS Shield Standard is always-on, using techniques to detect malicious traffic.
    AWS Shield Advanced provides enhanced detection.

### AWS WAF

AWS WAF (or AWS Web Application Firewall) provides a firewall that protects your web applications. A firewall is a network security mechanism that monitors and controls incoming and outgoing traffic based on a preset set of security rules.

WAF can stop common web attacks by reviewing the data being sent to your application and stopping well-known attacks, such as SQL injection or cross-site scripting (XSS).

Tips

    WAF is found under the Security, Identity, & Compliance sectin on the AWS Managemen Console.
    WAF can protect web sites not hosted in AWS through Cloud Front.
    You can configure CloudFront to present a custom error page when requests are blocked.

### Identity & Access Management

Identity & Access Management (IAM) is an AWS service that allows us to configure who can access our AWS account, services, or even applications running in our account. IAM is a global service and is automatically available across ALL regions.

Security Concepts

    User
    IAM Group
    IAM Role
    Policy

It is important that when protecting data and systems we verify that the users are who they say they are, and thus only access the specific data they are intended to. This concept is called least-privileged access. This is where IAM helps.

When creating an AWS account, the email addess used becomes the root level account and has full access and permissions. This means that you should not use your root-user credentials for everyday access. One way of securing the root account is by enabling Multi Factor Authentication or MFA.

There are several concepts involved in IAM:

* User: is an entity that you create that represents a person or service that interacts with other servers or applications in a AWS account. It consists in a username and access credentials.
* Group: collection of users. We can also specify security for a group.
* Rolse: Identity with a set of permissions and privileges that are not associated with a user or group. A user can assume a single role temporarily to perform an specific task.
* Policy: It is used to assign granular permissions and can be attached to users, groups and roles. A default set of policies is already provided by AWS, but we can create our own using JSON.

* EC2 Security Groups: are NOT part of IAM. They are a totally different thing from IAM security groups. EC2 SG are related to an EC2 instance and serve as a built-in firewall.

### Security in the Cloud

In this hands-on exercise, you will create an IAM policy and review the generated JSON.
Prerequisites:

    AWS account

Topics Covered:

By the end of this lab, you will be able to:

    Create an IAM policy using the visual editor.

Steps:

    Create a Policy
        On the AWS Management Console page, type IAM in the Find Services box and then select IAM.
        Click on Policies on the left-hand side.
        Click Create policy.
        Next to Service, click Choose a service.
        In the selection box, type S3.
        Select S3.
        Specify the actions allowed in S3 by clicking on List.
        Expand the Read action by clicking on the arrow next to it, then select GetObject.
        Next in the Resources section, ensure Specific is selected, and select the Any checkboxes next to bucket and object.
        Then click on Review policy.
        Enter a name for your policy in the Name box.
        Then click on Create policy.
    Review Policy
        After your policy is created, enter the name of the policy you just created in the Filter policies text box.
        Click on the name of your policy.
        Review the JSON for the policy you just created on the Permissions tab.
        Click on the Policy usage tab to see if this policy is in use. Notice this policy is not attached to any resources yet.

## Lesson 5 - Networking & Elasticity

Now that we know how to secure our applications and services, we also need to make sure that the users are able to find our web app and that we can serve our products with any require load.

### Networking

Networks reliably carry loads of data around the globe allowing for the delivery of content and applications with high availability. The network is the foundation of your infrastructure.

Cloud networking includes:

    network architecture
    network connectivity
    application delivery
    global performance
    delivery

* Network connectivity includes services that offer reliable and cost-effective ways taht allows to route users to internet applications -> instead of directly entering an IP address, I just use, for example, www.google.com. Behind the scenes there is a DNS or Domain Name System resolver that asks a Domain Authority - the registration service user to register google.com - for the IP address that maps to google.com. Then, we are routed to that address and the web gets displayed.

### Route 53

Route 53 is a cloud domain name system (DNS) service that has servers distributed around the globe used to translates human-readable names like www.google.com into the numeric IP addresses like 74.125.21.147.

Features

    scales automatically to manage spikes in DNS queries
    allows you to register a domain name (or manage an existing)
    routes internet traffic to the resources for your domain
    checks the health of your resources and routes the users to an alternate website if the web server is down.

Tips

    Route 53 is found under the Networking & Content Delivery section on the AWS Management Console.
    Route 53 allows you to route users based on the user’s geographic location.

### Elasticity in the Cloud

One of the main benefits of the cloud is that it allows you to stop guessing about capacity when you need to run your applications. Sometimes you buy too much or you don't buy enough to support the running of your applications.

With elasticity, your servers, databases, and application resources can automatically scale up or scale down based on load.

Resources can scale up (or vertically). In Amazon EC2, this can easily be achieved by stopping an instance and resizing it to an instance type that has more RAM, CPU, IO, or you can scale out (or horizontally), which increases the number of resources. An example would be adding more servers.

### EC2 Auto Scaling

EC2 Auto Scaling is a service that monitors your EC2 instances and automatically adjusts by adding or removing EC2 instances based on conditions you define in order to maintain application availability and provide peak performance to your users.

Features

    Automatically scale in and out based on needs.
    Included automatically with Amazon EC2.
    Automate how your Amazon EC2 instances are managed.

Tips

    EC2 Auto Scaling is found on the EC2 Dashboard.
    EC2 Auto Scaling adds instances only when needed, optimizing cost savings.
    EC2 predictive scaling removes the need for manual adjustment of auto scaling parameters over time.

It works with a messaging system or SNS - Simple Notification Service - that alerts you when launching new servers or terminating others. You can custom the message to include information such as the terminated or launched instance and the reason. You can configure EC2 Auto Scaling to send an SNS notification whenever your EC2 Auto Scaling group scales. 

There is another sclaing system - AWS Auto Scaling - that can be used to scale automatically other services such as DynamoDB.

> AutoScaling groups contains a collection of EC2 instances that share similar characteristics and are treated as a logical grouping.

### Elastic Load Balancing

Elastic Load Balancing automatically distributes incoming application traffic across multiple servers.

Elastic Load Balancer is a service that:

    Balances load between two or more servers
    Stands in front of a web server
    Provides redundancy and performance

Tips

    Elastic Load Balancing can be found on the EC2 Dashbaoard.
    Elastic Load Balancing works with EC2 Instances, containers, IP addresses, and Lambda functions.
    You can configure Amazon EC2 instances to only accept traffic from a load balancer.

* Redundancy: If you lose a server, the load balancer will send requests to other working server. This feature maintains continuous operations in an emergency.
* Performance: If a server starts having issues or bottlenecks, the load balancer will add more servers to the pool of available servers. Auto scaling automatically adjusts capacity to maintain a steady state.

In order to use the load balancer, you need to make sure that you launched the EC2 instances onto you plan to apply the load balancer.

### EC2 Auto Scaling

In this hands-on exercise, you will use Auto Scaling to automatically launch Amazon EC2 instances in response to conditions you specify. You will also see auto scaling in action as it automatically provisions a replacement instance.
Prerequisites:

    AWS Account

Topics Covered:

By the end of this lab, you will be able to:

    Use auto scaling to launch EC2 instances
    Create an auto scaling group
    Test auto scaling

Steps:

    Create a Launch Configuration
        On the AWS Management Console page, type EC2 in the Find Services box and then select EC2.
        Scroll down to the Auto Scaling section on the left-hand menu and click Auto Scaling Groups.
        Click the Create Auto Scaling group button.
        Review the steps and click on Get started.

        Create a launch configuration by first selecting an Amazon Machine Image (AMI). In the row for Amazon Linux 2 AMI (HVM), SSD Volume Type, click the Select button.

        Note: An AMI is a template for an instance that indicates the operating system, an application server, and applications.

        Confirm that t2.micro is selected.
        Click Next: Configure details.
        Enter a name of your choosing in the Name field.
        Expand the Advanced Details section.
        Next to IP Address Type, click on Assign a public IP address to every instance.
        Click Next: Add Storage. Review the screen.
        Click Next: Configure Security Group.
        Ensure Create a new security group is selected.
        Click Review.
        Click on Create launch configuration.
        On the Select an existing key pair or create a new key pair, select Create a new key pair, enter a key pair name in the Key pair name field, and click Download Key Pair.
        Click on Create launch configuration.
    Create an Auto Scaling Group
        On the Create Auto Scaling Group page, enter a group name of your choosing in the Group name field, ensure the Group size is set to 1, for Network leave the default value. If no default value is shown, click on Create new VPC, and select the first Subnet by clicking in the Subnet field.
        Click Next: Configure scaling policies.
        Ensure that Keep this group at its initial size is selected.
        Click Review.
        Review the selected options and click Create Auto Scaling group.
        Click Close.
    Verify your Auto Scaling Group
        Verify that the group has launched your EC2 instance by first ensuring the auto scaling group you just created is selected and examining the Details tab shown on the bottom of the screen.
        Click the Activity History tab. The status of your instance should be Successful, which means the instance is launched.
        Click on the Instances tab. Notice the Lifecycle column states InService.
    Test Auto Scaling
        Click on the Instances tab.
        Under the Instance ID column, click on the blue Instance ID link.
        You will be taken to the Amazon EC2 console Instances page.
        Your instance should be selected.
        Click the Actions button, scroll down to Instance State, and select Terminate. Then select Yes, Terminate.
        In the left-hand navigation pane, click Auto Scaling Groups.
        Click the Instances tab. You will eventually see a new instance appear. If the new instance doesn’t appear, click refresh occasionally to update the list.
        Click on the Activity History tab to review the history for the Instance.
    Delete Auto Scaling Resources
        At the top of the screen, click the Actions button next to the Create Auto Scaling group.
        Click the Delete option.

## Lesson 6 - Messaging & Containers

### Messaging in the Cloud

There are often times that users of your applications need to be notified when certain events happen, for example when a large withdrawal is made in your account. Notifications, such as text messages or emails can be sent through services in the cloud. The use of the cloud offers benefits like lowered costs, increased storage, and flexibility.

Using some cloud services you can both send notifications and track their lifecycle. Messaging is a form of notification where not a user but rather another service is receiving the notification. It usually occurs between internet-based applications and devices. Messaging systems are highly related to queueing technology.

### Simple Notification Service

Amazon Simple Notification Service (or SNS) is a cloud service that allows you to send notifications to the users of your applications. SNS allows you to decouple the notification logic from being embedded in your applications and allows notifications to be published to a large number of subscribers.

Features

    SNS uses a publish/subscribe model - the users, in order to receive the notifications, they need to sign-up or subscribe first.
    SNS can publish messages to Amazon SQS queues, AWS Lambda functions, and HTTP/S webhooks.

Subscribers can be either a person or another AWS service, and notifications can be sent using mobile push, text messages and email.

Tips

    SNS is found under the Application Integration section on the AWS Management Console.
    SNS Topic names are limited to 256 characters.
    A notification can contain only one message.

### Queues

A queue is a data structure that holds requests called messages. Messages in a queue are commonly processed in order, first in, first out (or FIFO).

Messaging queues improve:

    performance
    scalability
    user experience - the use of asynchronous processing, where a user doesn't wait for a response, improves the overall user experience.

By using queues, when a user performs a certain action, you can just notify that it was aknowledged and put that on the queue to be processed when resources are available.

### Simple Queue Service
Amazon Simple Queue Service (SQS) is a fully managed message queuing service that allows you to integrate queuing functionality in your application. SQS offers two types of message queues: standard and FIFO.

Features

    send messages,
    store messages and
    receive messages between applications without losing messages.

Tips

    The Simple Queue Service (SQS) is found under the Application Integration on the AWS Management Console.
    FIFO queues support up to 300 messages per second.
    FIFO queues guarantee the ordering of messages.
    Standard queues offer best-effort ordering but no guarantees.
    Standard queues deliver a message at least once, but occasionally more than one copy of a message is delivered.

You should use FIFO ordering when message ordering is critical and standard queues when messages can arrive more than once and be processed out of order. With FIFO, messages are processed exactly once.

### SNS

In this hands-on exercise, you will learn how to send alerts via SNS by creating a topic, subscribing to a topic, and publishing an alert message to a topic.
Prerequisites:

    AWS Account

Topics Covered:

By the end of this lab, you will be able to:

    Create a topic
    Subscribe to a topic
    Publish a message to a topic

Steps:

    Create a Topic
        On the AWS Management Console page, type sns in the Find Services box and then select Simple Notification Service. The SNS Dashboard appears.
        On the left-hand menu, click on Topics.
        Click on Create topic.
        Enter a name for your topic in the Name field.
        In the Access policy – optional section, for the Define who can publish messages to the topic section, ensure Everyone is selected allowing anyone to publish to the topic. For the Define who can subscribe to this topic section, ensure Everyone is selected.
        Click Create Topic. The topic screen will display.
    Subscribe to a Topic
        Click Create subscription from the Subscriptions section.
        For the Protocol field, select Email.
        For the Endpoint, enter the email that should receive the notifications.
        Click Create subscription.
        The subscription page will display and the status will be Pending confirmation. After your subscription is created, you must confirm it.
        In your email client, check the email address that you provided for the Endpoint and choose Confirm subscription in the email from Amazon SNS.
        In your web browser, a subscription confirmation screen appears.
    Publish a Message to a Topic
        From the menu on the left-hand side, click on Topics.
        Select the topic you created earlier and then click Publish message.
        Enter a subject in the Subject field.
        Enter a value in the Message body to send to the endpoint box in the Message body section.
        Scroll down and click Publish message.
        In your email client, read the email from Amazon SNS.

### Containers in the Cloud

Enterprises are adopting container technology at an explosive rate. A container consists of everything an application needs to run: the application itself and its dependencies (e.g. libraries, utilities, configuration files), all bundled into one package.

Each container is an independent component that can run on its own and be moved from environment to environment.


Docker is the leading container technology. There are several container orchestration services that help you manage docker clusters, such as Kubernetes. The whole idea behind is that everything that needs the application to run is bundled in a package - container, that can be easily moved from environment to environment or even used to scalate. Each container is an independent component that can run on its own.

Migrating a monolith application to a microservices architecture means decoupling all the parts of the application into discrete standalone components that can comunicate among themselves and work together or with other external systems. Each microservice is an individual component with no inter-dependencies.

 A container consists of everything an application needs to run: the application itself and its dependencies (e.g. libraries, utilities, configuration files), all bundled into one package.

### Elastic Container Service (ECS)

ECS is an orchestration service used for automating deployment, scaling, and managing of your containerized applications. ECS works well with Docker containers by:

    launching and stopping Docker containers
    scaling your applications
    querying the state of your applications

Tips

    ECS is under the Compute section on the AWS Management Console.
    You can schedule long-running applications, services, and batch processeses using ECS.
    Docker is the only container platform supported by Amazon ECS.


 ECS is used for automating deployment, scaling and managing your containerized applications. 

 A task definition is a blueprint that describes the container information for your application. ECS keeps copies of different versions of the same task. There, you adjust the disk and memory you require for your application to run.

### AWS Management

Tools to troubleshoot and manage applications + resource management.

### Logging & Auditing in the Cloud

It is important to have visibility into your cloud resources and applications. Being able to answer questions like, how is the server performing, what is the current load on the server, what is the root cause of an application error that a user is seeing, what is the path that leads to this error.

Being able to answer these question is imperative in order to provide goo duser experiences. However, monitoring distributed systems that run in the cloud can be difficult. For application that run in the cloud, you will need access to logging and auditing services to help you pro-actively monitor both resources and applications.

### Cloud Trail

Cloud Trail allows you to audit (or review) everything that occurs in your AWS account. Cloud Trail does this by recording all the AWS API calls occurring in your account and delivering a log file to you.
Features

CloudTrail provides event history of your AWS account activity, including:

    who has logged in
    services that were accessed
    actions performed
    parameters for the actions
    responses returned

This includes actions taken through the AWS Management Console, AWS SDKs, command line tools, and other AWS services.

Tips

    Cloud Trail is found under the Management & Governance section on the AWS Management Console.
    CloudTrail shows results for the last 90 days.
    You can create up to five trails in an AWS region.

CloudTrail logs actions performed through the AWS management console and AWS SDK, which means that any application using SDK to connect to any AWS service or using command line tools is going to be logged. This is very useful to keep track for any suspicious or unexpected activity.

You can also set up alerts or alarms should certain activities occur.

Cloud events can only be processed by one trail for free.

### Cloud Watch

Cloud Watch is a service that monitors resources and applications that run on AWS by collecting data in the form of logs, metrics, and events. You can also set alarms and create triggers to react to changes made on the account's resources. The ability to review log files is crucial during the development and support of the application.

You could use Cloud watch to review the logs written through a lambda application to then diagnose and monitor behavior. Moreover, you could use CloudWatch as a trigger of lambda functions, causing lambda to run on a given schedule.

Features
There are several useful features:

    Collect and track metrics
    Collect and monitor log files
    Set alarms and create triggers to run your AWS resources
    React to changes in your AWS resources

Tips

    CloudWatch is found under the Management & Governance section on the AWS Management Console.
    Metrics are provided automatically for a number of AWS products and services.

Cloud Watch can collect and track metrics, collect and monitor log files, and create triggers to run your AWS resources.

In this hands-on exercise, you will create a Cloud Watch event to notify via an SNS topic when an EC2 instance is created.
Prerequisites:

    AWS account
    SNS Topic created in previous lab

Topics Covered:

By the end of this lab, you will be able to:

    Create Cloud Watch event to react to the creation of an Amazon EC2 instance
    Send SNS notification via Cloud Watch when an event occurs

Steps:

    Create CloudWatch Rule
        On the AWS Management Console page, type cloud watch in the Find Services box and then select CloudWatch. The CloudWatch Dashboard appears.
        On the left-hand menu, under Events, select Rules.
        Click Create rule.
        For Service Name, select EC2.
        For the Event Type, select EC2 Instance State-change Notification.
        Select the Specific state(s) radio button. Select running from the drop-down box. Note: This configures the rule to trigger whenever an Amazon EC2 instance changes to the running state, which happens when an instance is launched or started.
        On the right-hand side of the screen, in the Target section, add a target by clicking on Add target.
        In the drop-down, change Lambda function to SNS topic.
        For the Topic, select the topic you created in the SNS hands-on exercise. Important: If the Topic doesn’t appear, the Access policy – optional section doesn’t have the correct permissions to allow other services to access the Topic.
        Scroll down and click the Configure details.
        Enter a name in the Name field. Ensure the state is Enabled. Click Create rule.
    Test CloudWatch Rule
        Navigate to the EC2 console page, by clicking on Services in the upper left-hand menu. Type EC2 in the text box and click on EC2 found in the search results.
        On the EC2 Dashboard page, click on Instances in the left-hand navigation.
        Click Launch Instance.
        Select the Amazon Linux 2 AMI (HVM), SSD Volume Type Amazon Machine Image (AMI). Important: You are free to choose a different AMI, but to avoid excessive charges, pick one that says, Free Tier Eligible.
        For the Instance Type, select the free-tier instance type of t2.micro.
        Click Review and Launch.
        Click Launch.
        Generate and download a new key pair and then launch the instance.
        Click Launch Instances.
        Click on View Instances.
        Once the Instance state changes to Running, check your email client for an email alert from the SNS Topic.
    Cleanup & Disable EC2 Instance and Cloud Watch Rule
        To avoid recurring charges for leaving an instance running, let’s disable the EC2 instance.
        From the EC2 Dashboard, select the instance just created, click Actions, then Instance State, and then select Terminate.
        To avoid recurring charges for leaving the Cloud Watch rule running, let’s disable it.
        From the SNS Dashboard, select Rules from under the Events section.
        Select the Rule you just created, by clicking the radio button next to the Rule.
        Click on the Actions button, and select Delete.

### Infrastructure as Code

Infrastructure as Code allows you to describe and provision all the infrastructure resources in your cloud environment. You can stand up servers, databases, runtime parameters, resources, etc. based on scripts that you write. Infrastructure as Code is a time-saving feature because it allows you to provision (or stand up) resources in a reproducible way.

This allows to manage a collection of related resources and treat them as a logical unit.

### Cloud Formation

AWS Cloud Formation allows you to model your entire infrastructure in a text file template allowing you to provision AWS resources based on the scripts you write.

Tips

    Cloud Formation is found under the Management & Governance section on the AWS Management Console.
    Cloud Formation templates are written using JSON or YAML.
    You can still individually manage AWS resources that are part of a CloudFormation stack.

Since your infrastructure is now code, you can check your scripts into version control.

Also, you can prepare the CloudFormation scripts from visual design tools in AWS. We can draw lines there to show dependencies among services. For example, an autoscaling group requires running EC2 insances, so the first points to the latter.

In this hands-on exercise, you will create an S3 bucket with AWS CloudFormation.
Prerequisites:

    AWS account

Topics Covered:

By the end of this lab, you will be able to:

    Create a CloudFormation stack using the CloudFormation Designer
    Launch S3 bucket using Infrastructure as Code
    Save and deploy a CloudFormation stack
    View resources created through CloudFormation

Steps:

    Create CloudFormation Stack

        On the AWS Management Console page, type cloud formation in the Find Services box and then select Cloud Formation. Important: The redesigned AWS CloudFormation console is available now. This tutorial covers the new designer. To access the new designer, click on the Try it out now and provide us feedback. message that displays in a message similar to what’s shown below.

        On the AWS Management Console page, type cloud formation in the Find Services box and then select Cloud Formation.
        If the left-hand menu options do not appear, expand the options by clicking on in the top left-hand corner.
        Select Designer from the left-hand menu.
        Locate S3 in the Resource Type section and expand it.
        Select Bucket and drag it to the designer window on the right-hand side.
        Copy the JSON below and replace entirely the JSON found in the Properties tab.

```
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "Basic S3 Bucket CloudFormation template",
  "Resources": {
    "S3BucketCreatedByCloudFormation": {
      "Type": "AWS::S3::Bucket",
      "Properties": {
        "AccessControl": "PublicRead"
      }
    }
  },
  "Outputs": {
    "BucketName": {
      "Value": {
        "Ref": "S3BucketCreatedByCloudFormation"
      },
      "Description": "Name of the newly created Amazon S3 Bucket"
    }
  }
}
```

...

Hit the Refresh button in the upper right-hand corner so that the Designer is not out of date.

    Save CloudFormation Stack
        In the CloudFormation Designer Toolbar, click the Document icon , and click Save.
        Click Local File and click Save. The JSON file will download.
        In the AWS CloudFormation Designer toolbar, click to validate your template. You will see a message that states, Template is valid.
    Deploy CloudFormation Stack
        In the CloudFormation Designer Toolbar, click to deploy the stack. The Create stack screen appears.
        Accept the defaults and click Next.
        Enter a Stack name. Leave Parameters empty. Click Next.
        Leave the defaults and click Next.
        Review the stack details and click Create Stack. The stack status will be CREATE_IN_PROGRESS. To the current status of the stack, select the Refresh button in the upper right-hand corner. Once the stack reaches the CREATE_COMPLETE status, the stack has been deployed.
    View S3 Bucket created by CloudFormation Stack
        From the Services menu option at the top, type in S3 and select S3.
        To quickly find the bucket created by the CloudFormation Stack, click on Date Created in the column heading to sort by the most recent buckets created.
        The newly created bucket appears at the top, cfs3stack-s3bucketcreatedbycloudformation-1at0fv1v9ndc1.
    Delete CloudFormation Stack
        To avoid on-going charges, delete the stack by navigating to the stack, and clicking the Delete button in the upper right-hand corner. Note: When the stack is deleted, all resources created by the stack template will be deleted also. 


### AWS CLI

We can also access our AWS account through the command line interface. From it, we can access and control services running on our AWS account. 

