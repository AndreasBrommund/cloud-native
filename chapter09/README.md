# 9. Cloud services - databases

The application needs a document database as a backend. Set up a DynamoDB instance using infrastructure as code.

1. To achieve statelessness in the application, we must move the the movie list from within the memory of the service into a persistent data store, that backs all instances of the service. To this end, we will use DynamoDB, a managed NoSQL service.
2. Inspect the `dynamo-db.yml` template. It contains the definition of our table and indexes on columns in the table.
3. Create a stack of the `dynamo-db.yml` template.
# TODO instructions about how to reconfigure boot app with dynamo movie repository
4. Change the source code of your movie application to start using DynamoDB as the data store.
4. Push to your `feature` branch, and make sure that the application builds and passes its tests.
5. Once the `feature` branch has been built, push to master and watch code pipeline build and deploy your new application.
6. Test your application by adding movies and refreshing the page.
