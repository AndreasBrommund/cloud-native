## Chapter 4. Container Registry (CD part i).

In the last chapter the `feature` branch received CI capabilities. In this chapter, you will make a pipeline for continuous delivery of the `master` branch.
The pipeline will produce a Docker image of the application that can be shipped to the servers running your application.

1. By now, you're an expert at creating CloudFormation stacks. Create a new stack, uploading the template called `container-registry.yml`. This will create a Docker Registry that will contain your `cloud-native-application` Docker images.
2. Create a CD pipeline, through CloudFormation. Create a new stack using the `code-pipeline-cd-part-1.yml` template. Name the stack `code-pipeline-cd`.
3. Browse to the new pipeline, called `cloud-native-application-pipeline-cd`. It will start building immediately. 
4. Once the step `BuildTestAndDeliver` has finished, verify that image of the application has been delivered to ECR. Go to the ECR console (Services -> ECR). A repository called `cloud-native-app` should be listed. When you click it, you should see an image with the `latest` tag.
