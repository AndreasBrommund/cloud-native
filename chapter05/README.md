# Chapter 5. Container Cluster

In this chapter we'll create a container cluster where your application, packaged in a docker image, can run.

The first step is to set up networking in your account. You'll need a VPC, two subnets, routing tables and an internet gateway.

1. Open the the `vpc.yml` and have a look at the `Parameters` block. You will have to enter three CIDR blocks, on for the VPC and one for each of the subnets.
1. Under the `Resources` block in in `vpc.yml` you'll see that besides the VPC and our two subnets, an internet gateway and routing tables will be created.
1. Go to CloudFormation in the AWS service menu and choose create stack. Select the `vpc.yml` template. Fill out the CIDR block fields for the VPC and the subnets and create the stack.
1. When the stack has been created, select VPC from the AWS service menu and click on "Your VPCs" in the column to the left to view the VPC you just created.
1. In the same column to the left you can view the subnets, the internet gateway and the route tables that you just created.

The second step is to create the loadbalancer that will front your services and distribute load between your different application instances.

1. Open the `load-balancer.yml` file and once again have a look at the `Parameters` block. The load balancer template file has two inputs: subnets and a VPC. These parameters will specify which VPC and subnets that the load balancer and its components will live in.
1. The template will create a load balancer with a security group that only allows incoming traffic on port 80 and 8080
1. A listener that connects to load balancer with one listener rule will be created as well.
1. Finally a target group with a health check will be created and references from the listener
1. Go to CloudFormation in the AWS service menu and choose create stack. Select the `load-balancer.yml`file. Choose the VPC and the two subnets you just created as parameter values to the stack and create the stack.
1. When the stack has been created select EC2 in the AWS service menu.
1. In the column to the left under the "Load Balancing" header, select "Load Balancers" and have a look at the load balancer you just created.
1. Under the same header in the column to the left, select "Target Groups" and have a look at the target group you just created. You can e.g. see monitoring of the target group.

The final step is to create the container cluster.

1. If you open the `ecs-cluster.yml` you'll see that there's not much going on. You'll create a cluster that'll have the same name as the stack you create.
1. Go to CloudFormation and create the cluster.
1. When the stack is created, select ECS from AWS service menu.
1. Click on the cluster you just created and you can view your at this point quite empty cluster.
