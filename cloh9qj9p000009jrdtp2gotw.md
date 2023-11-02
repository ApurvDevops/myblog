---
title: "Day 8 Basic Git & GitHub for DevOps Engineers."
datePublished: Thu Nov 02 2023 14:15:01 GMT+0000 (Coordinated Universal Time)
cuid: cloh9qj9p000009jrdtp2gotw
slug: day-8-basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698934451538/8d5f96f6-1daa-42cf-ba27-05f7c1e0d63a.png
tags: linux, github, 90daysofdevops, tws, day7-90daysofdevops

---

**What is Git?**

Git is a version control system, that allows any software developer, or development project to track changes made in files and coordinate work of those files among multiple people.

With the help of GIT, we can keep

* 🔄 **Version Control**: Keep a history of changes and who made the changes
    
* 🤝 **Collaboration**: Work with others seamlessly, we can rever to previous changes, if required
    
* 🧹 **Branching**: Easily create and manage branches. This is mostly used when work is divided into teams and everyone is working on different features and once done, everyone can merge the feature and create one single project.
    
* 🌐 **Remote Repositories**: Share code across the web. Because of this feature of git, so many open-source projects can work and people all around the globe can contribute.
    
* 📦 **Modularity**: Split code into manageable pieces, due to which it's now easy to find bugs and make changes in a local repo, test it in the test system before merging and deploying the code in prod.
    
* 🏗️ **Merging**: Combine code changes effortlessly, this goes with branching as once a feature is enhanced or created, we first create a separate branch and later on Merge it .
    

**What is GitHub?**

GitHub is a web-based platform that hosts version control using GIt. Git needs to be installed and used in the local system, then only we can work with GitHub. Guthub is owned by Microsoft, Guthub is very popular platform for developers to share projects and it is also used for hosting open-source projects.

Steps to use Github:

1. **Create an Account**: Sign up for a GitHub account.
    
2. **Create a Repository**: Start a new code project.
    
3. **Collaborate**: Invite others to work with you.
    
4. **Version Control**: Use Git to manage code changes.
    
5. **Explore**: Discover and contribute to open-source projects.
    

**What is Version control? How many types of Version Controls we have?**

As we discussed about about Git , so Git is basically tool to achieve version control. Version control is a technique where we track changes made in any file or any number fof file over a time, also it allows or enables to revert the entire project back to previous version

There are two main types of version control systems: centralized version control systems and distributed version control systems.

1. A centralized version control system (CVCS) uses a central server to store all the versions of a project's files. Developers "check out" files from the central server, make changes, and then "check in" the updated files. Examples of CVCS include Subversion and Perforce.
    
2. A distributed version control system (DVCS) allows developers to "clone" an entire repository, including the entire version history of the project. This means that they have a complete local copy of the repository, including all branches and past versions. Developers can work independently and then later merge their changes back into the main repository. Examples of DVCS include Git, Mercurial, and Darcs.
    

**Why we use distributed version control over centralized version control ?**

1. Better collaboration: In a DVCS, every developer has a full copy of the repository, including the entire history of all changes. This makes it easier for developers to work together, as they don't have to constantly communicate with a central server to commit their changes or to see the changes made by others.
    
2. Improved speed: Because developers have a local copy of the repository, they can commit their changes and perform other version control actions faster, as they don't have to communicate with a central server.
    
3. Greater flexibility: With a DVCS, developers can work offline and commit their changes later when they do have an internet connection. They can also choose to share their changes with only a subset of the team, rather than pushing all of their changes to a central server.
    
4. Enhanced security: In a DVCS, the repository history is stored on multiple servers and computers, which makes it more resistant to data loss. If the central server in a CVCS goes down or the repository becomes corrupted, it can be difficult to recover the lost data.
    

Overall, the decentralized nature of a DVCS allows for greater collaboration, flexibility, and security, making it a popular choice for many teams.

Excersise :

**Install Git on your computer :**

```plaintext
$ yum install git
```

**Create a free account on GitHub:**

a. Go to [GitHub](https://github.com/) and log in to your account.

b.Click on the '+' sign in the top-right corner and select "New repository".

c. Give your repository a name, choose visibility (public or private), and a description.

d. Optionally, choose to initialize the repository with a README file, a .gitignore file, or a license.

e. Click "Create repository".

1. **Create a new repository on GitHub and clone it to your local machine**
    
    **In the above steps, we have created a repo. Now we will close it in our local system**
    
    ```plaintext
    $ git config --global user.name "Your User name"
    $ git config --global user.email "Email id attached with Guthub"
    $ git config --list
    $ git clone <url to repo>
    ```
    
2. Make some changes to a file in the repository and commit them to the repository using Git
    
    ```plaintext
    $  vi README.md
    $ git add .
    $ git commit -m " Added some text in README.md"
    $ git status
    ```
    
3. Push the changes back to the repository on GitHub
    
    ```plaintext
    $ git push origin master
    
    You may get some error while trying to push it to git repo from command
    line. Below is the link that you may find very helpful
    
    https://ginnyfahs.medium.com/github-error-authentication-failed-from-command-line-3a545bfd0ca8
    ```