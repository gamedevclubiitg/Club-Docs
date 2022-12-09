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
1. Mergetool : Git may be able to automatically merge some changes made by different developers to .scene and .prefab files. But don't despair if you're still seeing merge conflicts: Unity ships with a Git-compatible merge tool named SmartMerge. 

    To enable SmartMerge, you'll need to add the following snippet to your Git config. For just one repository, add it to the .git/config file in the top-level directory of your repository. To enable SmartMerge for all repositories on your system, you'll need to add it to your global Git configuration. Locations vary, it's usually ~/.gitconfig on MacOS and Linux, but you can simply run git config --global -e to open it in your system editor.  
    
    * Windows : 
        ```
        [mergetool "unity_yaml"]
        cmd = 'C:/Program Files/Unity/Editor/Data/Tools/UnityYAMLMerge.exe' merge -p "$BASE" "$REMOTE" "$LOCAL" "$MERGED"
        trustExitCode = false
        keepTemporaries = true
        keepBackup = false
        
        [merge]
        tool = unity_yaml
        ```
    
    * Mac : 
        ```
        [mergetool "unity_yaml"]
        cmd = '/Applications/Unity/Unity.app/Contents/Tools/UnityYAMLMerge' merge -p "$BASE" "$REMOTE" "$LOCAL" "$MERGED"
        trustExitCode = false
        keepTemporaries = true
        keepBackup = false
        
        [merge]
        tool = unity_yaml
        ```
    

1. Generate and Add SSH key to github as shown below.

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

## Create Repository
1. Browse inside the project in terminal. Then run following command in terminal to initialize the git repository.
    ```
    echo "# some text" >> README.md
    git init
    ```
1. Add .gitignore and .gitattributes file.
    ```
    touch .gitignore
    touch .gitattributes
    ```
1. Open .gitignore and add following text into it.
    ```
    # Created by https://www.toptal.com/developers/gitignore/api/unity
    # Edit at https://www.toptal.com/developers/gitignore?templates=unity

    ### Unity ###
    # This .gitignore file should be placed at the root of your Unity project directory
    #
    # Get latest from https://github.com/github/gitignore/blob/main/Unity.gitignore
    /[Ll]ibrary/
    /[Tt]emp/
    /[Oo]bj/
    /[Bb]uild/
    /[Bb]uilds/
    /[Ll]ogs/
    /[Uu]ser[Ss]ettings/

    # MemoryCaptures can get excessive in size.
    # They also could contain extremely sensitive data
    /[Mm]emoryCaptures/

    # Recordings can get excessive in size
    /[Rr]ecordings/

    # Uncomment this line if you wish to ignore the asset store tools plugin
    # /[Aa]ssets/AssetStoreTools*

    # Autogenerated Jetbrains Rider plugin
    /[Aa]ssets/Plugins/Editor/JetBrains*

    # Visual Studio or VSCode cache directory
    .vs/
    .vscode/

    # Gradle cache directory
    .gradle/

    # Autogenerated VS/MD/Consulo solution and project files
    ExportedObj/
    .consulo/
    *.csproj
    *.unityproj
    *.sln
    *.suo
    *.tmp
    *.user
    *.userprefs
    *.pidb
    *.booproj
    *.svd
    *.pdb
    *.mdb
    *.opendb
    *.VC.db

    # Unity3D generated meta files
    *.pidb.meta
    *.pdb.meta
    *.mdb.meta

    # Unity3D generated file on crash reports
    sysinfo.txt

    # Builds
    *.apk
    *.aab
    *.unitypackage
    *.app

    # Crashlytics generated file
    crashlytics-build.properties

    # Packed Addressables
    /[Aa]ssets/[Aa]ddressable[Aa]ssets[Dd]ata/*/*.bin*

    # Temporary auto-generated Android Assets
    /[Aa]ssets/[Ss]treamingAssets/aa.meta
    /[Aa]ssets/[Ss]treamingAssets/aa/*

    # End of https://www.toptal.com/developers/gitignore/api/unity

    # Created by https://www.toptal.com/developers/gitignore/api/windows,osx,linux
    # Edit at https://www.toptal.com/developers/gitignore?templates=windows,osx,linux

    ### Windows ###
    # Windows thumbnail cache files
    Thumbs.db
    Thumbs.db:encryptable
    ehthumbs.db
    ehthumbs_vista.db

    # Dump file
    *.stackdump

    # Folder config file
    [Dd]esktop.ini

    # Recycle Bin used on file shares
    $RECYCLE.BIN/

    # Windows Installer files
    *.cab
    *.msi
    *.msix
    *.msm
    *.msp

    # Windows shortcuts
    *.lnk

    # End of https://www.toptal.com/developers/gitignore/api/windows,osx,linux
    ```
