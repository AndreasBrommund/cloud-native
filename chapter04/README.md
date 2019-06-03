# Chapter 4. Container Registry (CD part i).

In the last chapter the `feature` branch received CI capabilities. In this chapter, you will make a pipeline for continuous delivery of the `master` branch.
The pipeline will produce a Docker image of the application that can be shipped to the servers running your application.

1. By now, you're an expert at creating CloudFormation stacks. Create a new stack, uploading the template called `container-registry.yml`. This will create a Docker Registry that will contain your `cloud-native-application` Docker images.
1. If you open the `code-pipeline-cd.yml` template you'll see that it'll create two roles: one for the build step and one for the pipeline itself. The two most interesting parts can be found under `CodeBuildProject` and `Pipeline`. The `CodeBuildProject` resource is a CodeBuild project that will do the actual heavy lifting of building a Docker image and pushing that image to ECR. Under the `BuildSpec` heading you can see the three steps, where some housekeeping is done in the pre build step, the actual build is done in the build step and the post build step finally pushes the build docker image to ECR. Note the similarities between what you did in chapter 2, containerization and what the pipeline does. The `Pipeline` resource defines two stages, one for pulling the latest code from CodeCommit and one for running the `CodeBuildProject`.   
1. Create a CD pipeline, through CloudFormation. Create a new stack using the `code-pipeline-cd.yml` template
1. Browse to the CodePipeline console in AWS and have a look at your pipeline under the `cloud-native-application-pipeline` heading. It will start building immediately. 
1. Once the step `BuildTestAndDeliver` has finished, verify that image of the application has been delivered to ECR. Go to the ECR console from the service menu. A repository called `cloud-native-app` should be listed. When you click it, you should see an image with the `latest` tag.
