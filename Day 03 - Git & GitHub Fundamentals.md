# 100 Days of DevOps Challenge

# Day 03 - Git & GitHub Fundamentals 

## Introduction 
 
Git is one of the most important tools used in modern software development and DevOps. It helps developers and DevOps engineers track changes in source code, collaborate with team members, maintain different versions of applications, and safely manage code changes.

GitHub is a cloud-based platform that provides Git repository hosting and collaboration features. It allows teams to store Git repositories, review code, manage issues, create pull requests, and integrate repositories with CI/CD tools.

For a DevOps engineer, understanding Git and GitHub is essential because most CI/CD pipelines start when developers push code to a Git repository.

---

## What is Git?

Git is a distributed version control system used to track changes in files and source code.

Git allows us to:

* Track changes in source code
* Restore previous versions
* Create branches
* Merge code changes
* Work with multiple developers
* Maintain project history
* Collaborate with development teams
* Integrate source code with CI/CD pipelines

Git is installed on the local machine and works mainly through the command line.

### Simple Example

Suppose a developer creates an application:

```text
application/
├── app.py
├── requirements.txt
└── README.md
```

The developer makes changes every day.

Without Git, it can become difficult to understand:

* What was changed?
* Who changed it?
* When was it changed?
* What was the previous version?
* How can we restore an older version?

Git solves these problems by maintaining the history of the project.

---

# What is GitHub?

GitHub is a platform used to host Git repositories online.

It provides additional features such as:

* Remote repositories
* Pull Requests
* Code Reviews
* Issues
* Project Management
* GitHub Actions
* Team Collaboration
* Repository Security
* Documentation

For example:

```text
Developer
    |
    | git push
    v
GitHub Repository
    |
    | CI/CD Trigger
    v
Jenkins / GitHub Actions
    |
    v
Build
    |
    v
Test
    |
    v
Deploy
```

This is why Git and GitHub are very important in DevOps.

---

# Git vs GitHub

| Git                         | GitHub                          |
| --------------------------- | ------------------------------- |
| Version control system      | Git repository hosting platform |
| Installed locally           | Cloud-based platform            |
| Tracks code changes         | Stores Git repositories online  |
| Command-line tool           | Web-based platform              |
| Works without internet      | Usually used through internet   |
| Created for version control | Provides collaboration features |
| Example: `git commit`       | Example: Pull Request           |

Git and GitHub are different, but they are commonly used together.

---

# Why Git is Important in DevOps

Git is a fundamental part of CI/CD.

A typical DevOps workflow looks like:

```text
Developer
    |
    v
Write Code
    |
    v
Git
    |
    v
GitHub
    |
    v
CI/CD Pipeline
    |
    v
Build
    |
    v
Test
    |
    v
Docker Image
    |
    v
Container / Kubernetes
    |
    v
Production
```

When developers push code to GitHub, a CI/CD pipeline can automatically start.

For example:

```text
git push
   |
   v
GitHub
   |
   v
GitHub Actions / Jenkins
   |
   v
Build
   |
   v
Test
   |
   v
Deploy
```

This reduces manual work and makes software delivery faster.

---

# Installing Git

To check whether Git is installed:

```bash
git --version
```

Example:

```text
git version 2.x.x
```

If Git is installed, the version will be displayed.

---

# Git Configuration

Before using Git, configure your username and email.

### Configure Username

```bash
git config --global user.name "Your Name"
```

### Configure Email

```bash
git config --global user.email "your-email@example.com"
```

### Check Configuration

```bash
git config --list
```

You can also check individual values:

```bash
git config user.name
git config user.email
```

---

# Git Repository

A Git repository is a directory where Git tracks project files and their history.

There are two common ways to create a repository.

### Method 1: Create a New Repository

```bash
mkdir my-project
cd my-project
git init
```

The `git init` command creates a hidden `.git` directory.

```text
my-project/
├── .git/
└── files
```

The `.git` directory contains Git's internal information and history.

### Method 2: Clone an Existing Repository

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/example/project.git
```

This downloads an existing repository to your local machine.

---

# Git Working Areas

Git mainly works with three important areas:

```text
Working Directory
       |
       | git add
       v
Staging Area
       |
       | git commit
       v
Local Repository
       |
       | git push
       v
Remote Repository
```

### 1. Working Directory

This is where you create or modify files.

### 2. Staging Area

Files added using `git add` are placed into the staging area.

### 3. Local Repository

The `git commit` command saves staged changes into the local Git repository.

### 4. Remote Repository

The `git push` command sends local commits to a remote repository such as GitHub.

---

# Git Basic Workflow

The basic Git workflow is:

```text
Create / Modify Files
        |
        v
