---
title: "Day 6 Task: File Permissions and Access Control Lists"
datePublished: Sat Oct 28 2023 20:32:14 GMT+0000 (Coordinated Universal Time)
cuid: cloai0dj8000c09jxg75738lf
slug: day-6-task-file-permissions-and-access-control-lists
tags: linux, 90daysofdevops, shubhamlondhe, day6, tws

---

1 .Create a simple file and do `ls -ltr` to see the details of the files

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698490574052/7d4d23fe-046a-445b-9aa1-0d5098240f99.png align="left")

We have created file "testfile.txt" using the touch command and then ran ls -ltr

there are six ----------, this denote the type of file and access provided to the file that is created

Types of file:

There are six types of files:

(-)   : (Regular file) (Eg : text file,imagefile,binary...)               

d : (Directory)           

**c** : (Character device file) | (Character and block device files allow users and programs to communicate with hardware peripheral devices.) The server console is a character device file. Talks to devices in a character by character (1 byte at a time)

**b** : (Blockdevice file)      | (Eg: storage LUN files)Talks to devices 1 block at a time ( 1 block = 512 bytes to 32KB)

**s** : (Local socket file used for communication between processes)

**p** : (Named Pipe)

**l** : (Symbolic link)

Then the next part gives details about the access provided to the Owner/User, Group, and Other user consecutively.

Below is the image that shares the info when we do ls -ltr

