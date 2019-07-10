# Cloud DevOps Engineer - Deploy Infrastructure as Code (IAC)

## Introduction

We are starting from a scenario where we have a software engineer team that transforms a requirement sheet into code. On the other hand, the Operations team needs to deploy this code and make sure that performs at the top of its possibilities. With DevOps, we are trying to reduce the comunication gap between those teams to produce a single unit that creates the code, prepares the infrastructure and deploys the solution on top of that.

Being a separete team - operations - the one in charge of code deployment and infrastructure setup brings some downfalls:
* They do not know the code nor what the solution intends to make, they just have a workspace setup guide and they do their best to get that running.
* There are environment mismatches between where developers actually do their job - their own laptops or small environments - vs. the characterics brought by the final production environment in terms of both computing power and number of data available. Ideally we want identical environments for the development and production phase.
* Configuration drift issues: Imagine that there is an issue in the middle of the night of a solution. Then, the operations team comes in and does a small fix in that PROD server. The problem is that this change is manually and the config. in this server does not match what we have in the development environment. What happens, then, in further versions of the app?

DevOps gives best practices and tools for solving these problems:

    DevOps Tools: DevOp tools deploy and manage configuration changes to servers.
        Stackexchange has a discussion post detailing the difference between DevOps tools vs. Software Configuration Tools
    Allows for predictable deployments, because it’s an automated script.
    Enables Continuous Integration Continuous Deployment (CI/CD) so that new features are automatically deployed with all the required dependencies.

For example, with configuration management tools such as ansible, we can prepare the hardware and apply proper configurations by using code. Thus, replicating this same configuration in different environments is immediate, avoiding configuration drift.

With deployment automatization we make sure that the pipeline and testing that has been done in an environment can be easily replicated when going to PROD. The major significance here is predictability, as anyone can run the script with exact same results.


    Continuous Integration Continuous Deployment (CI/CD): Tracks the development workflow from testing through production. Continuous integration is process flow of testing any change made to your development flow, while continuous deployment tracks those changes through to staging and production systems.
        Check out this article by Atlassian.com that describes these in detail.
        This article by Florian Matlik describes the differences between continuous integration and continuous deployment.

## CloudFormation

CloudFormation is a tool in AWS for managing, configuring and deploying infrastructure (push code along with the necessary server configurations).

## Deciding Access Privileges within AWS

Programmatic Access

In the AWS console, choose "programmatic access." This allows us to use code to interact with AWS, instead of relying on mouse clicking in the console web pages.
Administrator Access

For IAM access, choose “administrator access.” This is just for initial setup of your account. Afterwards, you’ll want to limit access to only what you need.
Dev and Prod user accounts

In practice, Dev and DevOps members may have separate user accounts for the dev environment as opposed to the production environment. This makes it easier for developers by giving them wider privileges in the dev environment that would normally only be reserved for DevOps members in the production environment.
Access Key ID and Secret Access Keys

Remember not to save these in your code or to check into any repositories. Keep these private to you.

> OBS: You can create a separate AWS just for developers and assign them admin role as they are in a separate environment and cannot break anything.

Regarding AWS token and secret, It's great practice to change them every 90 days or sooner and also to just delete them or mark them inactive when not in use.

Additional Access Keys

Note that each user can have up to 2 access keys at the same time.
Why Making Keys Inactive is a Better Choice

You may make your access key temporarily inactive rather than destroying it and creating a new one. This may be helpful if you want to stop an automated process that uses that key (for example, a CI/CD process).

## CloudFormation - 2

    CloudFormation is a declarative language, not an imperative language.
    CloudFormation handles resource dependencies, so that you don’t have to specify which resource to start up before another. There are cases where you can specify that a resource depends on another resource, but ideally, you’ll let CloudFormation take care of dependencies.
    VPC is the smallest unit of resource.

Glossary

Declarative languages: These languages specify what you want, without requiring you to specify how to get it. An example of a popular declarative language is SQL.
Imperative languages: These languages use statements to change the state of the program.
Additional resources:

    Here is the Wikipedia page describing the differences between the two.
    Here is a Stack Overflow thread describing imperative languages.

 CloudFormation uses a lot of logic behind the scenes to make sure everything works as expected, even when you don't specify resources in a specific order.

 It's best to create several files by logic (i.e., servers, connections...) or by ownership / application.

 Ex: If you have a team of database, operations and networking experts, you would split your CloudFormation script into several files based on Type of resource: This allows each expert to work on, and become familiar with, their resources and leverage their already-existing knowledge.

 YAML and JSON

    YAML and JSON file formats are both supported in CloudFormation, but YAML is the industry preferred version that’s used for AWS and other cloud providers (Azure, Google Cloud Platform).

    An important note about YAML files: the whitespace indentation matters! We recommend that you use four white spaces for each indentation.

Glossary in CloudFormation scripts

