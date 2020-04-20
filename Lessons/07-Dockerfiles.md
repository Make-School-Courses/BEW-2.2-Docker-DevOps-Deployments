<!-- .slide: data-background="./../Slides/images/header.svg" data-background-repeat="none" data-background-size="40% 40%" data-background-position="center 10%" class="header" -->
# 🐳 Day 7: Docker Concepts in Practice

<!-- > -->

### ➡️ Table of Contents

1. [🏆 Objectives](#%f0%9f%8f%86-objectives)
1. [📦 Terminology](#%f0%9f%93%a6-terminology)
1. [👩‍🏫 [15m] Instructor: Recap](#%f0%9f%91%a9%e2%80%8d%f0%9f%8f%ab-15m-instructor-recap)
1. [💻 [20m] Instructor: Demo](#%f0%9f%92%bb-20m-instructor-demo)
1. [📚 Resources](#%f0%9f%93%9a-resources)
1. [🙏 Credits](#%f0%9f%99%8f-credits)

<!-- > -->

## 🏆 Objectives

1. Expand existing knowledge of common bash commands.
1. Create a `Dockerfile` that installs a dependency and runs several bash commands.

<!-- > -->

## 📦 Terminology

_Copy the blank markdown table below, then paste it into your notes._

_While participating in class, fill out the definitions for your reference in the future._

|                   Term |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Definition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|-----------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| **alpine linux**<br><br> | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |
| **container** <br><br> |
| **dependency** <br><br> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **image**       <br><br> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **layer**       <br><br> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **tarball**    <br><br> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

<!-- > -->

## 👩‍🏫 [15m] Instructor: Recap

<!-- v -->

### The Purpose of Containers

**TLDR**: _Everyone's computer is different, even if it looks the same._

<p><img src="https://make-school-courses.github.io/BEW-2.2-Docker-DevOps-Deployments/Lessons/Images/bork-why.jpg" width="700"></p>

<!-- v -->

### Distribute Everything You Need to Run a Codebase

A `Dockerfile` is distributed with the majority of Open Source projects to ensure you can run them on your unique machine.

<p><img src="https://make-school-courses.github.io/BEW-2.2-Docker-DevOps-Deployments/Lessons/Images/bork-dependency.jpg" width="700"></p>

<!-- v -->

### Images Are Made of Layers

<p><img src="https://make-school-courses.github.io/BEW-2.2-Docker-DevOps-Deployments/Lessons/Images/bork-images.jpg" width="700"></p>

<!-- v -->

### 1 Line of Code in Dockerfile = 1 Layer in Image

<p><img src="https://make-school-courses.github.io/BEW-2.2-Docker-DevOps-Deployments/Lessons/Images/bork-layers.jpg" width="700"></p>

<!-- > -->

## 💻 [20m] Instructor: Demo

1. **Creating a Dockerfile**

   ```bash
   cd my-project-dir
   touch Dockerfile
   code .
   ```

1. **Building and Testing a Dockerfile**

   ```bash
   docker build .
   ```

1. **Running a Dockerfile**

   ```bash
    docker run .
   ```

<!-- > -->

## 📚 Resources

`TODO`

<!-- > -->

## 🙏 Credits

- [Julia Evans (@bork)](https://twitter.com/b0rk): _Photo credit for comics used in lesson plan._
