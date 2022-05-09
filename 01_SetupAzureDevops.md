# 1. Introduction to Azure DevOps

Azure DevOps is a Software as a service (SaaS) platform from Microsoft that provides an end-to-end DevOps toolchain for developing and deploying software.  It also integrates with most leading tools on the market and is a great option for orchestrating a DevOps toolchain.

# 2. Setting up Azure DevOps

## Sign in to Azure DevOps

If you have already used Azure DevOps you can just use an existing organization and add a new project. The following describe the steps if you never did before:
- Go to https://dev.azure.com/

  The picure below shows the initial screen. It states "Sign in" on the right-hand side if you are not yet signed in.
  <br><img src="./images/ado_signin_initial.PNG" width="400"/><br>

- Login in with your CapGemini Account

  Click “Sign in” on the Top Right Corner. Select your Organisation Account or enter your Company Mail Address when prompted. When you are successfully signed in you are Redirected to https://dev.azure.com again.
  <br><img src="./images/ado_signin_finished.PNG" width="400"/><br>

## Create a new Azure DevOps Organization

To create an organization click on the button "Start Free". An organization is the top level entity that hosts your projects. State the name of your organization and select "Private as project visibility when prompted as shown below:
<br><img src="./images/ado_create_org.PNG" width="400"/><br>

## Create a new Azure Devops Project

After you setup your Organization, setup a new Project inside of it.

<br><img src="./images/ado_create_project.PNG" width="400"/><br>

The screenshot below shows the home of your new project after successful creation.

<br><img src="./images/ado_prj_overview.PNG" width="400"/><br>

The left-hand side contains the major navigation entries. Relevant in this hackathon are:
- the rocket symbol for pipelines
- the git symbol for git repositories
- project settings at the bottom

For further informtation about Azure Devops Projects visit this [Website](https://docs.microsoft.com/en-us/azure/devops/organizations/projects/create-project?view=azure-devops&tabs=browser)