Name: A name you want to give to the resource (does this have to be unique across all resource types?)
Type: Specifies the actual hardware resource that you’re deploying.
Properties: Specifies configuration options for your resource. Think of these as all the drop down menus and checkbox options that you would see in the AWS console if you were to request the resource manually.
Stack: A stack is a group of resources. These are the resources that you want to deploy, and that are specified in the YAML file.
Best practices

Coding best practice: Create separate files to organize your code. You can either create separate files for similar resources, or create files for each developer who uses those resources.
Documentation for CloudFormation syntax

You don't need to memorize the code that you need for each resource. You can find sample code in the documentation for CloudFormation for examples of how to write your CloudFormation scripts.

### Test
Find the cf test file in IAC/cf-test.yaml
We will first create a cloudFormation stack (group of resources) from the terminal with: 

```bash
aws cloudformation create-stack --stack-name cf-pmbrull-test --region us-west-2 --template-body file://cf-test.yml
```

We get back the following message:

```bash
{
    "StackId": "arn:aws:cloudformation:us-west-2:050540289117:stack/cf-pmbrull-test/2f1678d0-9e8d-11e9-a67e-02559443042e"
}
```

With the StackId we can check the cloudFormation. Moreover, if we wanted to change something from our code, we would send a update-stack instead of a create-stack, as the latter would fail.

## Manually deploy an EC2 Instance for use with the CLI Tool.

We have installed and configured the AWS CLI to do our work for this course. However, there’s an alternative.

Go ahead and create an EC2 Instance that you can SSH into (or Remote Desktop, if you prefer Windows). Do this manually, in the console. Be sure to limit access to your IP address only, using Security Groups.

Once the instance is running, create an IAM Role with Admin access to your account, associate the role to your EC2 and install the AWS CLI on it.

The CLI tool, in this case, will pick up the credentials from the role and won’t need hard-coded credentials

## Infrastructure Diagrams

Lucidchart

