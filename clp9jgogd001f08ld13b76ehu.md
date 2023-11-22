---
title: "Day 10 Advance Git & GitHub for DevOps Engineers."
datePublished: Wed Nov 22 2023 09:04:50 GMT+0000 (Coordinated Universal Time)
cuid: clp9jgogd001f08ld13b76ehu
slug: day-10-advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700241121283/c70c1f3b-c6c1-4bfb-988b-36dbd9fd5c3f.png
tags: github, advanced-git, 90daysofdevops, shubhamlondhe, day10-90daysofdevops

---

What is Git Branching? **🌿**

*Git branching provides flexibility, enabling teams to work on different parts of a project simultaneously while maintaining a stable main branch. It's a key feature for collaborative and agile development*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700397248559/33d2ff10-7b25-4ad1-b28d-ebc700a8e589.png align="left")

Branching Strategy **🌿**

*There are many ways or strategies of branching, below is the image that is bit old technique of doing branching where, we initially have 3 Branches, Master, Staging and the Developer*

**📍** *Developer Branch is the branch where we have actual code that is working and running in the production environment and, new feature is created. developed in this branch. Develope branch can also have multiple branches depending on what feature is being developed and who is working on it.*

*Note: Not all developed will work directly on develope branch as this will create a mess if everyone will work on the same branch, So everyone will create a branch from Develope branch i.e some feature branch and then add it to actual develop branch*

**📍** *Staging Branch is the branch where New features are tested that were developed in Develope branch, anything before going to production/Master, will get tested on this branch*

**📍** *Master Branch is the actual branch where actually live/ running / working code of your app resides. And no one works on it. as it is the approved working piece of code of the App.*

*There Could be one Branch in Master/ production, and it's not necessary, this will be there, it depends on the organization, that Branch is a Hotfix branch, this is a patch/ or temporary solution for anything that is creating issues in production and need to be fixed right away. The feature of this Hotfix branch will be integrated into the Develop branch as well so that developers are aware of the Fix that is being done.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700397406647/0bb777c8-273e-4583-9feb-b6ebe64050bd.png align="center")

*However in today's Scenario, we have different ways of doing things and there is no specific Branching strategy, it depends on teams or company size. Still, there is a Jira tool, that is called project management tool used to project tracking*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700399129663/dd8abcb8-04e0-4da4-ae97-272e56322058.png align="center")

**📍** *Whenever a New Toda ( Task/ Feature ) is to be developed it gets first in Jira with a Number and when someone starts working on it, it goes to the In-Progress state. Many a time Jira and Github are connected and once the Ticket goes in In-progress status, we see a New branch is created in the Development branch and everyone can see the code that is being written for that feature. Further it moves to Ready to test (UAT/ Staging) for get tested and once Done, project release is done, it means it goes into Production*

*Let actually now see how this branching is done*

*Below is the screenshot that shows the Current status of the branch of our Repository. And how can we create a new branch and move to a new Branch and back again to the Master branch?*

**📍 Git Status:**

```plaintext
git status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700401489019/ffe80305-b1bb-4ef4-b3c9-9d1e2b911aa3.png align="left")

**📍 *Git Checkout:*** *Creating new file in Dev branch and checking the status also Git adding and committing new changes in dev*.

```plaintext
git checkout -b dev
git status
git add newdev.txt
git add newdev.txt
git commit -m "Dev 1 commit"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700401538796/86b53ffd-091b-4bf6-96f9-be323e3daf95.png align="left")

*While we have added the newfeature in the Dev branch, we will see the files only on Dev branch not in the Dev Branch.*

*Check by doing ls in the dev and master branch*

```plaintext
git status
git ls
git checkout master
git status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700401726153/a272a1e8-cb5b-4673-9242-33b0793307a7.png align="left")

**📍 *Git merging the Dev to master Branch***

```plaintext
git merge dev
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700401801056/2b7ad17c-6896-45c7-a197-d91d91eb355e.png align="left")

*After the dev (new feature) branch is merged with the main branch, the HEAD will now point to the Main branch as shown below. This is mostly visible in Ubuntu system not in centos 7*

*Taking the correct screenshot from the Ec2 machine*

