---
title: "Get started with Git & GitHub"
date: "2022-07-11"
categories: 
  - "the-stuff"
tags: 
  - "git"
  - "github"
  - "powershell"
---

In one of the previous posts, we set up SSH to be used with GitHub. Next, we have a look at Git and GitHub itself and how to get started.

## This example

We're going to create a repository on GitHub named **private\_powershell**. After that, we set up everything we need on our local machine to work with Git and GitHub and connect the local repository with GitHub.

This typically always follows the same pattern.

1. Create a remote repository on GitHub and save the link for later
2. Create a folder on your local machine
3. Create a Readme.md file
4. Initialize git
5. Stage the Readme.md
6. Commit the Readme.md
7. Change the default branch name from **master** to **main**
8. Register GitHub as a remote repository
9. Push your stuff to the remote repository

I'm going to describe most of the steps as command statements in a code block - except the creation of the remote repo on GitHub for obvious reasons.

## Create a new remote repository on GitHub

As you can see, this is pretty straightforward.

## Initialize a local git repo and connect to GitHub

```powershell
# Create a local working folder for our stuff 
# Using plain PowerShell instead of 
# 'mkdir private_powershell' for bragging reasons
New-Item -Type Directory -Name "private_powershell" 

# cd into the new folder 
cd .\private_powershell 

# Create a Readme.md
"# A private repository for my powershell stuff" >> Readme.md 

# Initialize Git locally 
git init 

# Add the Readme.md to staging 
git add Readme.md 

# Our first commit! Hooooray!!!!
git commit -m "initial commit" 

# Let's change the default branch name from master to main 
git branch -M main 

# Registering GitHub as remote repo 
# You need the link from above. Remember?
git remote add origin git@github.com:blueteamer/private_powershell.git 

# Upload your stuff to the remote repository 
git push -u origin main 
```

**Note |** Most of the stuff you're reading here is provided by GitHub every time you create a repository online. But anyway, I put it here for me as a quicker reference and some explanations which are missing on the GitHub page - at least for me.

## References

- **[Create a new Item with PowerShell](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.2)** (Microsoft Docs)  
    \[https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.2\]
- **[Setting up a repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository)** (Atlassian Git Tutorial)  
    \[https://www.atlassian.com/git/tutorials/setting-up-a-repository\]
