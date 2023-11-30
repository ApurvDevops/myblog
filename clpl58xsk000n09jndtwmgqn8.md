---
title: "Day 12 Docker basics Part 1"
datePublished: Thu Nov 30 2023 12:00:09 GMT+0000 (Coordinated Universal Time)
cuid: clpl58xsk000n09jndtwmgqn8
slug: day-12-docker-basics-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701344431083/8e099ae1-38af-46be-8b6b-eac7d2f477cd.png
tags: 90daysofdevops, shubhamlondhe, day12, dockerbasic, installingdockeron-centos7

---

***What is Docker?***

*Docker is an open platform that can be said a* ***Platform as a service*** *for developing, shipping and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. Because of Docker the so-called dilemma, that "It runs on my system, but not running on your system" is removed*

*Before we dig deep into docker we must understand the concept of virtualization*

***Virtualization*** *is a technology that allows multiple operating systems (OS) or applications to run on a single physical machine. It involves creating virtual instances of computing resources, such as servers, storage devices, or networks, which can operate independently of one another on the same hardware. This is achieved by using a hypervisor or virtual machine monitor (VMM), a software layer that abstracts and manages the underlying physical hardware*

*The key component of Virtualization is Hypervisor & there are 2 types of Hypervisor*

***Type 1 Hypervisor****: This is a small OS or Firmware (aka Hypervisor)that is installed on Bare Metal, and virtualization is done on this.*

***Type 2 Hypervisor:*** *It treats your OS as a Host and runs over it. On top of this Software like Virtual Box and Vmware kind of tools are used, which can be used, to Install different OSs, Where your Base OS interacts with Vmware / Virtual Box. and shares the resource as per need.*

*The biggest Disadvantage is that you need to install a complete OS on Vmware to work on it. And that takes wholesome resources of your host machine, on which Hypervisor is running.*

![virtual machine - Are hardware drivers needed to be installed on the  management OS of a type 1 hypervisor? - Super User](https://i.stack.imgur.com/TAMdL.png align="left")

*Why Docker is Lightweight?*

*Docker uses a different type of Virtualization, whereas in traditional Virtulization complete OS along with the Kernel is installed on VMware, however, in the case of Docker, we are using the kernel of the host operating system because of which the resource usage is optimized.*

***Docker Architecture***

* *The Docker client talks to the docker host/server, which has Docker Deamon(dockerd) in it, which is installed in the host machine.*
    
* *Docker is based on creating images and using the image to create a container.*
    
* *In case the requested image is not present locally then dockerd makes a call to the DockerHub/ Docker registry and pulls the image from there to the host machine, which in turn helps to create and run a container.*
    

![Understanding Docker Architecture | by Vikram Gupta | Medium](https://miro.medium.com/v2/resize:fit:1400/1*2O2XM1Q_LhOWCDEhXScf8w.png align="left")

*Very Important point that must be understood*

*Program File or setup Files is used to create Image and from that image, Containers are created.*

* *Files ------ &gt; Images ------ &gt; Containers*
    
* *From Docker, File Image is created and From Image Container is created*
    

*So basically image is a set of files that is used to create and run a container.*

*Docker components*

1. *Docker Engine: Docker Engine is a core component of the Docker environment that give a platform for creating and running container.*
    
2. *Docker Deamon: Also known as DockerD / dockerd, is a background process that runs on the host system, for running and managing the container in the host system.*
    
3. *Docker Container: This is an isolated, standalone executable package that has everything needed to run a piece of software, including codes, libraries, executables etc. An Important point to note here is Docker container is a platform to provide containerization. Docker is a container orchestration tool*
    

***ContainerD: It's an Open source tool from CNCF, which focuses on providing a platform to run the containers. Containerd is an industry-standard runtime that serves as the underlying container engine for many container orchestration platforms like Docker***

1. *Docker CLI/ Docker client: This is a Command Line Interface, that is used to give commands to DockerD. The commands always start with docker &lt;command\_name&gt;*
    

*eg. docker ps, list all container*

1. *Docker image: Docker Engine uses Image as a basis for creating and running the container. Image is a lightweight, standalone executable package that has everything to run a piece of program.*
    
2. *Docker File: The Docker File has all the set of steps that are needed to create a docker image. It defines the base image, required dependencies, and specific commands to run the container.*
    
3. *Docker Hub/ Docker registry: Treat Docker Hub as a Git hub where we keep our development repository, but in Docker Hub we store images. In Docker Hub or Docker Repository, we can push, pull, tag our Docker Images, which can be pulled and used at any part of the world using a simple command. This is a cloud-based repository and is also used for community contribution*
    

```plaintext
docekr pull <image_name>:<tag>
```

*Installing Docker in Centos7*

```plaintext
#Updating the Package Database
sudo yum check-update

# It will add the official Docker repository, download the latest version of Docker, and install it:
curl -fsSL https://get.docker.com/ | sh

#It will start Docker Daemon
sudo systemctl start docker

#Check the status if it started
sudo systemctl status docker
```

*Adding a user in which docker is run, so that every time you need not give Sudo while running the Docker command. Once you add the user to the Docker group , make sure to restart your system using or even you can reload the Docker*

```plaintext
sudo usermod -aG docker <username>
systemctl restart
or 
systemctl restart docker
```

# Tasks

* Use the `docker pull` command to pull images from the docker hub
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701003363592/3f300f36-45b5-4ff9-8c20-0dd957ac0101.png align="center")
    
* Use the `docker images` command to see the images in your local host
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701003426151/ea51f220-895f-4441-9513-42a0442d6a26.png align="center")
    