```plaintext
git log --oneline
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700401911340/74326333-8d6f-4cf2-9c2f-f6dd95bff17e.png align="left")

*Diagrammatically, the merge will appear as below now;*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700401934876/b014cde4-387a-4fad-8a92-952e8abf6135.png align="left")

*Adding the latest updates in the git hub*

```plaintext
git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700422285201/9ec48b37-0eb7-45c8-9251-2b0090e5871f.png align="left")

*Another and better way of doing is to first set URL, instead of giving the token as a password in the command*

```plaintext
git remote set-url https://<token>@github.com/<repo_name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700422635477/b6360e8a-dbaa-4340-84a2-73abf769be06.png align="center")

*It will never as for any password moving ahead*

**📍 *Git Pull & Git Fetch***

*Git pull will only pull the changes or updates from the master branch to local repository. However, Git Fetch will pull/bring down all the updates from the Remote repository to the Local repository*

```plaintext
git pull origin master
git fetch
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700423406743/bec4de0c-b938-4a32-80ae-38c22b532290.png align="left")

**📍 *Git Rebase and Git Merge***

*Git Merge is the command that allows the developer to merge the changes from the dev branch to master branch. The logs are modified once the action is completed, but there is one shortcoming with Merge the commits from the develope / feature branch get removed and only the last commit will be visible in the master branch, where the merge happened. along with all the previous commits in the Master branch*.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700560727013/0dd18139-507d-49a6-9a53-08f86e747070.png align="left")

*Git rebase, is a similar command to merge but it keeps the commits that happened in the Develope /feature branch intact or we can say it keeps it in a Linear manner so that all of the Logs are visible on the Master branch well*

*Below is the sample*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700567024272/2d9af5bc-132f-4627-af42-94857177d5ba.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700567127278/0f87e292-6720-4c69-83ea-9a7139d40edc.png align="center")

*Now if we do rebase, the Head will point to the branch that we rebased And will show all the commits in the Develope/Feature branch, that we did.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700567465213/20272dac-f0c6-401c-83a2-9740c46d3c7f.png align="left")

*Commands that were used*

```plaintext
git merge <branch name>
git rebase <branch name>
git checkout <branch name>
```

**📍 *Git Revert & Git Reset :***

*Git Revert is used to revert the changes that were done by mistake. While we do git revert, the wrong work, will be reverted but the commit message will remain there.*

*For Eg. We have added some content in the Dev branch in the New\_3.txt file, and also commited it in the repo with the commit Message "Friday Party"*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700577532272/5b12970e-18a7-4a2a-a016-9397ec4eafc6.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700577639110/a4042588-c067-41aa-b484-ef83b9b207c1.png align="left")

*But later on, revert it*

```plaintext
git revert <hash code of the commit>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700577719650/832d2b9e-cbc4-4fd3-8e2e-613ffa5dc450.png align="left")

*After reverting the lines that were added got removed however the commit message will be there*

***Git Reset***

*Git reset is used to move the current branch head to a specific commit, effectively “resetting” the branch to that commit. It is often used to undo changes or unstaged files.*

*There are three types of git reset:*

*\-* ***$ git reset — soft HEAD~1****— This form of reset is the least destructive. It moves the HEAD pointer to a different commit while leaving your working directory and staging area unchanged  
  
\- $* ***git reset — hard HEAD~1*** *— changes are permanently discarded.  
  
\- $* ***git reset — mixed*** *— default behavior if no option is specified.*

*Below is an example where we see a demo of a soft reset.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700637846374/a2b648b5-dd38-44b5-b6ec-6134f00c5190.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700638751361/c3c22287-d015-4124-8887-f5ef72194beb.png align="center")

*Above are screenshots before doing a Soft Reset.*

*Below we will see screenshots after doing a soft reset*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700638791730/2ede28c8-fce7-4575-bc3f-72ce913ad0a2.png align="center")

*After doing a reset, we see the files have been removed from tracking and now its unstaged, which is evident from the* `git status`

*Another Screenshot that will display what if we do* `git reset --hard <hashcode>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700639206487/7c4273e5-6f72-46a4-856e-c290aa03c2e2.png align="center")

*The difference between both of them is in the case of a Soft reset it is still visible in an untracked file in the staging area, that needed to be staged and committed, it's still available in the local repo. However, when we do a Hard reset, it is removed and cannot be recovered.* ***It's Dangerous to do a Hard reset***