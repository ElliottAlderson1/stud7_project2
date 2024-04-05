# Notes for Git lab

The minimum role to create an issue is a Guest.

## How do you connect a local Git repo to a remote repository your team has set up in GitHub, GitLab or Bitbucket?

There are two ways to push a local project to a remote Git repo: the recommended way, which is somewhat convoluted, and my easy sort-of-cheating way, which is much easier.

- The recommended way is to use the `git remote add origin` command.
- The easy way is to clone the remote repo, followed by a bit of copy and pasting.

We'll cover both approaches in this git remote add origin tutorial and let you decide which option suits you the best.

The simple method is described at the end of this article, so please don't click away before checking it out. It might make your Git journey a lot easier.

## Simple git remote add origin use

The `git remote add origin` command works best under the following two conditions:

- The remote repository has no Git commit history.
- The remote repository has absolutely no files in it.

Let's start this git remote add origin tutorial with a happy assumption that both conditions are true.

## How to use Git's remote add origin command

The steps to add a local project to a remote repo with the git remote add origin command are as follows:

1. Use git init to create a new local repository.
2. Add files and perform a git commit.
3. Obtain the Git URL of the remote repo.
4. Issue the git remote add origin command.
5. Use the git push command to upload your files.

### Step 1: Create a local Git repo

To connect a new project to a remote Git repository, you must create a Git repo locally, add files and perform at least one commit. The terminal window commands to do this are as follows:

```bash
git init
git touch alpha.txt
git add alpha.txt
git commit -m "Git commit history created"
```

These commands create a local Git repository that includes one file and one commit.

### Step 2: Add a reference to the remote repo

To connect this new project to a repo on a remote hosting service such as GitHub, GitLab or Bitbucket, obtain the Git URL of the remote repository and issue the following command:

```bash
git remote add origin https://github.com/cameronmcnz/remote-repo-url.git
```
This adds a reference to the remote server in your local project.

![alt text](figure1-h.jpg)

### Step 3: Push your changes to the server

After the remote reference is configured, you can transfer your local files to the server with the `git push` command.

```bash
git push -u origin master
```

When this command completes, the files in your local repository, along with your branch's full commit history, are pushed up to the remote server.

This example assumes you created the local repository with a branch named "master," which is still the current default for Git. This creates a new branch on the server named "master" as well.

![alt text](figure2-h.jpg)

## Collaborative Git operations

That's how easy it is to use the `git remote add origin` command when there is no commit history on the remote server.

After you add the remote server to your local Git installation, you can perform future push, pull and fetch operations normally.

- git push origin sends your local updates to the remote server.
- git pull pulls updates down from the local server and updates your workspace.
- git fetch pulls updates down from the local server without updating your workspace.

## Use main, not master

Locally installed Git software defaults to master for the primary branch name when it is created in a new repository.

However, GitHub, GitLab and Bitbucket have all moved away from master and use the name main instead. You should too.

To rename your local master branch to main and push the main branch after the `git remote add origin` command runs, follow these steps:

```bash
git branch -M main
git remote add origin https://github.com/scrumtuous/repos-git-url.git
git push -u origin main
```

## What if the remote repo isn't empty?

If the remote repo isn't empty, connecting to a remote Git repository becomes a bit more complicated.

If you push your new Git repo to a remote repository with an existing commit history, you will encounter the "failed to push some refs to remote" error.

One way to resolve this problem is to push with force, which is coded as git push --force or git push -f, but this is a dangerous operation if others are also working with the remote repository. A better option is to rebase, which preserves the Git commit history.

![alt text](figure3-h.jpg)

## Push to origin with force

A push with force to the recently added remote origin server looks like the following:

```bash
git branch -M main
git remote add origin https://github.com/scrumtuous/repos-git-url.git
```

```bash
git push -u -f origin main
```

Again, if others on your team cloned this repo, problems will occur the next time they go to fetch or pull updates because the entire commit history on the main branch will have been rewritten.

If you're the only one working in this repo you'll be fine, but if the repo has been shared a rebase and push will be required.
Safely rebase and push a new project

To safely push an existing project to a remote Git repo that isn't empty, complete the following steps:

- Run the git remote add origin command.
- Perform a git pull.
- Rebase your local branch onto the pulled branch.
- Push your rebased files back to the server.
- Delete your old local branches.

The following commands assume your local branch is named master and the remote branch is named main. When performed, divergent Git commit histories are safely combined and a push to origin does not require force.

```bash

git remote add origin https://github.com/example/repo-git-url.git
git pull origin
git switch master
git rebase main
git push origin
git branch -d main
```

## Commands references

```bash
git config --global user.name "John Doe"
git config --global user.email "your_email_address@example.com"
git config --global --list
git init
git add . 
git commit -m "message"
git --version
git branch --set-upstream-to=origin/main main
git push --allow-urelated-histories #If you are still getting the error with histories
git status
git clone git@gitlab.com:gitlab-tests/sample-project.git
git show HEAD
git log --oneline -3
```