# Chapter 7.  Verify that the application is reachable over the internet

At this point everything is in place for calling your application over the internet via the load balancer. Let's verify that that's the case.

1. Select EC2 from the AWS Service menu.
2. Go to load balancers under the Load balance heading in the column to the left.
3. Find your application's load balancer and copy it's DNS name.
4. Use you browser, curl or something similar and do a `GET` to `http://<Load balancer DNS name>/movies` and verify that you get a response.
5. You can create movies by `POST`ing with a similar curl: `curl -X POST http://<Load balancer DNS name>/movies -H 'Content-Type: application/json' -d '{"title": "Plötsligt i Vinslöv", "yearOfRelease": "1999"}'`
