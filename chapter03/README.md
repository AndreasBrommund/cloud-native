# Chapter 3. Your first pipeline (CI).

This chapter will teach you how to create a pipeline that runs tests whenever you push to your CodeCommit repository.
The pipeline and its steps is defined in code. Inspect the CloudFormation template `code-pipeline-ci.yml`. 

1. Open the CloudFormation console. (Services in the upper left corner, then search for CloudFormation.)
2. Press Create Stack. Upload existing template -> `code-pipeline-ci.yml`. Name the stack `code-pipeline-ci`, and go through the rest of the wizard. Tick the checkbox about acknowledging IAM rights in the last step.
3. The resources defined in the template you uploaded are being provisioned by AWS. Much faster and safer than pressing buttons and manually entering values in the gui! Once the status changes to `CREATE_COMPLETE`, all resources have been created.
4. In the outputs section of the stack you just created, there is a URL to the pipeline you just created. Press it to view your pipeline. (This is the same as going to the CodePipeline console by browsing.)
5. The `cloud-native-application-pipeline-ci` pipeline is red (failed) because of some problem with the first step, `Source`. Press *details*. The reason why the build failed was because it tried to build something that does not yet exist - a branch called `feature` in your source code repository.
6. Open a terminal and go to the location of your `cloud-native-application`. To set up a branch called `feature` that CodePipeline can work with, run `git push origin master:feature`.
7. Go back into the `cloud-native-application-pipeline-ci` pipeline in the CodePipeline console. You will see that a new build was triggered, and that the code is building. After a while, the build will be completed, and the pipeline will be green.
8. Change your source code to break the tests. Commit your code with the breaking test and push to the `feature` branch. Inspect the `BuildAndTest` stage when the build fails.
9. Correct the build by making the tests run again, commit the and push the code, so that your pipeline is green again.
