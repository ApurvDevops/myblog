---
title: "Day 11 Advanced Git and Github :: Part 2"
datePublished: Thu Nov 23 2023 14:18:16 GMT+0000 (Coordinated Universal Time)
cuid: clpba3lxb00010ajqepsocyoe
slug: day-11-advanced-git-and-github-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700748853235/ce1ef556-2881-43ca-a8d6-ffd5c0c66428.png
tags: github, 90daysofdevops, tws, day11of90daysof-devops

---

***Git Cherry Pick***

*Git cherry-pick is a command that allows you to select specific commits from one branch and apply them to another. This can be useful when you want to selectively apply changes that were made in one branch to another.*

*To use git cherry-pick, you first create two new branches and make some commits to them. Then you use* `git cherry-pick <commit_hash>` *command to select the specific commits from one branch and apply them to the other.*

*Below is a screenshot of the Demo*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700657707910/f85e60d1-c127-4df4-a691-c560baf9db36.png align="center")

```plaintext
git cherry-pick <hash code of commit that need to be added in other branch>
```

*Another important point to be noted is you should be on the brach where you want to add the feature*

***Git Stash:***

*Git stash is a command that allows you to temporarily save changes you have made in your working directory, without committing them. This is useful when you need to switch to a different branch to work on something else, but you don't want to commit the changes you've made in your current branch yet.*

*To use Git stash, you first create a new branch and make some changes to it. Then you can use the command git stash to save those changes. This will remove the changes from your working directory and record them in a new stash. You can apply these changes later. git stash list command shows the list of stashed changes.*

*You can also use git stash drop to delete a stash and git stash clear to delete all the stashes.*

```plaintext
git stash <File name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700726700501/e35de2e0-0645-4490-a14f-543be97b402e.png align="center")

***Resolving Conflicts :***

*Conflicts can occur when you merge or rebase branches that have diverged, and you need to manually resolve the conflicts before git can proceed with the merge/rebase. git status command shows the files that have conflicts, git diff command shows the difference between the conflicting versions and git add command is used to add the resolved files.*