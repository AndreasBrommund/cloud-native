# Chapter 1. Version control

Clone the application code into your own repository.

1. Log into your AWS-account. Once logged in, make sure that you are in the Ireland region (eu-west-1).
2. You will create a git code repository for the application inside AWS. The code repository service is called CodeCommit.
3. Everything that we do in AWS will be done by running code. The AWS service CloudFormation allows you to describe and provision all the infrastructure resources you need, by describing them as code. 
4. Have a look at the `code-commit.yml` file in the chapter01 folder which describes your CodeCommit repository
5. To create your CodeCommit repository using the `code-commit.yml` template, go to CloudFormation in the AWS service menu on your AWS account
6. Click on `Create stack` and select the template file. Click `Next`.
7. Give the stack a(ny) name and disable rollback on failure under *Advanced options* > *Stack creation options*. Disabling rollback on failure will help you to investigate what went wrong if the stack fails to be created.
8. Click `Next`, followed by `Create stack` and wait for the stack to be created 
9. Browse to the repository you just created in CodeCommit. Click on *Services*, type *CodeCommit*, and click on *Repositories*. You should see the *cloud-native-application* repository. Open it, and you will see instructions for setting up SSH access to CodeCommit.
10. Follow the instructions for setting up SSH access on your OS. 
11. The application code skeleton is available on [Github](https://github.com/Omegapoint/cloud-native-application). Clone the repository from Github and open the `.git/config` file.
12. In the `.git/config` file, change the url property under the `[remote "origin"]` header to the git clone path provided by CodeCommit. The new url line should look like this or something similar: `url = ssh://git-codecommit.eu-west-1.amazonaws.com/v1/repos/cloud-native-application`
13. Run `git push`. Refresh the browser window with CodeCommit. The code you just pushed to your repository should be visible in the browser.
