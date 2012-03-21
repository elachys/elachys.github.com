---
date: '2011-04-05 14:38:02'
layout: post
slug: git-basics-cheatsheet
status: publish
title: Git basics cheatsheet
wordpress_id: '148'
categories:
- Git
---

## Clone


Use the following to clone a repo and put it's contents in a local directory.
`git clone http://repourl.com mydirectory`


## Status


See what files you have to check in, and some other general stats

`git status`


## branches


Switch between branches using the following

`git checkout branchname`

Create a branch and switch to that branch

`git checkout -b mybranchname`


## committing


Once you have changed a file, you must add it to the latest commit (much like svn), although the changes are not actually sent to the remote server until you "push" them

`git add myfile.html`
`git commit -m "what i have done to the file"`


## push


Push once all your changes have been made and you've made a new commit

`git push origin branchname`


## ignore files


Create a file in the root of your repo called .gitignore

You can either ignore single files or use * as a wildcard



## show history


You can show the history of a repo by doing:
`git log`



## Show information about a particular commit


After using `git log` to see all your commits, you might want to look at one in a little more detail, well just use this:
`git show myhashstring`



## Cherry picking


If you only want to get a certain commit, you can do the following (-x retains the original commit message).
`git cherry-pick -x my-commit-hash`



## Current remote repo url


If you want to clone a repo you already have setup somewhere else but can't remember the clone path. Use:
`git remote -v`



## Ignore file permissions

## 
Stops git tracking file permission changes.
`git config core.filemode false`