1. Open .gitattributes and add following text into it.
    ```
    ## Unity ##

    *.cs diff=csharp text
    *.cginc text
    *.shader text

    *.mat merge=unityyamlmerge eol=lf
    *.anim merge=unityyamlmerge eol=lf
    *.unity merge=unityyamlmerge eol=lf
    *.prefab merge=unityyamlmerge eol=lf
    *.physicsMaterial2D merge=unityyamlmerge eol=lf
    *.physicMaterial merge=unityyamlmerge eol=lf
    *.asset merge=unityyamlmerge eol=lf
    *.meta merge=unityyamlmerge eol=lf
    *.controller merge=unityyamlmerge eol=lf


    ## git-lfs ##

    #Image
    *.jpg filter=lfs diff=lfs merge=lfs -text
    *.jpeg filter=lfs diff=lfs merge=lfs -text
    *.png filter=lfs diff=lfs merge=lfs -text
    *.gif filter=lfs diff=lfs merge=lfs -text
    *.psd filter=lfs diff=lfs merge=lfs -text
    *.ai filter=lfs diff=lfs merge=lfs -text

    #Audio
    *.mp3 filter=lfs diff=lfs merge=lfs -text
    *.wav filter=lfs diff=lfs merge=lfs -text
    *.ogg filter=lfs diff=lfs merge=lfs -text

    #Video
    *.mp4 filter=lfs diff=lfs merge=lfs -text
    *.mov filter=lfs diff=lfs merge=lfs -text

    #3D Object
    *.FBX filter=lfs diff=lfs merge=lfs -text
    *.fbx filter=lfs diff=lfs merge=lfs -text
    *.blend filter=lfs diff=lfs merge=lfs -text
    *.obj filter=lfs diff=lfs merge=lfs -text

    #ETC
    *.a filter=lfs diff=lfs merge=lfs -text
    *.exr filter=lfs diff=lfs merge=lfs -text
    *.tga filter=lfs diff=lfs merge=lfs -text
    *.pdf filter=lfs diff=lfs merge=lfs -text
    *.zip filter=lfs diff=lfs merge=lfs -text
    *.dll filter=lfs diff=lfs merge=lfs -text
    *.unitypackage filter=lfs diff=lfs merge=lfs -text
    *.aif filter=lfs diff=lfs merge=lfs -text
    *.ttf filter=lfs diff=lfs merge=lfs -text
    *.rns filter=lfs diff=lfs merge=lfs -text
    *.reason filter=lfs diff=lfs merge=lfs -text
    *.lxo filter=lfs diff=lfs merge=lfs -text
    ```
1. Stage all unstaged files.
    ```
    git add .
    ```
1. Also, you can Stage any file as following.
    ```
    git add file_name
    ```
1. Commit all the staged files.
    ```
    git commit -m "first commit"
    ```
1. Rename "master" branch to "main".
    ```
    git branch -M main
    ```
1. Create new repository on github. Don't add any license or readme file. Only set name, description (optional), scope (public/private).

1. Link remote repo (acronym for repository) to local repo.
    ```
    git remote add origin repo_link
    ```
1. Push current changes to remote repo.
    ```
    git push -u origin main
    ```
1. Initialize Git LFS.
    ```
    git lfs install
    ```

## Join Repository
1. Accept the invitation from the owner.
1. Clone Repo to your local system. Browse to the location where you want copy project in terminal. Then run following command in terminal and paste ssh link of repo in place of repo_link.
    ```
    git clone repo_link
    ```
1. Initialize Git LFS.
    ```
    git lfs install
    ```
1. Open the project in unity hub. (I will not be already there. You will have to click Open button in top right of unity hub and then browse to the project folder you just downloaded.)
<br>

