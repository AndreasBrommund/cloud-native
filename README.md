# Cloud Native

## Goal

The goal is to deliver an application into production globally in an automated and reproducible fashion.

## Principles

- Containerization
- Continuous Integration
- Continuous Deployment
- Infrastructure as Code
- Performance efficiency
- Cost optimization
- Security
- Reliability
- Serverless
- Managed Services

## Prerequisites

You need to have the following installed on your laptop:

- Java
- Docker
- Git
- An IDE: IntelliJ or Eclipse for example

## Chapters

### 1. Version control

Clone the application code into your own repository

#### Principles
- Continuous Integration
- Infrastructure as Code

### 2. Containerization

How to execute and distribute an environment agnostic application.

#### Principles
- Containerization

### 3. Your first pipeline (CI)

Set up a pipeline that pulls your code and runs the unit test suite.

#### Principles
- Continuous Integration
- Infrastructure as Code

### 4. Container Registry (CD part i)

Extend the pipeline to push your docker image to the docker registry (ECR)

#### Principles
- Continuous Integration
- Infrastructure as Code

### 5. Container Cluster

Set up a Fargate cluster as the runtime environment for your docker containers using infrastructure as code.

#### Principles
- Infrastructure as Code
- Performance efficiency
- Cost optimization
- Security

### 6. Container cluster deployment pipeline (CD part ii)

Extend the pipeline to deploy docker containers in the container cluster using images from the docker registry.

#### Principles
- Continuous Deployment

### 7. Verify that the application is reachable over the internet

Connect to the load balancer address of the running application container and verify that it's reachable and up and running.

### 8. Scale out the application

Modify the code that defines the container cluster to run more instances in parallel.

#### Principles
- Reliability

### 9. Cloud services - databases

The application needs a document database as a backend. Set up a DynamoDB instance using infrastructure as code.

#### Principles
- Serverless
- Managed Services

### 10. Global scale out and failover

Run the application in multiple regions using geolocation routing in Route 53. Simulate the outage of a data center - thanks to your global presence your application is still available!

#### Principles
- Reliability
- Scalability

### 11. Billing and cleanup

What's the cost of the resources we've created and how can we remove no longer needed resources.

#### Principles
- Managed Services

## Course ToDos

- Verify that there are no service limits when e.g. running a cluster per student

## Cloud Native - Part ii

Build upon the first part and add new principles

### Principles:
- 3R's of Enterprise Security
- Auto-scaling
- Monitoring and Tracing
- Structured log data
