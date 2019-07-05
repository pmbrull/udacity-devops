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


