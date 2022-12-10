# Content
* [Flow](#flow)
    * [Workflow](#general-worflow)
* [Merge Conflicts](#merge-conflicts)
* [Commit Guidelines](#commit-guidelines)
* [Extra](#extra)

# Flow
* We will have several branches in version control.
* There will be a "**main**" branch which will always have the latest working state of project.
* Rest all the work will be done in branches forked out from "main" and will be merged to "main" branch once the work (for which branch is created) is complete and it is working with rest of the project.
* All the branches will always be update from "main" branch as we are building upon what is already present in "main" brach.
* ### General worflow:
    1. Create a branch when you start working from main branch.
    1. Daily pull updates from main branch.
    1. Once your work is done, Again pull from main branch for latest changes.
    1. Check whether anything is crashed (not working).
    1. Inform heads. It will be checked finally and merged with the main branch.

# Merge Conflicts
* Merge conflicts occur when multiple members have changed same file or while merging two branches with same file modified.
* To resolve merge conflicts, here are some resources:
    * Plastic SCM
        * [Unity Doc on Plastic SCM](https://docs.unity3d.com/2017.3/Documentation/Manual/plasticSCMIntegration.html)
    * Git
        * [Command line](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)
        * [Video resource](https://www.youtube.com/watch?v=xNVM5UxlFSA)

# Commit Guidelines
* Write a commit message which summarize the work you are commiting. Limit of commit message in git is 50 characters.
* A commit should be Small & limited to as few files as possible in order to be able to keep the changes and scope limited. Put some thought into isolating ongoing work clearly from existing project state.
* Always commit relevant META files of changes for a file in Unity Project
* Strictly limit files in a commit to the scope of work at hand. Unity can often change state of unwanted and unrelated files and generate/modify META for them. These aren't necessarily to be part of project and hence don't need to be added to repo.
* Review all the files that are actually part of the scope of work directly or indirectly and only commit their changes. If we commit something that references uncommitted changes/files , it
can break the project state and lead to script compile errors. Understanding the scope & nature of work and what all parts of the project are to be modified is crucial.
* No files are ever deleted from workspace/repo. So don't add useless files with thinking you can delete it in future. Those can be deleted from branch you are working on but it will be stored on cloud. It may bloat the size of repo.


# Remarks
* Github has [branch locking](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches) feature. Locked branch will accept changes from allowed members and rest of the members can pull request to request change in a locked branch. This can reduce the chance of crashing the project in main branch.
* Plastic SCM has [file locking](https://docs.unity3d.com/2017.3/Documentation/Manual/plasticSCMIntegration.html) feature, i.e., you can lock a file you are working on and no one else can edit that file and commit in that time. This will reduce merge conflicts.
* [Here](https://drive.google.com/file/d/1DI4Y1j0AMVGryiKq6QyhHoTO4bO5Yuak/view?usp=share_link) is a cheat sheet with some common commands of Git.