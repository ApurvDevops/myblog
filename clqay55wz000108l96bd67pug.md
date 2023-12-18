---
title: "Day 13 Docker Basic Part 2"
datePublished: Mon Dec 18 2023 13:23:16 GMT+0000 (Coordinated Universal Time)
cuid: clqay55wz000108l96bd67pug
slug: day-13-docker-basic-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702905739925/931bb2d4-06c6-4efc-a23c-a6db92f31f02.png
tags: dockerhub, day13, trainwithshubham, tws, dockernetworking, dockeradvanced

---

***Docker Hub****: It's like a Repository for Docker Images, similar to GitHub where we store the code of the project, whereas, Docker Hub, stores the Images that are created from those program files.*

*Docker push: This is used to push Docker images to Docker hub. Before we can push we need to tag the image,  that we want to push.*

```plaintext
docker tag <image_name> <dockerhub_username>/<image_name>
eg, docker tag node-app:latest testloginapurv/node-app:latest

docker push <dockerhub_username>/<image_name>
eg, docker push testloginapurv/node-app:latest
```

*Docker Pull: As we know while we work on GitHub, we can clone or pull codes from GitHub, similarly we can pull the images that we pushed in the Docker hub.  
If there are no images in our system, that we are looking for, then it will pull from the Docker HUB*.

```plaintext
docker rmi <image_name>
eg, docker rmi  docker rmi node-app:latest

docker pull  testloginapurv/node-app:latest   
```

**Docker Volume:**

***So when your container is running, you can access all the data, but when that container dies or is removed, that data becomes inaccessible, then the data inside the container is gone***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701172178005/2fbcac55-15fe-4e99-b7c1-f0596c4685be.png align="center")

*The solution to this problem is to Bind your computer's storage to the container. But the catch is only to bind the WORKING DIRECTORY, else if we take the complete container, there will be lots of space consumption, in our local system. We will only be storing the folder where the actual data/images/ files are. When a new container is created this will get attached or Bind to volumes where actual data is stored from the previous container.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701172370628/3f9a6245-29da-4210-b583-2c795dcc2cea.png align="center")

*Creating volume*

```plaintext
docker volume create --name <name_of_volume> --opt type=<type_of_volume> --opt device=<location_of_volume_folder> --opt o=bind

docker volume create --name django-todo-volume --opt type=none --opt device=/home/Apurv/docker-demo/volumes/django-app --opt o=bind

 Note: The "bind" option indicates that the volume 
        should be mounted as a bind mount. A bind mount is a way 
        to mount a file or directory from the host machine into a container.
```

*Now run a container using any image*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702408411353/656dd6f5-f556-4a2f-a934-dc465545bc98.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702408422360/5282fe66-b6fa-4d1c-b83c-e5edfbf872e6.png align="left")

*Now the Container is running, try adding a few items to this and then Kill the Container*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702408439014/a6543f29-b23b-4288-8a44-397210dffa14.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702409172503/aa8a2629-6994-413f-8450-88ead553cb98.png align="left")

```plaintext
docker ps
docker kill <Container_id>
docker run -d -p <hostport>:<container port> --mount source=<container_volume>,target=<app_data_folder>  <name_of_image>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702409254192/48348484-b132-4faa-96ea-7e3c59255321.png align="center")

*You will again see the same data,*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702409276408/2416e6bf-7dbd-41fb-a486-23f10d97e24b.png align="center")

*This is how Docker volumes are used, where even though the Container gets killed, the data will persist and the next container will have the same data*

**Docker Network**

*How can we execute using Docker Network or More (Multi-Tier Application)?*

*Two running Containers do not communicate with each other. To make them communicate with each other we need to create a Network between them*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702725385787/280f6673-07e2-40fc-8fd4-f9dd7529f359.png align="center")

*If we run 2 container MySQL and a two-tier Flask app, and give the MySQL as a backend it won't work, because there is no network established between of them to communicate*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702900354790/3048a9c7-1960-498a-8958-311726eae7e1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702900374810/7c189965-c3e5-4f6e-9683-04f5c3d3ac5e.png align="center")

*It is basically looking for the database server, which is there but not connected. So In case we try and give the MySQL container name while running the Flask application, it might work*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702900889529/ec4b904c-241c-458d-933b-4f020571116e.png align="center")

*However, we still see, it's not able to find the container*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702900907250/58985f54-99c6-463a-8655-2ed8e7b110cd.png align="left")

*Here comes the Docker Network which will create and establish the Network between both of the Container.* 

```plaintext
docker nwetwork ls 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702902701893/fc80abc3-8a33-404f-9092-374dd2af41f2.png align="left")

*To resolve this problem we definitely need to create a network and give the network to be used, while running the container*

```plaintext
docker network --create 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702902858479/d1d1fd75-f0c3-4888-bb01-3ba26c2961ba.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702903218977/c8b46d7c-0b5d-4e02-a883-d006339ac5df.png align="center")

```plaintext
docker run -d -p <hostport>:<containerport> -e MYSQL_ROOT_PASSWORD=<password> -e MYSQL_DATABASE=<DBname> -e MYSQL_USER=<username> -e MYSQL_PASSWORD=<userpassword> --name <Contianer name> --network <Network_name> <image name>
```

*Try checking the Network using*

```plaintext
docker inspect
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702903380755/fa4d7a6c-d14f-4829-8bdb-3a54a035228c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702905127564/4620a86c-2156-4054-9678-d45ee7ca1b86.png align="center")

*We can see the data in the Backend as well*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702905156511/a34a93a8-2ba7-44b0-84a6-f1293d3aa2d7.png align="left")

**Docker system prune:: to remove dead containers**