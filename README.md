# DevOps Lab
In this tutorial, you will create a toolchain from a template that contains a specific set of tool integrations and code to develop and deploy a sample Cloud Foundry app using Watson translation service that is written in Node.js. The toolchain is preconfigured for continuous delivery, source control, issue tracking, and online editing. After you create the toolchain, you change the app's code and push the change to the GitHub repository (repo). When you push changes to your repo, the delivery pipeline automatically builds and deploys the code that is in the repo.


### Prerequisites

1.	An IBM Cloud account: The account is free and provides access to everything you need to develop, track, plan, and deploy apps. [sign up ](https://console.bluemix.net/).
 for a free account.
2.	A GitHub account If you don't have one,
 [sign up](https://github.com/).
3.	Verify the [toolchains and tool integrations](https://console.bluemix.net/docs/services/ContinuousDelivery/cd_about.html#public_and_dedicated) that are available in your region and IBM Cloud environment. A toolchain is a set of tool integrations that support development, deployment, and operations tasks.

## Getting started

### Task 1: Create a toolchain



Give it a try! Click the button below to fork into IBM DevOps Services and deploy your own copy of this application on IBM Cloud.

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/watson-developer-cloud/language-translator-nodejs)


Tip: For instructions to navigate to the toolchain templates and select a toolchain to create, see [Navigating to the toolchain templates](https://www.ibm.com/cloud/garage/tutorials/toolchain_nav).

2.	On the creation page, Change the toolchain to your Application name

![Image2.png](https://github.com/nailahDev/DevOps/blob/master/Images/1.png)

3.	If you haven't authorized with GitHub, you are prompted to do so. Click Authorize and follow the instructions to link your IBM Cloud account to a GitHub account.
![Image1.png](https://github.com/nailahDev/DevOps/blob/master/Images/0.png)

4.	Review your GitHub settings and, if needed, change them. Each toolchain comes with a sample app, but you can select another repo to use.



•	To enable issue for ideas, enhancements, tasks, or bugs, select the Enable issues.

•	To track the deployment of code changes by creating tags, labels, and comments on commits, pull requests, and referenced issues, select the Select Track deployment of code changes check box.

5.	Click Deploy, You can see the deployed app by clicking View App.
![Image1.png](https://github.com/nailahDev/DevOps/blob/master/Images/0.png)


 Note: If you do not see a route when you click the arrow on the View App button, either the pipeline is not finished deploying or an error occurred while your app was being deployed. in the Delivery Pipeline choose *Deploy stage* -*View logs and history*  to see the status of the deployment.

6. Return to the Toolchains page.
The Toolchains page displays all the toolchains that are in your org. For each toolchain, you can see icons that represent the tool integrations that are in that toolchain. From this list, you can rename and delete toolchains.

7. Click your new toolchain to open its Overview page.




### Task 2: Modify the code

1.	On the toolchain's Overview page, *click Eclipse Orion Web IDE*. Your GitHub repo is automatically loaded in your workspace.

2.	In the file navigator, expand the repo for your current toolchain and go to the index.ejs file in the Views folder.

![Image4.png](https://github.com/nailahDev/DevOps/blob/master/Images/3.png)


1. Edit the `index.ejs` file and change
```
<h1>language translator</h1>
to
<h1>Your Name language translator</h1>
```
4. to push your changes you need to:

• Go to the Eclipse Orion Web IDE menu, click the **Git icon**.

![Image5.png](https://github.com/nailahDev/DevOps/blob/master/Images/4.png)
- In the Working Directory Changes section, type a commit message and make sure that the changed file is selected.

• Click **Commit** to put the changes in the local master branch.

• To push the changes to the origin/master branch, click Push. The origin/master branch is used by the pipeline, which automatically builds and deploys your changes.

5. When the pipeline process is completed, go to your toolchain's Overview page and click **View App**

6. Verify that your changes are visible in the running app.

   ![Image5.png](https://github.com/nailahDev/DevOps/blob/master/Images/5.PNG)

### Task 2: Add a stage to the pipeline

1.	Click on the toolchain's **Overview** page.
2.	Click on the Delivery Pipeline tool integration to view the build and deployment activity for your app. The pipeline has two stages: one where your app is built and another where it is deployed.

   ![Image6.png](https://github.com/nailahDev/DevOps/blob/master/Images/5.5.png)


The Build stage contains a build job that compiles your project in preparation for deployment.

3.	To add a third stage to deploy a test instance of your app, click **Add Stage**.
4.	Click the stage name, MyStage, and change the name to **Test**.
5.	Click the **JOBS** tab.
6.	Click **ADD JOB**, and then select the **Test** job type.
8.	For this lab choose simple Test, you can select other types of tests such as Advanced Test or vulnerability advisor to test your containers health or any other test that fit your needs.

7.	Review the values that are specified in the Organization and Space fields. Those values specify the org and space that the test instance of the app is deployed to. Make sure that a valid org and space are selected.

9.	Click save
10.	Drag the stage that you just created so that it is between the first two stages.

![Image7.png](https://github.com/nailahDev/DevOps/blob/master/Images/6.PNG)

11.	Run the stage



### Task 3:IBM Cloud Availability Monitoring

To ensure that your app is always available and satisfying users, teams must monitor its availability and response time with simulated tests.
1. To add Availability Monitoring to a toolchain:
- Click Add a Tool.
- Click Availability Monitoring.
- Click Create Integration.


1.	Go to the IBM Cloud Apps dashboard. Click the application to monitor. By default, the application's Overview page opens.

2.	Click ***Monitoring***.
3.	View the monitoring information.

![Image8.png](https://github.com/nailahDev/DevOps/blob/master/Images/10.PNG)


4.	Click See Monitoring Details. On the Monitoring Details page, scroll to the Synthetic Tests section and look for the card that represents the default test that runs to check site availability for the URL.

![Image9.png](https://github.com/nailahDev/DevOps/blob/master/Images/9.PNG)

5.	On the card, click the menu and click *** Edit *** to view the test configuration.

![Image8.png](https://github.com/nailahDev/DevOps/blob/master/Images/10.PNG)


6.	View the information about the test, including its name and the URL that is used to test the site availability.

7.	View the settings to customize how the test runs. You can change several configuration parameters, including the interval at which the test is run and the locations that it is run from.
8.	Change the interval parameter to 1 minute so that you can quickly see when a failure occurs. Click Finish.


![Image10.png](https://github.com/nailahDev/DevOps/blob/master/Images/12.png)


1.	Open the detailed monitoring information for the application by clicking ***See Monitoring Details***


To make sure that monitoring is working, you will stop the application and see that the availability monitor reflects that the application is not available.
1.	Go to the application's dashboard and click Overview.
2.	Simulate an outage by stopping the app.
3.	Click Monitoring to see the Availability Monitoring dashboard. The dashboard reflects that the application is not available.

![Image11.png](https://github.com/nailahDev/DevOps/blob/master/Images/13.png)


4.	Return to the Monitoring page, and restart the app.

### Task 4: Adding DevOps Insights to a Toolchain

DevOps Insights is available through integration with IBM® Cloud Continuous Delivery toolchains. You can add DevOps Insights to any toolchain by selecting it from the tool integration catalog.


To add DevOps Insights to a toolchain:
- Click Add a Tool.
- Click DevOps Insights.
- Click Create Integration.

DevOps Insights is now available on your toolchain's Overview page. Your repo and issue-tracking system are scanned automatically for data.
Using DevOps Insights

If your toolchain includes GitHub, GitLab, or JIRA, DevOps Insights automatically provides you with information about your codebase and team after some initial data gathering and analysis. If your toolchain does not include any of those integrations, add one of them and then follow these steps:

1.  From your toolchain's Overview page, click DevOps Insights.
2. Click Team Dynamics or Developer Insights and then choose any data category.

![Image8.png](https://github.com/nailahDev/DevOps/blob/master/Images/8.PNG)


3. Explore your project's data by viewing the dashboards in the data category. If you want to know more about a graph or what you might do with its information, click Information or Guidance.

![Image7.png](https://github.com/nailahDev/DevOps/blob/master/Images/7.PNG)



4.  After you explore Team Dynamics and Developer Insights, configure Deployment Risk to help you enforce code quality. Deployment Risk is compatible with both Delivery Pipeline for Continuous Delivery and Jenkins.
To learn more about using DevOps Insights, see [IBM Cloud Docs](https://console.bluemix.net/docs/services/DevOpsInsights/about_risk.html#about-deployment-risk)
 .

### Summary

In this tutorial you learned the IBM Garage Method and created a toolchain that includes a sample application, a Git repository, Eclipse Orin Web (IDE), and a delivery pipeline. Then, you  delivered a cognitive application to production on IBM Cloud. You also learned about the application availability monitoring & DevOps Insights that is provided by IBM Cloud.
