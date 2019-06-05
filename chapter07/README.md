# Chapter 7.  Verify that the application is reachable over the internet

At this point everything is in place for calling your application over the internet via the load balancer. Let's verify that that's the case.

1. Select EC2 from the AWS Service menu.
1. Go to load balancers under the Load balance heading in the column to the left.
1. Find your application's load balancer and copy it's DNS name.
1. Use you browser, curl or something similar and make a call to `http://<Load balancer DNS name>/movies` and verify that you get a response.
