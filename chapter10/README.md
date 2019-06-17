# 10. Global scale out and failover

Run the application in multiple regions using and balance traffic with failover routing in Route 53. Simulate the outage of a data center - thanks to your global presence your application is still available!
This step requires somewhat more proficiency and assumes that you have a hosted DNS zone in AWS.

1. Deploy your entire application stack (VPC, Load balancer, ECS cluster, and Service) into another region, for example somewhere in America.
2. You must make your DynamoDB table global. Unfortunately, this cannot be achieved through infrastructure as code. Go to your DynamoDB table, and press Global tables. Follow the instructions (your table must be emptied, unfortunately) and deploy your table in your secondary region.
2. Inspect the template `route53.yml`. It manages a DNS zone, and sets up failover routing to the underlying hosts - your load balancers in Europe and America.
3. Deploy the template. Inspect the DNS records that are created in Route53, and the health check. The health check should be green and up.
4. Browse to your domain, and inspect the app. You can see which AWS region it is running in by browsing to `/region`.
5. Simulate the outage of the service by scaling down the desired count of the ECS task in your primary region to 0. Verify that your load balancer in the primary region starts to return 503.
6. After at most two minutes, your health check in Route 53 should be red and report that the primary region is down. Try browsing to your domain again. The service should still be available, and you should now be served from the secondary failover region. Route53 has switched over the DNS record when the health check failed.
7. Scale your primary service back up - after the health check starts reporting that your service is healthy the application is once again served from the primary region.
