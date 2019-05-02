# Persisting Data with Docker Volumes

### Table of Contents

1. [Why You Should Know This](#why-you-should-know-this)
2. [Learning Objectives (5 min)](#learning-objectives-5-min)
3. [Initial Exercise (30 min)](#initial-exercise-30-min)
4. [Overview/TT I (30 min)](#overviewtt-i-30-min)
5. [BREAK (10 min)](#break-10-min)
6. [In Class Activity I (30 min)](#in-class-activity-i-30-min)
7. [Wrap Up (15 min)](#wrap-up-15-min)
8. [Additional Resources](#additional-resources)
9. [Credits](#credits)

## Why You Should Know This

Docker Volumes allow a developer to persist data across container launches.

## Learning Objectives (5 min)

1. Identify and describe how a Docker Volume works.
2. Reflect on your experiences at DockerCon.
3. Design
4. Implement

## Initial Exercise (30 min)

### DockerCon Reflection (15 min)

Take 15 minutes to reflect about your experiences at DockerCon. If you have notes from the sessions you attended, open them up to help guide you. Additionally,here are a few prompts to help:

- What technology was the coolest?
- Which topic did you feel provided the most value to developers or DevOps professionals?
- Did you meet anyone who inspired you? How?
- Did you see any products you wanted to investigate?

Write a few bullet points about your experience in your notebooks. We'll come together as a class to discuss.

### Reflection Discussion (15 min)

Let's talk about what we learned!

## Overview/TT I (30 min)

Docker Volumes can be confusing! The remedy? Learning about how container filesystems work!

### Getting to Know the Docker Filesystem

1. Docker images are stored as a series of read-only layers.
2. Starting a container takes the read-only image and adds a read-write layer on top!
3. When the container modifies an existing file, the file is copied out of the read-only layer and into the read-write layer.
4. The version in the read-write layer only hides the underlying file in the read-only layer. It doesn't destroy it, and it still exists in the read-only layer.
5. When a container is deleted, relaunching the image starts a fresh container without any of the changes made in the previously running container --- those changes are lost!

Docker calls this layering technique the [Union File System](https://docs.docker.com/glossary/?term=Union%20file%20system)

### Saving Data in the Filesystem

Keen eyes will notice that the fifth step "resets" the container! How do we prevent that, and actually persist our data?

#### Say Hello to Docker Volumes

Volumes are:

- Directories that live outside the default Union File System.
- Exist as normal directories and files on the host filesystem!

That's it! Docker Volumes are directories that live on your local machine. A container can talk to them, even if that container has been deleted before!

#### Creating a Volume

There are many different ways to create a volume.

The **most direct way** is to **declare a volume at runtime using the `-v` flag**:

```bash
$ docker run -it --name vol-test -h CONTAINER -v /data debian /bin/bash
root@CONTAINER:/# ls /data
root@CONTAINER:/#
```

This command makes the directory `/data` inside the container live outside the Union File System and directly accessible on your host machine.

Any files that the container image held inside `/data` will be copied into the volume when the container starts.

You can find out where the volume lives on the host by using `docker inspect` at the terminal, like so (_you may need to `brew install jq` first_!). You'll see output on your terminal similar to the following...

```bash
$ docker inspect -f "{{json .Mounts}}" vol-test | jq .
[
  {
    "Name": "8e0b3a9d5c544b63a0bbaa788a250e6f4592d81c089f9221108379fd7e5ed017",
    "Source": "/var/lib/docker/volumes/8e0b3a9d5c544b63a0bbaa788a250e6f4592d81c089f9221108379fd7e5ed017/_data",
    "Destination": "/data",
    "Driver": "local",
    "Mode": "",
    "RW": true,
    "Propagation": ""
  }
]
```

We can also get similar info from the `docker volume inspect` command, now that we know that the name of the volume is `8e0b3a9d5c544b63a0bbaa788a250e6f4592d81c089f9221108379fd7e5ed017`:

```bash
$ docker volume inspect 8e0b3a9d5c544b63a0bbaa788a250e6f4592d81c089f9221108379fd7e5ed017
[
    {
        "Name": "8e0b3a9d5c544b63a0bbaa788a250e6f4592d81c089f9221108379fd7e5ed017",
        "Driver": "local",
        "Mountpoint": "/var/lib/docker/volumes/8e0b3a9d5c544b63a0bbaa788a250e6f4592d81c089f9221108379fd7e5ed017/_data",
        "Labels": null,
        "Scope": "local"
    }
]
```

In both cases, the output tells us that Docker has mounted `/data` inside the container as a directory somewhere under `/var/lib/docker`.

Let’s add a file called `test-file` to the directory from the host:

```bash
$ sudo touch /var/lib/docker/volumes/8e0b3a9d5c544b63a0bbaa788a250e6f4592d81c089f9221108379fd7e5ed017/_data/test-file
```

We can see it inside our container with this command, run from inside the container:

```bash
$ root@CONTAINER:/# ls /data
test-file
```

You can also create volumes inside of a `Dockerfile`:

```Dockerfile
FROM debian:wheezy
VOLUME /data
```

Or using the `docker volume create` command:

```bash
$ docker volume create --name my-vol
my-vol
```

There is another major use case for volumes that can only be accomplished through the `-v` flag: mounting a specific directory from the host into a container.

Example:

```bash
$ docker run -v /Users/dani/data:/data debian ls /data
```

What do you think this command does?

This command mounts the directory `/Users/dani/data` on the host as `/data` inside the container.

Any files already existing in the `/Users/dani/data` directory will be available inside the container.

Why is this useful? For sharing files between the host and the container, for example mounting source code to be compiled.

Note that the host directory for a volume cannot be specified from a `Dockerfile`, in order to preserve portability (the host directory may not be available on all systems). When this form of the `-v` argument is used any files in the image under the directory are not copied into the volume. Such volumes are not “managed” by Docker as per the previous examples — they will not appear in the output of `docker volume ls` and will never be deleted by the Docker daemon.

### Final Tips & Tricks: Permissions

Often you'll need to set permissions and ownership on a volume, or initialize a volume with some default data or config files. It's important to be aware that anything after the `VOLUME` instruction in a `Dockerfile` will not be able to make changes to that volume!

#### Doesn't Work

Now that you know the above trick, why do you think the following `Dockerfile`  wouldn't work as expected?

```Dockerfile
FROM debian:wheezy
RUN useradd foo
VOLUME /data
RUN touch /data/x
RUN chown -R foo:foo /data
```

#### Works Great

To contrast, why do you think the following `Dockerfile` will work?

```Dockerfile
FROM debian:wheezy
RUN useradd foo
RUN mkdir /data &amp;&amp; touch /data/x
RUN chown -R foo:foo /data
VOLUME /data
```

#### Here's Why

**Docker is clever enough to copy any files that exist in the image under the volume mount into the volume and set the ownership correctly**. This won’t happen if you specify a host directory for the volume (so that host files aren’t accidentally overwritten).

If you can’t set permissions and ownership in a `RUN` command, you will have to do so using a `CMD` or `ENTRYPOINT` script that runs when the container is started.

## BREAK (10 min)

## In Class Activity I (30 min)

### Embracing Persistence

1. Open up the project that you intend to dockerize as submitted on the tracker.
2. With a partner, discuss and describe how you can add a persistent volume to your container orchestration strategy, and the purpose it will serve. Where will your volume come in handy?
   1. Common usage include database persistence, etc.
3. Once you've planned your strategy together, you can begin implementing your persistent volume.
4. Add, commit, and push your changes to your repo by the end of the class period!

## Wrap Up (15 min)

Ask students for feedback about what they'd like to learn in the following class sections.

Whiteboard the discussion!

## Additional Resources

1. [Docker Volumes](https://medium.com/docker-captain/docker-volumes-d55d18aafbc0)

## Credits

Lecture heavily borrowed and adapted to format from the following exceptional Medium post: [Understanding Volumes in Docker](https://container-solutions.com/understanding-volumes-docker/).
