---
layout: post
title:  "Cleaning Git Repos"
date:   2017-06-12 22:04:31 -0700
categories: git, github, clean, nuke, hello
---

## Wash & Clean your Git repo & Github

We're going to kick this blog off with a litle post on Git. I hope to write about different topics and I hope to write at least once a month. Time will tell if I can keep that up. 

If you're like me, you not only use [git](https://git-scm.com/) & [github](https://github.com) as a version control system but also to to keep code for your projects in sync across computers. I am sure there are better solutions for this, but I like this model. 

I write code/scripts at work - check them in and then continue them on a different PC at home.

Over time, I have way too many check-ins and I want to get rid of them. I am not working in a team - I've just gotten my baseline working and I have no use for all the information associated with those check-ins and the space that they consume. I thought [git](https://git-scm.com) would offer a a command to do this - but I don't think it does. After some searching, here is what I came up with. In my setup - I use the master branch (simple personal projects) and use github as my cloud repo. 

Goal - to remove any information about prior check-ins and make the current commit the first checkin.

Steps 

1. Create a new Branch 
2. Add all files to this branch & commit them. 
3. Delete the master branch 
4. Rename the current branch to master
5. Force push the master to github 
6. Remove all old files

````git
git checkout --orphan newBranch
git add -A  # Add all files and commit them
git commit
git branch -D master  # Deletes the master branch
git branch -m master  # Rename the current branch to master
git push -f origin master  # Force push master branch to github
git gc --aggressive --prune=all     # remove the old files
````

There you have it - that is all it takes to wash up and clean you git repo and save some bytes. 
