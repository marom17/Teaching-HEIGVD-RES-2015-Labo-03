# Teaching-HEIGVD-RES-2015-Labo-03

## Objectives

There are 2 main objectives with this lab:

* The first objective is to **get familiar with Docker** and to be able to create images, run containers and inspect the environment. We have prepared the configuration files and supporting data, so your task will essentially be to issue Docker commands and to do some little modifications of the configuration files.

* The second objective is to **get familiar with the syntax of the HTTP protocol**. You will connect to an HTTP server using `telnet` and type a valid HTTP request. You will also observe the HTTP traffic between a browser running on your host and a server running in a Docker container with the `tcpdump` tool.

## Guidelines

For this lab, we ask you to **work individually** (because it is important that everyone has a working Docker environment).

We ask you to **write a report**, in which you describe all the operations that you have done and where you include screenshots. **Please upload your report in moodle and do not sent it by mail**.


## Phase 1: Setup the Docker environment

In the slides of Lecture 3 (UDP) and Lecture 4 (HTTP), we have introduced the basics of Docker. We have shown examples for creating images, running containers and getting information about the running environment. Now it's your turn to get it working on your machine. 

1. You will use [this repo](https://github.com/SoftEng-HEIGVD/Teaching-HEIGVD-RES-2015-Vagrant) as a starting point (make sure that you have **pulled the last commits** and that you are on the **fb-docker-setup** branch).

2. in the `box/docker` folder, you will see several folders that we have prepared as a basis for different docker images. In this lab, we will use `image_expressjs`. It contains a node.js application built on top of the [express.js](http://expressjs.com/) web framework.

3. Go through the code of these two files: `docker/image_expressjs/file_system/views/message.jade` and `docker/image_expressjs/file_system/routes/message.js`. You don't really need to understand how express.js works to complete the lab, but what happens here is that in `message.js` we register a controller on the `/message` URL. So, when a client issues an HTTP request targeting this URL, the controller is executed. In the code, you will see that we deal with content negotiation: if the client wants JSON, we simply serialize a Javascript object, if the client wants HTML, we forward a request to the view (`message.jade`).

4. Edit `message.js` and replace `olivier liechti` with your name.

5. **Create a Docker image** (as presented in the lecture slides).

6. **Run a Docker container** from this image (idem).

7. Find out what is the **IP address** assigned to this container (idem).

8. In your report, please include screenshots of what you see when you use the `docker images`, `docker ps` and `docker inspect` commands.



## Phase 2: Validate your setup

If you have done everything correctly, you should have an HTTP server running in your Docker container. To validate that this is the case, **launch a web browser on your host** and type in the URL (you have to figure out what is the correct IP address and port number!).

Please access two URLs: the root URL (e.g. `http://x.x.x.x:nn/`) and the message endpoint URL (e.g. `http://x.x.x.x:nn/message`). 

**Please include a screenshot of both pages in your browser (we want to see the location bar, with the URL) in your report.**

## Phase 3: Connect to the HTTP server via telnet and send HTTP requests

1. From the **vagrant box**, send an HTTP request to GET the `/message` resource and ask for an `application/json` representation.

2. From the **host**, send an HTTP request to GET the `/message` resource and ask for a `text/html` representation.

**Please include a dump of what you have typed and what you have seen on the console in your report.**


## Phase 3: Inspect the HTTP traffic with tcpdump

In the previous lecture, we have shown how to use `tcpdump` to capture traffic between your host and a Docker container. We ask you to use this technique to analyze the HTTP traffic exchanged between the web browser running on your host and the web server running in your container. 

**In your report, please include a dump of what you see in the console during the exchange.**


