# Getting started with git

## install it
If you don't already have git, you can install it from [here](https://git-scm.com/)

## get a github account
If you don't already have one, you'll need to if you want to keep changes on there.
Private repositories are free and easily available on github, so your code is hidden from prying eyes.

## Get a decent terminal
On mac, at least, to do some of the commandline stuff you'll want a non-terrible terminal emulator, like iTerm2.
[iterm2 website](https://iterm2.com/)

# introduction

This doc will cover 2 very basic workflows

    * working on a repository that already exists
    * starting one from scratch, on github.

The first is a good way to get used to a git workflow.

Once you know how to operate it, you can start using it for your own projects.

# Working with an existing repository

## intro
This part will cover the following things (the git commands in parentheses in each point)
  * getting a local copy of the code from a central server (*clone*)
  * updating a local copy if you already have one (*pull*)
  * creating a new branch for your changes (*checkout*)
  * making changes to a file
  * seeing what you've changed (*status*)
  * staging the changes (*add*)
  * saving the changes to git history (*commit*)
  * sending the changes to the remote repository (*push*)

For now we will be doing all the git stuff using a terminal, although you can do it in an number of editors and code tools.

GitHub actually provide a github desktop app and an editor called Atox
VSCode - microsoft visual studio (free)  - very good actually.

## The commands bit

### Download a copy of the repository

    git clone https://github.com/karaukeband/karauke_udn

This will create a local directory (folder, if you prefer) called `karauke_udn` and put all the remote files in it.
You'll need to be in that directory to do anything to it now, so
    
    cd karauke_udn

### Inspect your copy and its history
Inside the repository you can run git commands to see what's going on. There won't be much yet.

    git status

Will show you the current state of your copy, including whether you have any local changes that you haven't committed yet.
    
    git ls-files

will list the files git knows about. Which should be all of them.

    git log -10

will show you the last 10 commits on the current branch:
```git
    $ git log -10
    commit 19c1c85e4c932cef6fd957f52c54abcecc9d5885 (HEAD -> master)
    Author: Stuart Sears <stuart@sjsears.com>
    Date:   Thu Feb 13 17:43:36 2020 +0000

        adds christmas songs in case we can ever be bothered to use them

    commit f24446b6197c71ce4ed62572c7de0bc8efa3e2c3
    Author: Stuart Sears <stuart@sjsears.com>
    Date:   Thu Feb 13 17:10:07 2020 +0000

        updates CSS from core ukbook project

        - allows local customisation

    commit ee83a4e291bf6d2ee617d9c1e096e4a1b78501de (origin/localcss)
    Author: Stuart Sears <stuart@sjsears.com>
    Date:   Thu Feb 13 17:04:04 2020 +0000

        song reflowing, variable font sizes

    commit c3a51399e38abd54e35065b7e29777d13cf731ab
    Author: Stuart Sears <stuart@sjsears.com>
    Date:   Wed Feb 12 09:12:49 2020 +0000

        removes D from interludes
```








