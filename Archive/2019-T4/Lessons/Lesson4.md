# Practical Applications of Docker

**Table of Contents**
1. [Why You Should Know This (2 min)](#why-you-should-know-this-2-min)
2. [Learning Objectives (3 min)](#learning-objectives-3-min)
3. [Initial Exercise (15 min)](#initial-exercise-15-min)
4. [Overview/TT I (30 min)](#overviewtt-i-30-min)
5. [BREAK (10 min)](#break-10-min)
6. [In Class Activity I (60 min)](#in-class-activity-i-60-min)

## Why You Should Know This (2 min)

When you learn a new technology, it can be tough to know how to use it to improve your day-to-day experience. Today's lesson focuses on the practical applications of the commands we learned on Day 2 and Day 3.

## Learning Objectives (3 min)

1. Identify the key differences between virtualization, containers, and Docker.
2. Gain familiarity with real-world container usage patterns and practices.
3. Build your first Dockerized application in Node.js!

## Initial Exercise (15 min)

* **Sign up for [DockerCon SF 2019](https://dockercon19.smarteventscloud.com/portal/newreg.ww?utm_source=docker&utm_medium=blog&utm_campaign=your+kubernetes+guide+at+dockercon&utm_content=&utm_term=your+kubernetes+agenda+at+dockercon&utm_budget=)**! Code is on the whiteboard --- use it for a **free pass** to attend **April 28 through May 2**! See the **conference schedule [here](https://www.docker.com/dockercon/agenda/)**.
    > DockerCon 2019 is a 3 day technology conference, where customers and community come to learn, share and connect with each other. Attendees are a mix of developers, systems admins, architects, and IT decision makers —from beginner, to intermediate, and advanced users—who are all looking to level up their skills and go home inspired and ready to invest and implement their containerization strategies.
* Update your [progress](https://make.sc/trackbew2.2) on the tracker, and **be sure to indicate if you've signed up for DockerCon**.
  * Passes are limited to the first 100 signups and only currently extended to Make School students and staff.

## Overview/TT I (30 min)

### Virtualization, Containers, & Docker

At this point in the class, you already know that Docker is a useful tool for DevOps. But you might be asking yourself, **why do these technologies exist in the first place**?

#### History

##### Hardware-Based Servers

<img src="https://github.com/Make-School-Courses/BEW-2.2-Docker-DevOps-Deployments/blob/master/Images/server_room.jpg" height="300">

Before the cloud, there were servers. They lived in big rooms, like this. Each **server** within the **server rack** contained a single hardware configuration, like your desktop computer, and had the ability to host many websites on the same server.

In order to scale up, companies had to research new hardware and make sure it was compatible with their software before making a big purchase order. Most server configurations were written by hand in a manual process. Automation was in it's early days back then.

##### Virtualization

Hardware based servers are expensive, hard to scale, and often required a manual process. Not to mention, anything that affected one website --- like the server being down --- affected them all!

Virtualization was introduced as the first antidote. This technique allowed sysadmins to create any number of ***"virtual"* operating systems on a single hardware-based server**.

Killer feature? **Snapshots**: *the state of the virtual machine at an exact point in time*. You could now **rollback** any mistake!

##### Containers

Virtualization added the ability to **isolate one application or website from another** on a hardware-based server, but it **required running an entire OS** --- not very efficient.

Containers are a l**ayer on top of virtualization** (or a hardware-based server) that utilizes the server (or *host*)'s operating system components to provide a sandbox your application or website could run in --- a very lightweight solution!

##### Docker

Docker took containers a step further, by **automating the deployment of applications or websites inside of a container**, as well as the automation of OS-level virtualization on Linux --- that means, it does all the tough stuff for you, and allows you to focus on your project's code and dependencies.

**Docker containers** are created from **Docker images** --- a **snapshot** of an application's code and dependencies. Docker also introduced **recipes for deployment, called Dockerfiles**, that **execute the necessary steps to create a Docker image**.

## BREAK (10 min)

## In Class Activity I (60 min)

### Dockerize a Node App

1. Find a buddy to pair with.
2. Go through each step in this [Dockerizing a Node.js Web App](https://nodejs.org/de/docs/guides/nodejs-docker-webapp/) together.
3. Virtualizing your first application can be tough. Be sure to ask the instructor for help if you get stuck!
4. If you finish early, read through the [Docker and Node.js Best Practices Guide](https://github.com/nodejs/docker-node/blob/master/docs/BestPractices.md) linked at the bottom of the tutorial.
