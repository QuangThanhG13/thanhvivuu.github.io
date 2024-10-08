---
title : "GibHub homework"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2.2 </b> "
---

# Advanced Exercise: Project Management with Git

## Step 1: Install Git
- Go to [git-scm.com](https://git-scm.com/).
- Download and install Git following the instructions for your operating system.

## Step 2: Configure Git
1. Open the terminal (or Command Prompt on Windows).
2. Configure your name and email with the following commands:

```shell
   git config --global user.name "Your Name"
   git config --global user.email "email@example.com"
   ``` 
## Step 3: Initialize a Repository
1. Create a new directory and move into it:
```shell
mkdir AdvancedGitProject
cd AdvancedGitProject
```

2. Initial a git repository 
```shell
git init
```
- git init is used to initialize a new Git repository 
+ Creates a .git Directory
+ Prepares the Project for Version Control : Flow the changes from the 
+ Sets Up the Initial Branch: By default, `git init` --> creates a new branch called `main`

![1](/thanhvivuu.github.io/images/images/1.png?raw=true)
 
## Step 4: Add and Commit Changes 
1. Create a README.md file and add a description:
```shell
echo "# AdvancedGitProject" >> README.md
```
2. Add and commit the changes:
```shell
git add README.md
git commit -m "Add README file"
```

## Step 5: Create a New Branch and Use Rebase
1. Create and switch to a new branch:
```shell
git checkout -b feature-branch
```
![2](/thanhvivuu.github.io/images/images/2.png?raw=true)

2. Create a feature.txt file, add content, and commit the changes
```shell 
   echo "This is a new feature" >> feature.txt
   git add feature.txt
```
![3](/thanhvivuu.github.io/images/images/3.png?raw=true)
3. Switch back to the main branch
```shell
git checkout main
```

4. Create a hotfix.txt file, add content, and commit the changes:
```shell
echo "This is a hotfix" >> hotfix.txt
git add hotfix.txt
git commit -m "Add hotfix.txt"
```
![img_4.png](/thanhvivuu.github.io/images/images/4.png?raw=true)

5.Rebase the feature-branch onto the main branch:
```shell
git checkout feature-branch
git rebase main

```
- `git rebase main`: Rebase nhánh `feature-branch` lên nhánh `main` có nghĩa là:
+ Lấy tất cả các `commit` từ nhánh `feature-branch` và áp dụng chúng lên đỉnh của nhánh `main.`
+ Cập nhật nhánh `feature-branch` với các thay đổi mới nhất từ nhánh `main`.
+ Đảm bảo rằng các thay đổi trên nhánh `feature-branch` được áp dụng sau các thay đổi trên nhánh `main`, giúp lịch sử commit của nhánh `feature-branch` trở nên đồng bộ với nhánh `main.`
![img_5.png](/thanhvivuu.github.io/images/images/5.png?raw=true)

-Create files here 
![img_6.png](/thanhvivuu.github.io/images/images/6.png?raw=true)

- Nghĩa là sẽ lấy commit từ nhanh  `feature-branch` này cập nhập vào nhánh `main`.
![img_8.png](/thanhvivuu.github.io/images/images/8.png?raw=true)

##### Lý Thuyết `Git reabse`
- Được hiểu như là Reset base cho barch, giả sử mình có 1 nhánh `feature/crawl_video_links`
![img_2.png](img_2.png)


## Step 6: User Cherry picks 
1. Create a new commit on the main branch
```shell
git checkout main
echo "Another fix" >> anotherfix.txt
git add anotherfix.txt
git commit -m "Add anotherfix.txt"
```
2. Cherry-pick this commit onto the `feature-branch`: 
```shell
git checkout feature-branch
git cherry-pick <commit-hash>
```
![img_7.png](/thanhvivuu.github.io/images/images/7.png?raw=true)
![img_9.png](/thanhvivuu.github.io/images/images/9.png?raw=true)

- Trong hình cho ta thấy `git cherry-pick ed7bb320f46b3b3842174c661c88e2e3ab120ded`  dùng để chọn và áp dụng một commit từ một nhánh khác vào nhánh hiện tại.
  - tôi đã tạo file `anotherfix.text` ở nhanh main và sử dụng `git cherry-pick ...` để chuyển sang nhánh feature 
![img_10.png](/thanhvivuu.github.io/images/images/10.png?raw=true)


## Step 7: Use Stash
1. Make some changes on the `feature-branch` that you don't want to commit yet
```shell
echo "Some temporary changes" >> temp.txt
```
2. Stash the changes:
```shell
git stash
```
3. Perform other tasks:
```shell 
   git checkout main
   echo "Work on another task" >> another_task.txt
   git add another_task.txt
   git commit -m "Work on another task"
```
4. Retrieve the changes from the stash
```shell
git checkout feature-branch
git stash pop
```
- Nếu mình chưa muốn commit vào file thì sử dụng `git stash`
![GitNB](/thanhvivuu.github.io/images/images/11.png?raw=true)
  + `git stash`: Lưu trữ các thay đổi chưa được commit để quay lại làm việc sau.
  + `git stash pop`: Lấy lại các thay đổi từ stash và áp dụng chúng lên nhánh hiện tại.
  + `git stash list`: Xem danh sách các mục stash hiện có.

![images](/thanhvivuu.github.io/images/images/12.png?raw=true)

## Step 8 : Use Submodule
1. Add a submodule to your project (e.g., add a repository from GitHub):
 ```shell
git submodule add <repository-url>
```

## Step 9: Push to GitHub
1. Push your changes to GitHub
```shell
git remote add origin <repository-url>
git branch -M main
git push -u origin main
```

## Rebase Git 9000 steps 
#### Target 
![img.png](img.png)

#### Change to  
![img_1.png](img_1.png)

#### Step:
```shell
$ git checkout bugFix 

$ git rebase main

$ git checkout side

$ git rebase bugFix

$ git check another

$ git rebase bugFix

$ git rebase another main 
```










 
