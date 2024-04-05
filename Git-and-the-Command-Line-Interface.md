## Installing Git
For Windows download latest
- https://github.com/git-for-windows/git/releases/

For Linux
- RHEL and derivatives typically include older versions of git
- All others follow the instructions on 
 - https://git-scm.com/download/linux

To verify installation
~~~shell
git --version
~~~

To update an existing windows installation
~~~shell
git  --update
~~~

## Git User Variables
You have to assign two global variables.

~~~shell
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
~~~
You can also use
~~~shell
user.signingkey
core.excludesfile
help.autocorrect
~~~
#### Verify configuration
~~~shell
git config --list
~~~
#### SSH options
If cloning with https, you may need to disable SSL certificate (very rare)
~~~shell
git config --global https.sslverify false
~~~
## The Command Line
Options come first and then arguments
- argument can be misunderstood as either a revision or a path
~~~shell
git diff -- HEAD
git diff HEAD --
~~~
Many commands allow wildcards in paths
~~~shell
$ git restore *.c
$ git restore \*.c
~~~

~~~bash
git restore #restore working tree file
~~~

## Performing Version Control Tasks
Initialize a project
~~~bash
git init
~~~
It starts with a single branch called "master"/"main" along with the `git` file added.

Or you can create a clone
~~~bash
git clone git@https://10.10.41.10/ron/repo
~~~

### Tracking in Git 
Prevent mistakes, understand evolution, collaborate more.

- `git diff` compares changes by comparing the current working directory and the last commit, or between any two commits
- `git log` shows the commit history for your repository, including the author, date, and commit message (`-n` #  to show specific # of lines)
- `git blame` shows the revision history for a file, along with the author and date of each change
- `git status` shows the current status of your repository, including which files have been modified, which changes have been staged, and which files are untracked

### Committing Changes
Basic steps for committing changes in git:

1. Make changes to files in your local Git repository
2. `git add` command to stage the changes you want to include in your next commit (use `.` for all)
3. `git commit` command to create a new commit (`-m` to add the comment)
4. Provide a Git commit message 
~~~ shell
git add test.txt 
 git add .
git commit -m  "first commit“
~~~

#### Commit Messages
- First line limited to 50 characters followed by a blank line and a more detailed description of the changes
- Use the imperative mood ("Add feature" instead of "Added feature") 
- Use bullet points for multiple changes
- Provide context to help other developers understand changes
- Refer to relevant issues or tickets

Commits are permanent but can be amended if needed

### Undo Staged Changes - Git  Reset
Undo changes yet to be committed.
1. Navigate to the repository that contains the changes you want to unstage
2. `git status` to see which changes are staged
3. `git reset` to unstage all changes or `git reset` followed by the name of the file(s)  you want to unstage (ex `git reset filename`)
4. `git status` command again to see which changes have been unstaged.

`git restore` may be needed to place the file back in the working tree/directory

### Undo Commits (Reset)
Move back for soft, mixed, or hard reset.
1. Navigate to the repository containing the commit to reset
2. `git log` to copy the commit hash for the state to reset to
3. `git reset` followed by the type of reset and the commit hash


**Soft reset**: resets to the previous commit but keeps the changes in the working directory. 
~~~bash
git reset --soft [commit hash]
~~~

**Mixed reset**: This resets the repository to the previous commit, and removes the changes from the staging area, but keeps them in the working directory. This is the default reset type if you don't specify a type.
~~~bash
git reset --mixed [commit hash]
~~~

**Hard reset**: This resets the repository to the previous commit and removes all changes from the staging area and the working directory.
~~~bash
git reset --hard [commit hash]
~~~

### Undo Commits - Revert
A reset moves the head back, a revert creates a new commit and undoes the changes like a reset

1. Navigate to the repository containing the commit to revert
2. `git log` to copy the commit hash for the state to revert to
3. `git revert` followed by the commit hash you want to revert to
4. Provide a Git commit message 

## Version Control Tasks
### Branching
Create independent lines of development in a repository

1. Navigate to the directory that contains the “master” branch
2. `git branch` and the name of the new branch (ex. `git branch development`)
3. `git branch` to see verify branch was created in the repository
4. `git checkout development` to switch to the new branch

### Merging Branches
Combine changes in one branch into another branch.

1. Navigate to the repository you want to merge changes into
2. `git branch` and ensure you are on the branch that you want to merge changes into
3. `git merge` followed by the name of the branch you want to merge changes from (ex `git merge [development]`) 
4. Git will prompt you to resolve conflicts manually

`git mergetool` to run one of several merge utilities to resolve merge conflicts
`Git log [--oneline]` View current and prior commits and comments

## Git Options
Each command has its own arguments and options.
~~~bash
git add  [--patch | -p] 
y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help
~~~

## Git Help

`git help git` for an overview of the system.
`git help –g` displays the concept guides


`git help` syntax
~~~bash
git help [-a|--all]
~~~
Prints all the available commands on the standard output
~~~bash
git help [-m | --man]
~~~
Display manual page for the command in the `man` format.


## Renaming, Moving, and Deleting files with Git
Rename with `git mv` command.
~~~bash
git mv router_1.cfg Core_Router_1.cfg
~~~
Or move to a new directory.
~~~bash
git mv router_2.cfg backup_configs/router_2.cfg
~~~
Remove with the `git rm` command.
~~~bash
git rm router_3.cfg
~~~