# Git Cheat Sheet
Tags: #cheatsheet, #git, #pull, #push, #branch, #commit, #merge, #remote <br>
Related: [[]] <br>

Todo: reverting merges, git stashes, unstaging commits, reverting to remote head, git messages,

## What is git?
Git is a version control system created by Linus Torvalds in 2005. It allows you as a developer to track your changes in a scope of files and organise multiple "branches" of files. Beyond just development, git has proved to be a simple and effective tool I have used in my personal life to keep track of my wallpapers and some documents/notes. 

### Basic Git Flow Explanation
We'll go through the specific terms in the next stage, but first we'll outline the most simple procedure for how git works. Imagine git is a professional gift wrapper at their workstation. When new gifts come in, you wrap them and send them to the recipient. Similarly, when code changes are made, you send them to git's work station by the command `git add`. The gift wrapper's work station is called the 'staging area' in git. When you `git commit`, these changes are packaged by git and are ready to be delivered to the recipient. In our case, the recipient is often the repo on your cloud host (Github, Gitlab, Bitbucket).

### Summarised Basic Git Flow
code changed -> changes added to staging area -> committing staged changes -> commits pushed to remote

## Terminology
`repository` or repo is a folder defining the scope of your git changes. All this means is that you can track the changes for any files within this folder, and we refer to this root folder as a repo. 

`branch` is a certain timeline of changes. You often begin a repo on main (in the old days it would be master) branch. Different branches can be considered kind of as "parallel timelines", containing the same product but in different versions. Branches are used to allow multiple people to work on the same project while not interfering with each other unless necessary. 

`remote` is the term used to refer to the cloud resource which your code is synced to. As an example, the github repo which is accessible on github is the remote repo and the folder you interact with after cloning it is the local repo. Your remote is often called `origin`, and is not affected unless you `push` some changes to it.

`merge` is what you do when you want to combine the changes from one branch into another. This does not affect the source branch, only copies all the changes to the destination. 

`pull request` is a request you make in order to merge a source branch to a destination branch. This is a feature offered in git hosts as opposed to git itself and should always be used instead of merging because it provides a chance to describe the changes and have the merge request be reviewed by peers. 

`merge conflicts` are when you are attempting to merge two branches, however there are some changes where git cannot determine which is correct. Let's consider the src and dst branch. Now if the src branch is branched from the dst but the dst has had changes since the branch, when merging src into dst git will not know if the current dst information is 'correct' or the incoming src information is. Don't worry though, if this happens you just open your file and upon seeing both versions of the conflict you choose one of the segments to keep. 

`fork` is where within a git host you create a copy of an existing, however it has a link to the repo it was forked from. This is useful because if 1000 people were working on the same repo and each had 1 branch, there would be far too many branches to maintain. Instead individuals can have their own forks of the original repo and pull or push from the original. The original repo can be added as a remote to your local repo, but instead of 'origin' it is typically called 'upstream'.

## Commands

> git add

Adds a single file, or multiple files separated by a space to the staging area of the local git directory.

`git add .` adds everything in the current folder to the staging areal. Because `.` is the symbol for current directory. Multiple files can be added in this fashion: `git add index.html index.css`.

> git commit

Commits the staging area to a "package" of changes ready to be pushed to the destination. Pass in a meaningful commit message used to summarise which changes you are committing. 

> git push

Pushes all local commits to the remote repository. 

`git push -u origin [BRANCH NAME]` initialises a new branch at the origin. 

`git push origin [BRANCH NAME]` pushes to a specified branch at origin. 

> git branch

Creates a new branch with the specified name but does not switch to it. 

`git branch -d [BRANCH NAME]` can be used to delete a specific branch, should do this from another branch. 

`git branch` by itself lists all available local branches. 
`git branch <new-branch> <base-branch>`

> git checkout

Switches to another branch that has already been created.

`git checkout -b [BRANCH NAME]` creates a new branch with the specified name AND switches to the new branch.

> git clone

Clones a repository from GitHub using the URL found within the repository on Github.com

This "downloads" the repo from GitHub as a local directory and initialises the directory as a git folder. **You want to be inside this downloaded directory to be able to perform other git actions such as `add`, `commit` and `push`.**

## Commit Message Etiquette