![r/linux - Try to explain linux shell ls command in short](https://preview.redd.it/l48w7ytz91461.jpg?width=640&crop=smart&auto=webp&s=a45b11a6694842fe973d3f1659f328348834df45 align="left")

Below is the image that shows how the file's permission in calculated

![chmod Cheatsheet : r/linux](https://preview.redd.it/vkxuqbatopk21.png?auto=webp&s=81f97dac1e1ceb5054ee43cbe96ec6fa55215695 align="left")

* The highest permission is –7—(4+2+1)
    
* Maximum permission -  777, but effective 666 in case of a file for security reasons in Linux, no user will get execute permission.
    
* For the directory case, effective permission is 755
    
* The lowest permission is –000 not recommended
    
* Minimum permission – effective permission 644 in case of a file  \* \[   (umask \[UNIX MASK\] value- 022 )  \]
    
* For directory case default permission is execute permission.
    

Each of the three permissions is assigned to three defined categories of users. The categories are:

*    owner   —   The owner of the file or application.
    
    "chown" is used to change the ownership permission of a file or directory.
    
* group — The group that owns the file or application.
    
    "chgrp" is used to change the group permission of a file or directory.
    
* others — All users with access to the system. (outised the users are in a group)
    
    "chmod" is used to change the other users permissions of a file or directory.
    

1. Write an article about File Permissions based on your understanding from the notes.
    

Special Permission

**SUID (Set User Id)**: If SUID is set on an executable file and a normal user execute it then the process will have the same rights as the owner of the file being execute instead of the normal user. (Eg: password command)

\[root@server 90days\]# ls -ltr /usr/bin/passwd -rwsr-xr-x. 1 root root 27832 Jun 10 2014 /usr/bin/passwd

 ## passwd command is suid set so any non-root user can change their own password, as its executes as root.

\[root@server 90days\]# ls -ltr testfile.txt -rw-r--r--. 1 root root 0 Oct 28 18:58 testfile.txt ##1st field is file type , next 3\*3 is for access permission(user, group, other), link count, owner of the file, group owner, size, date and file name.

\[root@server 90days\]# chmod u+s testfile.txt ## ## suid applied on user permission so u+s.

\[root@server 90days\]# ls -lrts testfile.txt 0 -rwSr--r--. 1 root root 0 Oct 28 18:58 testfile.txt ## "S" denotes suid applied on the file .

\[root@server 90days\]# ls -lrts testfile.txt

\[root@server 90days\]# ls -lrts testfile.txt 0 -rwsr--r--. 1 root root 0 Oct 28 18:58 testfile.txt ## If the user has execute right and suid both then instead of "S"(Capital) it will show "s".

\[root@server 90days\]# chmod 4744 testfile.txt ## This is absolute method the first field(hear 4) is for special permission(hear suid) and remain are for user,group and other .

4-SUID

2-SGID

1-STICKY BIT

SGID(Set Group Id): If SGID is set on any directory, all subdirectories and files created inside will get the same group ownership as the main directory, it doesn't matter who is creating.

 The owner of the file will be the file creator and the group owner will inherit from the directory. : If SGID is set on any directory, all subdirectories and files created inside will get the same group ownership as the main directory, it doesn't matter who is creating.

The owner of the file will be the file creator and the group owner will inherit from the directory.

\[root@server 90days\]# mkdir testdir

\[root@server 90days\]# ls -ld testdir

drwxr-xr-x. 2 root root 6 Oct 28 19:07 testdir

\[root@server 90days\]# chmod g+s testdir/ ## sgid applied on group permission so g+s(We can use g+2 also).

\[root@server 90days\]# ls -ldr testdir/

drwxr-sr-x. 2 root root 6 Oct 28 19:07 testdir/ ## Here is "s" is on group execute filed

**STICKY BIT** : it is used on folders in order to avoid deletion of a folder and its content by other users though they having write permissions on the folder contents. Except owner and root user, No one can delete other users data in this folder(Where sticky bit is set). though other users have full permissions.

\[root@server 90days\]# chmod o+t testdir/

\[root@server 90days\]# ls -ldr testdir/

drwxr-sr-t. 2 root root 6 Oct 28 19:07 testdir/ ## Hear "t" is for sticky bit . As execute permission is there for other so its showing "t" instead of "T".

Lets try to change the persmission

\[root@server 90days\]# chmod 744 testdir/

\[root@server 90days\]# chmod o+t testdir/

\[root@server 90days\]# ls -ld testdir/

drwxr-Sr-T. 2 root root 6 Oct 28 19:07 testdir/ ## Now we dont have execute persmission in directory other than user so "T" is showing.

1. Read about ACL and try out the commands `getfacl` and `setfacl`
    

Standard file permissions are satisfying when files are used by only a single owner and a single designated group. However, If we want to give access to a user or group which not listing on default file permission, then ACL will come in use.

With ACL, you can grant permission to multiple users and groups, identified by user name, group name, UID, GID. using the same permission flags used with regular file permission: read, write and execute.

To check ACL is enable in our file system or not type cat /etc/fstab, where if mounted file system is defaults means ACL is enable in our file system.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698524376710/6f147708-ab8d-47ca-a57e-fc0ead104521.png align="center")

\[root@server 90days\]# touch testacl

\[root@server 90days\]# ls -ltr testacl

\-rw-r--r--. 1 root root 0 Oct 29 02:25 testacl #This (.) is denote for special permission and ACL.

\[root@server 90days\]# getfacl testacl

file: testacl

owner: root

group: root

user::rw- group::r-- other::r--

\[root@server 90days\]# useradd acluser #added one user

\[root@server 90days\]# setfacl -m u:acluser:rw testacl ## Hear we have set read and write permission for *acluser* user, who dont have access to the file before.

\[root@server 90days\]# getfacl testacl

file: testacl

owner: root

group: root

user::rw-

user:acluser:rw-

group::r--

mask::rw-

other::r--

\[root@server 90days\]# ls -ltr testacl

\-rw-rw-r--+ 1 root root 0 Oct 29 02:25 testacl ## If ACL set to any file, then "+" sign will come on "ls -ltr" output

To remove setfacl value command is

setfacl -x username filename

\[root@server 90days\]# setfacl -x acluser testacl \[root@server 90days\]# getfacl testacl

file: testacl

owner: root

group: root

user::rw- group::r-- mask::r-- other::r--

\[root@server 90days\]#