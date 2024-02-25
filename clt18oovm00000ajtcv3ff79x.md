---
title: "Day 18 Jenkins part 3 ( Advanced | Declarative Pipeline)"
datePublished: Sun Feb 25 2024 08:19:48 GMT+0000 (Coordinated Universal Time)
cuid: clt18oovm00000ajtcv3ff79x
slug: day-18-jenkins-part-3-advanced-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708849174082/f0e35c5d-7006-490e-95ff-a443383d21eb.png
tags: jenkins-devops, 90daysofdevops, declarativepipelines

---

***What is Pipeline -****A pipeline is a collection of steps or jobs interlinked in a sequence.*

***Declarative:****Declarative is a more recent and advanced implementation of a pipeline as a code.*

***Scripted:****Scripted was the first and most traditional implementation of the pipeline as a code in Jenkins. It was designed as a general-purpose DSL (Domain Specific Language) built with Groovy.*

# Why you should have a Pipeline

*The definition of a Jenkins Pipeline is written into a text file (called a*[*Jenkinsfile*](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)*)*[*which in tu*](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)*rn can be committed to a project’s source control repository.  
This is the foundation of "Pipeline-as-code"; treating the CD pipeline as a part of the application to be versioned and reviewed like any other code.*

*Creating aJenkinsfile and committing it to source control provides a number of immediat*[*e benefits:*](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)

* *Automatically creates a Pipeline build process for all branches and pull requests.*
    
* *C*[*ode review/i*](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)\*teration on the Pipeline (along with the remaining source code).\*Pipeline s[yntax](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)
    

```plaintext
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                //
            }
        }
        stage('Test') {
            steps {
                //
            }
        }
        stage('Deploy') {
            steps {
                //
            }
        }
    }
}
```

# Task-01

* Create a New Job, this time select Pipeline instead of Freestyle Project.
    
* Follow the Official Jenkins [Hello world example](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
    
* Complete the example using the Declarative pipeline
    

# Steps

There are 2 ways of doing it : Below is the First way of doing

1. Install the [**Docker Pipeline plugin**](https://plugins.jenkins.io/docker-workflow/) through the **Manage Jenkins &gt; Plugins** page
    
2. After installing the plugin, restart Jenkins so that the plugin is ready to use
    
3. Copy one of the [examples below](https://www.jenkins.io/doc/pipeline/tour/hello-world/#examples) into your repository and name it `Jenkinsfile`
    

![Classic UI left column](https://www.jenkins.io/doc/book/resources/pipeline/classic-ui-left-column.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708846861968/8f94a5cc-d3d4-48b1-93f7-2b605f0eb47d.png align="center")

Once the project is created, go to Pipeline section and paste the code

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708848287214/b3fb6851-72c4-4a4a-b0ae-cb5f0e65f598.png align="center")

```plaintext
pipeline {
    agent { docker { image 'python:3.12.1-alpine3.19' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
```

And Simply Run the project manually, "Build Now"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708848379759/570c81fd-a293-4da1-9e55-16b73c155df8.png align="center")

Below is the Second way of doing

1 . Create a Repository in Github

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708848418619/4f365352-3b4d-454a-a811-1acfb54063f9.png align="center")

Put the Jenkins file there, and the code to run the Jenkins pipeline

```plaintext
Jenkinsfile (Declarative Pipeline)
/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'python:3.12.1-alpine3.19' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
```

2 . Create another project in Jenkins with Configuration and select "Multi-Configuration Project"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708848661437/ecb2572b-5478-49b6-9227-470a47353848.png align="center")

3 . Give a Source Add the Github Repo where Jenkins file is there

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708848740224/48c8bfe6-145a-46f7-babe-f859c8428818.png align="left")

Save and Run the Pipeline Manually

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708848800884/684c2cff-064c-491c-9c4b-14c5d72b6466.png align="center")

*This example provides a simple introduction to Declarative Pipelines in Jenkins. You can further expand and customize your pipeline by adding more stages, steps, and integrations based on your project's requirements.*