# 8. Scale out the application

Modify the code that defines the container cluster to run more instances in parallel.

1. For redundancy and performance, we want to run several instances of our popular movie service.
2. In CloudFormation, go to the stack that you defined for your service, and update it (using the same template). In the parameters, set `DesiredCount` to 2, and go through the wizard.
3. ECS will provision a second instance of the service, and the load balancer will balance load equally among the available services. Go to the ECS service in the AWS console, and look at the details of your service. You will se that when the CloudFormation stack has finished updating, your service will be running two instances of the movie task.
4. Browse to your application again.
5. Notice that the behavior when adding and getting movies repeatedly is a bit erratic. Why is that? Consult the code of your application, particularly `MockedMovieRepository`.
6. The state is kept in the memory of the application. It is therefore inconsistent across instances of the servers, and not persistent in the event of a service shutdown.
