# Chapter 6. Container cluster deployment pipeline (CD part ii)

To finalize our continuous deployment pipeline so that we can deploy and run our application in AWS we need to first create our service in AWS ECS and secondly we need to extend our pipeline with a deployment step.

## Setting up the service 

To be able to run our application we need to create a service definition and the service we define have to have a role that allows the service to access the resources it needs to start up and run. We have to create the role first as the service definition has a reference to the role.

1. Open `fargate-task-execution-role.yml` and you'll see that the template will create one resource, an IAM role.
1. The role will allow the task in ECS that'll run our service to download our application's Docker image from ECR, log to CloudWatch and access DynamoDB
1. Go to CloudFormation in the AWS service menu and create a stack using the `fargate-task-execution-role.yml` template.
1. When the stack has been created, go to IAM from the AWS service menu.
1. Select roles from the menu on the left and then click on the role you just created, `AmazonECSTaskExecutionRolePolicy`
1. Click on the arrow in the policy list and see that you've created a role with the privileges specified in the template.

With the execution role in place we can create the service that will run our application.

1. Have look at the `service.yml` template that we'll use to create our service.
1. In the parameters block you can see the dependencies that the service has. The service will need to know which cluster to run in, which repository to fetch its Docker images from, which role it should use when executing tasks, the desired number of tasks the service should schedule, the target group it should belong to to, which security group to use and finally which subnets the service should belong to.
1. There are three resources that the service template will create: the service itself, a log group in CloudWatch to stream log events to and a task definition.
1. Create a stack in CloudFormation using the `service.yml` template. The input to the stack is outputs from previous stacks.
1. The instances of your application that the service launches will all log to a log group in CloudWatch. Browse to CloudWatch from the AWS service menu. 
1. Open the log group of your application and you'll see the different log streams. Each of the log streams corresponds to one instance of your application. Open the latest logstream and verify that you get the same printouts as when you were successfully running the application locally.

## Extending the pipeline

In chapter 4 we created a pipeline that builds, tests, packages the application in a Docker image and finally pushes the image to the Docker repository (ECR). Now it's time to extend the pipeline into a proper continuous deployment pipeline. What's missing is the final stage where the pipeline schedules the newly built Docker image to run in the ECS container cluster.

1. Open the `code-pipeline-cd.yml` template in this folder and compare it to the template in chapter 4. The difference is the addition of a final pipeline stage that deploys the latest image to the ECS cluster. That is done through the `image.json` file that the `post_build` phase creates.
1. In CloudFormation select your pipeline stack and update the stack with the `code-pipeline-cd.yml` template from this folder.
1. Trigger the pipeline by doing a commit of your choice the `cloud-native-app` repo.
1. Watch the pipeline build, package and deploy your change to the ECS cluster in the CodePipeline console.
