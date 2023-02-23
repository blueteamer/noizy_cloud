---
title: "Using Git - Common use cases"
date: 2023-02-23T06:57:14+01:00
draft: true
---


# Using Git - Common use cases 

- Initialize Git 

## Working in main branch 
- Make changes to your files 
- Add changed files to staging 
- commit changes and make somekind of a snapshot 
- upload changes to GitHub 

## making further changes 
- get latest changes from GitHub on main 
- make working branch 
- switch to working branch 
- make changes to files 
- commit changes to working branch 
- when finished, merge working branch with main 
- upload changes to GitHub 

## making changes and save inbetween 
- get latest changes from GitHub on main 
- make working branch 
- switch to working branch 
- make changes to files 
- upload working branch to GitHub 


## Get working branch from GitHub 
- download working branch from GitHub 


## Navigating in Git 

>> main 
git checkout -b workingbranch -> make new branch and switch to that branch 

>> workingbranch 
do some work here -> edit this 
do some work there -> and edit that 

>> workingbranch 
git add . -> add changed files to staging 

>> workingbranch 
git commit -m "I did some great stuff" -> commit everything in staging

>> workingbranch 
git checkout main -> switch back to main 

>> main 
git merge workingbranch -> merge the workingbranch with the current one, main

>> main 
git push origin branchname -> upload main to GitHub (not sure)

>> main 
git pull -> download from GitHub to main (not sure)

Source: 
https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging




