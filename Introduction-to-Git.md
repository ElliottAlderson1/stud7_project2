### Git benefits
Track changes, let multi devs work on non linear development.

## Git Architecture

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/e9161cec-e6ca-4177-93bf-ce0530755ff5)


The Git workflow is divided into three states:
- `Working directory` (working tree) - Modify files in your working directory, the sandbox you work in, **changes are marked with a modified flag**, new file or other changes are marked as untracked
- `Staging area` (Index) - Stage the files and add snapshots of them to your staging area, where changes you want for next commit are placed. Moving `untracked` files to staging area, those files become `tracked` and included in Git checkups
- `Git directory` (Repository) - Perform a commit that stores the snapshots permanently to your Git directory. With the `git commit` command you move snapshot of staging are to local repo, saved as a new commit in the currently used branch. **Files not staged are not included in commit**
- `Remote Repository` where files reside, and local copies are pulled from like a local server, GitHub, or BitBucket

## Version Control Process
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/03dd36a3-0f4a-4acb-b47c-1e3c4bde1f29)
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/cf7c9a52-e7bb-4ea8-be9e-b3756e4ffbcf)

- `Add` Moves changes from the working directory to the staging area, lets you prepare a snapshot before committing
  - `git add --dry-run` can test for issues without making changes
- `Commit` Takes the staged snapshot and commits it to the project history
- `Push` lets you move a local branch to another repository, which serves as a convenient way to publish contributions
- `Pull` Pulling is the automated version of git fetch, then immediately merges it into the current branch
- `Fetch` downloads a branch from another repository, along with all of its associated commits and files. it doesn't try to integrate anything into your local repository
- `Merge` integrate changes from divergent branches. After forking the project history with git branch, git merge lets you put it back together again
- `Reset` Undoes changes to files in the working directory

## Git on Windows 
### Git Bash
Application for Microsoft Windows environments which provides an emulation layer for a Git command line experience
### Git GUI
Just about every Git command line function
### Shell Integration
Right-click on a folder in Windows Explorer to access the BASH or GUI

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/b802df2d-a4e9-4428-8bf9-e4cf13ec089f)

