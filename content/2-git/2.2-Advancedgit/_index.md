---
title : "Advanced Git"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

# Advanced Git

## 1. Advanced Branching and Merging
![img.png](/Users/vuquangthanh/Desktop/Nb_Thanhvivuu/static/images/GitNB/img.png)

- **Branching Strategy**: Branching strategies like Git Flow, GitHub Flow, and Trunk-based Development help organize and manage the development process.
- 
- **Rebase**: Used to move or combine a series of commits from one branch to another. Rebase makes the commit history cleaner by removing unnecessary merge commits.
- **Cherry-pick**: Selectively apply a commit from one branch to another without merging the entire branch.
- **Merge Conflicts**: How to resolve merge conflicts and use tools like `git mergetool`.

## 2. Advanced Git Commands and Usage
- **Stash**: Save unfinished changes without committing them, allowing you to switch to other tasks. Use `git stash apply` or `git stash pop` to restore stashed changes.
- **Bisect**: Locate bugs by bisecting the commit range to find the offending commit.
- **Filter-branch and BFG**: Modify commit history, such as removing large files or sensitive information that was previously committed.

## 3. Git Hooks
Git hooks are scripts that execute automatically when certain events occur in Git, such as commit, push, or merge. Common hooks include:
- **Pre-commit**: Check the source code before committing.
- **Pre-push**: Validate or execute actions before pushing to a remote.
- **Post-checkout**: Execute after a new branch is checked out.

## 4. Managing Large Repositories and Advanced Techniques
- **Shallow Clone**: Clone a repository with limited depth to reduce time and storage space.
- **Sparse Checkout**: Allows downloading only a portion of the repository, useful for projects with large directory structures.
- **Large File Storage (LFS)**: Used to manage large binary files that Git doesn't handle well.

## 5. Security and Access Control
- **GPG Commit Signing**: Sign commits to ensure authenticity.
- **Access Control**: Manage repository access permissions through platforms like GitHub, GitLab, or Bitbucket.

## 6. Performance Optimization
- **Garbage Collection**: Use `git gc` to clean up and optimize storage space.
- **Submodules**: Manage sub-repositories within a main repository.
- **Subtree**: An alternative to submodules, allowing the management of code from external repositories.

## 7. External Tools and Utilities
- **Git GUI Tools**: Graphical interface tools like SourceTree, GitKraken, and GitHub Desktop help manage repositories and workflows more easily.
- **Continuous Integration (CI)**: Integrate Git with CI/CD services like Jenkins, GitLab CI, and GitHub Actions to automate testing and deployment.

## 8. Best Practices
- **Commit Messages**: Write clear and meaningful commit messages.
- **Branch Naming Conventions**: Use branch naming conventions for easy management and tracking.
- **Code Reviews**: Conduct code reviews before merging into the main branch.
