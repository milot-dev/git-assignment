# Git Assignment Project
## Overview

### This project demonstrates Git skills including:

* Initializing a repository
* Making multiple commits with unclear messages
* Cleaning up commit history via rebase and squash
* Recovering lost commits
* Creating branches and tags
* Defining Git aliases
* Pushing the final repository to GitHub

#### The goal of this assignment was to practice proper Git workflows and maintain a clean, understandable commit history.

## Project Structure
```
project.txt
README.md
```
**project.txt** contains example project updates including feature implementation and bug fixes.

## Git Workflow Steps
#### 1. Initialize Repository
``` 
git init
git add project.txt
git commit -m "Initial project"
```
#### 2. Make Several Commits With Unclear Messages
```
git commit -m "update"
git commit -m "stuff"
git commit -m "fix"
git commit -m "fix that i forgot to commit"
```
#### 3. Clean Up Commit History

##### Used interactive rebase to rewrite history and give commits meaningful messages:
```
git rebase -i HEAD~4
```
##### Reword, squash, or pick commits as needed
```
reword 47062a0 update
reword abd078b stuff
pick 7c539e5 fix
squash b6a8d97 fix that i forgot to commit
```
##### Final cleaned history:
```
661ff10 Fix bugs on feature A and B
44c53be Implement features to handle distributed systems
6cdadc8 Update project requirements
518616a Initial project
```
#### 4. Simulate Mistake & Recover Commit

##### Added a new untested feature:
```
git add .
git commit -m "Implement new untested feature"
```
##### Removed it to simulate a mistake:
```
git reset --hard HEAD~1
```
##### Recovered the lost commit using reflog:
```
git reflog
git checkout 7f64a78
git branch recovered-untested-feature
git switch recovered-untested-feature
```
#### 5. Branching & Tagging

##### Created a new branch for the recovered commit:
```
git branch recovered-untested-feature 7f64a78
git switch recovered-untested-feature
```
##### Tagged the cleaned-up commits:
```
git switch main
git tag -a v1.0 -m "Project version 1.0"
git switch recovered-untested-feature
git tag -a v1.1.0 -m "Project version 1.1.0"
```
#### 6. Create a Git Alias

##### Defined a custom alias to visualize commit history:
```
git config --global alias.tree "log --graph --decorate --oneline --all"
git tree
```
##### Example output:
```
* 7f64a78 (HEAD -> recovered-untested-feature) Implement new untested feature
* 661ff10 (tag: v1.0) Fix bugs on feature A and B
* 44c53be Implement features to handle distributed systems
* 6cdadc8 Update project requirements
* 518616a Initial project
```
#### 7. Push Repository to GitHub

##### Added remote:
```
git remote add origin https://github.com/milot-dev/git-assignment
```
##### Pushed main branch and tags:
```
git push -u origin main
git push --tags
```
##### Pushed recovered branch:
```
git push -u origin recovered-untested-feature
```
## Final Commit History

#### Main branch (main):
```
28a47f5 Fix bugs on feature A and B
a860720 Implement features to handle distributed systems
15f372e Update project requirements
47efd28 Initial project
```
#### Recovered branch (recovered-untested-feature):
```
aed22c6 Implement new untested feature
28a47f5 Fix bugs on feature A and B
a860720 Implement features to handle distributed systems
15f372e Update project requirements
47efd28 Initial project
```
## Summary

### This assignment demonstrates:

* Cleaning up messy commit history with interactive rebase and squash
* Recovering lost commits using reflog
* Creating and switching branches
* Using Git aliases for visualizing history
* Tagging versions
* Properly pushing branches and tags to GitHub

#### By the end of the assignment, the repository is clean and versioned.
