---
date: '2011-04-28 03:15:28'
layout: post
slug: git-squash-commits
status: publish
title: 'Git: Squash commits'
wordpress_id: '169'
categories:
- Git
---

If you want to modify the last 2 commits
`git rebase -i HEAD~2`
This should (hopefully)  display the interactive editor. You'll more than likely want to leave the first line as is, and then change "pick" to "squash" for the second commit.
Once you're done, close the editor (ctrl+x) and save the file. A new interactive screen will popup allowing you to make a commit message, then close and save the file as before.
`git log` will now show the new commit (with it's new commit id).
You'll then need to push the commit. 

If you get a fast-forward error when you go to push (this happens most of the time for me) you can force it with -f. If you do this, make sure you've pulled the latest copy or commits can go missing / out of sync.
`
git push -f origin master
`
