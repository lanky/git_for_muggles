# Getting started with git

## install it
If you don't already have git, you can install it from [here](https://git-scm.com/)

### on windows
get the latest (as of the date I wrote this) maintained version from [here](https://github.com/git-for-windows/git/releases/download/v2.32.0.windows.2/Git-2.32.0.2-64-bit.exe) and run it.

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

GitHub actually provide a github desktop app and an editor called Atom
VSCode - microsoft visual studio (free)  - very good actually.

## The commands bit

### Download a copy of the repository

This is called `cloning` because that's basically what it does - creates an identical copy of the files on your local machine.

```sh
$ git clone https://github.com/karaukeband/karauke_udn
Cloning into 'karauke_udn'...
Username for 'https://github.com': YOURUSERNAME
Password for 'https://lanky@github.com': YOURPASSWORD
remote: Enumerating objects: 278, done.
remote: Counting objects: 100% (278/278), done.
remote: Compressing objects: 100% (277/277), done.
remote: Total 278 (delta 0), reused 278 (delta 0), pack-reused 0
Receiving objects: 100% (278/278), 162.96 KiB | 2.91 MiB/s, done.
```

This will create a local directory (folder, if you prefer) called `karauke_udn` and put all the remote files in it.
You'll need to be in that directory to do anything to it now, so
    
    cd karauke_udn

### Inspect your copy and its history
Inside the repository you can run git commands to see what's going on. There won't be much yet.
```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

Will show you the current state of your copy, including whether you have any local changes that you haven't committed yet.
    
    git ls-files

will list the files git knows about. Which should be all of them and may be a long list.

    git log -4

will show you the last 10 commits on the current branch:
```git
    $ git log -4
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

        removes D from interlude
```
## making changes to the repository

While you could go ahead and start editing things, the normal approach is to create a new branch (and in the case of the `karauke_udn` repository it's required - you can't push directly to the live book). A custom branch is also easily discarded for when you inevitably screw things up. And you will, everybody does when theya re new to git.

So, to make changes we will
  * create a new 'feature' branch
  * change to the new branch
  * edit away to our heart's content
  * commit the things we want to keep
  * when we're happy, push them to github, keeping them in our new branch
  * create what is known as a pull request to ask someone else to review them and merge them into the master branch, which in this repo is used for the live book.

Let's get on with it...

### Creating a new branch
branches are really easy to create in git, and are 'cheap' - they don't create new copies of files, so their creation is more or less instantaneous.

    git branch

will show you branches that exist locally, and which one you are on, marked with a  '*'
```
$ git branch
* master
```
There may be other branches that exist on the remote server, we don't care about those.

    git branch muggles

Will create a branch, based on the last commit from your current branch (which is master, unless you've been cheating)

### Do some stuff
Let's edit a file and see what happens.

First, to avoid mucking anything important up (although it will all be recoverable), let's work on a custom branch

    git checkout -b git_training

(this is a shortcut, you could also have used `git branch git_training` followed by `git checkout git_training` to change to the new branch)


This creates a new branch called `git_training` and switches you to it.
Any changes you make now cannot affect the main 'live' book without
deliberate action.

Pick a file from the `current` directory and make some changes to it

Here's a childish example:

    echo 'poo' >> current/im_a_believer_-_the_monkees.udn

(make sure there are 2 chevrons (>>) not just one)

The non-commandline version would be to open the `current/im_a_believer_-_the_monkees.udn`
file in a text editor (like Notepad, Notepad++, but definitely not Word, LibreOffice Writer 
or a similar word processor) and adding the work 'poo' at the end of the document.

Once you've changed the file, let's see what git thinks:

```sh
$ git status
On branch git_training
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   current/im_a_believer_-_the_monkees.udn

no changes added to commit (use "git add" and/or "git commit -a")

```

so, git has noticed you've changed the file. Let's get it to show us what you did:

    $ git diff current/im_a_believer_-_the_monkees.udn
```diff
diff --git a/current/im_a_believer_-_the_monkees.udn b/current/im_a_believer_-_the_monkees.udn
index 4b6f7d3..c1d899e 100644
--- a/current/im_a_believer_-_the_monkees.udn
+++ b/current/im_a_believer_-_the_monkees.udn
@@ -50,3 +50,4 @@ I couldn't (F)leave her if I (D)tried
 
 {skatty ending over chorus chords x 1 then cha cha end}
 
+poo

```

As you can see, it shows you having added the word 'poo' and shows you some context lines and line numbers to show where in the file you made this change.
