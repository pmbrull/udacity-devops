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

## Using Docker Format Containers

### Docker Containers

* It is a single-purpose virtual machine.
* Allows us to package code and all its dependencies
* Takes up less space than a VM
* Multiple containers can run on the same machine

Containers are all about having many apps running on just one host. Also, it hides away from the developers the abstraction that makes it possible for one container to run on any host arbitrarily.

As an exercise, we will create a local environment for testing:
> mkalias; vudacity. We will install pylint, black, pytest, ipython

### Makefiles

A Makefile is just a convenient way to set up a set of operation for a project. Example:

```makefile
setup:
    python3 -m venv ~/.myrepo

install:
    pip install -r requirements.txt

test:
    python -m pytest -vv --cov=myrepolib tests/*.py
    python -m pytest --nbval notebook.ipynb

lint:
    pylint --disable=R,C myrepolib cli web

all: install lint test
```


#### Breaking Down the Makefile

If you haven't seen a Makefile before, this may seem like a lot of random commands all jumbled together. Let's briefly go through each.

    setup: You have seen most of this line before, which is dealing with our Python 3 virtual environment.
    install: This installs the requirements for our environment. In our case, it also install the pytest and pylint libraries used later on in the Makefile.
    test: This is broken into two parts for testing.
        First, it will use .py files in the tests directory. The -vv flag ensures short test durations are still shown (see documentation), while the -cov flag helps to calculate what the test coverage of the code is (see [documentation](https://docs.pytest.org/en/latest/usage.html#profiling-test-execution-duration)) in a given directory.
        The second line is used to test Jupyter Notebook cells. The --nbval flag makes pytest pay attention to jupyter notebooks (see [documentation](https://pypi.org/project/pytest-cov/)).
    lint: This will lint what is in the myrepolib directory, as well as the cli.py and web.py files in our current directory (see video). The --disable=R,C is used to disable the "convention" (C) and "refactor" (R) message classes (see related [Stack Overflow post](https://stackoverflow.com/questions/31907762/pylint-to-show-only-warnings-and-errors)).
    all: You may notice this line looks a little different than the above lines, with the commands on the same line. This will execute our install, lint and test commands.

After Makefile Creation

Once the Makefile is created, you can use:

    make install
    make lint

To install dependencies and test your code.

#### Exercise: Create A Basic Makefile

Makefiles can be incredibly useful ways to build up a chain of commands that build, test and deploy software.

Now that you've seen an example of a Makefile, you are ready to create one of your own. Makefiles have plenty of different commands and variables that can be used - check out [this page](https://makefiletutorial.com/) for a long list of them.

While you will start from scratch in this exercise, if you need to look at another example of a Makefile, you can check out [this Makefile](https://github.com/udacity/DevOps_Microservices/blob/master/containerization/Makefile) in the course repository. This additional example Makefile will be used in the next lesson on containerization.
Instructions

    Create an empty Makefile using the touch command
    Create two commands: cmd1 and cmd2 and make this echo the name of the command.
        Note that Makefiles will normally print out each line as it goes, but here we want it to just explicitly echo the command names. Check out the link above to figure out how you can stop a line from printing.
        Makefiles have an automatic variable that contains the target name for the commands you create. You can also find this in the link above to add to your Makefile.
    Create an all command that runs both cmd1 and cmd2
    Run make all to see the output

##### One Potential Solution

Here is an example of a Makefile you could create for this exercise:

```makefile
cmd1:
        @echo "$@"

cmd2:
        @echo "$@"

all: cmd1 cmd2
```

Note that after cmd1 and cmd2, and before @echo, should be a tab. The @ at the start of these lines prevents make from automatically printing the lines, while "$@" is the variable for a string containing the target name, in this case either cmd1 or cmd2. To double-check that make is actually showing the command name from within the command itself, try to echo something else from within one of them, such as Hello World!, and check the results.

### Linting and CircleCI

Here are the steps Noah took in the above video:

    Added to the Makefile:

    ```makefile
    validate-circleci:
        circleci config process .circleci/config.yml

    run-circleci-local:
        circleci local execute

    lint: # This line should already be there with regular pylint
        hadolint path/to/Dockerfile
    ```

    Runs hadolint Dockerfile
    Uses the config.yml file within a .circleci directory
    In the parent directory, runs make run-circleci-local to simulate what will happen in the remote CircleCI environment
    Uses the CircleCI website (a related blog post is linked below) to test remotely

> hadolint is a tool that is going to lint our Dockerfile.

### Running Dockerfiles


    Use `docker image ls` to see all of your created Docker images
    `docker run -it {image name} bash` ran Noah's Docker image

#### Docker Cheat Sheet

Here is a quick Docker cheat sheet for your reference: [LINK](https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf)

#### Noah's Dockerfile

Below is Noah's Dockerfile for your reference:

```Dockerfile
FROM python:3.7.3-stretch

# Working Directory
WORKDIR /app

# Copy source code to working directory
COPY . app.py /app/

# Install packages from requirements.txt
# hadolint ignore=DL3013
RUN pip install --upgrade pip &&\
    pip install --trusted-host pypi.python.org -r requirements.txt
```

### Exercise: Deploying to Amazon ECR

With a build server, local Docker file and lint files, we have everything built for our Python environment. The final step is to get this environment & microservice we've created deployed into an Amazon environment. We'll use Amazon's Elastic Container Registry (ECR) to do so. This allows us to put the whole bundled container and application onto Amazon.

In the below video, Noah walks through the steps necessary to deploy to Amazon ECR. You can follow along with the video, or additionally follow the exercise steps at the bottom of the page. All cloud providers also have their own container registries. These are important because they allow you to keep private containers that will be sourced for cloud-based deployments.

#### Instructions

    Create an empty Dockerfile using the touch command, or use a previously existing Dockerfile
        Use the FROM directive to source Python as a base image: https://hub.docker.com/_/python
        Build your container locally
    Create a new ECR repository following the instructions [here](https://docs.aws.amazon.com/AmazonECR/latest/userguide/ECR_GetStarted.html).
    Push your container to the ECR repository you created

Additional Reference

    ECR Registry Upload: [LINK](https://aws.amazon.com/blogs/compute/authenticating-amazon-ecr-repositories-for-docker-cli-with-credential-helper/)

The whole idea of using AWS ECR is that anyone in the organization can use the docker image that I'm creating.

## Containerization of an Existing Application

### Exercise: Docker Based Apps

#### Instructions

    Navigate to the `containerization` director in the Github repo.
    Check out the pre-built Flask app that will be containerized. If you haven't used Flask before, you can check out this free Udacity course (web.py), or check out Flask's documentation.
    Look through the Dockerfile for the container (also included below).
    Look through the Makefile to be run within the container.

The only real new thing so far is the inclusion of the Flask app - you got familiar with Dockerfiles and Makefiles in the Using Docker Format Containers Lesson, as well as how to create them. There are some additional steps we still want to go through to get the App up and running, but the important thing to notice here is that it doesn't necessarily matter what the application itself is, you can still easily containerize it.
Noah's Dockerfile

The Dockerfile in Noah's video is provided below:

```Dockerfile
FROM python:3.7.3-stretch

# Working Directory
WORKDIR /app

# Copy source code to working directory
COPY . flask_app/web.py /app/

# Install packages from requirements.txt
# hadolint ignore=DL3013
RUN pip install --upgrade pip &&\
    pip install --trusted-host pypi.python.org -r requirements.txt

# Expose port 80
EXPOSE 80

# Run app.py at container launch
CMD ["python", "web.py"]
```

> OBS: Building a Dockerfile from another Dockerfile lets you re-use high-quality work.

### More on Ports

Ports are not usually just randomly assigned numbers. Many ports are used for specific activities in networking. Port 80 is the commonly used port number for HTTP requests, which is why we are exposing that port to the host computer - it's where the Flask app is listening for requests. You may also see other ports, such as port 8080, used with different applications. What this means is that the server is listening on that port, so a request to that server must also append the "special" port number to an HTTP request (such as example.website.com:8080), so that the sending client uses port 8080, instead of the normal HTTP port 80.

You can see some additional common ports [here](https://www.utilizewindows.com/list-of-common-network-port-numbers/).

For more information specific to Docker ports, see [this post](https://runnable.com/docker/binding-docker-ports).

### Exercise: Build and Deploy

#### Instructions

    Run `docker build --tag=api .` from the directory containing your Dockerfile. If you want to use a different tag name, feel free to do so.
    Wait for awhile as your Docker image is built (note: you are welcome to get a jump start on the next exercise, if desired, while this completes).
    Use docker image ls to make sure your new Docker image is shown. You won't see the other containers in Noah's video - those are all of his other Docker images on his computer.
    Run `docker run -p 8000:5001 api`. If you changed the tag name in the first step, make sure to replace api here with your tag name. Note above that the -p notes port 5001 from the Docker container (as specified in web.py for our flask app) is exposed on port 8000 on the host computer.
    The container will tell us the Flask app is running on port 5001, but since we exposed port 8000 on our host to it, we will actually access the running app using port 8000. We haven't looked at Swagger documentation before here, but you can access it at http://localhost:8000 in your browser when the docker container is running. Note that Swagger is part of the implementation of this specific Flask app - if you make your own Flask app, Swagger won't be included unless you include it in your own code.
    Test out one of the Swagger commands from the running containerized app.

#### More on Swagger

[Swagger](https://swagger.io/solutions/api-documentation/) helps provide automated documentation for your APIs using the [OpenAPI specifications](https://github.com/OAI/OpenAPI-Specification).

Check out an example of a Swagger-based API [here](https://petstore.swagger.io/#/). Udacity actually uses Swagger for its internal-facing APIs!

#### Code Example

    Data Engineering API Example by Noah: [LINK](https://github.com/udacity/DevOps_Microservices/tree/master/containerization)

The run_docker.py file in the video is included below:

```Dockerfile
#!/usr/bin/env bash

# Build image
docker build --tag=api .

# List docker images
docker image ls

# Run flask app
docker run -p 8000:5001 api
```

### Exercise: Containerize an App

Containers are a powerful mechanism to reuse code from experts. Test your knowledge of the power of containers in the following exercise by building a container and containerizing an app from scratch!

#### Instructions

    Create an empty Dockerfile using the touch command
    Use the FROM command and reference the latest version of Python here.
    Include the "Hello World" Flask example as an app within your container
        Copy any relevant directories and libraries in the Dockerfile
        Make sure any relevant requirements are installed in the Dockerfile
        Expose the port from the Flask example oin the Dockerfile - make sure you check which one is used by the example!
        Have your Dockerfile run the relevant commands for your app
    Build your container
    Run the container, opening up a bash shell
    Verify the correct version of Python is installed: python --version

#### Tips

Below are potential options for building and running your container.

To build your container, if tagging your container as my-python-app:

    `$ docker build -t my-python-app .`

To run the container, given my-python-app as the image tag and my-running-app as the container name:

    `$ docker run -it --rm --name my-running-app my-python-app`

## Container Orchestration with Kubernetes

You can install kubernetes + minikube from [this link](https://linuxhint.com/install-minikube-ubuntu/).

### Checking for virtualization

The other command used is `sysctl -a | grep machdep.cpu.features`

### Overview of Kubernetes

Kubernetes is a useful tool for working with containerized applications. Given our previous work with Docker containers and containerizing an app, working with Kubernetes is the next logical step. Kubernetes was born out of the lessons learned in [scaling containerized apps at Google](https://queue.acm.org/detail.cfm?id=2898444), and is used for automating deployment, scaling and managing such containerized applications.

### Demo

You can follow the demo yourself below, or read through a [quick primer](https://kubernetes.io/docs/tutorials/kubernetes-basics/create-cluster/cluster-intro/) beforehand: [Create a cluster](https://kubernetes.io/docs/tutorials/kubernetes-basics/create-cluster/cluster-interactive/)

To go more in-depth with Kubernetes, we also suggest going through the remaining starter tutorials on the [Kubernetes website](https://kubernetes.io/docs/tutorials/kubernetes-basics/).

Kubernetes came out of Google as they needed a system to schedule jobs at scale. It manages and runs container clusters.

With Kubernetes it's easy to scale up our application. For example, suppose we have one kubernetes app called `test-app`, we could just run: `kubectl scale deployments/test-app --replicas=6`.

### Monitoring, Logging and Debugging with Kubernetes

The [Prometheus Operator](https://github.com/coreos/prometheus-operator) helps to integrate Prometheus monitoring directly with Kubernetes. There is also the kube-prometheus package which includes additional helpful components (including the Prometheus Operator) for monitoring, as well as the [Prometheus Adapter](https://github.com/directxman12/k8s-prometheus-adapter).

Prometheus is not the only monitoring tool available for Kubernetes though - if you are interested in other options as well, check out [this link](https://kubernetes.io/docs/tasks/debug-application-cluster/resource-usage-monitoring/).

On the next page, you'll get to perform an exercise to get monitoring set up with Prometheus, as well as think through designing a monitoring system of your own.

Reference: [Prometheus](https://prometheus.io/) - Open source monitoring solution.

### Exercise: Prometheus Monitoring

Monitoring is an essential component of DevOps best practices. In this exercise, you will set up Prometheus Monitoring.
Instructions

Install and configure Prometheus as shown [here](https://prometheus.io/docs/prometheus/latest/getting_started/#downloading-and-running-prometheus).
Setup monitoring on to allow Prometheus to monitor itself.
Consider a normal distribution, "six sigma" and the 68-95-99.7 rule. Computer systems events are often normally distributed, meaning that all events within three standard deviations from the mean occur with 99.7 of the occurrences.
Design a process that alerts senior engineers when events are greater than three standard deviations from the mean and write up how the alerts should work, i.e.
    Who should get a page when an event is greater than three standard deviants from the mean?
    Should there be a backup person who gets alerted if the first person doesn’t respond within five minutes?
    Should an alert wake up a team member at one standard deviation? What about two?

### Exercise: Logging

Logging is an important concept to master for professional software development. Test your skills in this exercise by getting the logs from a running pod.

Start your kubernetes application
Grab your application logs for your pod (given a pod named my-pod) by running this command: `kubectl logs my-pod`.

### Exercise: Debugging

As with coding itself, once you have launched your app with Kubernetes, it's likely you will need to do some debugging to get everything working properly. Here, you'll do some debugging with an example app to build your skills with Kubernetes.

#### Instructions - Pod Issues

Let's say you have deployed a Kubernetes app, but have the pod does not seem to be running.

* First, use `kubectl get pods` to check the names of your running pods. You may notice the pod with an issue is shown as in a Pending status instead of Running.
* Using the NAME of the specific pod from step 1, use `kubectl describe pod {POD NAME}` to get more information about that pod.
* From the output of the above command, search until you find the Events header. This should give you a Reason and Message related to the failure, such as FailedScheduling. An issue like this could be due to the necessary resources not being available for the pod, such as CPU limits.
* From what we have seen before, `kubectl scale` could be used in such a situation to correctly scale up and provide the necessary resources for our Pending pod. On the next page, you'll get to see an automated way to scale up your apps which improves on the manual functionality of `kubectl scale`.

#### Instructions - Node Issues

In this case, consider a Kubernetes app where the pod is working, but behaving strangely. Alternateively, you may have noticed an issue where no pod will schedule onto a particular node. In this case, there is likely an issue with the specific node that needs to be debugged. While the overall process is fairly similar to debugging issues, the syntax of commands is slightly different, so let's walk through these.

* First, use `kubectl get nodes` to check the names of the available nodes. You may notice the node with an issue is shown as in a NotReady status instead of Ready.
* Using the NAME of the specific node from step 1, use `kubectl describe node {NODE NAME}` to get more information about that node.
* The outputs here can vary quite a bit, but the issue could be caused by a disconnection from the network, some other negative Event, too high of resource usage, etc.

### Autoscaling with CPU or Memory

If you did the [Scaling Demo](https://kubernetes.io/docs/tutorials/kubernetes-basics/scale/scale-intro/) earlier, you already saw one way to scale your apps:

```
kubectl scale {deployment name} --replicas={desired number of replicas}
```

The Horizontal Pod Autoscaler does this work for you.

The Horizontal Pod Autoscaler built into Kubernetes is incredibly useful for expanding the number of Pods available based on processing or memory needs. The underlying algorithm itself, somewhat simplified, is as follows:

```
newNumPods = ceil(currentNumPods * (currentMetric / desiredMetric))
```

This means, if by some metric, we are currently at 2.5X our desired metric level, we will scale up our number of pods by 2.5X, rounded up to the nearest one pod.

#### Reference

Autoscale Pod: [LINK](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)
Additional HPA walkthrough: [LINK](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)

## Operationalizing Microservices

### Alerts and Incidents Response

Monitor Node Health: [link](https://kubernetes.io/docs/tasks/debug-application-cluster/monitor-node-health/)

While having alerts is important, they should be targeted, actionable, automated and safe. So, what can be worse than not having alerts for critical failures?
* Too many alerts
* Alerts that are not actionable
* Alerts that can be automated but are not
* Alerts that compromise the health of employees

### Disaster Recovery

Backup and Migrate Kubernetes: [LINK](https://github.com/heptio/velero)

What are some core principles of Disaster Recovery? Having more than one copy of critical data, and test-restoring backups regularly, are both key to disaster recovery.

### CI/CD Pipeline Integration

Earlier in the course, we briefly touched on CircleCI through its inclusion within a Makefile Noah used.

CircleCI is a great tool to help with continuous integration, and it works well with Kubernetes. You can read some information in this CircleCI blog post on one application combining Kubernetes with CircleCI, and on the next page, it will be your turn to add CircleCI to your build.

### Exercise: CircleCI

It is easy to look at build servers as a nice to have when they are a must-have for DevOps best practices. One ubiquitous cloud-based build server is CircleCI. In this exercise, you will incorporate many of the concepts from this course: Docker, Makefiles, and build systems.

#### Instructions

* Follow these [instructions](https://circleci.com/docs/2.0/local-cli/#processing-a-config) for setting up local CircleCI
* Change the template below and add to your Makefile (this template is similar to what we used in earlier lessons)
* Run `validate-circleci` and `run-circleci-local` for your project, making sure to change any values that are unique to your project.

```Makefile
setup:
    python3 -m venv ~/.udacity-devops

install:
    pip install --upgrade pip &&\
        pip install -r requirements.txt

test:
    #python -m pytest -vv --cov=myrepolib tests/*.py
    #python -m pytest --nbval notebook.ipynb

validate-circleci:
    # See https://circleci.com/docs/2.0/local-cli/#processing-a-config
    circleci config process .circleci/config.yml

run-circleci-local:
    # See https://circleci.com/docs/2.0/local-cli/#running-a-job
    circleci local execute

lint:
    hadolint demos/flask-sklearn/Dockerfile
    pylint --disable=R,C,W1203 demos/**/**.py

all: install lint test
```

### Load Testing

Locust Helm Chart: [LINK](https://github.com/helm/charts/tree/master/stable/locust).

### Exercise: Locust Load Testing

Load testing is a critical part of developing a reliable Microservice. This allows you to verify that the application can perform at scale. In this exercise, you will set up a basic load test with locust.

#### Instructions

* Install locust using instructions [here](https://docs.locust.io/en/latest/installation.html).
* Configure a basic load test of the predict service endpoint in the sample app as shown [here](https://docs.locust.io/en/latest/quickstart.html).
* How many requests does your application accept before latency significantly rises or it crashes?
* Come up with a solution that will scale this on your own laptop or desktop (consider whether you can use some of the scaling techniques in the last lesson * here!).
* Verify that you have solved your first bottleneck and increased the requests per second at least 10% higher.
