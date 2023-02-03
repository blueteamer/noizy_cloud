---
title: "Working with branches in Git"
date: "2022-07-18"
tags: 
  - "tools"
  - "github"
  - "powershell"
---

Using branches is an important part of working with Git. In this post, we're going to have a closer look at this topic.

<!--more-->
## Table of content 
{{< toc >}}

## What will be covered?

We're assuming that Git and GitHub are in place and some code is already written, committed and pushed towards our GitHub remote repository.

As a next step, we want to add more functionality but also want to keep our code base working.

**Note |** If you are working with Git, there is an important rule: Never mess with the Main branch!  
Whenever you feel the urge to modify or delete or add or what-so-ever you need to do to your code, do it in a separate branch - a **working branch!** Test everything. And if it's doing as expected, merge it back to the main branch so everyone knows your changes are valid and won't break anything (at least in theory).

## How is this done?

The process is fairly simple and straightforward. On a high level it is something like this:

- Get the latest changes for Main from the remote repository.
- Create a **working branch** where you can ape around.
- When you're done, move back to the main and again, get the latest changes.
- Merge your changes into the Main branch.
- Push the updated Main branch to the remote repository.
- Clean up and remove the **working branch** as it is no longer needed.

### Step 1: Create a branch

As a first step, we check what branches are already in our local repository. Then, we get the latest changes from the remote repository and create the new **working branch** named **ImproveCreateRepoFeature.**

```powershell
# Check the current branch and get all available branches
git branch -a

# Get the latest changes from the remote repository 
git pull 

# Create the working branch 
git checkout -b ImproveCreateRepoFeature
```

**git checkout -b** is doing several steps at once. It is creating the branch and moves us to the newly created branch.

**Note |** Using **git branch -a** will show you that you are now in the new branch (indicated by a small \* character in front of the branch's name).

### Step 2: Make your changes and commit them to the branch

So, I made some modifications to the public command of my module, changed the name of a file and some other stuff. Testing says I'm good, so I proceed with the commit.

```powershell
# Adding all changes to staging
git add .

# Commiting the changes 
git commit -m "Changed the naming of cmdlts and parameters."

# Checking if everything is fine in Git-Land 
git status 
```

**git status** tells me that everything is ok on my current branch, which is nice.

### Step 3: Switch back to main and merge the changes

Next, we're switching back to the Main branch and getting the latest changes from the remote repo. After that is done - and no errors occur - we can merge our changes.

**Note |** We're doing this because if we're working in a bigger team it might happen, that someone else has merged his changes with the Main branch in the meanwhile. And it is required to always merge with the latest code base - otherwise, you'll get stuck in a mess.

```powershell
# Switch back to main
git checkout main 

# Get latest changes
git pull 

# Merge your changes 
git merge ImproveCreateRepoFeature
```

### Step 4: Clean up and remove the branch

To avoid having a list of hundreds of branches when you use **git branch**, it is a good practice to get rid of unused branches. As soon as you don't need the branch anymore (e. g. when you merged it into main), you can delete it.

**Note |** I was told you should use **git merge <name of your branch> --no-ff** to prevent using Fast-forward mode of merging. Using this trigger will keep the commit comments from the branch which is cool to read later on. Though, honestly not sure about this. Haven't understood that topic fully and in detail, yet.

```powershell
# Remove the obsolete branch 
git branch -d ImproveCreateRepoFeature 
```

And that's it. Now you can repeat the steps for any changes you're doing.

## Noteworthy stuff

What we covered here is pretty easy stuff. It becomes way more complicated if you create branches of branches and a thousand people are doing stuff at the same time. When errors during the merging occur - this is fun as hell.

So, long story short. This helps with the less complex set ups and the common procedure working with Git. For everything else: The Google-Luck-Combination, my friend!

## References

- **[Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)** (git-scm.com)  
    \[https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging\]
