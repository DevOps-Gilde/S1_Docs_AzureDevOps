# 1. Introduction to Application Pipeline

You should now have Completed the Following things:
1. Setup your Azure DevOps Organization/ Project
2. Setup your Azure DevOps Repository
3. Setup your Azure DevOps Service Connection
4. Setup the Infrastucture

Next you will deploy the code to your web application. The code we already created for you. The major task left for you is to create a pipeline based on the provided code.

# 1. Setting up the Application Pipeline

## Setup the pipeline

Setting up the pipeline follows the same steps as in the infrastructure case (see there for details). The existing yaml file you havve to use in the pipeline is `app-pipeline.yaml`.

## Deploy the web app

Deploying the pipeline follows the same general principles as for the infrastructure. Note the following specifics:
- It takes approximately 5 minutes until your web site is online
- The url of the web site follows the default naming patterns which is `https://<YourWebAppName>.azurewebsites.net/`
- Upon success you should see a “Hey, Node developers” welcome screen.