git status
        |
        v
git add
        |
        v
git commit
        |
        v
git push
```

Example:

```bash
git status

git add .

git commit -m "Add application files"

git push origin main
```

---

# git status

The `git status` command shows the current state of the working directory.

```bash
git status
```

It can show:

* Modified files
* New files
* Deleted files
* Staged files
* Untracked files
* Current branch

Example:

```text
On branch main

Changes not staged for commit:
  modified: app.py

Untracked files:
  config.yaml
```

---

# git add

The `git add` command moves changes to the staging area.

Add one file:

```bash
git add app.py
```

Add multiple files:

```bash
git add app.py README.md
```

Add all changes:

```bash
git add .
```

The staging area allows us to choose which changes should be included in the next commit.

---

# git commit

The `git commit` command saves staged changes to the local repository.

```bash
git commit -m "Add application configuration"
```

A good commit message should clearly describe the change.

Examples:

```bash
git commit -m "Add Dockerfile"
```

```bash
git commit -m "Fix deployment configuration"
```

```bash
git commit -m "Update Kubernetes manifests"
```

---

# git log

The `git log` command displays commit history.

```bash
git log
```

A shorter version:

```bash
git log --oneline
```

Example:

```text
a379060 Add Day 02 notes
91b21ac Add Git fundamentals
4a83c21 Initial commit
```

This helps us understand the history of the project.

---

# git diff

The `git diff` command shows changes that have not been staged.

```bash
git diff
```

To see staged changes:

```bash
git diff --staged
```

This is useful for reviewing changes before committing.

---

# Git Branches

A branch is an independent line of development.

Branches are commonly used when developers work on new features or fixes without directly changing the main production code.

Example:

```text
                feature-login
               /
main ---------- 
               \
                feature-payment
```

Common branches:

```text
main
develop
feature/login
feature/payment
bugfix/login
```

---

# Create a Branch

Create a new branch:

```bash
git branch feature-login
```

List branches:

```bash
git branch
```

Switch to a branch:

```bash
git checkout feature-login
```

Modern Git also supports:

```bash
git switch feature-login
```

Create and switch to a new branch:

```bash
git checkout -b feature-login
```

Or:

```bash
git switch -c feature-login
```

---

# Git Merge

Merge is used to combine changes from one branch into another.

Suppose we have:

```text
main
  |
  |---- feature-login
  |
```

After completing the feature, we can merge it into `main`.

First switch to main:

```bash
git switch main
```

Then merge:

```bash
git merge feature-login
```

Git will combine the changes into the main branch.

---

# Merge Conflict

A merge conflict happens when Git cannot automatically combine changes.

For example:

```text
Developer A
    |
    v
main ---> change app.py

Developer B
    |
    v
feature ---> change same part of app.py
```

When the branches are merged, Git may report a conflict.

Example:

```text
<<<<<<< HEAD
print("Hello")
=======
print("Hello World")
>>>>>>> feature-login
```

The developer must manually decide which version should remain.

After resolving the conflict:

```bash
git add .
git commit -m "Resolve merge conflict"
```

---

# git clone

`git clone` downloads a remote repository to your local machine.

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/example/devops-project.git
```

After cloning:

```bash
cd devops-project
```

Then check:

```bash
git status
```

---

# Git Remote

A remote repository is a Git repository hosted somewhere outside your local machine.

For example:

```text
Local Repository
      |
      | origin
      v
GitHub Repository
```

Check remote repositories:

```bash
git remote -v
```

Example:

```text
origin  https://github.com/example/project.git (fetch)
origin  https://github.com/example/project.git (push)
```

`origin` is the commonly used default name for the remote repository.

---

# git push

The `git push` command uploads local commits to a remote repository.

```bash
git push origin main
```

For a new branch:

```bash
git push origin feature-login
```

The general syntax is:

```bash
git push <remote> <branch>
```

---

# git pull

The `git pull` command downloads changes from the remote repository and integrates them into the current branch.

```bash
git pull origin main
```

Typical workflow:

```bash
git pull
```

Make changes:

```bash
git add .
git commit -m "Update application"
```

Push changes:

```bash
git push
```

---

# git fetch

`git fetch` downloads changes from the remote repository without automatically merging them into the current branch.

```bash
git fetch
```

Difference:

```text
git fetch
    |
    v
Download remote changes
    |
    v
Review changes
```

While:

```text
git pull
    |
    v
Download remote changes
    |
    v
Merge changes
```

---

# GitHub Repository

A GitHub repository is an online location where project source code and Git history are stored.

