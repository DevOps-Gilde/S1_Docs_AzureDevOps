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

Next, we could set a trigger which will run the pipeline after every commit on this repository:
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

## Azure DevOps Variable Groups

Create a New Variable Group called "infravars"
<br><img src="./images/pipelinevariablegroups.PNG" /><br>


<br><img src="./images/variablegroups.PNG" /><br>

We all are use the same Subscription and same Resource Group but
everybody uses his own App Service Plan and his own Webapp.

Therefore, pick unique names e.g. robsplan21 or robswebapp21 for your App Service Plan 
and Webapp variables.

Use for Resource Group (rg) ws-devops.

* asp = App Service Plan must be unique in each resource group (your own)
* rg   = Resource Group must be unique in each subscription (use ws-devops)
* so   = Service Connection Name which you have set in your project (Settings -> Service connections)
* wa  = Webapp must be unique worldwide (your own)

Of course, you can use your own variables names, they must correspond with your pipeline.

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

## Setup Pipeline in Azure DevOps

<br><img src="./images/createpipeline.PNG" /><br>