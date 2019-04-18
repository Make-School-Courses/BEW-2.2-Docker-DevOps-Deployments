# Advanced Container Orchestration Techniques

### Table of Contents
1. [Why You Should Know This (2 min)](#why-you-should-know-this-2-min)
2. [Learning Objectives (XX min)](#learning-objectives-xx-min)
3. [Overview / TT (30 min)](#overview--tt-30-min)
4. [In Class Activity I (XX min)](#in-class-activity-i-xx-min)
5. [BREAK (10 min)](#break-10-min)
6. [In Class Activity II (XX min)](#in-class-activity-ii-xx-min)
7. [Wrap Up (XX min)](#wrap-up-xx-min)
8. [After Class](#after-class)
9. [Additional Resources](#additional-resources)

## Why You Should Know This (2 min)

Today's plan focuses on **tips and tricks I learned using `docker-compose` IRL**!

## Learning Objectives (XX min)

## Overview / TT (30 min)

Let's go over some strategies and best practices I've personally leveraged in the real world when architecting containers to deploy my applications to my developers and stakeholders.

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

## In Class Activity I (XX min)

## BREAK (10 min)

## In Class Activity II (XX min)

## Wrap Up (XX min)

## After Class

## Additional Resources

1. **[Exception Perceptions: 4 Best Practices for Using Docker Compose](https://blog.sentry.io/2019/02/28/exception-perceptions-docker)**:
