# Infrastructure Repository and Pipeline

## Introduction

You should now have Completed the Following things:
1. Setup your Azure DevOps Account
2. Added the Service Connection in Azure DevOps

Next you will create your own Pipeline to setup your first own Website on Azure. This will only be the most basic Infrastructure Setup. In a later Step we will then alter the Websites Content.

If you want to learn more about the concept of a pipeline you can do it here:

[Microsoft Docs Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/what-is-azure-pipelines?view=azure-devops)


# 1. Setting up the Infrastructure Pipeline

The first Step in Creating a Pipeline with Azure DevOps

## Azure Cli

The Pipeline we are Proposing here is using the Azure CLI to create the App Service Plan and the WebApp on Azure.

Azure CLI Docs: 
<br> https://docs.microsoft.com/de-de/cli/azure/what-is-azure-cli

Azure AppServicePlan and WebApp: 
<br> https://docs.microsoft.com/en-us/azure/app-service/overview

## Creating the Pipeline



Now start writing the infrastructure pipeline to deploy an App Service Plan and a WebApp in Azure step by step

Warning: The formatting of YAML (yml) files is based on spaces and tabs and therefor the following lines should be copied with care.
It is advised to use Visual Studio Code to validate the copied file.  
Starting with making the variable group available to the pipeline. From now on we can reference any variable that is held in the variable group under libraries (described under 2):
variables:
- group: infravars

Next, we need to set a trigger which will run the pipeline after every commit on this repository:
(we set it to none to avoid unwanted pipeline runs)

trigger: none

Then we need to set an operating system in which our pipeline will run:
pool:
  vmImage: ubuntu-latest

After that we define the smallest building block of a pipeline which is called step and
can be a task or a script.

This Task that we want to use is a special Azure CLI task that will execute our commands like would do it on the Azure Portal in the cloud shell:

steps:
- task: AzureCLI@2
  inputs:
    azureSubscription: '$(so)'
    scriptType: 'bash'
    scriptLocation: 'inlineScript'
    inlineScript: |
      az appservice plan create -g $(rg) -n $(asp) --is-linux --number-of-workers 1 --sku B1
      az webapp create -g $(rg) -p $(asp) -n $(wa) --runtime "node|10.14"

If you want to learn more about the concept of a pipeline you can do it here:

https://docs.microsoft.com/de-de/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops


## Code runner

After we define the Triggers and the Name of the workflow we need to Specify its "`jobs`".
In our Example we only need one Job "`deploy`".

Next we Specify what image we Expect our job to run on:
"`runs-on: ubuntu-latest`"

```
jobs:

  deploy:
    runs-on: ubuntu-latest
    
```

To learn more about the Workflow Syntax and Jobs visit:
https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#jobs



## Deployment of AppService and WebApp

Next the Script creates with the Build in Azure CLI "`uses: azure/CLI@v1`" the AppService Plan and the corresponding WebApp. 

```
    - name: Azure CLI script
      uses: azure/CLI@v1
      with:
        inlineScript: |
          az appservice plan create -g ${{ secrets.rg }} -n ${{ secrets.asp }} --is-linux --number-of-workers 1 --sku B1
          az webapp create -g ${{ secrets.rg }} -p ${{ secrets.asp }} -n ${{ secrets.webapp }}  --runtime "node|10.14"
```

AppService with Azure CLI
<br> https://docs.microsoft.com/de-de/cli/azure/appservice/plan?view=azure-cli-latest

WebApp with Azure CLI
<br> https://docs.microsoft.com/de-de/cli/azure/webapp?view=azure-cli-latest#az_webapp_create


You will see there is a tiny difference in your File to this Code Snipped.
Just Copy over the Missing Part.

# 2. Run your Pipeline

After you Set up your Secrets and fixed the Code in your Repository.
You can try to run your Workflow.
To do so go to Actions and select the Infra workflow on the Left site.

Now Select Run workflow on the Right side.

<br><img src="./images/runWorkflow.PNG" width="800"/><br>

## Workflow Progress

Wait for your Workflow to finish.
If the Task does not run through you may ask one of us to Help you out.
## Check your WebApp is online after approx. 5 minutes

https://`[yourWebAppName]`.azurewebsites.net/

You should see a &quot;Hey, Node developers&quot; welcome screen.

Congratulations, you have deployed your first WebApp infrastructure.
 Now, you can go ahead and deploy some code to your WebApp.