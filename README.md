


# Git Tutorial 
## Maya Gonzalez
### Background

So you just finished yout coding project and now we would like to show off your talent and hardwork by publishing it to the public. We will accomplish this using Git, a version control system, that allows us to track changes to files. Git is great because it allows us to methodically track any changes we make to this project. Git can tell us when, who, and why a change was made. Imagine I wanted to make some changes to your project, or you were working with a partner and needed to merge your edits together.

*Let's begin!*

Let’s start in the terminal. You can seach ‘terminal’ on a Mac or ‘cmd’ on a Windows computer. Once in the terminal, we want to navigate to a location where we can work out of. For the sake of simplicity, let’s work out of a special folder on our Desktop.

To change the directory, type the following commands\
```> cd desktop```\
```> ls```\

The ls command lists files within this Desktop directory. Create a new folder for this project while in the Desktop directory.
```> mkdir git-tutorial```

This folder is known as our working directory. We just created a new folder within our current Desktop directory, but we now want to change the directory to the new folder.
`> cd git-tutorial`

We are now going to start a new repository. The following command creates a .git file within our current directory or folder, which allows us to track all the changes made to this project from our working directory.
`> git init`

We’ll now clone an existing repository, which allows us to get the latest version of this existing repo into our working directory. Any updates made to the existing repo will not be reflected in our working directory after we use this clone command, unless any additional measures are taken.
`> Git clone https://github.com/Maya-Gonzalez/git-example2`

We just cloned a repository but have not changed our current directory. Let’s try looking at the new contents within our current directory
`> ls`
`> cd git-example2`
`> ls`

Now you can see all the file that originated from the repo we just cloned. Very cool! Not quite magic, but very close.

Let’s view the status of this project
`> git status`

The message should let us know what branch we are on, in this case it should be master, and a message saying that our branch is up to date with ‘origin/master’. This brings us to a major topic of branches.

## Branches
You can think of branches in Git as the branches of a tree. Branches allows us to continue editing and developing an aspect of a project without necessarily affecting the main project, similarly to how a tree branch diverges from the main tree trunk. The master branch is the primary branch in Git, and can be thought of as the tree trunk. Say you are working on a feature and need to decide if your or your team wants to eventually incorporate it into the larger project. Creating and working from a branch is a good method for this situation.
### Creating a New Branch
Creating a new branch essentially creates a reference to the current state of the repo.
`> Git branch development`

The command simply created a new branch, but we are still on the master branch. It is useful to know what branch you are currently on, luckily git keeps track of this information through a special pointer known as HEAD. We can check what branch we are on through the git log command
`> git log`
![Head Pointer](https://static.javatpoint.com/tutorial/git/images/git-log-4.png)
### Switching Branches
In order to change the branch we are currently on, we need to execute the following command. Likewise, this will change where the HEAD pointer is pointing to, from the master branch to our new branch development
`> git checkout development`
A message should now let us know that we have switched to this branch.
### Making Changes
To demonstrate how we can utilize our new knowledge, let’s try to make some changes to our development branch and see what happens. We’ll make a new file.
`> nano newfile.txt`

We are working out of our working tree, which basically stores only the files on the computer. Here we can view and modify files. With the following command, we can now move this file into the staging area.
`> git add newfile.txt`

Adding a new file moves the file from our working tree into the staging area. The staging area stores changes and files that are ready to be committed. Both the working tree and the staging area have no effect on either the local or remote repositories until we made a commit and push, respectively. Let’s check how this new file addition affected our working directory.
`> git status`

We’ll see what branch we’re currently on and any new changes that have been made. The output mentions ‘changes to be committed’, which nicely segways us to a major topic in git, the commit.
![git status](https://static.javatpoint.com/tutorial/git/images/git-status2.png)
### Commiting Changes
Commiting changes essentially is moving any changes made in our working directory into the staging area. It is common practice to add a message to your commit, so that you and others can be reminded of what each commit signified.
`> git commit -m “commit message”`

Any changes we make to this branch will not be reflected on the master branch unless we make a deliberate action to do so. This is why utilizing branches in any project is super useful! Since branches can have differences, it may be useful to distinguish the differences between two branches. This can be accomplished with the following command.
`> git diff <branch-name> <other-branch-name>`
![git diff](https://static.javatpoint.com/tutorial/git/images/git-diff.png)
## Stashing
Now, say you made some edits but don't necessarily want to commit those changes quite yet. Git allows us to 'stash' changes, which means that we are able to save uncommitted changes locally. This action allows us to make other changes, checkout other branches, and perform any other git operations. It is almost like we are putting current changes on a temporary shelf to come back for later. This is especially useful when switching between contexts. 
`> git stash`

Once these changes are stashed, we can move freely to other branches and start working on a separate aspect of the project. If we have multiple stashes or just want to check what shashes we have, can check with the following command
`> git stash list`

Stashes are ordered and numbered in a last-in-first-out approach. The naming convention includes WIP and then the branch and commit the stash was created from.
![git stash](https://static.javatpoint.com/tutorial/git/images/git-stash14.png)
We then will want to follow the same processes mentioned above to add our files to the staging area, then commit then to the local repo. 

Once we are ready to retrieve and reapply our stashed changes, we can use either of the following commands. The first command is useful is we need to access those changes multiple times. The pop command is preferred if we only need to make those changes once, as the stashed changes will be applied then removed from the stash. 
`> git stash apply`
`> git stash pop`
## Merge
Let’s say you have a teammate who was working on another feature and now you want to incorporate their changes into your working directory.

Let’s try making changes to this project. For the sake of this tutorial, let’s practice making another branch with some new edits. In the real world, you may have a teammate who is working on another branch. The following command combines the creation and checkout of a new branch in one command
`> git checkout -b <new-branch-name>`
`> nano newFile.txt`
`> git add newFile.txt`
`> git commit -m “added newFile”`
`> git merge <other-branch-name>`
    
 The merge command will incorporate any commits from that branch into the branch you are currently on.
 
Now you know everything you need to know to get started! Good luck with your project and never give up!
