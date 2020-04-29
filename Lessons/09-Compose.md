# 🐳 Docker Compose

<!-- omit in toc -->
## ⏱ Agenda

1. [[**5m**] Attendance & Announcements](#5m-attendance--announcements)
1. [[**15m**] Warm Up](#15m-warm-up)
1. [[**30m**] 📖 Overview](#30m-%f0%9f%93%96-overview)
   1. [Features](#features)
   1. [Use Cases](#use-cases)
   1. [How to Actually Use It](#how-to-actually-use-it)
   1. [Compose Commands](#compose-commands)
1. [[**15m**] 😎 Break](#15m-%f0%9f%98%8e-break)
1. [[**20m**] ⏺ Live Code: Compose & Django](#20m-%e2%8f%ba-live-code-compose--django)
1. [[**60m**] 🔭 Lab](#60m-%f0%9f%94%ad-lab)

<!-- omit in toc -->
## 🏆 Objectives

## [**5m**] Attendance & Announcements

## [**15m**] Warm Up

Complete the **[KataCoda: Container Orchestration](https://www.katacoda.com/courses/docker/11)** tutorial in pairs.

**NOTE**: This tutorial asks you to install docker-compose before starting. **IF YOU ARE ON A MAC, SKIP THIS INSTRUCTION.**

## [**30m**] 📖 Overview

<p align="center">
  <img src="https://cdn.nearsoft.com/uploads/2017/09/docker-compose-lede-800x450.png" width="400">
</p>

Docker Compose is a tool for **defining and running multi-container Docker applications**.

With Docker Compose, you use a **YAML file (`docker-compose.yml`) to configure your application’s services**. Then, **with a single command**, you **create and start all the services from your configuration**.

**This file is created by you, and located in the root of your project directory**.

### Features

- **Multiple isolated environments** on a single host.

- **Preserve volume data** when containers are created.
  - Preserves volumes used by your services.
  - Ensures that any data you’ve created in volumes isn’t lost.
  - When `docker-compose up` runs, if it finds any containers from previous runs, it copies the volumes from the old container to the new container.

- Only **recreate containers if there's been a change**.
  - Caches the configuration used to create a container. When you restart a service that has not changed, Compose re-uses the existing containers. Re-using containers means that you can make changes to your environment very quickly.

- **Variables** / **can move a composition between environments**.
  - You can use variables in your compose file to customize your composition for different environments / different users.
  - See [Variable Substitution](https://docs.docker.com/compose/compose-file/#variable-substitution) for more details.

### Use Cases

- **Development Environments**
  - When you’re developing software, the ability to run an application in an isolated environment and interact with it is crucial.
  - The Compose command line tool allows you to both run an isolated environment ***and*** interact with it.

- **Automated Testing Environments**
  - An important part of any Continuous Deployment or Continuous Integration process is the automated test suite.
  - Automated end-to-end testing requires an environment in which to run tests.
  - Compose provides a convenient way to create and destroy isolated testing environments for your test suite.

- **Single Host Deployments** _(DigitalOcean, AWS, etc)_
  - Compose has traditionally been focused on development and testing workflows, but with each release we’re making progress on more production-oriented features. You can use Compose to deploy to a remote Docker Engine.

### How to Actually Use It

Using Docker Compose is a **three step process**:

1. Define a Dockerfile for each app
1. Define the services that make up the app in `docker-compose.yml`.
1. Run `docker-compose up` to run all your services together.

Congratulations! You have **orchestrated your containers** --- **enabling each app to run together in an isolated environment**.

### Compose Commands

Docker Compose (`docker-compose`) has several commands you can run to manage the lifecycle of the application:

- Start, stop, and rebuild services
- View the status of running services
- Stream the log output of running services
- Run a one-off command on a service

Use this handy [DevHints.io cheatsheet](https://devhints.io/docker-compose) anytime you need to reference `docker-compose` commands.


## [**15m**] 😎 Break

## [**20m**] ⏺ Live Code: Compose & Django

**GOAL**: See how to use docker-compose in real life through a live code demonstration that walks you through the following tutorial: [Quickstart: Compose and Django](https://docs.docker.com/compose/django/).

## [**60m**] 🔭 Lab

- Complete [**Tutorial 5: Orchestration Hands-On Lab**](https://training.play-with-docker.com/orchestration-hol) and turn it in on [Gradescope](https://www.gradescope.com/courses/105262/assignments/421698).

- I will also have a breakout room to answer any questions you have one-on-one during this lab period!


<!-- omit in toc -->
## 📚 Resources & Credits

- [YAML Validator](https://codebeautify.org/yaml-validator): Use this tool to make sure your YAML syntax is valid.
