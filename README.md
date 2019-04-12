# Cloud Native

## Goal

The goal is to deliver an application into production globally in an automated and reproducible fashion.

## Principles

- Containerization
- Continous Integration
- Continous Deployment
- Infrastrucure as Code
- Performance effiency
- Cost optimization
- Security
- Reliability
- Serverless
- Managed Services

## Chapters

### Version control

Clone the application code into your own repository

### Containerization

How to execute and distribute an environment agnostic application.

#### Principles
- Containerization

### Your first pipeline (CI)

Set up a pipeline that pulls your code and runs the unit test suite.

#### Principles
- Continous Integration

### Container Registry (CD part i)

Extend the pipeline to push your docker image to the docker registry (ECR)

#### Principles
- Continous Deployment

### Container Cluster

Set up a Fargate cluster as the runtime environment for your docker containers using infrastructure as code.

#### Principles
- Infrastrucure as Code
- Performance effiency
- Cost optimization
- Security

### Container cluster deployment pipeline (CD part ii)

Extend the pipeline to deploy docker containers in the container cluster using images from the docker registry.

#### Principles
- Continous Deployment

### Verify that the application is reachable over the internet

Connect to the load balancer address of the running application container and verify that it's reachable and up and running.

### Scale out the application

Modify the code that defines the container cluster to run more instances in parallel.

#### Principles
- Reliability

### Cloud services - databases

The application needs a document database as a backend. Set up a DynamoDB instance using infrastructure as code.

#### Principles
- Serverless
- Managed Services

### Global scale out

Run the application in multiple regions using geolocation routing in Route 53.

#### Principles
- Managed Services

## Course ToDos

- Verify that there are no service limits when e.g. running a cluster per student
- Determine what the best account set up is for the course
- What is the relationship between this course and the CI/CD introduction course? Will this course supersede the CI/CD course?

## Cloud Native - Part ii

Build upon the first part and add new principles

### Principles:
- 3R's of Enterprise Security
- Auto-scaling
- Monitoring and Tracing
