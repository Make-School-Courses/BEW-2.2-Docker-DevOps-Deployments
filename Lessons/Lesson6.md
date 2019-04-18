# Advanced Container Orchestration Techniques

### Table of Contents
1. [Why You Should Know This (2 min)](#why-you-should-know-this-2-min)
2. [Learning Objectives (3 min)](#learning-objectives-3-min)
3. [Overview / TT (30 min)](#overview--tt-30-min)
4. [BREAK (10 min)](#break-10-min)
5. [In Class Activity I (30 min)](#in-class-activity-i-30-min)
6. [In Class Activity II (45 min)](#in-class-activity-ii-45-min)
7. [Additional Resources](#additional-resources)

## Why You Should Know This (2 min)

Today's plan focuses on **tips and tricks I learned using `docker-compose` IRL**!

## Learning Objectives (3 min)

## Overview / TT (30 min)

Let's go over some strategies and best practices I've personally leveraged in the real world when architecting containers to deploy my applications to my developers and stakeholders.

### `Dockerfile` or `docker-compose.yml`?

A `Dockerfile` contains everything needed to set up the environment to run your application. `Dockerfiles` typically follow this recipe:

 1. Start with an image.
 2. Create a directory for your project inside the container.
 3. Copy the project's code to the directory inside the container.
 4. Install the project's dependencies using a package manager _(`npm`, `pip`, etc)_.
 5. Expose the port(s) the application will run on.
 6. Run a command _(`npm start`, `flask run`, etc)_.

`docker-compose.yml` is a supplement to a `Dockerfile` that enables developers to configure and launch one to many containers at once --- your application included!

### One Command to Get Started

When a new developer clones your repository, they should only need to run `docker-compose up` to get started.



### Variable Substitution

Imagine you have a `docker-compose.yml` file in your project with the following configuration:

```yaml
version: '2'
services:
  ghost:
    image: ghost:${GHOST_VERSION}
    ports:
      - ${GHOST_PORT}:2368
```

Set `GHOST_VERSION` and `GHOST_PORT` all in one command by running `GHOST_VERSION=2 GHOST_PORT=8080 docker-compose up`!

### Use `.env` For Local Environment Settings

Compose supports declaring default environment variables in an environment file named `.env` placed in the folder where the `docker-compose` command is executed (current working directory).

**Syntax Rules**:

- Compose expects each line in the `.env` file to be in `VAR=VAL` format.
- Lines beginning with `#` are processed as comments and ignored.
- Blank lines are ignored.
- There is no special handling of quotation marks.
    - This means that they are part of the `VAL`.

### Override Compose Files Safely

1. Add ` *.override.yml` to the `.gitignore` file in the root of the repository.
2. Create a `docker-compose.override.yml` file in order to set custom settings and override the root `docker-compose.yml` file.
3. Level up your DevOps strategy by adding a `docker-compose.override.sample.yml` file to your repository. Make sure there are lots of comments that clearly explain which values can be customized for each developer's environment!


### Auto-Format Your Compose File

Compose files can get messy and difficult to read quickly, especially in microservice architectures. Use this handy [`compose_format`](https://github.com/funkwerk/compose_format) command to check your Compose file and auto-format it based on best practices for readability.

```bash
cat docker-compose.yml | docker run -i funkwerk/compose_format
```

### Waiting on a Dependency

`mongo`, `postgres`, and many other dependencies take time to start up.

How do you get a container to start _before_ another?

**`Dockerfile`**:

```Dockerfile
FROM node:latest

RUN mkdir -p /usr/src/project_name
WORKDIR /usr/src/project_name

COPY package*.json /usr/src/project_name/
RUN npm install
COPY . /usr/src/project_name

EXPOSE 3000

# Launch the wait tool, then your application.
# Source: https://dev.to/hugodias/wait-for-mongodb-to-start-on-docker-3h8b
ADD https://github.com/ufoscout/docker-compose-wait/releases/download/2.2.1/wait /wait
RUN chmod +x /wait
CMD /wait && npm start
```

**`docker-compose.yml`**:

```yaml
version: "3.3"
services:
  mongo:
    container_name: mongo
    image: mongo
    volumes:
      - ./data:/data/db
    ports:
      - "27017:27017"

  app:
    container_name: app
    build: .
    ports:
      - "3000:3000"
    links:
      - mongo
    depends_on:
      - mongo
    environment:
      WAIT_HOSTS: mongo:27017

volumes:
  mongo_data:
```

## BREAK (10 min)

## In Class Activity I (30 min)

### Trying Something New with Docker

Our first activity highlights how simple it can be to use Docker to learn a new framework!

Follow the **[Quickstart: Compose and Django](https://docs.docker.com/compose/django/)** tutorial to install and experiment with [Django](https://www.djangoproject.com/), the framework for perfectionists with deadlines.

Django written in Python, and is similar to Flask --- but with more batteries included. _**Absolutely no experience with Django is required to complete this tutorial!**_

**Deliverable**: Raise your hand and show the instructor the Django start page running on `localhost` to receive credit for this activity.

## In Class Activity II (45 min)

### Project Kickoff

Get started Dockerizing one of your existing, working projects.

**Today, focus on the following steps** to get started:

1. Create a `Dockerfile`.
2. Create a `docker-compose.yml` file.
3. **Link your repository in the [tracker](https://make.sc/trackbew2.2)**.

The project rubric will be posted soon and linked in this space!

Please note, in order to earn credit for the project, **anyone MUST be able to RUN YOUR ENTIRE PROJECT by EXECUTING AT MOST 3 commands** in the terminal:

   1. `git clone git@github.com:YOUR_USERNAME/YOUR_PROJECT_NAME && cd YOUR_PROJECT_NAME`
   2. *(OPTIONAL)* Configure environment using `docker-compose.override.yml`.
   3. `docker-compose up`

## Additional Resources

1. **[Exception Perceptions: 4 Best Practices for Using Docker Compose](https://blog.sentry.io/2019/02/28/exception-perceptions-docker)**
2. **[Share Compose Configurations Between Files and Projects](https://docs.docker.com/compose/extends/)**
3. **[Control Startup and Shutdown Order in Compose](https://docs.docker.com/compose/startup-order/)
