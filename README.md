# git-forever

My notes on Git and GitHub basics from 2020, kept as a reference. They walk through setting up Git, the everyday commands and a short cheatsheet at the end.

The step-by-step part is based on Asabeneh Yetayeh's [Git-and-Github](https://github.com/Asabeneh/Git-and-Github) guide.

A few things have changed since I wrote this:

- GitHub now names the default branch `main`. If your repository uses `main`, replace `master` with `main` in the commands below.
- Newer Git versions also have `git switch` (change branches) and `git restore` (undo changes). The older `git checkout` and `git reset` commands below still work.

## What is version control?

Version control keeps a history of every change to a set of files. If something breaks, you can go back to an earlier version, compare it with the current one and see who changed what.

## Git

Git is a version control tool. It runs on your own machine and tracks changes in a project folder (a repository).

## GitHub

GitHub is a website that hosts Git repositories. You use it to keep your projects online and to work on them with other people.

## 1. Install Git and sign up on GitHub

- Git: install [Git](https://git-scm.com/downloads)
- GitHub: sign up on [GitHub](https://github.com/signup)

## 2. Configure your name and email

```shell
git config --global user.name 'yourname'
git config --global user.email 'youremail'
```

## 3. Create a local Git repository

A local repository is a project folder on your computer. Open a terminal (on Windows, Git Bash) and run:

```shell
mkdir project_name
cd project_name
```

## 4. Initialize Git

Inside a new or existing project folder, initialize the repository:

```shell
git init
```

Once the repository is initialized, Git tracks changes to the files and folders in it.

## 5. Add files to the staging area

To add a single file:

```shell
git add filename
```

To add multiple files:

```shell
git add filename1 filename2
```

To add all files and folders at once:

```shell
git add .
```

## 6. Unstage a file

```shell
git reset HEAD filename
```

## 7. Commit the changes

A commit is a snapshot of your files at that point in time.

```shell
git commit -m 'your message'
```

The commit message should describe the change you made.

## 8. Create a branch

A branch is a copy of the project at the moment you create it. Say you have a working application and want to add a feature without touching the working version: create a branch, build the feature there, and merge it back when it's done. You can create as many branches as you want.

To only create a branch:

```shell
git branch branchname
```

To create a branch and switch to it at the same time:

```shell
git checkout -b branchname
```

To switch between branches:

```shell
git checkout master
git checkout branchname
```

To list all branches:

```shell
git branch
```

## 9. Create a repository on GitHub

Go to [GitHub](https://github.com/) and create a repository by clicking the plus icon in the top right corner.

## 10. Connect your local repository to GitHub

This connects your local repository with the remote one on GitHub:

```shell
git remote add origin remote_repository_url
```

`origin` is just a name for the remote URL. You could use any word, but `origin` is the convention. If this step runs without errors, you are ready to push.

## 11. Push

Commit your changes, then push them to the remote repository:

```shell
git push -u origin master
```

## 12. Merge

In most projects you will have several branches, for example `master`, `develop` and feature branches. Feature branches get merged into `develop`, and `develop` gets merged into `master`. You can merge any branch into any other. For example, to merge a `feature` branch into `develop`:

```shell
git checkout develop
git merge feature
```

## 13. Pull

If your team has merged new work into `develop`, your branch is behind. Pull the latest `develop` into your branch, then merge your branch back:

```shell
git checkout yourbranch
git pull origin develop
git checkout develop
git merge yourbranch
git push -u origin develop
```

## Git cheatsheet

Basic Git commands that come up often:

```shell
git --version                 # check the installed version
git help                      # general help
git help commit               # help for a specific command

git init                      # initialize a repository on your machine

git config --list             # show the current configuration
git config --global user.name "username"   # set your user name
git config --global user.email "email"     # set your email

git add first.txt             # stage one file
git add second.txt third.txt  # stage multiple files
git add .                     # stage all files and folders

git commit -m 'commit message'      # commit staged changes
git commit -a -m 'commit message'   # stage tracked files and commit
git commit -am 'commit message'     # same as above, shorter

git log                       # show the commit history
git log --author="name"       # show commits by a specific author
git status                    # show the state of your files

git diff                      # compare the working copy with the staging area
git diff --staged             # compare the staging area with the last commit

git rm filename               # delete a file and stage the deletion
git mv filename1 filename2    # rename a file
git mv filename foldername/filename2   # move a file into a folder

git checkout -- filename      # throw away changes in the working copy
git reset HEAD filename       # remove a file from the staging area
git checkout 01e7ba -- filename   # get a file as it was in commit 01e7ba

git remote add anyname repositoryUrl   # add a remote
git push -u origin master     # push to GitHub
```
