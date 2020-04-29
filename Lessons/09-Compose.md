# 🐳 Docker Compose

<!-- omit in toc -->
## ⏱ Agenda

1. [[**15m**] Warm Up](#15m-warm-up)
1. [[**30m**] 📖 Overview](#30m-%f0%9f%93%96-overview)
   1. [Features](#features)
   1. [Use Cases](#use-cases)
1. [[**15m**] 😎 Break](#15m-%f0%9f%98%8e-break)
1. [[**60m**] 🔭 Lab](#60m-%f0%9f%94%ad-lab)

<!-- omit in toc -->
## 🏆 Objectives

## [**15m**] Warm Up

Complete the **[KataCoda: Container Orchestration](https://www.katacoda.com/courses/docker/11)** tutorial in pairs.

## [**30m**] 📖 Overview

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

<!-- ## [**00m**] ⏺ Live Code -->

## [**15m**] 😎 Break

## [**60m**] 🔭 Lab

- Complete Tutorial 5: Orchestration Hands-On Lab and turn it in on [Gradescope](https://www.gradescope.com/courses/105262/assignments/421698).

- I will also have a breakout room to answer any questions you have one-on-one during this lab period!

<!-- omit in toc -->
## 📚 Resources & Credits

- [YAML Validator](https://codebeautify.org/yaml-validator): Use this tool to make sure your YAML syntax is valid.