* Use the `docker run` command to start a new container and interact with it through the command line. \[Hint: docker run hello-world\]
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701003460852/38916fe3-fd6e-4093-a0c3-1f50fbd004aa.png align="center")
    
    *Or apparently, we can also use the image in the local host to run and create a container using the run. Normally it will exit after running, depending on what's in image that we are running*
    
    ```plaintext
    docker run image_name
    ```
    
* Use the `docker ps` command to check the container status
    
    ```plaintext
    docker ps # will show if the container are running
    docker ps -a # will show all the continer that are running and exited
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701003574158/3d066b4d-6af8-4d23-87a0-2fef848f8ece.png align="center")
    
* Use the `docker inspect` command to view detailed information about a container or image.
    
    ```plaintext
    docker inspect <continer_name or Image_name>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701003870434/c6050a3c-0fe1-4ce1-b976-9ee14d05fd07.png align="center")
    
* Use the `docker port` command to list the port mappings for a container.
    
* Use the `docker stats` command to view resource usage statistics for one or more containers.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701332404225/74a1f252-ccad-4a90-b5a8-e082bc01f4fa.png align="center")
    
* Use the `docker top` command to view the processes running inside a container.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701332460902/2e603daf-c0d3-4de5-8ff5-1a4ec8cc8047.png align="center")
    
* Use the `docker save` command to save an image to a tar archive.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701338895150/241b8edd-c7a2-4b41-8386-0c45f9fa0ee5.png align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701338913458/cb97a0ba-e201-4966-b2c2-efe58884dba6.png align="left")
    
* Use the `docker load` command to load an image from a tar archive.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701339129432/1b9f3626-5590-4cea-92ce-4404b19d322e.png align="center")
    
* Use the `docker kill` command to load an image from a tar archive.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701332483412/37b5abcb-482a-4d33-9f71-1ec342f98d78.png align="center")
    

Docker File:

*As described in the basics of Docker, a Dockerfile, is a file, that has all the steps to create an image from the program file, and that Image is the user to create a container.*

*Below is a simple project for a Dockerfile of a simple Java application*

```plaintext
Hell.java (Simple java program)

public class Hello {
  public static void main(String Args[]){
      System.out.println("Hello New Image");
     }
}

Dockerfile
# pull base image for java 11
FROM openjdk:11

#create a working directory to copy all the files
WORKDIR /app

# Code copy to image for running continer 
COPY Hello.java /app

#Compile the code
RUN javac Hello.java

# App is now ready to run , pass the arguments
CMD ["java","Hello"]
```

After this file is created we just Need to build it and Run the container from the Image

```plaintext
docker build -t java-app:v1
# v1 is a tag

docker run java-app:v1
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701344075917/6f571950-9484-4143-8a67-7cd4352636c8.png align="center")