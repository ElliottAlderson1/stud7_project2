You can now write commands specifically for situations that are much more appropriate.

if you want to switch branches than we can use

`git switch develop`
`# same as 'git checkout develop`
`'git switch -c new-branch`
`# same as 'git checkout -b new-branch'`

and also you can use if you restore a file

`git restore README.md`
`# same as 'git checkout -- README.md`
`'git restore --staged README.md`
`# same as 'git reset HEAD README.md'`

## How to undo change in working directory with `checkout`
To discard changes on file in working directory
```bash
git checkout -- Core_Router_1.cfg
```
## How to undo change with staging tree
```bash
git restore --staged Core_Router_1.cfg
```
It says it is not staged for a commit now, and in the working directory if you staged it earlier. Undo the `add` command.

## Ignore File by Git
Create a file named `.gitignore` then add the file you want to ignore like `password.txt` then add and commit the `.gitignore` file.

# Branching
Create a new branch called `development`, and switch to it.
```bash
git branch development
git checkout development
```
Create a new branch with checkout
```bash
git checkout -b bug_fix
```

### Display differences
With this command 
```bash
git diff development..bug_fix```

### Rename branch
Move to branch, and execute this command (new name is the argument here)
```bash
git branch -m build_file_five
```

### Delete a Branch
```bash
git branch -d branch_to_delete
```

