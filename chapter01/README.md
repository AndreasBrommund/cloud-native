## Chapter 1. Version control

Clone the application code into your own repository.

1. Log into your AWS-account. Once logged in, make sure that you are in the Ireland region (eu-west-1).
2. You will create a code repository for the application inside AWS. The code repository service is called CodeCommit. *TODO:* Create manually or create through CFN?
3. Browse to the repository you just created in CodeCommit. Press *Services*, type *CodeCommit*, and press *Repositories*. You should see the *cloud-native-application* repository. Press it, and you will see instructions for setting up SSH access to CodeCommit.
4. Follow the instructions for setting up SSH access on your OS. 
5. The application code skeleton is available on [Github](https://github.com/Omegapoint/cloud-native-application). Clone the repository from Github, then move its contents into your own *cloud-native-application* that's hosted on CodeCommit - and push.
6. Refresh the browser window with CodeCommit. The code you just pushed to your repository should be visible in the browser.
