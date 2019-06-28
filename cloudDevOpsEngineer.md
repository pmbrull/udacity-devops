# Cloud DevOps Engineer

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
