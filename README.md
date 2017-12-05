# DevOps Lab
In this tutorial, you create a toolchain from a template that contains a specific set of tool integrations and code to develop and deploy a sample Cloud Foundry app using Watson translation service that is written in Node.js. The toolchain is preconfigured for continuous delivery, source control, issue tracking, and online editing. After you create the toolchain, you change the app's code and push the change to the GitHub repository (repo). When you push changes to your repo, the delivery pipeline automatically builds and deploys the code that is in the repo.
Prerequisites


Prerequisites

1.	*An IBM Cloud account* The account is free and provides access to everything you need to develop, track, plan, and deploy apps. [sign up] [https://console.bluemix.net/]  for a free account.
2.	*A GitHub account* If you don't have one, [sign up][https://github.com/].
3.	*Verify the toolchains and tool integrations* [https://console.bluemix.net/docs/services/ContinuousDelivery/cd_about.html#public_and_dedicated] that are available in your region and IBM Cloud environment. A toolchain is a set of tool integrations that support development, deployment, and operations tasks.

## Getting started

### Task 1: Create a toolchain

1.	Open the creation page for the Simple Cloud Foundry toolchain by clicking the Create toolchain button.


Give it a try! Click the button below to fork into IBM DevOps Services and deploy your own copy of this application on Bluemix.

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/watson-developer-cloud/language-translator-nodejs)

Tip: For instructions to navigate to the toolchain templates and select a toolchain to create, see Navigating to the toolchain templates.
2.	On the creation page, Change the toolchain to your name
3.	If you haven't authorized with GitHub, you are prompted to do so. Click Authorize and follow the instructions to link your IBM Cloud account to a GitHub account.
4.	Review your GitHub settings and, if needed, change them. Each toolchain comes with a sample app, but you can select another repo to use.

•	To enable issue for ideas, enhancements, tasks, or bugs, select the Enable issues.

•	To track the deployment of code changes by creating tags, labels, and comments on commits, pull requests, and referenced issues, select the Select Track deployment of code changes check box.
5.	Click Deploy, You can see the deployed app by clicking View App.

Note: If you do not see a route when you click the arrow on the View App button, either the pipeline is not finished deploying or an error occurred while your app was being deployed. in the Delivery Pipeline choose *Deploy stage* -*View logs and history*  to see the status of the deployment.



### Task 2: Modify the code

1.	On the toolchain's Overview page, *click Eclipse Orion Web IDE*. Your GitHub repo is automatically loaded in your workspace. The name of the repo that is shown in the file navigator is the name that you specified for the sample GitHub Enterprise repo when you created the toolchain.
2.	In the file navigator, expand the repo for your current toolchain and go to the index.ejs file in the Views folder.

3.	Edit the h1 text to change the text that is displayed by the app name. Your changes are automatically saved.image
1. Edit the `index.ejs` file and change
```
<h1>language translator</h1>
to
<h1>Your Name language translator</h1>
```
4. to push your changes you need to:

    - Go to the Eclipse Orion Web IDE menu, click the **Git icon**.
    - In the Working Directory Changes section, type a commit message and make sure that the changed file is selected.
    - Click **Commit** to put the changes in the local master branch.
    - To push the changes to the origin/master branch, click Push. The origin/master branch is used by the pipeline, which automatically builds and deploys your changes.

•  When the pipeline process is completed, go to your toolchain's Overview page and click **View App**

•  Verify that your changes are visible in the running app.


### Task 3: Add a stage to the pipeline

1.	Click on the toolchain's **Overview** page.
2.	Click on the Delivery Pipeline tool integration to view the build and deployment activity for your app. The pipeline has two stages: one where your app is built and another where it is deployed.

The Build stage contains a build job that compiles your project in preparation for deployment. The Simple builder type packages your app, expecting the code to be in the root folder. If you use any other builder type, the build stage compiles your app, builds it, or both. This job generates artifacts that can be sent to a build archive directory. However, by default, the artifacts are placed in the project's root directory.

The Deploy stage contains a deploy job that deploys the artifacts created by the Build stage. If a manifest file in the root folder exists, it is used to determine which buildpack to use. For more information about pipeline stages, see the IBM Cloud Docs.

3.	To add a third stage to deploy a test instance of your app, click **Add Stage**.
4.	Click the stage name, MyStage, and change the name to **Deploy Stage - Test**.
5.	Click the **JOBS** tab.
6.	Click **ADD JOB**, and then select the **Test** job type.
8.	For this lab choose simple Test, you can select other types of tests such as Advanced Test or vulnerability advisor to test your containers health or any other test that fit your needs.

7.	Review the values that are specified in the Organization and Space fields. Those values specify the org and space that the test instance of the app is deployed to. Make sure that a valid org and space are selected.
Image
9.	Click save
10.	Drag the stage that you just created so that it is between the first two stages.
11.	Run the stage



### Task3: Adding DevOps Insights to a Toolchain

DevOps Insights is available through integration with IBM® Cloud Continuous Delivery toolchains. You can add DevOps Insights to any toolchain by selecting it from the tool integration catalog.

DevOps Insights is also part of many toolchain templates. If you create a toolchain from a template that includes DevOps Insights, make sure that DevOps Insights is set to Advanced. Then, create the toolchain and skip to Using Insights.

To add DevOps Insights to a toolchain:
- Click Add a Tool.
- Click DevOps Insights.
- Click Create Integration.

DevOps Insights is now available on your toolchain's Overview page. Your repo and issue-tracking system are scanned automatically for data.
Using DevOps Insights

If your toolchain includes GitHub, GitLab, or JIRA, DevOps Insights automatically provides you with information about your codebase and team after some initial data gathering and analysis. If your toolchain does not include any of those integrations, add one of them and then follow these steps:

1.  From your toolchain's Overview page, click DevOps Insights.
2. Click Team Dynamics or Developer Insights and then choose a data category.
3. Explore your project's data by viewing the dashboards in the data category. If you want to know more about a graph or what you might do with its information, click Information or Guidance.

4. After you explore Team Dynamics and Developer Insights, configure Deployment Risk to help you enforce code quality. Deployment Risk is compatible with both Delivery Pipeline for Continuous Delivery and Jenkins.