A repository can contain:

```text
project/
├── README.md
├── Dockerfile
├── Jenkinsfile
├── .gitignore
├── src/
└── k8s/
```

A DevOps repository may contain:

* Application source code
* Dockerfiles
* Kubernetes manifests
* Terraform code
* Jenkinsfiles
* GitHub Actions workflows
* Ansible playbooks
* Documentation

---

# .gitignore

The `.gitignore` file tells Git which files should not be tracked.

Example:

```text
node_modules/
.env
*.log
*.tmp
__pycache__/
.terraform/
*.tfstate
```

This is important because sensitive information should not be committed to Git.

For example:

```text
.env
```

might contain:

```text
DATABASE_PASSWORD=secret
AWS_ACCESS_KEY=xxxxx
```

Secrets should never be stored directly in a public GitHub repository.

For DevOps projects, secret management should be handled using appropriate tools such as:

* AWS Secrets Manager
* AWS Systems Manager Parameter Store
* GitHub Secrets
* HashiCorp Vault

---

# GitHub Pull Request

A Pull Request, commonly called a PR, is used to propose changes to a repository.

Typical workflow:

```text
Developer
   |
   v
Create Feature Branch
   |
   v
Make Changes
   |
   v
Commit
   |
   v
Push Branch
   |
   v
Create Pull Request
   |
   v
Code Review
   |
   v
CI/CD Checks
   |
   v
Merge
```

Pull Requests are commonly used in professional development teams.

---

# GitHub Actions

GitHub Actions is a CI/CD automation platform provided by GitHub.

A GitHub Actions workflow can automatically:

* Build applications
* Run tests
* Build Docker images
* Push images to registries
* Deploy applications
* Run security scans
* Execute automation tasks

Example workflow:

```text
Developer pushes code
        |
        v
GitHub Repository
        |
        v
GitHub Actions
        |
        v
Build
        |
        v
Test
        |
        v
Docker Build
        |
        v
Push to ECR
        |
        v
Deploy to EKS
```

This is one of the important connections between Git and DevOps.

---

# Git and Jenkins

Git can also be integrated with Jenkins.

Example:

```text
Developer
    |
    v
GitHub
    |
    | Webhook
    v
Jenkins
    |
    v
Build
    |
    v
Test
    |
    v
Docker Build
    |
    v
Deploy
```

A Jenkins pipeline can be triggered whenever code is pushed to GitHub.

Example Jenkinsfile:

```groovy
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/example/project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building application'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running tests'
            }
        }
    }
}
```

---

# Git Tags

Tags are used to mark specific points in Git history.

For example:

```bash
git tag v1.0.0
```

List tags:

```bash
git tag
```

Push a tag:

```bash
git push origin v1.0.0
```

Tags are commonly used for software releases.

Example:

```text
v1.0.0
v1.1.0
v2.0.0
```

---

# Git Revert

`git revert` creates a new commit that reverses the changes introduced by an earlier commit.

First find the commit:

```bash
git log --oneline
```

Then:

```bash
git revert <commit-id>
```

This is generally safer for shared branches because it preserves the existing Git history.

---

# Git Reset

`git reset` can move the current branch pointer and can be used to remove commits or unstage changes depending on the option.

Example:

```bash
git reset HEAD file.txt
```

This unstages the file.

A hard reset is more destructive:

```bash
git reset --hard HEAD~1
```

Use destructive reset commands carefully because they can remove local changes.

---

# Common Git Commands

| Command      | Purpose                        |
| ------------ | ------------------------------ |
| `git init`   | Create a new repository        |
| `git clone`  | Clone an existing repository   |
| `git status` | Check repository status        |
| `git add`    | Stage changes                  |
| `git commit` | Save changes                   |
| `git log`    | View commit history            |
| `git diff`   | View changes                   |
| `git branch` | Manage branches                |
| `git switch` | Switch branches                |
| `git merge`  | Merge branches                 |
| `git remote` | Manage remote repositories     |
| `git fetch`  | Download remote changes        |
| `git pull`   | Download and integrate changes |
| `git push`   | Upload commits                 |
| `git tag`    | Create release tags            |
| `git revert` | Reverse a commit               |

---

# Practical Git Workflow

Here is a complete example of creating and pushing a project to GitHub.

### Step 1: Create Project

```bash
mkdir devops-project
cd devops-project
```

### Step 2: Create File

```bash
echo "# DevOps Project" > README.md
```

### Step 3: Initialize Git

```bash
git init
```

### Step 4: Check Status

```bash
git status
```

### Step 5: Add Files

```bash
git add .
```

### Step 6: Commit

