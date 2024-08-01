---
title : "Theory Git"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.1 </b> "
---

# Theory GitHub Basics


## Introduction to Git and GitHub

Git is a free and open-source distributed version control system.  

GitHub is a code hosting platform for version control and collaboration.


## Basic Git Concepts


1. **Version Control**:

   - Tracks changes to the source code.

   - Stores different versions of the code.

   - Allows rollback to old versions for inspection and bug fixes.


2**Repository (Repo)**:

   - A place where all files and the history of changes are stored.

   - Can be stored locally or on services like GitHub.



## Basic Git Commands


- `git init`: Initialize a new repository.

- `git add <file>`: Add a new file to the repository.

- `git commit -m "message"`: Commit changes with a message.

- `git remote add origin <url>`: Add a remote repository.

- `git push origin <branch>`: Push commits to the remote repository.

- `git pull origin <branch>`: Pull changes from the remote repository.

- `git status`: Check the status of the repository.

- `git log`: View commit history.


## Using GitHub

**Pull source code from thanhvivuu.GitHub**


### Step 1 : Clone the repository 

Open terminal :

```shell 

 git clone https://github.com/QuangThanhG13/thanhvivuu.github.io

 ```


### Step 2 : Change to the directory 

```shell

 cd : thanhvuu.github.io 

 ```


### Step 3 : Create a new Branch (Optional) 

  - If you want to work on a new feature or make changes without affecting the existing code, create a new(Khong anh hg den code cu) branch to isolate your work

```shell

   git checkout -b new-feature-branch

```


### Step 4 Check the Status 

```shell

git status 

```


### Step 5 :Stage the Changes 

- Add the modified files 

```shell

git add .

```

- Or add specific files

```shell

git add path/to/file

```


### Step 6 : commit the changes

```shell

git commit -m "massage"

```


### Step 7 : Push the changes

```shell

git push origin main

```

- if you're using a new branch: 

```shell

git push origin new-branch-name

```




