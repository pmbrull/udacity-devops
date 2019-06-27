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

