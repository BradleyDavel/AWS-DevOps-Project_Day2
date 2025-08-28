<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect a GitHub Repo with AWS
![Build Status](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge)
![GitHub](https://img.shields.io/badge/GitHub-Repo-blue?style=for-the-badge&logo=github)
![AWS](https://img.shields.io/badge/AWS-Enabled-orange?style=for-the-badge&logo=amazon-aws)
![Made With](https://img.shields.io/badge/Made%20with-VS%20Code-blue?style=for-the-badge&logo=visual-studio-code)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=for-the-badge)


**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-github)

**Author:** Bradley Davel  
**Email:** bradley.davel@outlook.com

---

## Connect a GitHub Repo with AWS

![Image](http://learn.nextwork.org/sparkling_indigo_heroic_bat/uploads/aws-devops-github_dd9d254e)

---

## Introducing Today's Project!

In this project, I will demonstrate how to store a web application's code in a Git repository. I'm doing this project to:

🐱 Set up Git and GitHub.

🤝 Connect your web app project to a GitHub repo.

🪄 Make changes to your web app code - and watch your GitHub repo update too.

💎 Set up a README file for your repo.

### Key tools and concepts

In this project, I learned how to:

Set up Git and GitHub to manage version control.

Connect a local project to a GitHub repository, enabling smooth code collaboration and backup.

Push and pull code changes between local and remote environments.

Create and manage a README file to make the repository more professional and informative.

Understand the workflow of code changes → from making edits locally → to committing changes → to syncing them with GitHub.

### Project reflection

It took me around 10 minutes to complete the project from start to finish. The setup was straightforward, and most of the time was spent configuring Git correctly and making sure the repository was connected and updating as expected.

I did this project to show my practical skills with Git and GitHub - from setting up version control and connecting a project repository, to making code changes and documenting it with a professional README. It’s an essential foundation for DevOps workflows and demonstrates my ability to manage code collaboratively and efficiently.

This project is part two of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project the 26th of August.

---

## Git and GitHub

Git is a distributed version control system (VCS).
It helps developers track changes in their source code during software development.

Distributed: Every developer has a full copy of the repository (with complete history), not just the latest version.

Version Control: You can track, compare, and roll back changes.

Collaboration: Makes it easy for multiple people to work on the same project, merging changes efficiently.

👉 In short, Git is used to manage code versions, collaborate with teams, and ensure project history is preserved. 

I installed Git using the commands:
sudo dnf update -y
sudo dnf install git -y


GitHub is a cloud-based platform that works with Git. It provides:

-A central remote repository where you can push and pull code.

-Tools for collaboration, such as pull requests, issue tracking, and code reviews.

-Integration with CI/CD pipelines, project boards, and security scanning.

👉 We’re using GitHub because it makes teamwork easier, keeps code safe in the cloud, and gives us a clear history of who changed what and when. It also lets you work from anywhere, instead of being tied to one machine.

![Image](http://learn.nextwork.org/sparkling_indigo_heroic_bat/uploads/aws-devops-github_efaadbf7)

---

## My local repository

To store your code using Git, you create repositories (aka 'repos'), which are folders that contain all your project files and their entire version history. Hosting a repo in the cloud, like on GitHub, means you can also collaborate with other engineers and access your work from anywhere.

o start using Git for your project, you need to create a local repository on your computer.

When you run git init inside a directory e.g. nextwork-web-project, it sets up the directory as a local Git repository which means changes are now tracked for version control.

You can think of Git branches as parallel versions or 'alternate universes' of the same project. For example, if you wanted to test a change to your code, you can set up a new branch that lets you diverge from the original/main version of your code (called master) so you can experiment with new features or test bug fixes safely. We won't create new branches in this project and we'll save all new changes directly to master, but it's best practice to make all changes in a separate branch and then merge them into master when they're ready.

![Image](http://learn.nextwork.org/sparkling_indigo_heroic_bat/uploads/aws-devops-github_7bf21bae)

---

## To push local changes to GitHub, I ran three commands

### git add

The first command I ran was:
git add . 

A staging area is When you stage changes, you're telling Git to put together all your modified files for a final review before you commit them. This is incredibly handy because you get to see all your edits in one spot, which means its much easier to check if there were are mistakes or unwanted changes before you commit.

Hey! Want to see what changes are staged? Run git diff --staged to review your code changes.

### git commit

The second command I ran was git commit -m "Updated index.jsp with new content"

The -m flag lets you leave a message describing what the commit is about, making it easier to review what changed in this version.

### git push

The third command I ran was:
git push -u origin master

By using -u you're also setting an 'upstream' for your local branch, which means you're telling Git to remember to push to master by default. Next time, you can simply run git push without needing to define origin and master.

---

## Authentication

When I commit changes to GitHub, Git asks for my credentials because Git needs to double check that you have the right to push any changes to the remote origin your local repo is connected with. To do this, Git is now authenticating your identity by asking for your GitHub credentials.

### Local Git identity

Git needs my name and email because Git needs author information for commits to track who made what change. If you don't set it manually, Git uses the system's default username, which might not accurately represent your identity in your project's version history.

Running git log showed me the history of commits, which also mentions the commit author's name. In this case "EC2 Default User" which isn't really correct

![Image](http://learn.nextwork.org/sparkling_indigo_heroic_bat/uploads/aws-devops-github_9a27ee3b)

---

## GitHub tokens

GitHub authentication failed when I entered my password because GitHub phased out password authentication to connect with repositories over HTTPS - there are too many security risks and passwords can get intercepted over the internet 🤺 You need to use a personal access token instead, which is a more secure method for logging in and interacting with your repos.

A token in GitHub is a unique string of characters that looks like a random password. For example, a GitHub token might look like ghp_xHJNmL16GHSZSV88hjP5bQ24PRTg2s3Xk9ll. As you can imagine, tokens are great for security because they're unique and would be very hard to guess. I'm using one in this project to authenticate with my GitHub repository over HTTPS instead of using a password.

I could set up a GitHub token by following these steps:

Log into GitHub

Go to github.com and sign in.

Open Developer Settings

Click on your profile picture (top-right).

Select Settings → Developer settings.

Generate a Personal Access Token (PAT)

Navigate to Personal access tokens → Tokens (classic).

Click Generate new token (classic).

Configure the Token

Give it a name/description (e.g., EC2 Project Token).

Choose an expiration date (best practice is not to set it to “no expiration”) but we set it to 7days for the duration of the project we are busy with.

Select scopes (checked repo).

Generate & Save the Token

Click Generate token.

Copy the token shown (e.g., ghp_xHJNmL16GHSZSV88hjP5bQ24PRTg2s3Xk9ll).

⚠️ GitHub only shows it once, so store it safely (like in a password manager).

Use the Token in Git

When pushing or cloning via HTTPS, Git asks for username/password.

Username = your GitHub username.

Password = the token you just created.

![Image](http://learn.nextwork.org/sparkling_indigo_heroic_bat/uploads/aws-devops-github_fa11169d)

---

## Making changes again

I wanted to see Git working in action, so I updated the index.jsp file. I couldn't see the changes in my GitHub repo initially because saving them in VS Code only updates my local repository. My local repo in VS Code is separate from the GitHub repo in the cloud.

To make my changes appear on GitHub, I need to run commands that push them from my local repository to the origin.

I finally saw the changes in my GitHub repo after running the following commands:

git commit -m "Add new line to index.jsp"
git push


![Image](http://learn.nextwork.org/sparkling_indigo_heroic_bat/uploads/aws-devops-github_6becb2bc)

---
