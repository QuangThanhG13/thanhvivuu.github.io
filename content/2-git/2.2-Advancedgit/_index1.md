---
title : "Examples of Branching Strategies(GH flow)"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.1.1 </b> "
---
# Examples of Branching Strategies

## 1. Git Flow Example

**Scenario**: A development team is preparing to release version 1.0 of an application.

- **Main Branch (`main`)**: Contains the stable, released version of the application.
- **Develop Branch (`develop`)**: Contains the latest development changes for the next release.

**Steps**:

1. **Feature Branches**:
    - **`feature/user-authentication`**: A developer creates this branch from `develop` to add user authentication functionality.
    - **`feature/payment-integration`**: Another developer creates this branch from `develop` to add payment integration.

2. **Merging Features**:
    - After completing and testing features, they are merged into `develop`.

3. **Release Branch**:
    - When features are ready for release, a **`release/1.0`** branch is created from `develop`. This branch is used for final bug fixes and release preparation.
    - Once ready, `release/1.0` is merged into both `main` and `develop`, updating the official release and ensuring bug fixes are also in the development branch.

4. **Hotfix Branch**:
    - If an urgent issue needs fixing in version 1.0, a **`hotfix/1.0.1`** branch is created from `main`, the issue is fixed, and the branch is merged into both `main` and `develop`.

## 2. GitHub Flow Example

**Scenario**: A development team is adding an "About Us" page to the company's website.

**Steps**:

1. **Create a Branch**:
    - A developer creates the **`add-about-page`** branch from `main` to work on the "About Us" page.

2. **Make Changes**:
    - On the `add-about-page` branch, the developer adds HTML and CSS files for the "About Us" page. Each significant change is committed and pushed with descriptive messages like `add initial about page content` and `style about page`.

3. **Create a Pull Request**:
    - Upon completion, the developer creates a pull request from `add-about-page` to `main`, describing the changes and their purpose. They also link the pull request to a relevant issue.

4. **Review and Feedback**:
    - Colleagues review the pull request, leaving comments or suggestions. The developer may make additional commits to address the feedback.

5. **Merge and Deploy**:
    - Once the pull request is approved, it is merged into `main`, and the changes are deployed to the website.

6. **Delete the Branch**:
    - After merging, the `add-about-page` branch is deleted to avoid confusion with other ongoing work.

## 3. Trunk-Based Development Example

**Scenario**: A company continuously develops a web application with frequent feature additions.

**Steps**:

1. **Direct Commits to Trunk (`main`)**:
    - All developers work directly on the `main` branch, committing small, frequent changes.

2. **Short-lived Feature Branches**:
    - If necessary, developers can create short-lived feature branches (e.g., `feature/update-dashboard`) for complex features but must complete and merge them back into `main` quickly.

3. **Continuous Integration**:
    - Each commit to `main` triggers an automatic CI process, running tests and deploying changes if all tests pass.

4. **Feature Flags**:
    - Incomplete new features are hidden behind feature flags, allowing them to be deployed without impacting users.

**Summary**:  
In Trunk-Based Development, the `main` branch is always kept stable and deployable. Features and bug fixes are integrated continuously and quickly.
