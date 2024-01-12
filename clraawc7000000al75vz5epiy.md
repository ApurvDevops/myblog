---
title: "Day 15 Day Part 4 ( Advanced Docker :: Multistage Docker build)"
datePublished: Fri Jan 12 2024 07:12:15 GMT+0000 (Coordinated Universal Time)
cuid: clraawc7000000al75vz5epiy
slug: day-15-day-part-4-advanced-docker-multistage-docker-build
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705043528865/f8dda897-ad38-4fc0-8a5b-5779f879213b.png
tags: shubhamlondhe, dockermultistage, multistage, advance-docker

---

## **Docker Multi-stage builds**

* *Multistage Docker builds are a feature in Docker that allows you to use multiple FROM statements in your Docker file, creating multiple build stages. Each stage represents a phase in the build process, and the final image is built from the last stage.*
    
* *The primary motivation behind multistage builds is to create smaller and more efficient Docker images. The idea is to have one stage for building and compiling the application, and another stage for packaging and distributing the application. This way, the final image only contains the necessary artifacts and dependencies needed to run the application, rather than the entire build environment.*
    
* *Below is an example where we are initially creating a image using normal Docker file and once we have created a staged docker file we will see the changes in size of image*
    

*Steps*:

1)*First we need to pull the Image from repo*

```plaintext
git clone https://github.com/ApurvDevops/python-multistage-docker.git
```

2)  *Then Create a Docker file of the python app*

```plaintext
FROM python:3.9 AS backend-builder
WORKDIR /app
COPY backend/ /app
RUN pip install --no-cache-dir -r requirements.txt
EXPOSE 5000
CMD ["python","app.py"]

Creating image from above docker file
docker build -t python-app .
```

3) *Once done, we see the Size of image* 

```plaintext
docker images
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704984166548/2dbf7f74-1648-4c88-87fa-4a47a53a11a4.png align="left")

4) *Now we will create a Multi Stage Docker file and then check the size of image*

```plaintext
# -------------------- Stage 1 --------------------
#---------------Fixed Docker file----
FROM python:3.9 AS backend-builder
WORKDIR /app

COPY backend/ /app
RUN python -m venv venv
RUN . venv/bin/activate && pip install --no-cache-dir -r requirements.txt

# ------------------ Stage 2 ----------------------
FROM python:3.9-slim-buster
WORKDIR /app
COPY --from=backend-builder /app /app
EXPOSE 5000
ENV NAME World
CMD ["/bin/bash", "-c", "source venv/bin/activate && python app.py"]

creating image for above file
docker build -t python-app-multi-stage .
```

5) *Now check the size of the file*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704984317032/565e9e21-c20c-4bdb-ad75-5c9fe2d35755.png align="left")