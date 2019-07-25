# Cloud DevOps Engineer - Microservices at Scale using AWS & Kubernetes

## What is AWS Lambda?

From the [documentation](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html):

    AWS Lambda is a compute service that lets you run code without provisioning or managing servers.

    AWS Lambda executes your code only when needed and scales automatically, from a few requests per day to thousands per second.
    You pay only for the compute time you consume - there is no charge when your code is not running.

As any function, they can have an input and an output.

But, what is FaaS? - Function as a Service
* Serverless platform that executes logic
* Does not store data
* Typically event driven
* AWS Lambda was first public cloud offering

You can use AWS Lambda to run your code in response to events, such as HTTP requests.
SQS Queue

Some of the FaaS applications are:
* Data Engineering
* Machine Learning
* Single page web apps
* Mobile apps

Amazon Simple Queue Service (Amazon SQS) offers a secure, durable, and available hosted queue that lets you integrate and decouple distributed software systems and components.

    A queue is just a type of list that orders data in a particular way; typically in a first-item-in = first-item-out order (FIFO), as shown below.

Learn more about SQS in the [documentation](https://aws.amazon.com/sqs/).


## MXNet and Lambda

Learn more about deploying models using MXNet and AWS Lambda in this [AWS blog post](https://aws.amazon.com/blogs/compute/seamlessly-scale-predictions-with-aws-lambda-and-mxnet/), where they link to a repository of example code!

## A Model for Serverless

Using Frameworks, Platforms and Toools.

Though we'll be using AWS cloud tools, there are a number of other providers that you can use to build serverless applications with auto-scaling capabilities. The skills you learn in this lesson will be widely applicable to these other platforms. Some of the larger, cloud providers include:

    Amazon Web Services [ Chalice & Cloud Formation]
    Terraform
    Google Cloud Platform
    Microsoft Azure

And you are welcome to check these out, especially if you have a platform that you already prefer.

### Events and Actions:

Events can be:
* Uploading a file
* Putting a message in a Queue
* Time

To summarize, events triggers actions, which can just be a piece of code stored in a FaaS.

## Lesson Outline

In this lesson, you'll learn to deploy serverless applications, using AWS Lambda. This lesson breaks up the topic of serverless applications into smaller concepts:

    What are Functions as a Service (FaaS)?
    Characteristics of cloud-native applications
    Creating an AWS Lambda function using Cloud9
    Responding to events, such as HTTP requests
    Creating a JSON response

## Request-Response

Much of this lesson will rely on creating and understanding the request-response method of computer communication. From the Wikipedia page:

    Request–response is one of the basic methods computers use to communicate with each other, in which the first computer sends a request for some data and the second responds to the request. Usually, there is a series of such interchanges until the complete message is sent; browsing a web page is an example of request–response communication.

Request–response can be seen as a telephone call, in which someone is called and they answer the call.

In this lesson, requests are typically HTTP requests with some input data, and a response will be a JSON-formatted set of output values.

## Benefits of FaaS

* Simplicity
* Event based
* Can be more cost-effective: There is billing on-demand; based on consumption and executions
* Leverage Cloud-Native technologies
* Complete abstraction of servers away from the developer
* Services that are event-driven and instantaneously scalable

## Cloud Native

> Designed for the cloud

We want to build services capable of:
* Autoscaling
* Infinite compute
* Infinite storage
* Advanced APIs

## What is Fault-Tolerance?

Fault tolerance - the property that enables a system to continue operating properly in the event of the failure of one or more of its components.

    An example is a typical car, which is designed so it will continue to be drivable if one of the tires is punctured or damaged.
    In computer systems, a fault-tolerant design enables a system to continue its intended operation, possibly at a reduced level, rather than failing completely, when some part of the system fails.

Moreover, cloud native systems are:
* Elastic
* Fault-tolerant
* Designed for failure
* Event driven

## AWS Console & Cloud9 Environment

The majority of work that you do in this lesson will be completed using [AWS Cloud9](https://aws.amazon.com/cloud9/), which lets you code, run, and debug code in your browser! For certain exercises, you will be expected to work through a Cloud9 environment, which has access to all the libraries we need as well as data management and deployment tools!

If you are familiar with the AWS console and Cloud9, you may proceed to the next video to get set up. If not, it is suggested that you read through these instructions carefully to setup an AWS account.

### 1. Create an AWS Account

First, visit Amazon AWS and click on the Create an AWS Account button.

    If you have an AWS account already, sign in.
    If you do not have an AWS account, sign up.

When you sign up, you will need to provide a credit card. But don’t worry, you won’t be charged for anything yet. Furthermore, when you sign up, you will also need to choose a support plan.

    You can choose the free Basic Support Plan.

Once you finish signing up, wait a few minutes to receive your AWS account confirmation email. Then return to Amazon AWS and sign in.
The Console

In the future, you can access the AWS console by visiting console.aws.amazon.com. The AWS console is a central hub from which you can access all of the various Amazon Web Services, including SageMaker.

### 2. Apply AWS Credits

All students are provided with AWS credits to train their neural networks. To get your AWS credits, go to the 'Resources' tab in the left of the classroom; there will be an 'AWS Credits' link to click there.

AWS credits in the "Resources" tab

Click on the 'Go to AWS' button to request your credits. This should bring up a form which you will need to complete.

    In your AWS account, your AWS Account ID can be found under 'My Account', which is itself found in the dropdown under the name of your account, between the bell and the 'Global' dropdown.

After you've gone through all the steps, you'll receive an email with your code. The email will be sent to the email address you entered on the AWS credits application. It may take up to 48 hours to receive this email, though it is much quicker in most cases

Under "AWS Promotional Credit " in the email, you'll find your code. Use this code on the link provided, which is your account credits page.

### 3. Set up a Cloud9 Environment

Then, you'll need to set up a Cloud9 environment that is connected to the main Github repository for this course. This environment will be the primary way in which we interact with the Cloud9 ecosystem.

[Here](https://github.com/noahgift/awslambda/blob/master/beginners_guide_aws_lambda.ipynb) there is a guide on how to configure Cloud9 environment and write AWS Lambda functions in Python.

You can create many different environments. Moreover, this environment is linked to your AWS environment. So, for example, you can run `aws s3 ls` and get your list of buckets from the cloud9 terminal. Moreover, you can invite anyone to this environment and pair programming!

However, one of the best things of cloud9 is that from there you can code lambda functions (AWS Resources tab).

If there are some syntax errors when coding Python 3 functions on the prints, you need to tell the editor that it's indeed Python 3 and not 2. You can do that in project settings > Python Support.

> A basic lambda_handler function accepts as input (event, context)

Also, from the AWS Resource tab, you can click on your lambda functions and deploy them to AWS cloud. Then, in the console, you can look for your new lambda function. What it is interesting is that by accessing your lambda function through the Lambda service, you can still modify, test it and access to AWS CloudWatch.

## Event-Handling

When returning a response from a lambda function, it is important that it is a JSON with `"statusCode": 200`, to let know the application that made the request that everything went OK. Also, `"headers": { "Content-type": "application/json" }` tells the person receiving the code that this is a JSON payload. Finally, the actuall return values should be inside a `body`.

Note that we cannot just test the lambda functions as usual Python functions with `Lambda (local)` Run option, but we can also test it as if it was a web service. However, this means that we need to create the function accepting this API Gateway with a Resource Path and some Security. Then, we can test using a POST method on the path defined before.

After testing the API Gateway response, our code is ready to deploy it a microservice in AWS. (Tests done with udacityChange examples).

Note that if we deploy a lambda function with enabled API Gateway, this will appear as a trigger for the function in AWS console. If we click on it, it will give us an API endpoint that we can also use for testing in cloud9 environment. To do so, activate the virtual environment created for the function with `sourve venv/bin/activate` and `pip install ipython`, as we are going to use the ipython shell. Run `ipython` to enter this shell and you can also install packages there, such as `pip install requests`. We will use this package to request for the API Gateway. 

```python
url = 'https://tdpaaxpk27.execute-api.us-west-2.amazonaws.com/Prod/change'                            

result = requests.post(url, json={"amount": "1.89"})                                                  

result                                                                                                
# <Response [200]>

result.json()                                                                                        
# {'res': [{'7': 'quarters'}, {'1': 'dimes'}, {'4': 'pennies'}]}
```