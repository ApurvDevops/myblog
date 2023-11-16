---
title: "Day 9  Deep Dive in Git and Github for Devops Engineers"
datePublished: Thu Nov 16 2023 19:59:44 GMT+0000 (Coordinated Universal Time)
cuid: clp1m7rvd000209ihhze2gmei
slug: day-9-deep-dive-in-git-and-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700164687028/2d8cdddf-0027-4611-b49f-af6f78c637d8.png
tags: github, git, 90daysofdevops, shubhamlondhe, tws

---

1. What is Git and why is it important?
    
    *Git is a version control system, that allows any software developer, or development project to track changes made in files and coordinate work of those files among multiple people.  
    With the help of GIT, we can keep  
    🔄* ***Version Control***\*: Keep a history of changes and who made the changes  
    🤝\* ***Collaboration***\*: Work with others seamlessly, we can rever to previous  
    changes, if required  
    🧹\* ***Branching***\*: Easily create and manage branches. This is mostly used when  
    work is divided into teams and everyone is working on different features  
    and once done, everyone can merge the feature and create one single  
    project.  
    🌐\* ***Remote Repositories***\*: Share code across the web. Because of this feature of  
    git, so many open-source projects can work and people all around the globe  
    can contribute.  
    📦\* ***Modularity***\*: Split code into manageable pieces, due to which it's now easy to  
    find bugs and make changes in a local repo, test it in the test system before  
    merging and deploying the code in prod.  
    🏗️\* ***Merging***\*: Combine code changes effortlessly, this goes with branching as  
    once a feature is enhanced or created, we first create a separate branch and  
    later on Merge it .\*
    
2. What is the difference Between the Main Branch and the Master Branch?
    
    🛠️ *There is no such difference between the Main and Master branches in Git. The master branch has been central to various development workflows, serving as the main point of reference for stable code. Despite the widespread usage of the master branch, the software development community has recognized the need for a more inclusive default branch name, leading to the introduction of the "main" branch to replace the master branch in Git repositories.*
    
3. Can you explain the difference between Git and GitHub?
    
    ![Git vs. GitHub](https://devmountain.com/wp-content/uploads/2022/01/Gitvs_Github-1a-1.jpg align="left")
    
4. How do you create a new repository on GitHub?
    
    *🧑‍💼 Before creating a new repository in Github, you must have an account in  
          Github, and this account creation is as easy as creating your social media  
          accounts like Facebook or Instagram. And the best part is you can use your*
    
    *gmail account to sign up your GitHub account*
    
    *Below are the steps to Create a Repository in GitHub*
    
    *There are 2 places from where you can create a repository*
    
    ![](https://lh7-us.googleusercontent.com/y_X_2vjS-_FQ5dDsCHWjg-2jzANY0L-sc-g3y8u3m3B43slNXqLKhkAgCqL6Jv4pEHVC2y2dC7YorFtXvXEz37t7kWD_h2YRquy-HbTSgbODhS7tzhkozV16uCDsXgThL0-BVOw9EM2HL5YbVhc_CVd2Ns0PUxdEmP8mzRagvvF3psJSW2ta3U0oXfQY2A align="left")
    
    ***This is available on Left panel***
    
    ![](https://lh7-us.googleusercontent.com/o-23jnBwpmKikHwZhc7Zv_XU4mYYZaXqlJXnZvitmMakw1YM1Ok6G7gZN2czCCAAMGMb3mIPPU7VzWufHUPWzi4zqSHhnTF7jA6Jq_yGleipfBQJ4G0_vImCAeZ2hlLS1NTG-YqSeHaWg51gNaklJZHTXAOaCyujwZBdM5O7SVWukH5-1cGFxF1ardqXTQ align="left")
    
    ***This is available beside your profile icon on Top right side of your GitHub account.***
    
    *Once you Press New Repository, you go to another page to Create a Repository*
    
    ![](https://lh7-us.googleusercontent.com/R5AYdJlJulZgygnsyJxZJp0heqgfIo_ZsDy91cKSY4UmKhb8KcZQkfn148LFG2q1G7p2aaSeo1blJJw3xyRdmAQTYglFu_ofn6vL30V7YFkFK6BqPT_x2_Yisxl3RtD5RxILCABVn8-3tw6vErSnoNxz_rjSCli3GTy5WOoVDq96UQGI3NNzLnYZL3kdQw align="left")
    
    *Once You give a name to your repository and Define its visibility, public or private, you can press “create repository” on the bottom corner of the page.*
    
    *🌟🎉 Tada you have created your first repository*
    
5. What is the difference between local & remote repositories? How to connect local to remote?
    
    🎈 *A remote repository is hosted on a remote (this could be on the internet or an off-site server; it could even be the same machine in a different path) and is shared among multiple team members. A local repository is hosted on a local machine for an individual user.*
    
    In the above example, we have created a repository and now we want to
    
    connect local to remote repository.
    
    1. *Add this as a remote for your local repository by running the following commands in your terminal*
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700162693301/d6bdaaf6-7905-4de0-b888-306fccfd1796.png align="center")
    
    *2    Now add something in this repository, we have added a file "newfile2.txt"*
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700162744418/c59fa15d-fd37-4d25-822c-70a8111812df.png align="right")

3 *Now after adding a new file in git we must commit it so that this should be saved*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700162965364/944cc8e7-d313-45b6-b95b-0db92824a697.png align="center")

*However, you must have seen that while we try to commit, it is through an error asking us to provide a* `user.email and user.name.` *These are the details that are used to know who is committing the changes to git. Basically, this Set your user name and email address, which will be associated with your commits.*

*That can be checked using git command* `git log`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700163179512/002268ac-01d7-4608-afe5-06522af7c9bb.png align="left")

 *4 Now these changes are only saved and committed locally on the desktop on, this has to be pushed in your actual GitHub repository*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700163715413/6a355fb2-0857-4fdf-ba6c-6b6e3c2fc487.png align="center")

*🔑 In the screenshot, you will notice that I am being prompted to add my username and password. To avoid this you will need to authenticate to GitHub as follows.*

*🔑 Create a token in your GitHub: click on your pic in the top right-hand corner of the GitHub → settings → developer settings → personal access tokens → token classic → generate a new token generate token new (classic) → Copy this code and paste it in notepad.*

*🔑 Next run this command with the token included, in your terminal:*

```plaintext
$ git remote set-url origin https://<add your token here>@github.com/S47sawan/devops.git
```

*🔑 Or else you can also paste the same code generated in the above step while prompting for a password when you run git push command, in either case, you will be able to push the changes from the local repo to the central repo with any password authentication or prompts for a password*