```bash
git commit -m "Initial commit"
```

### Step 7: Add Remote

```bash
git remote add origin <repository-url>
```

### Step 8: Rename Branch

```bash
git branch -M main
```

### Step 9: Push to GitHub

```bash
git push -u origin main
```

Now the project is available in the GitHub repository.

---

# Git Workflow Used in DevOps

A practical DevOps Git workflow can look like this:

```text
                    GitHub
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
      main          develop        feature
        |              |              |
        +--------------+--------------+
                       |
                       v
                   CI Pipeline
                       |
                       v
                    Testing
                       |
                       v
                 Docker Build
                       |
                       v
                 Container Registry
                       |
                       v
                  Deployment
                       |
                       v
                    AWS/EKS
```

Git acts as the source of truth for application and infrastructure code.

---

# Git Best Practices

## 1. Write Meaningful Commit Messages

Good:

```bash
git commit -m "Add Kubernetes deployment manifest"
```

Bad:

```bash
git commit -m "update"
```

---

## 2. Use Branches

Do not make every change directly on the main branch.

Use feature branches:

```bash
git switch -c feature/login
```

---

## 3. Pull Before Starting Work

Before making changes:

```bash
git pull
```

This helps keep the local branch updated.

---

## 4. Review Changes Before Commit

Use:

```bash
git status
```

and:

```bash
git diff
```

before committing.

---

## 5. Never Commit Secrets

Do not commit:

```text
passwords
API keys
AWS access keys
private keys
database credentials
.env files
```

Use secret-management solutions instead.

---

## 6. Keep Commits Small

Instead of making one huge commit:

```text
Update everything
```

create meaningful commits:

```text
Add Dockerfile
Add Kubernetes deployment
Update service configuration
Fix application configuration
```

---

# Important Git Concepts for DevOps Interviews

For a DevOps engineer, the following Git concepts are especially important:

1. Git vs GitHub
2. Git repository
3. Working directory
4. Staging area
5. Commit
6. Branch
7. Merge
8. Merge conflict
9. Pull Request
10. Git remote
11. `git fetch`
12. `git pull`
13. `git push`
14. `.gitignore`
15. Git tags
16. Git revert
17. Git reset
18. Git hooks
19. Git branching strategies
20. Git integration with CI/CD

---

# Git in a Real DevOps Environment

In a real company, developers may follow a workflow like:

```text
Developer creates feature
          |
          v
feature branch
          |
          v
Code commit
          |
          v
Push to GitHub
          |
          v
Pull Request
          |
          v
Code Review
          |
          v
Automated Tests
          |
          v
Security Scan
          |
          v
Build Docker Image
          |
          v
Push Image to Registry
          |
          v
Deploy to Kubernetes
          |
          v
Monitoring
```

The DevOps engineer may be responsible for the automation between GitHub and the deployment environment.

---

# What I Practiced Today

Today I practiced the basic Git workflow:

```bash
git init
git status
git add .
git commit -m "Initial commit"
git branch
git switch
git log
git remote -v
git push
git pull
```

I also learned how GitHub repositories, branches, Pull Requests, and CI/CD pipelines work together.

---

# Key Takeaways

Git is a distributed version control system that helps teams manage source code and track changes.

GitHub provides online Git repository hosting and collaboration features.

The basic Git workflow is:

```text
Working Directory
       |
       v
git add
       |
       v
Staging Area
       |
       v
git commit
       |
       v
Local Repository
       |
       v
git push
       |
       v
GitHub
```

Git is an essential DevOps skill because it integrates directly with CI/CD tools such as Jenkins and GitHub Actions.

---

# Day 03 Summary

Today I learned:

* What Git is
* What GitHub is
* Git vs GitHub
* Git repository
* Working directory
* Staging area
* Local repository
* Remote repository
* Basic Git commands
* Git branches
* Branch merging
* Merge conflicts
* Pull Requests
* GitHub Actions
* Git and Jenkins integration
* `.gitignore`
* Git tags
* Git revert
* Git reset
* Git best practices
* Git workflow in DevOps

---

# Day 03 Completed

Another step completed in my DevOps learning journey.

```text
Day 01 → Linux Fundamentals
Day 02 → Linux Networking Fundamentals
Day 03 → Git & GitHub Fundamentals
```

I will continue building my DevOps knowledge step by step and documenting everything as part of my #90DaysDevOpsChallenge.

#90DaysDevOpsChallenge #Day03 #Git #GitHub #DevOps #AWS #CICD #Jenkins #GitHubActions #Docker #Kubernetes #Terraform #Cloud #DevOpsEngineer #LearningInPublic
