---
title: "Devops Day2"
datePublished: Sun Oct 22 2023 12:10:59 GMT+0000 (Coordinated Universal Time)
cuid: clo1fgnn5000509lac5p6acds
slug: devops-day2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697974707243/1b4e93d3-5be1-408c-8b37-9b31a3cad182.jpeg
tags: devops, linux-for-beginners, 90daysofdevops, tws, devopscommunity

---

Today is day 2 of 90 days of the dev-ops task.

# What is the Linux command to

### What is a Linux Command?

A Linux command is a text-based instruction that a user gives to the Linux operating system to perform a specific task or operation. These commands are executed in the terminal, a text-based interface that allows users to interact with the system by typing commands and receiving text-based responses.

Linux commands are essential for a variety of tasks, from managing files and directories to configuring system settings and running applications. The power of Linux commands lies in their efficiency, precision, and versatility.

### **Structure of a Linux Command**

A typical Linux command follows a specific structure:

Linux Command Structure

Command Name: This is the name of an operation you want to perform. 

For example, if you want to list all files and directories in a directory, ls is a command

* **Options:** Options modify/expand the behaviour of a command. They are preceded by a hyphen (-) and are typically single letters. For instance, the -l option with the ls command displays a detailed list.
    
* Arguments: Arguments are the targets or operands on which the command operates. They can be files, directories, or other items you want the command to act upon.
    

  
Let's look at a few common Linux commands to illustrate their usage.

### Common Linux Commands

1\. ls - List Files and Directories

The ls command is used to list files and directories in the current directory. For example, to list the contents of your home directory, you would type:

 ls ~

2\. pwd - Print Working Directory

The pwd command displays the current directory's full path. To see your current directory, simply type:

pwd

3\. mkdir - Make a Directory

To create a new directory, you can use the mkdir command. For instance, to create a directory named "my\_folder," use:

mkdir my\_folder

4\. cp - Copy Files

The cp command is used to copy files and directories. To copy a file named "file.txt" to a directory called "backup," you would type:

cp file.txt backup/

5\. rm - Remove Files

To delete a file, the rm command is employed. Be cautious with this command, as it doesn't move files to a trash/recycle bin. To remove a file named "unwanted.txt," use:

rm unwanted.txt

Few Directory Commands

* cd ~  or just cd  --&gt; change directory to the home directory
    
* cd - --&gt; Go to the last working directory.
    
* cd .. --&gt; change directory to one step back.
    
* cd ../.. --&gt; Change directory to 2 levels back.
    

Linux commands can appear complex at first, but with practice, they become a powerful tool for managing your Linux system. These are just a few basic commands, and there are hundreds more to explore. Linux is very powerful and if not handled properly it may lead to devastating results for your infra

# Few Task for Day 2

1. Check your present working directory.
    
    sol: pwd
    
2. List all the files or directories including hidden files.
    
    sol: ls -al
    
3. Create a nested directory A/B/C/D/E
    
    sol: mkdir -p A/B/C/D/E