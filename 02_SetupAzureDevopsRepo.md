# 1. Introduction to Azure DevOps Repositories

You should now have Completed the following things:
1. Setup your Azure DevOps Organization/ Project

Next you will you will create your Git repository within Azure DevOps. Git is a version control system that developers use all over the world. It helps you track different versions of your code and collaborate with other developers. But Git is not just for code, it can be used for any kind of text document.

Using the built-in repositories of Azure DevOps has the following benefits:
- You don't need an additional environment to host your code such as GitHub enterprise
- They are well integrated with other features like pipelines

# 2. Setting up the Azure DevOps Repository

## How to Setup Azure DevOps Repository

We created a repository in GitHub that is intended as starting point. Partially code changes are required from your side for setting up the infrastructure. Two steps are required:
1. Creating the repository in Azure DevOps
2. Adjusting the code

For the second step various options exist:
- Using in-place editing with the browser within Azure DevOps after import

  Only small code changes are required from your side. This is the **recommended method if you are not familiar with local code adjustment** via Visual Studio Code or comparable tooling.

- Using local tools to adjust the code

## How to import GitHub repository into Azure DevOps

Initially Azure DevOps creates a default repository that has the same name as the project. Our starter project can be directly imported into Azure DevOps. The screenshot below shows how an existing GitHub repository can be imported:
<br><img src="./images/repo_import_trigger.png" /><br>

You will be then prompted for the GitHub repository. The link is as follows: https://github.com/DevOps-Gilde/S1_Code_AzureDevOps. You can use the default name.
<br><img src="./images/repo_import_source.png" /><br>

After successful import you have now an additional entry when you browse your repositories.

After the import the branch "Solution" is selected as default. Make sure you switch to the "main" branch. Otherwise you are missing the objective since you see the alraedy fully implemented solution.

<br><img src="./images/repo_import_sw_branch.png" /><br>

## Recommended way: Adjusting Code (In-place Azure DevOps Repo)

To adjust existing files select the file you want to edit. The screen below shows the resulting situation:
<br><img src="./images/repo_inplace_editing.png" /><br>

Use the "Edit" button at the right-hand side to switch into edit mode. After the first change an additional "Commit" button will appear. Use this button to trigger the commit. Just go with the defaults after being prompted and click "Commit" to confirm.

## Optional: Adjusting Code (Locally in Visual Studio Code)

### Install Git and Visual Studio Code

Follow the installation wizards and use always defaults if being prompted. Visual Studio Code requires the additional installation of the Git extension.

### Clone Azure DevOps repo to visual studio code

When opening a new Window of Visual Studio Code you will see the *Getting Started* page which offers you the option to *Clone Git Repository...*
<br><img src="./images/vc_clone_repo.jpg" width="400"/><br>

To clone the Git repo from Azure DevOps you first need the url. The screenshot below shows the starting point to obtain this url from the Azure DevOps UI:
<br><img src="./images/repo_clone_trigger.png" width="400"/><br>

When you click on this option a new window will open on the top where you can enter your *project url* from Azure DevOps
<br><img src="./images/vc_add_repo_url.PNG" width="400"/><br>

After pressing *Enter*, you will be asked where to store the project on your computer.
<br><img src="./images/vc_select_folder.PNG" width="400"/><br>

After selecting a location, your Project will be copied to your computer and VS Code will offer you in the bottom right to open the cloned project.
<br><img src="./images/vc_open_project.PNG" width="400"/><br>

You can either open the project in the current window or open it in a new window of VS Code.

### Work with Git

In the new window you will now see all files of the projects.

<br><img src="./images/vc_work_in_project.PNG" width="400"/><br>

When you start working in the project, you will notice that the colour of the filenames will change to:

* Green *U* = New File
* Yellow *M*= Changed File
* Red *D*= Removed File
  <br><img src="./images/vc_edit_file.PNG" width="400"/><br>
  The Change of colour shows you that Git has noticed that you changed a file in the project

When you now click again on the *Git symbol* on the left, you can see a list of all changed files.
<br><img src="./images/vc_add_change.PNG" width="400"/><br>

When you select one of the files, Git will show you the difference between the last version of the file and the current file.
<br><img src="./images/vc_changes_in_git.PNG" width="600"/><br>

### Create a Commit

To finally save the changes and add a new version to git you need to make a commit which contains all changed files you want to bundle together. Therefore you need to select the changes you want to add by presseing the **plus** next to the filename. All added files are then displayed in the "Stage" area.

To create a commit which contains all staged files, you need to add a **Commit Message** and press *Enter* 
<br><img src="./images/vc_create_commit.PNG" width="400"/><br>

The *Commit* saves now all the changes made in the files and can be used to revert changes if needed.

### Pushing changes to the Azure DevOps Repo

To save the changes in the cloud we need to push our commits to Github. Therefor you need to click on the three dots **...** in the top right of the git window.
In this Popup you can click in *Push* to upload your changes.
<br><img src="./images/vc_push_changes.PNG" width="400"/><br>

# Glossar

* Commit => Creates a bundle of all changes with a comment of what has been changed. It can be seen of a Snapshot of the project and its always possible to revert changes by jumping back to a older commit 
* Clone => Creates a copy of a remote project repository on your local machine. 
* Fork => Creates a copy of a git project. The copied version can be used to create customizations on a project. Hence the copy is still connected to the original project it is always possible to apply changes and updates into your customized version of the project. In contrast to clone the idea is to start a new separate journey.
* Push => Uploads all changes that have been made on the local project to a remote location (i.e. Github)
* Pull => Downloads all changes that have been made on the remote project since the last pull. This is needed when working with multiple people on one project so you always have the newest version on your local machine.

# More Information

* [Git Handbook](https://guides.github.com/introduction/git-handbook/)
* [Git Cheat Sheet](https://about.gitlab.com/images/press/git-cheat-sheet.pdf)
