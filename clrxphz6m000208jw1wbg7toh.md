---
title: "Day 17 Jenkins Part 2"
datePublished: Sun Jan 28 2024 16:19:42 GMT+0000 (Coordinated Universal Time)
cuid: clrxphz6m000208jw1wbg7toh
slug: day-17-jenkins-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706459161560/8211d159-4863-400d-8841-82918c2c6805.png
tags: jenkins-devops, 90daysofdevops, day17, tws

---

**🏗️What is CI/CD?**

* *CI or Continuous Integration is the practice of automating the integration of code changes from multiple developers into a single codebase. It is a software development practice where the developers commit their work frequently into the central code repository (Github or Stash). Then there are automated tools that build the newly committed code and do a code review, etc as required upon integration. The key goals of Continuous Integration are to find and address bugs quicker, make the process of integrating code across a team of developers easier, improve software quality and reduce the time it takes to release new feature updates.*
    
* *CD or Continuous Delivery is carried out after Continuous Integration to make sure that we can release new changes to our customers quickly in an error-free way. This includes running integration and regression tests in the staging area (similar to the production environment) so that the final release is not broken in production. It ensures to automate the release process so that we have a release-ready product at all times and we can deploy our application at any point in time.*
    

**🏗️ What Is a Build Job?**

* *A Jenkins build job contains the configuration for automating a specific task or step in the application building process. These tasks include gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in different environments.*
    
* *Jenkins supports several types of build jobs, such as freestyle projects, pipelines, multi-configuration projects, folders, multibranch pipelines, and organisation folders.*
    

**🏗️What is Freestyle Projects ??**

*A freestyle project in Jenkins is a type of project that allows you to build, test, and deploy software using a variety of different options and configurations. Here are a few tasks that you could complete when working with a freestyle project in Jenkins:*

**✅ Task-01**

* Create a agent for your app. ( which you deployed from docker in earlier task)
    
* Create a new Jenkins freestyle project for your app.
    
* In the "Build" section of the project, add a build step to run the "docker build" command to build the image for the container.
    
* Add a second step to run the "docker run" command to start a container using the image created in step 3.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706455094689/d45d4e18-3a27-4f18-8534-476ffe643d93.png align="center")
    
    With below configurations
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706455154456/be20f6a7-371a-4d68-ac81-5f0732d018ca.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706455183263/0164dfd3-8371-4658-b8b3-f88f96aa3c05.png align="center")
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706455356824/d315d025-d807-4e4e-bed5-aa103f34e8d2.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706455407616/43249880-36df-417b-af28-5769b2790664.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706455755322/e0267c25-ac25-48a9-8ccc-dcdf5d513062.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706455799263/44c7bb75-863f-4867-8967-43dbf923a2cc.png align="center")
    
    Click on Build now
    
    ![Click on  "BUILD NOW"](https://cdn.hashnode.com/res/hashnode/image/upload/v1706456029404/5553db81-f472-4297-aab4-28bdf21bbb74.png align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706456145572/a66b640d-ca57-4746-b8f3-10d34f4634e4.png align="center")
    
    Application is working now
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706456242974/5495ac05-074a-4ecd-90fa-043efa4bb18a.png align="center")
    
    But if we again try to build the project , it will fail, see below snip
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706456302262/174f3ed9-8a9a-4811-8d4b-625d7414eb32.png align="center")
    
    With below error
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706456320470/40a97e47-65d9-4852-a092-9d3ff78adf85.png align="center")
    
    And here comes the Task 2 that will demonstrate the concept of Docker-compose, in Jenkins Build step
    

**✅Task-02**

* Create Jenkins project to run "docker-compose up -d" command to start the multiple containers defined in the compose file (Hint- use day-19 Application & Database docker-compose file)
    
* Set up a cleanup step in the Jenkins project to run "docker-compose down" command to stop and remove the containers defined in the compose file.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706457983349/ff725611-4ffe-4a00-b06c-3ef9ae99f648.png align="center")
    
    Then try to Build the job as many times as you want, this job will not fail now, because we have already gave docker-compose down , and this stops the container.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706458721329/aa7885a4-ca87-4c17-9e50-b95ea86ba761.png align="left")