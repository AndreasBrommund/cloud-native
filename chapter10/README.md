# 10. Global scale out and failover

Run the application in multiple regions using geolocation routing in Route 53. Simulate the outage of a data center - thanks to your global presence your application is still available!

1. Deploy your entire application stack (VPC, Load balancer, ECS cluster, and Service) into another region, for example somewhere in America.
# TODO: create a template for a hosted zone with geolocation routing, with input of the two ELBs
2. Inspect the template `dns.yml`. It manages a DNS zone, and sets up geolocation based routing to the underlying hosts - your load balancers in Europe and America.
3. 
