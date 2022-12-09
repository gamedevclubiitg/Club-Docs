# Overview
* Primary goal of using version control is to keep versions of project. example, you don't have to give names car1, car2, carfinal for different version of same file.
* Also it is used to collaborate multiple members on same project. One can synchronize its work, or work separately and merge with other work.


# Plastic SCM
A distributed version control with strong merging, great GUIs and support for huge files. Plastic SCM is a distributed version control designed for big projects It excels on branching and merging, graphical user interfaces, and can also deal with large files and even file-locking (great for game devs).
## Setup
1. Install "Version Control" package in unity.
1. Download and Install "Plastic SCM - Cloud Edition".
1. Sign Up using your Unity ID.
1. Don't try to create organization as it is banned in India.
## Create Workspace
1. Open Plastic SCM window by clicking on Plastic SCM button in top left of UNITY. Alternatively, you open from Window tab -> Plastic SCM.
1. Click on "Create Workspace".
1. Click on "new", then Select Organization and Repo Name.
1. Select "Plastic workspace" in "How do you prefer?" section. 
1. Click on "Create Workspace". Your workspace is now created and uploaded on cloud.

## Join Workspace
1. Open Plastic SCM software.
1. Go to home screen and select organization which contains the required repository.
1. You will find the project in the left panel. Download the project at your desired location.
1. Open the project in unity hub. (I will not be already there. You will have to click Open button in top right of unity hub and then browse to the project folder you just downloaded.)
<br><br>

# Git
Fast, scalable, distributed revision control system. Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

## Setup
1. Install Git.
1. You can use Terminal / Github Desktop / Sourcetree for further process. 
1. Using Terminal (Git bash in Windows) here.
1. Configure your name and email on git which will dispalyed in your commits.
    ```
    git config --global user.name "Your Name"
    git config --global user.email "youremail@yourdomain.com"
    ```

## Create Repository
1. Browse inside the project in terminal. Then run following command in terminal to initialize the git repository.
    ```
    echo "# some text" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    ```
1. Rename "master" branch to "main".
    ```
    git branch -M main
    ```
1. Create new repository on github.
1. Link remote repo (acronym for repository) to local repo.
    ```
    git remote add origin repo_link
    ```
1. Push current changes to remote repo.
    ```
    git push -u origin main
    ```

## Join Repository
1. Accept the invitation from the owner.
1. Clone Repo to your local system. Browse to the location where you want copy project in terminal. Then run following command in terminal and paste ssh link of repo in place of repo_link.
    ```
    git clone repo_link
    ```
1. Open the project in unity hub. (I will not be already there. You will have to click Open button in top right of unity hub and then browse to the project folder you just downloaded.)
<br>

## SSH Key Authentication
1. Use following commands to generate SSH key.
    ```
    ssh-keygen -t rsa -b 4096 -C "your_email@gmail.com"
    eval $(ssh-agent -s)
    ssh-add ~/.ssh/id_rsa
    tail ~/.ssh/id_rsa.pub
    ```
1. After running last command, you will get SSH key. Copy it.
1. In Setting of your repository on github, Open "GPG and SSH keys".
1. Select "Add SSH key".
1. Paste SSH key you had copied and give a name in the title section.
1. Save the key.

```
git lfs install
```