We’ll use [https://www.lucidchart.com/pages/](Lucidchart) - to create cloud diagrams. Other applications that generate diagrams include Visio or Cloudcraft.


 If you have too much going on inside a subnet, for example, you could create a Cloud Architecture diagram just for that one subnet and have a separate diagram that shows the VPC, AWS Account and/or region.

 You never want to have single points of failure in the solution you are designing. For example, use multiple AZ! For high availability solutions, make sure that there is two pieces of everything. If you want to optimize cost, just one piece - discard high availability. It is cheaper to run a single copy of your web server or service, however, keep in mind that if something happens to it, there's no alternative in place in this case.

> Availability Zones (AZ): An AZ is a data center (physical building). 

 Best Practices

    Choose to have more than one availability zone to avoid a single point of failure.
    Include more than one availability zone to design for high availability, .
    You may choose to reduce to one AZ, possibly for prototyping and design for low cost. But it is not recommended for production environments.

### Virtual Private Cloud (VPC)

A virtual private cloud is a pool of networked cloud resources. It can span more than one availability zone.
The equivalent of this would be a data center. However, thanks to availability zones, VPCs can span more than one physical building. This is an amazing feature that protects against real world disasters like electrical failures, fires and similar events.

We can define a CIDR Block as follows: 10.0.0.0/16. This example means that we reserve the top 16 bits - two octets, or the first two numbers, to be the fixed part on your network.
This leave us with the last two numbers - two octets or 16 bits - that can take up to 256 values => around 65.000 IP addresses available within your private cloud.

Now, a subnet is simply a small subset of those IP addresses. The idea behin subnets is that:
* It creates logical separation between resources
* Blocks or Allows access to/from groups of resources and
* Provides services to a specific set of resources.

Another example could be the following: 10.0.1.0/24, where the top 3 numbers - three octets - are constant. This leaves us with 255 available addresses.

Key points to remember:
* VPCs provide you with private IP addresses for your networking resources
* Subnets are smaller subsets of your available IP address space
* The /00 at the end is the number of bits, from left to right that are fixed
* Subnets help with routing and services to specific groups of resources
* Create subnets and VPCs with future expansion in mind

The key is to use the IP addresses into the subnets for routing traffic. If have a routing table you can specify some traffic to stay in a VPC, or to go to any of the subnets. We can use subnets as a measure of security. For example, deploy the web app in a public subnet for the users to access, but DBs in a private one.

Subnets

    A subnet is a subset of the overall VPC network and it only exists in a single availability zone, unlike its parent network, the VPC.

    A subnet contains resources, and can be assigned access rights that apply to all resources within that subnet.

    Subnets can be public or private. Public subnets are accessible to external users. Private subnets are only accessed internally by other resources within your cloud container.

Use IP addresses for routing traffic

    Use IP addresses as the “keys” for routing traffic. We can route traffic to stay within the VPC, or within a particular subnet, for security reasons.
    For example, a database or any sensitive data will be placed in a private subnet. A public server, like a web server, can be placed in a public subnet. Routing rules applied to a subnet allow us to define access to all resources placed inside that subnet.

Internet Gateway

    An internet gateway is a resource that enables inbound and outbound traffic from the internet to your VPC.
    An internet gateway allows external users access to communicate with parts of your VPC.
    If you create a private VPC for an application that is internal to your company, you will not need an internet gateway.

Network Address Translation (NAT) Gateway: provides outbound-only internet gateway for private services to access the internet. This keeps the private service protected from inbound connections, but allows it to connect to the internet in order to perform functions such as downloading software updates. The NAT gateway serves as an intermediary to take a private resource’s request, connect to the internet, and then relay the response back to the private resource without exposing that private resource’s IP address to the public.

Note: Place NAT Gateways inside the public subnets and not the private subnets. NAT gateways need to be in the public subnet so that they can communicate with the public internet, and handle requests from resources that are in a private subnet.

OBS: If you have an internal only application, you don't need an IGW, but you can use a VPN that only allows access from your company IP, making it unreachable from the outside.

So, about NAT:
* Provices outbound internet access to resources in Private subnets
* "Translates" incoming public traffic into private traffic
* It needs public access itself, remember to place it in a PUBLIC subnet.

Auto Scaling:
* Needs more than one subnet
* It can be used for both High Availability and Elasticity - the ability to expand and contract your resources to meet demand.

Load Balancer

    A load balancer takes incoming traffic and distributes it to two or more resources. For example, it can take inbound user requests to access your website, and it can distribute the requests evenly among two or more servers.
    Without a load balancer, having public-facing servers in more than one AZ would mean that users would have to use a different URL to reach each of the AZs. This can be impractical compared to just a single URL.

    It's a service designed to distribute work requests meant for a target group, which is a collection of servers providing a common service.
    As requests come in, the Load balancer will spread the requests evenly accross its target group.

    We can also set an autoscaling group to launch servers that then a load balancer can use as target.

    It needs to be specified accross two or more AZs. This means that it is not a single point of failure, as it one AZ goes down, it still can run on the other. Same thing applies for the IGW, route table and auto-scaling groups. Those services you can assume that are not going to fail, as there are multiple copies behind the scenes for you.

Security Groups

    Security groups manage traffic at the server level (the resource level). Security Groups aren’t for managing higher level groups such as subnets, VPC, or user accounts.
    The same security group can be assigned to multiple resources that require the same security access settings defined by that security group.
    While you could certainly specify just one type of traffic, it's common practice to include rules for both inbound and outbound in a single Security group. 
    you can be as specific as 1 IP address ( when giving access to yourself, for example ) or as broad as the entire network ( 0.0.0.0/0)

Routing Table

Routing in the cloud is a very critical component. Some definitions:
* It is a set of entries or rules associated with one or more of your subnets inside your VPC
* These rules allow or deny traffic to/from the address ranges that you specify
* Rules can be as open as the entire world or resticted to a single IP address.

S3 buckets cannot be inside a VPC, as this is just a service that they provide to you and needs the global AWS network.

## Networking Infrastructure

When creating your .yml file remember that using the Description Field is optional. Here we start by adding a short description of our name and project we are working on.

Description: >
    Carlos Rivas / Udacity 2019


Recommended best practices

Although descriptions are optional , Resource fields are required. Remember to include at least one resource (e.g., a VPC, an EC2 instance, a database) in the CloudFormation .yml script, otherwise it will give an error when you try to run the script..

Resources:
    VPC:
        TYPE: AWS::EC2::VPC


Practice Fixing Errors

    Practice fixing errors, as this will help you prepare for real scenarios on the job.
    For instance, try altering correct, working yml scripts to see if they generate an error.
    Practice reading error messages to understand what caused the error, and how to fix them.

Common commands used

Common commands we’ll use are aws cloudformation create-stack, and aws cloudformation update-stack.

> OBS: running the create / update stack commands takes a lot of boilerplate for a simple action, so it is handy to prepare bash scripts to make things faster.

Connecting VPC's & Internet Gateways

It's important to note when connecting an Internet Gateway to a VPC, we need to define an additional resource called InternetGatewayAttachment. This attachment references both the VPC and the InternetGateway. Here is the syntax for the following connection:

Type: AWS::EC2::VPCGatewayAttachment
Properties: 
  InternetGatewayId: String
  VpcId: String
  VpnGatewayId: String

Don't hard-code parameters

Avoid hard coding parameter values. Instead, use a separate parameter file to store parameter values. Note that the parameter file should be in .json format, as .yml format is not yet supported for the parameter file.

Here is an example parameters file from network-parameters.json which is holding key-value pairs for the Environment & VpcCiIDR.

[
    {
        "ParameterKey": "EnvironmentName",
        "ParameterValue": "UdacityProject"
    },
    {
        "ParameterKey": "VpcCIDR",
        "ParameterValue": "10.0.0.0/16"
    }
]


Setting Parameters

Parameters should be declared above your Resources:

Parameters:
whatever you consider a changing value, put it as a parameter instead of hard-coding it into your script
Resources:

and should follow the general format of:

Parameters:
  ParameterLogicalID:
    Type: DataType
    ParameterProperty: value

Here we set the EnvironmentName parameter in our sample code from the video:

Parameters:
    EnvironmentName:
        Description: An Environment name that will be prefixed to resources
        Type: String

Default Parameters

You can also provide default values for parameters in case one was not passed in. In this example you can see that VpcCIDR has a default value of 10.0.0.0/16.

```
Parameters:
    EnvironmentName:
        Description: An Environment name that will be prefixed to resources
        Type: String

    VpcCIDR:
        Description: Please enter the IP range (CIDR notation) for this
        Type: String
        Default: 10.0.0.0/16
```

Calling CloudFormation

When calling AWS CloudFormation, you’ll pass in the name of the .yml file as well as the name of the parameter file as parameters to the CloudFormation call.

For example:

aws cloudformation create-stack --stack-name MyStack --template-body file://MyCloudformationScript.yml  --parameters file://MyEnvironmentVariables.json 

    Note that CloudFormation knows to create the resources in order, based on their dependencies (VPC and InternetGateway, before creating the InternetGatewayAttachment).

To associate different resources together it is useful to set a Tag as a parameter, i.e., EnvironmentName and call it when creating the resources as:

```
VPC:
    Type: AWS::EC2::VPC
    Properties:
        CidrBlock: !Ref VpcCIDR
        EnableDnsHostname: true
        Tags:
            - Key: Name
              Value: !Ref EnvironmentName
```

For example, for VPCGatewayAttachment we can also associate the VPC id by name using `!Ref <ResourceName>`. In the example, it should be `VpcId: !Ref VPC`


Adding Subnets

To specify a Subnet for your VPC you use the following syntax:

```
Type: AWS::EC2::Subnet
Properties: 
  AssignIpv6AddressOnCreation: Boolean
  AvailabilityZone: String
  CidrBlock: String
  Ipv6CidrBlock: String
  MapPublicIpOnLaunch: Boolean
  Tags: 
    - Tag
  VpcId: String
```

Here is the actual setup of our 2 private Subnets:

```
PrivateSubnet1:
    Type: AWS::EC2::Subnet
    Properties:
        VpcId: !Ref VPC
        AvailabilityZone: !Select [ 0, !GetAZ's '' ]
        CirderBlock: !Ref PrivateSubnet1CIDR
        MapPublicIpOnLaunch: false
        Tags: 
            -   Key: Name
                Value: !Sub ${EnvironmentName} Private Subnet (AZ1)

PrivateSubnet2:
    Type: AWS::EC2::Subnet
    Properties:
        VpcId: !Ref VPC
        AvailabilityZone: !Select [ 1, !GetAZ's '' ]
        CirderBlock: !Ref PrivateSubnet1CIDR
        MapPublicIpOnLaunch: false
        Tags: 
            -   Key: Name
                Value: !Sub ${EnvironmentName} Private Subnet (AZ2)
```

You can see the index being used from the returning AvailabilityZone's array. Notice that our subnets are not sharing AvailabilityZones. We are keeping them separated like we displayed in our diagrams from the previous lesson:

PrivateSubnet1: AvailabilityZone: !Select [ 0, !GetAZ's '' ]

PrivateSubnet2: AvailabilityZone: !Select [ 1, !GetAZ's '' ]

This code:

!select [0, !GetAZs‘’]

calls the function GetAZ, which returns a list of availability zones, which are indexed 0, 1 etc.
Tip

    Name your subnets using tags, to keep track when you create many subnets.

What we want to do here is just make sure that the two subnets are located into different AZs to ensure High Availability.

Adding a NAT Gateway

You can use NAT Gateways in both your public and/or private Subnets. The following code is the basic syntax for declaring a NAT Gateway:

Type: AWS::EC2::NatGateway
Properties: 
  AllocationId: String
  SubnetId: String
  Tags: 
    - Tag


The following declarations are from the sample code shown in the above video:

 NatGateway1EIP:
        Type: AWS::EC2::EIP
        DependsOn: InternetGatewayAttachment
        Properties: 
            Domain: vpc

    NatGateway2EIP:
        Type: AWS::EC2::EIP
        DependsOn: InternetGatewayAttachment
        Properties:
            Domain: vpc

    NatGateway1: 
        Type: AWS::EC2::NatGateway
        Properties: 
            AllocationId: !GetAtt NatGateway1EIP.AllocationId
            SubnetId: !Ref PublicSubnet1

    NatGateway2: 
        Type: AWS::EC2::NatGateway
        Properties:
            AllocationId: !GetAtt NatGateway2EIP.AllocationId
            SubnetId: !Ref PublicSubnet2


The EIP in AWS::EC2::EIP stands for Elastic IP. This will give us a known/constant IP address to use instead of a disposable or ever-changing IP address. This is important when you have applications that depend on a particular IP address. NateGateway1EIP uses this type for that very reason:

 NatGateway1EIP:
        Type: AWS::EC2::EIP
        DependsOn: InternetGatewayAttachment
        Properties: 
            Domain: vpc

Tip

    Use the DependsOn attribute to protect your dependencies from being created without the proper requirements.

In the scenario above the EIP allocation will only happen after the InternetGatewayAttachment has completed.

Therefore, we can use for NatGateway1 and 2 the following property `AllocationId: !GetAtt NatGateway1EIP.AllocationId` to use the IP that was just allocated for our resources.

Another important piece of networking are the Route Tables:

```
PublicRouteTable:
    Type: AWS:EC2:RouteTable
    Properties:
        VpcId: !Ref VPC
        Tags:
            - Key: Name
              Value: !Sub ${EnvironmentName} Public Routes

DefaultPublidRoute:
    Type: AWS:EC2:Route
    DependsOn: InternetGatewayAttachment
    Properties:
        RouteTableId: !Ref PublicRouteTable
        DestinationCidrBlock: 0.0.0.0/0
        GatewayId: !Ref InternetGateway
```

Glossary

Routing: Routing is the action of applying routing rules to your network, in this case, to your VPC.
Routing rule: Resources follow the routing rule, which defines what resource has access to communicate with another resource. It blocks traffic from resources that do not follow the routing rule.


Route Tables

We create RouteTables for VPCs so that we can add Routes that we later associate with Subnets. The following is the syntax used to define a RouteTable:

```
Type: AWS::EC2::RouteTable
Properties: 
  Tags: 
    - Tag
  VpcId: String
```

The only required property for setting up a RouteTable is the VpcId. Here is an example table from the video lesson:

```
PublicRouteTable:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Public Routes
```

Routes

The following is the syntax used to set up our Route:

```
Type: AWS::EC2::Route
Properties: 
  DestinationCidrBlock: String
  DestinationIpv6CidrBlock: String
  EgressOnlyInternetGatewayId: String
  GatewayId: String
  InstanceId: String
  NatGatewayId: String
  NetworkInterfaceId: String
  RouteTableId: String
  VpcPeeringConnectionId: String
```

The DestinationCidrBlock property is used for destination matching and a wildcard address (0.0.0/0) to reference all traffic. So in the following example, when we use the wildcard address 0.0.0.0/0, we are saying for any address that comes through this route, send it to the referenced GatewayId:

```
DefaultPublicRoute: 
        Type: AWS::EC2::Route
        DependsOn: InternetGatewayAttachment
        Properties: 
            RouteTableId: !Ref PublicRouteTable
            DestinationCidrBlock: 0.0.0.0/0
            GatewayId: !Ref InternetGateway
```

OBS: Route rules apply for more specific to less specific. So, if I have a rule routing to 10.0.0.1, it will be applied before 0.0.0.0.

SubnetRouteTableAssociation

In order to associate Subnets with our Route Table we will need to use a SubnetRouteTableAssociation. SubnetRouteTableAssociations are defined using the following syntax:

```
Type: AWS::EC2::SubnetRouteTableAssociation
Properties: 
  RouteTableId: String
  SubnetId: String
```

This only takes two properties, which are the id's used for our RouteTable and our Subnet. You can see references used in the example from our video lesson above:

```
PublicSubnet1RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PublicRouteTable
            SubnetId: !Ref PublicSubnet1
```

Important Note: Routes should be defined starting with the most specific rule and transitioning to the least specific rule.

```
PublicRouteTable:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Public Routes

    DefaultPublicRoute: 
        Type: AWS::EC2::Route
        DependsOn: InternetGatewayAttachment
        Properties: 
            RouteTableId: !Ref PublicRouteTable
            DestinationCidrBlock: 0.0.0.0/0
            GatewayId: !Ref InternetGateway

    PublicSubnet1RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PublicRouteTable
            SubnetId: !Ref PublicSubnet1

    PublicSubnet2RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PublicRouteTable
            SubnetId: !Ref PublicSubnet2


    PrivateRouteTable1:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Private Routes (AZ1)

    DefaultPrivateRoute1:
        Type: AWS::EC2::Route
        Properties:
            RouteTableId: !Ref PrivateRouteTable1
            DestinationCidrBlock: 0.0.0.0/0
            NatGatewayId: !Ref NatGateway1

    PrivateSubnet1RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PrivateRouteTable1
            SubnetId: !Ref PrivateSubnet1

    PrivateRouteTable2:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Private Routes (AZ2)

    DefaultPrivateRoute2:
        Type: AWS::EC2::Route
        Properties:
            RouteTableId: !Ref PrivateRouteTable2
            DestinationCidrBlock: 0.0.0.0/0
            NatGatewayId: !Ref NatGateway2

    PrivateSubnet2RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PrivateRouteTable2
            SubnetId: !Ref PrivateSubnet2
```

> OBS: If your servers have no internet access it's probably because...

    You created the internet gateway but forgot to attach it to your VPC
    You placed your NAT Gateway inside private subnets with no routes to the outside world
    You have a missing route in your routing table
    You crated a routing table but forgot to associate your subnet(s) with it

Outputs

Outputs are optional but are very useful if there are output values you need to:

    import into another stack
    return in a response
    view in AWS console

To declare an Output use the following syntax:

```
Outputs:
  Logical ID:
    Description: Information about the value
    Value: Value to return
    Export:
      Name: Value to export
```

The Value is required but the Name is optional. In the following example we are returning the id of our VPC as well as our Environment's Name:

```
VPC: 
    Description: A reference to the created VPC
    Value: !Ref VPC
    Export:
        Name: !Sub ${EnvironmentName}-VPCID
```

where `!Sub` stants for substitution and is useful to create names based on parameters.

Join Function

You can use the join function to combine a group of values. The syntax requires you provide a delimiter and a list of values you want appended.

Join function syntax:

```
Fn::Join: [ delimiter, [ comma-delimited list of values ] ]
```

In the following example we are using !Join to combine our subnets before returning their values:

```
PublicSubnets:
        Description: A list of the public subnets
        Value: !Join [ ",", [ !Ref PublicSubnet1, !Ref PublicSubnet2 ]]
        Export:
          Name: !Sub ${EnvironmentName}-PUB-NETS
```

## Servers and Security Groups

Security Groups

The following is the syntax required to create a SecurityGroup:

```
Type: AWS::EC2::SecurityGroup
Properties: 
  GroupDescription: String
  GroupName: String
  SecurityGroupEgress: 
    - Egress
  SecurityGroupIngress: 
    - Ingress
  Tags: 
    - Tag
  VpcId: String
```

Although they are not required, the SecurityGroupEgress and SecurityGroupIngress property rules are the most critical to the SecurityGroup as it defines where the traffic will go. While SecurityGroupEgress defines outbound traffic, SecurityGroupIngress defines the inbound traffic.


Ingress rules and egress rules

    Ingress rules are for inbound traffic, and egress rules are for outbound traffic.
    Ingress rules restrict or allow traffic trying to reach our resources on specific ports.
    Egress rules restrict or allow traffic originating from our server -- typically we are ok allowing all outbound traffic without restrictions as this doesn’t pose a risk for a security breach.

By default, Security Groups provide the following to the resources to which they are assigned: Outbound is always allowed and Inbound is always denied unless specified. When creating a SecurityGroup using cf, we need to specify the rule type (ingress or egress), the IP address or range and the start and end port.

WHen specifying an autoscaling group, we need to set the Scaling Policy and Launch Configuration. The Launch configuration will tell the scaling group what you want to launch, and the scaling policies will tell it WHEN to execute the scaling, either up or down.

The following is the syntax used for AutoScaling LaunchConfiguration:

```
Type: AWS::AutoScaling::LaunchConfiguration
Properties: 
  AssociatePublicIpAddress: Boolean
  BlockDeviceMappings: 
    - BlockDeviceMapping
  ClassicLinkVPCId: String
  ClassicLinkVPCSecurityGroups: 
    - String
  EbsOptimized: Boolean
  IamInstanceProfile: String
  ImageId: String
  InstanceId: String
  InstanceMonitoring: Boolean
  InstanceType: String
  KernelId: String
  KeyName: String <- Used to allow SSH to that machine. Once everything is tested, it's better to disallow that key.
  LaunchConfigurationName: String
  PlacementTenancy: String
  RamDiskId: String
  SecurityGroups: 
    - String
  SpotPrice: String
  UserData: String
```

The ImageId and Instance Type are the only required properties for a LaunchConfiguration. However, there are many useful properties you will likely want to include.

```
WebAppLaunchConfig:
    Type: AWS::AutoScaling::LaunchConfiguration
    Properties:
      UserData:
        Fn::Base64: !Sub |
          #!/bin/bash
          apt-get update -y
          apt-get install unzip awscli -y
          apt-get install apache2 -y
          systemctl start apache2.service
          cd /var/www/html
          aws s3 cp s3://udacity-demo-1/udacity.zip .
          unzip -o udacity.zip
      ImageId: ami-005bdb005fb00e791
      IamInstanceProfile: !Ref ProfileWithRolesForOurApp
      SecurityGroups:
      - Ref: WebServerSecGroup
      InstanceType: t3.small
      BlockDeviceMappings:
      - DeviceName: "/dev/sdk"
        Ebs:
          VolumeSize: '10'
```

In the above example we have done the following:

    Specified 10gbs for our VolumeSize.
    Referenced the previously defined WebServerSecGroup for our SecurityGroup
    Set our InstanceType to t3.medium for our EC2 Instance

OBS: Should a server in your auto-scaling group fail, you would, for the purpose of business continuity, it's perfectly fine to quickly destroy the server and allow Auto-Scaling to take over and spin up a new one. That said, if it happens again, soon thereafter you may have a bigger problem at hand so you should try to log in and figure out what's going on.

Now, if we don't create any rule, the autoscaling group will think that everything is healthy. The idea here is that if we have an app running on a specific port, create a listener on that port to make sure that everything is running fine and in case that there is no response, turn that instance down and generate another one.

The following is the required syntax for TargetGroup:

```
Type: AWS::ElasticLoadBalancingV2::TargetGroup
Properties: 
  HealthCheckEnabled: Boolean
  HealthCheckIntervalSeconds: Integer
  HealthCheckPath: String
  HealthCheckPort: String
  HealthCheckProtocol: String
  HealthCheckTimeoutSeconds: Integer
  HealthyThresholdCount: Integer
  Matcher: 
    Matcher
  Name: String
  Port: Integer
  Protocol: String
  Tags: 
    - Tag
  TargetGroupAttributes: 
    - TargetGroupAttribute
  TargetType: String
  Targets: 
    - TargetDescription
  UnhealthyThresholdCount: Integer
  VpcId: String
```

Health Checks are the requests your Application Load Balancersends to its registered targets. These periodic requests test the status of these targets. You can see us defining our Health Check properties in the example below:

```
 WebAppTargetGroup:
    Type: AWS::ElasticLoadBalancingV2::TargetGroup
    Properties:
      HealthCheckIntervalSeconds: 35
      HealthCheckPath: /
      HealthCheckProtocol: HTTP
      HealthCheckTimeoutSeconds: 30
      HealthyThresholdCount: 2
      Port: 80
      Protocol: HTTP
      UnhealthyThresholdCount: 5
      VpcId: 
        Fn::ImportValue:
          Fn::Sub: "${EnvironmentName}-VPCID"
```

In the above example we specify the following:

    The port where our targets receive traffic - Port: 80
    The protocol the load balancer uses when performing health checks on targets - HealthCheckProtocol: HTTP
    The time it takes to determine a non-responsive target is unhealthy - HealthCheckIntervalSeconds: 35
    The number of healthy/unhealthy checks required to change the health status - HealthyThresholdCount: 2 UnhealthyThresholdCount: 5

OBS: we can think of a target group as the association of a load balancer and an autoscaling group.

OBS2: In the examples of the videos, they explained a mistake when setting up the security group for the Load Balancer. It was configured using the port 80 for both inbound and outbound rules. This is a mistake as we are limiting the load balancer to talk to anything but the HTTP port 80 to other resources, but we have our webapp running at 8080! This means the LB could not properly reach the app.

### Research the EC2 Parameter Store

One way to avoid hard-coding ever-changing values into your server infrastructure is by using parameters. Examples of parameters that frequently change include database connection details, and sensitive data, such as passwords and secret API access keys.

Using the AWS CLI Tool, store and retrieve parameters from the EC2 Parameter Store. Play around with changing the value from the EC2 Console and not just the CLI Tool.

It’s critical that you practice this, as this is not only a best practice but also a common practice.

### Parameter store
Inside AWS system manager we can find the option to create parameters in parameter store. We can access those, for example, using the AWS CLI:
```
aws ssm get-parameters --names "test-param"
```

Keeping sensitive data away from your servers and only providing it to your software when needed is yet another layer of security that will give your cloud customers peace of mind.

## Storage and Databases

Persisting Data

    Most applications need their data to persist and not be lost, which requires a database.
    We don't want a database to be a single point of failure, so we'll use resources that are designed for reliability. For example, RDS for the database, and S3 for the filestore.
    Relational Database Service (RDS): AWS service for creating databases.

Choosing a database

    AWS Aurora and MySQL have no additional licensing costs. Microsoft SQL Server will have additional licensing costs.

Mult-AZ deployment

    If you are using a database in a development environment, you can save money by using a single Availability Zone.
    For production databases, use multiple AZs for reliability. If one AZ fails, the other one will still be available.

A single RDS Server can host multiple databases

    Note that you can use a single RDS database that hosts multiple applications, each with different logins and users for those applications. In other words, you don’t need to create a separate RDS service for each application.


If I wanted to store information from my app and make sure it doesn't create a single point of failure for my application, I'd choose... Mutli-AZ RDS database, database on EC2 with replicas in another AZ or DynamoDB Service. In fact, all the above options are valid. The problem with a database on EC2 is that you are responsible for eliminating that point of failure by creating additional replicas -- but it's certainly possible! Also note-worthy: DynamoDB works but it is a document store and not a relational database, which is great and sufficient for most cases but not all.

Network and Security

    Subnet groups are needed for deploying in multiple AZs.
    We want to place our RDS in more than one Availability Zone (data center). We can place the RDS in two AZs to eliminate single point of failure and to have high availability.
    We created 4 subnets (2 private and 2 public), so the RDS can potentially be duplicated in all four subnets.
    However, keep in mind that we usually prefer to put databases in a private subnet, for security. There may be use cases where you put a database in a public subnet, but generally put it in the private subnets.

Usually, don't make a database public

    We'll choose "No" for public accessibility" to keep a database private.
    We'd normally use a private IP address to access a database.

AZ

    Let AWS choose the availability zone. Choose "no preference."

VPC Security Groups

Default means every resource in the VPC can talk to any other resource that is within that same VPC. We'll keep this default, to allow resources in the VPC to reach the database.
Encryption

    We can use encryption for sensitive production workloads. We can disable encryption for our database here.

SQL Queries that take a long time use resources that slow down your transactional database. These are better served by a separate copy of your DB.

Using CloudFormation

    Note that since setting up a database is usually a one-time event, you can just use the console (point and click) to create the database server instead of writing CloudFormation code. Using CloudFormation is still an option if you choose.

CloudFormation retention policy

    You'll want your data to persist even if your stack of resources is updated or deleted.
    Retention policy: keeps a service even if the entire stack of infrastructure is marked for removal. In CloudFormation, the syntax is DeletionPolicy: retain. This is very useful to assign to your data storage (database, file storage), to make sure that your data is saved even when the stack is updated or deleted.

When to use Filestores

    Use filestores instead of databases for large files, such as videos and text documents.
    Configuration files and sensitive encrypted data are best stored in specific filestores rather than inside the servers. Autoscaling groups may create or destroy servers, so keep data that you want to persist in separate resources such as a filestore.

Knowing that the server can be discarded by the auto-scaling group, which of these files can I safely place in it anyway?
Anything that is temporary in nature or can be easily re-generated can be stored on a transitory disk (or ephemeral disk as it is also known), such as intermediate steps generated by a build process, temporary calculations leading to a result or test files.

S3 bucket

    Choose a DNS compliant name for the S3 bucket.

Command line arguments

```
aws s3 ls <link to S3 bucket>
```

This line above lists files in the S3 bucket.

```
aws s3 cp <file name> <link to S3 bucket>  
```

This line above copies a file from your local machine to the S3 bucket.
Versioning

    You can keep past versions of your S3 bucket, which means that deleted files will still exist in prior versions of your S3 bucket.

Can I have my application write directly to S3? No - The same goes for reading data: don't expect the blazing fast performance that you'd have when reading from your local file system. While it's possible to write code that will put files directly on S3, S3 is NOT like a regular computer hard-drive, it will slow your application down significantly. It's best to generate your data on some sort of temporary storage and only then upload your files to S3.

Key Points

    S3 can be used to store your config files, media or log files.
    Your servers don't need credentials to access S3 provided they have a role assigned.
    We recommend you choose RDS as opposed to installing a database in your own servers that you have to manage and back up yourself.

## Project: Deploy a high-availability web app using cloudFormation

### Server specs

You'll need to create a Launch Configuration for your application servers in order to deploy four servers, two located in each of your private subnets. The launch configuration will be used by an auto-scaling group.

You'll need two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu 18. So, choose an Instance size and Machine Image (AMI) that best fits this spec. Be sure to allocate at least 10GB of disk space so that you don't run into issues. 

### Security Groups and Roles

Since you will be downloading the application archive from an S3 Bucket, you'll need to create an IAM Role that allows your instances to use the S3 Service.

Udagram communicates on the default HTTP Port: 80, so your servers will need this inbound port open since you will use it with the Load Balancer and the Load Balancer Health Check. As for outbound, the servers will need unrestricted internet access to be able to download and update its software.

The load balancer should allow all public traffic (0.0.0.0/0) on port 80 inbound, which is the default HTTP port. Outbound, it will only be using port 80 to reach the internal servers.

The application needs to be deployed into private subnets with a Load Balancer located in a public subnet.

One of the output exports of the CloudFormation script should be the public URL of the LoadBalancer.

Bonus points if you add http:// in front of the load balancer DNS Name in the output, for convenience.

### Other Considerations


You can deploy your servers with an SSH Key into Public subnets while you are creating the script. This helps with troubleshooting. Once done, move them to your private subnets and remove the SSH Key from your Launch Configuration.

It also helps to test directly, without the load balancer. Once you are confident that your server is behaving correctly, increase the instance count and add the load balancer to your script.

While your instances are in public subnets, you'll also need the SSH port open (port 22) for your access, in case you need to troubleshoot your instances.

Log information for UserData scripts is located in this file: cloud-init-output.log under the folder: /var/log.

You should be able to destroy the entire infrastructure and build it back up without any manual steps required, other than running the CloudFormation script.

The provided UserData script should help you install all the required dependencies. Bear in mind that this process takes several minutes to complete. Also, the application takes a few seconds to load. This information is crucial for the settings of your load balancer health check.

It's up to you to decide which values should be parameters and which you will hard-code in your script.

See the provided supporting code for help and more clues.

If you want to go the extra mile, set up a bastion host to allow you to SSH into your private subnet servers. This bastion host would be on a Public Subnet with port 22 open only to your home IP address, and it would need to have the private key that you use to access the other servers.

Last thing: Remember to delete your CloudFormation stack when you're done to avoid recurring charges!
