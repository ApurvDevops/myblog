---
title: "Day 7 Task: Understanding package manager and systemctl"
datePublished: Wed Nov 01 2023 10:20:55 GMT+0000 (Coordinated Universal Time)
cuid: cloflxmm0000809l989fg7tw1
slug: day-7-task-understanding-package-manager-and-systemctl
tags: linux, 90daysofdevops, shubhamlondhe, tws, systemd-vs-systemctl

---

### **What is a package manager in Linux?**

In simpler words, a package manager is a tool that allows users to install, remove, upgrade, configure and manage software packages on an operating system. The package manager can be a graphical application like a software center or a command lines tool like apt-get or Pacman.

You’ll often find using the term ‘package’ in tutorials and articles. To understand a package manager, you must understand what a package is.

### **What is a package?**

A package is usually referred to as an application but it could be a GUI application, command line tool or a software library (required by other software programs). A package is essentially an archive file containing the binary executable, configuration file and sometimes information about the dependencies.

### **Different kinds of package managers**

Package Managers differ based on the packaging system but the same packaging system may have more than one package manager.

For example, RPM has Yum and DNF package managers. For DEB, you have apt-get, aptitude command line-based package managers.

**APT:** (Advanced Package Tool): Used in Debian and Ubuntu-based distributions.  
**YUM**:(Yellowdog Updater, Modified): Used in Red Hat and CentOS-based distributions.  
**DNF:** (Dandified YUM): An improved version of YUM, used in newer Red Hat distributions.  
**RPM:** Package Manager: Created by Red Hat. RPM is the Linux Standard Base packaging format and RPM has YUM and DNF package managers.

**Tasks**

1. You have to install docker and Jenkins in your system from your terminal using package managers
    

**Installing Docker in Centos**

**a.** Before we install Docker Engine in Centos New host we need to we need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

**Setup a Yum Repository**

Install the `yum-utils` package (which provides the `yum-config-manager` utility) and set up the repository.

```plaintext
$ sudo yum install -y yum-utils 
$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo  
```

Install Docker Engine

```plaintext
 $ sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

 Incase you want to Install Specific version
 $ yum list docker-ce --showduplicates | sort -r
```

Installation is done, we just need to start and check the status of our Docker

```plaintext
$ systemctl Start docker
```

```plaintext
$ systemctl status docker 
```

**Installing Jenkins in our System**

. Before we install jenkins in our host, we must have java installed , as Jenkins needs java to execute

Step 1 : Install Java

```plaintext
$ sudo yum  install java-1.8.0-openjdk-devel
```

Step 2: Add Jenkins Software Repository

This step is to turn on the repository for Jenkins. To do this, use the following command to bring in the GPG key and add repo to your system

```plaintext
  $ sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
  $ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

Step 3: Install Jenkins on Centos 7

```plaintext
$ yum install jenkins
```

installation is done, just start the service and check its status

```plaintext
$ yum start jenkins
$ yum status jenkins
```

### **systemctl and Systemd**

`systemctl` and `systemd` are two key components of the modern init system used in many Linux distributions. They play a vital role in managing and controlling services, processes, and system resources on a Linux system.

**systemd**:

**systemd** is a system and service manager for Linux operating systems. It is responsible for initializing the system, managing system services, and handling system resources. It replaces the older init(initd) system, with improved process handing

* systemd is designed to improve the initialization and management of system services, providing a more parallel and efficient startup process compared to traditional init systems.
    
* It introduces the concept of service units, which are configuration files that define how services are started, stopped, and managed.
    

**systemctl:**

**systemctl** is a command-line utility that interacts with systemd. It allows you to control and manage **system services, view their status, enable or disable them, and perform various other system-related tasks.**

* You can use `systemctl` to start, stop, restart, reload, enable, disable, and check the status of services. For example:
    

`systemctl start service-name`: Starts a service.

* `systemctl stop service-name`: Stops a service.
    
* `systemctl restart service-name`: Restarts a service.
    
* `systemctl enable service-name`: Enables a service to start automatically at boot.
    
* `systemctl disable service-name`: Disables a service from starting automatically at boot.
    
* `systemctl status service-name`: Shows the status and information about a service.
    

Below is the flow how systemd and systemctl actually works ?

* systemd reads unit files (service unit files, socket unit files, etc.) that define how services and other system components should be managed.
    
* systemctl is used to interact with these unit files and control services, timers, sockets, and other systemd-managed units.
    
* systemctl communicates with the systemd daemon to start, stop, and manage services based on the unit files' configurations.
    

**systemctl Vs service**

<mark>When invoked, the </mark> *<mark>service</mark>* <mark> command looks up the script to run at the path </mark> *<mark>/etc/init.d/SCRIPT</mark>*<mark>.</mark> It then runs the script, passing the *COMMAND* unchanged as the arguments. We can, of course, run the script using its path directly, bypassing the *service* command. But, **the *service* command guarantees a predictable running environment by removing most of the variables and setting the root path as the current working directory.**

<mark>The&nbsp;</mark> *<mark>systemctl</mark>* <mark> command interacts with the SystemD service manager to manage the services.&nbsp;</mark> **<mark>Contrary to&nbsp;</mark> *<mark>service </mark>* <mark>command, it manages the services by interacting with the SystemD process instead of running the init script</mark>**<mark>.</mark>

Here's a comparison of using the `systemctl` and `service` commands to start, stop, and restart the Nginx web server in a tabular format:

Below is an example of how both commands are used to start, stop and restart nginx server.

| Action | `systemctl` Command | `service` Command |
| --- | --- | --- |
| Start Nginx | `sudo systemctl start nginx` | `sudo service nginx start` |
| Stop Nginx | `sudo systemctl stop nginx` | `sudo service nginx stop` |
| Restart Nginx | `sudo systemctl restart nginx` | `sudo service nginx restart` |

Both `systemctl` and `service` can be used to control Nginx, but `systemctl` is more commonly used on systems with the systemd init system, which is the case for many modern Linux distributions. The `service` command is more common on older systems that use traditional init systems. It's a good practice to check which command is available on your specific Linux distribution.