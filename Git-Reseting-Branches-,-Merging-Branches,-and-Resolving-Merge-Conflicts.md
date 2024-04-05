## Adding a Remote
To add a remote to an existing repository.
```bash
git remote add origin
```

## Reset types

- Soft
  - Moves HEAD pointer
  - Does not change staging index
  - Does not change working directory
  - Command:

    ```bash
    git reset --soft <tree-ish>
    ```

- Mixed
  - Moves HEAD pointer
  - Changes staging index to match repository
  - Does not change working directory
  - Command (both do the same thing):

    ```bash
    git reset --mixed <tree-ish>
    ```

    ```bash
    git reset <tree-ish>
    ```

- Hard
  - Moves HEAD pointer
  - Changes staging index to match repository
  - Changes working directory to match repository
  - Command:

    ```bash
    git reset --hard <tree-ish>
    ```

## Commits

The `-am` option combines the `-a` option and the `-m` option. The `-a` option will stage tracked files that have been modified or deleted.
```bash
git commit -am "Commit B: Adds second line"
```

## Performing a soft reset
A soft reset moves the HEAD pointer to a tree-ish location (branch, SHA, relative HEAD location) in the git log.  All changes for that location will be in the staging tree after the soft reset.
```bash
git reset --soft HEAD^
git log --oneline #verify head point with this command
```
This command HEAD^ will go back one commit from current HEAD
```bash
git reset --soft <sha from the git log --oneline>
```
This command sends you to the commit 

## A mixed reset
A mixed reset is the default reset function. It moves the HEAD pointer to a tree-ish location (branch, SHA, relative HEAD location) in the git log.  All changes for that location will be in the working directory after the mixed reset. 

Both sections of code below perform the same function because mixed is the default reset action:
```bash
git reset --mixed HEAD^ #The HEAD^ command goes back one commit from the current HEAD pointer's location
git reset HEAD^ #same thing
```
Send back up with SHA
```bash
git reset <SHA_>
```

## A Hard Reset
A hard reset moves the HEAD pointer to a tree-ish location (branch, SHA, relative HEAD location) in the git log.  All changes for that location will be discarded after the hard reset.
```bash
git reset --hard HEAD^
```
Go back up
```bash
git reset --hard <SHA_>
```

# Merging Branches
### Merge the new_feature branch into the development branch
Switch to `development` branch and view the differences...
```bash
git checkout development
git diff development..new_feature
```
While in `development` merge `new_feature` into it
```bash
git merge new_feature
```
# Resolving Merge Conflicts

```bash
git log --oneline -5
```
add `-5` there to see most recent changes.

Attempt to merge, it will fail and if you `cat file_1.txt` it will show you 
```bash
  This is file 1
  <<<<<<< HEAD
  This is another line
  =======
  This is a new line
  >>>>>>> development
```

The extra lines were added by git when it found a merge conflict.  At this time, we are seeing the changes from both branches in the same file. Everything from `<<<<<< HEAD` to `=======` is in the `master` branch (the branch we are merging into). Everything from `=======` to `>>>>>>>` `development` is in the development branch (the branch we are merging into).

So you want to edit the file (delete either HEAD or other branch's part) and add & commit back up with `git commit -am "Fixes merge conflict"`. Then if you merge it should say they are up to date, you can delete the other branch now.

