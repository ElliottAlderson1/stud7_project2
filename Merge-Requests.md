```bash
git merge
```

### Branches
Branches create isolation, creates a stable environment for development, testing, collaboration, and hotfixes.
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/256078b8-1dc7-4e7f-82ba-4647e772537a)

## Git Merging Strategies
Unless specified, git will chose the most appropriate strategy. 
### Explicit Merges
The **default** merge type. Creates a new merge commit, altering commit history and shows where merge was executed, shoes which commits were parents of merge commit. 
### Implicit Merges
Via rebase or fast forward merge. Does not create a merge commit. It takes a number of commits from specified branch HEAD and put them to the top of the target branch. Triggered by rebase events or fast forward merges
### Squash on Merge
Takes commits from target branch and squashes them into one commit, then applied to the HEAD of the merge base branch. Commit history of the target branch becomes a squashed branch commit when squashed and merged.
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/c987e844-9e8f-4bdb-8ec0-77744672403a)
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/d35588f5-7ce2-4000-9b41-7447410bb250)

#### Recursive
`Recursive` is the default merge strategy when pulling or merging one branch.  
```bash
git merge -s recursive branch1 branch2
```
The `-s` is just for defining strategy.
#### Resolve
`Resolve` two heads using a 3-way merge algorithm. It tries to carefully detect crisscross merge ambiguities and is considered generally safe and fast.
```bash
git merge -s resolve branch1 branch2
```

### Three Way Merges
#### Octopus
Default for more than two heads. If needs manual resolution, octopus will refuse merge attempt. Used for bundling similar feature heads together.


`Octopus` Merge strategy for more than two heads
```bash
git merge -s octopus branch1 branch2 branch3 branch
```
#### Subtree
Extension of recursive strategy. When merging A and B, if B is a child subtree of A, B is first updated to reflect the tree structure of A, This update is also done to the common ancestor tree that is shared between A and B.

## Creating a Merge Request
### Preparing to Merge
#### Confirm the Receiving Branch
#### Fetch Latest Remote Commits
### Merging
#### Fast Forward Merge
A fast-forward merge can occur when there is a linear path from the current branch tip to the target branch. Instead of “actually” merging the branches, all Git has to do to integrate the histories is move (i.e., “fast forward”) the current branch tip up to the target branch tip

### Workflow
Gitlab will show merge request has been submitted. Click `create merge request` to change the merge request. Fill out form, you will get a new merge request form.

## Merge Approvals
If alone, not required to approve. In team, you need to assign an approver, this will require request to be submitted as a Draft. Create rules on a project basis, can be configured to group level. Gitlab offers these buttons for merge request:
- Approve
- Approve Additionally
- Revoke Approval

## Merge Conflicts
Technology cannot decide, when two changes in same line or set of lines in two different commits. Also when a file was modified in one and deleted in another.
#### Undo a Conflict
You can always undo with the commands
```bash
git merge -abort
git rebase -abort
```

#### Solve a Conflict
Three ways to resolve:
1. Accept the Local version
2. Accept the remote version
3. Review Changes Individually
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/f09e4fd5-e449-493a-a5e2-c00a049078e2)

- Separator characters
```git
 <<<<<<<  HEAD (current branch)
 ======= Conflict dividers
 >>>>>>> (merging branch)
```

```bash
git log --merge
```

## Pull Remote Repository
```bash
git switch main
git pull
```
![image](https://github.com/dpweldo/DEVOTC/assets/102386243/a1cfd7fc-5d89-452a-89ce-1c92e0811489)

#### Git Pull
When using git pull, only the current working branch is affected. This means whatever the latest changes are done in the remote repository, it gets downloaded automatically and clubbed together in the local repository. So other branches remain as it is without getting affected.

#### Git Fetch
Used to extract information of last updated commits, included branches and files from its remote repository with its related objects. This command of git is specially used to rebuild the previous history of the specific branch in which you have to do changes

it doesn’t affect your local repository. So, it only downloads new data from the remote repository. Fetch is used to protect your latest code from the problem of a merge conflict. It is the best way to use git fetch with git merge on pulled code

![image](https://github.com/dpweldo/DEVOTC/assets/102386243/280da66f-b849-46bf-a238-333bee061638)
