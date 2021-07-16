# git_for_muggles
A brief guide to the git commandline for the perplexed

## What is this git thing, anyway?
**Git** is a "Version Control System" (aka VCS). It's purpose is to keep track of the contents of files and any changes made to them, allowing you to see what changed and when and who made the change, and to undo any or all of them.

## The basic terms

A list of common terms (usually actions) that apply to git

### `clone`
`git clone` fetches a copy of a remote repository and all its history into a local directory

### pull
`git pull` is used in an already existing local copy and it fetches any updates that have been made to code on your 'remote'

### checkout
`git checkout` changes to (and optionally creates) a different branch. More on branches later.

### add
`git add` adds files, or changes to files to a 'staging' area - a collection of things you want to commit

### commit
`git commit` adds any staged changes to the git history, with a message
A commit creates a record that consists of several things
  * the changes you made
  * your name/email
  * a unique ID for the change (known as a *hash*)
  * a list of the files that are affected by the change
  * a message that describing the change

### log
`git log` shows you the commit history, you can see changes for the entire repository, or individual directories or files

### examples



### push
`git push` pushes (sends) any changes you have committed to your local copy to the remote server (e.g. github)

## more advanced terms/actions

### branches
A *branch* in git is a list of changes (`commits`), starting from a known state. This sounds more complicated than it is.
Every repository has at least one branch, usually known as *master*

It is common practice to create a new branch for changes you want to make to a repository, this keeps those changes away from the current master unitl you are certain they are correct and work as desired. Once you are happy with your changes you can merge them into your live code (usually the master branch).

`git branch NAME` creates a new branch based from the latest commit you would see in `git log`


### rebase

e.g. `git rebase master`
presuming you are working on a branch not called master, but hwich

rebase applies changes to your current branch from another. It does this by moving backwards (called *rewinding*. Yes, really) in history on both branches to find a common ancestor (a commit with the same ID in both branches). It then adds all the changes 


### merge
### revert
### reset


