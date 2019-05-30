# Chapter 2. Containerization.

To be able to reliably and reproducibly build, ship and deploy our application we will utilize containerization through Docker.

1. Open the the Cloud Native Application repository in your IDE
1. From the IDE or the terminal, run `mvn clean package`. This will compile the application, run the unit tests and build a fat jar containing all class files needed to run the application.
1. Make sure that you can run the fat jar and that the application starts. Run `java -jar target/application-*.jar` from the commandline
1. The next step is to automate what you just did manually and make sure that we can compile, test, package and run the application no matter what the underlying infrastructure is.
1. Have a look at the `Dockerfile` in the application repository which is a recipe for Docker how to build a runnable Docker image
1. There are two stages in the Dockerfile: one to compile, test and package the application using a Maven Docker image and a second stage that runs the fat jar in a Java 11 Docker image. The second stage defines the Docker image that will be kept, the first stage is thrown away after the build.
1. Build the Docker image locally: `docker build -t cloud-native-app .`
1. Make sure that the Docker image is stored in your local Docker repository: `docker image ls`
1. Run the application locally: ` docker run -e AWS_REGION=eu-west-1 -t cloud-native-app`
