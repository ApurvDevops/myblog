---
title: "Day 20 Jenkins Agents And Web-hooks"
datePublished: Mon Mar 04 2024 10:41:48 GMT+0000 (Coordinated Universal Time)
cuid: cltcta441000608ib3rqba2dx
slug: day-20-jenkins-agents-and-web-hooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709548845541/54c24a8d-7dc9-4296-a29e-3903d5fb4ea3.png
tags: webhooks, jenkins-devops, jenkins-agent-configured, jenkins-master-server, day-20, advance-jenkins

---

# Jenkins Agents

**Jenkins Master (Server)**

*🧑‍💼 Jenkins’s server or master node holds all key configurations. Jenkins master server is like a control server that orchestrates all the workflow defined in the pipelines. For example, scheduling a job, monitoring the jobs, etc.*

**Jenkins Agent ( Slave)**

*🧑‍💼 An agent is typically a machine or container that connects to a Jenkins master and this agent that actually execute all the steps mentioned in a Job. When you create a Jenkins job, you have to assign an agent to it. Every agent has a label as a unique identifier.*

*When you trigger a Jenkins job from the master, the actual execution happens on the agent node that is configured in the job.*

*A single, monolithic Jenkins installation can work great for a small team with a relatively small number of projects. As your needs grow, however, it often becomes necessary to scale up. Jenkins provides a way to do this called “master to agent connection.” Instead of serving the Jenkins UI and running build jobs all on a single system, you can provide Jenkins with agents to handle the execution of jobs while the master serves the Jenkins UI and acts as a control node.*

![](https://user-images.githubusercontent.com/115981550/215276859-fa140ab7-e905-41c9-8ae2-1eef577c5e72.png align="center")

**Pre-requisites**

Let’s say we’re starting with a fresh Ubuntu 22.04 Linux installation. To get an agent working make sure

* Install Java ( same version as Jenkins master server ) and Docker on it.
    
* Both the Master and Slave should be in Same VPC ID
    
* In case you are running job using Docker, so agent should have Docker and Docker-compose
    

Dashboards-&gt;Nodes-New Nodes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709222423190/d5e5820b-4eb3-4796-8b12-fb04814be44b.png align="left")

**Label**: Whatever you are mentioning the name of Label this will be used in out Jenkins pipeline so keep a note of it.

Remote root Directory, will be the path of Directory in Master server, where project will be stored

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709220103352/59ee05ce-2556-42cd-8863-9901a12620ee.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709222236599/c9665657-66a9-4f53-a1ed-ff262238f85b.png align="center")

Host: Will be your Jenkins agent public IP address

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709222274062/7632c9b0-c331-40eb-a422-b0a2e2238093.png align="center")

We will create a Credentials, where the key that we are giving her will be Public key, that was created using ssh-keygen command. We will paste that public key here.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709222794490/54b6ff5b-efda-4392-a3d4-f34790a5ec41.png align="center")

Once above setup is done, we must go to nodes and Click on `Launch Agent` or `Relaunch agent` (if you are restarting your server again, then it will show to relaunch agent)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709481736639/316d82d1-9810-46e6-a80d-7dc285459b7d.png align="center")

And once your agent configuration is successful , you will see below output

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709481846645/ac91afd9-8a86-465f-bfa7-b31a2dbe4342.png align="center")

And once you are done we need to give the agent name in which agent should the pipeline will execute.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709481988951/451f21fe-308d-4472-a53f-f59b2f7ec8f1.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709481962322/7496e165-99df-4534-ba37-61dc824d491b.png align="left")

As we can now see the job is now running on Jenkins-agent

# **Web-Hooks**

*In above example we have have created a pipeline, where we have written the code in that pipeline, In case if the Sever is crashed then the code will go away, so we need a backup or strategy . That's where WEB-HOOKS come into picture.*

*So this is basically, you create a Jenkins File and store it in GitHub Repo. And create a link between your Jenkins job and Jenkins file that is stored in GitHub repo*

*And when ever any change is happened in Jenkins File , pipeline gets triggered and the job starts running, And Obviously, you can control the behaviour of triggering the pipeline*

**Steps to setup the Web hook**

1. First we need to setup a repo, with the Jenkins file and the stage in it as required
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709547387011/4ed90322-fb22-48a9-bdae-620fec60b2bc.png align="center")

2. Create Jenkins Pipeline job with this GitHub repo
    

![](https://kodekloud.com/community/uploads/db1265/optimized/3X/8/8/88291c0f1a871a7c60d3dbc0defa5d1312032f51_2_624x273.png align="left")

![](https://kodekloud.com/community/uploads/db1265/optimized/3X/7/4/7450f3ff41a842e442490ad89f09881f5fbeee07_2_624x425.jpeg align="left")

Under Pipeline &gt; Definition, choose Pipeline script from `SCM,` then choose Git and `paste the link source code git` . Next, update Branch Specifier from `master to main` which is the default branch of GitHub.

![Screen Shot 2023-06-23 at 11.41.03](https://kodekloud.com/community/uploads/db1265/optimized/3X/e/3/e3f8bcda9ad9018918d15e7a765192fdf549d4ed_2_690x389.png align="left")

Click to checkbox GitHub hook trigger for GITScm polling under Build Triggers.

![](https://kodekloud.com/community/uploads/db1265/optimized/3X/d/2/d2bbacc299f998ead82a895e9cd8546884ad4b72_2_624x235.png align="left")

![](https://kodekloud.com/community/uploads/db1265/optimized/3X/b/a/ba4bac17eeea232ee1288a6489667c4c726687ca_2_624x204.png align="left")

That’s all, now you can scroll down and click the Save button.  
In my experience, whenever we have just configured a new Jenkins job, we should try to build this job manually to ensure our actions will work as expected.

So we click Build Now to start executing Jenkins-file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709548133822/70922418-bfe2-4d48-afb7-46d187f32af6.png align="center")

3. Configure web-hook GitHub for triggering Jenkins job
    

We can see the pipeline is built successfully. So now, we can set up the GitHub web hook to trigger Jenkins whenever developers push the new code.

From the GitHub repository, which we have just created above, click on Settings &gt; Web-hooks &gt; Add Webhook.

![](https://kodekloud.com/community/uploads/db1265/optimized/3X/f/c/fcd593fe9f7513856e0e98fb56564ebb6be8accb_2_624x297.png align="left")

Under Payload URL, input your Jenkins URL/github-webhook/ and click Add webhook button.

**\*\*After URL we need to write git-hub-web-hook, because we want the git to know that we are using web-hook to poll and then trigger the pipeline, we have already mention the git-hub repo, while configuring, so no need to give that again**\*\*  
An Example of Payload URL: [http://localhost:8080/github-webhook/](http://3.1.80.7:8080/github-webhook/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706535044804/8f231f0d-f3ad-4c13-8a56-7fd353c3f90c.png align="left")

Even you can see for which event you may want to trigger the web-hook. Its the option "Let me select individual events"

Once added , you can now wait it to be Green Tick after adding the web-hook, as shown below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706535320030/9d9cce59-f6dc-4cd1-941f-6ba5d9e32466.png align="left")

Now you can try making any changes in Jenkins-file or add a README file that will also work and the pipeline will get triggered.

*Thank you for reading this Blog. Hope you learned something new today! If you found this blog helpful, please like, share, and follow me for more blog posts like this in the future😊😊*