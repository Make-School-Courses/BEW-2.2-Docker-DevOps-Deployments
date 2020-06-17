<p align="center"><img src="Images/docker.svg" height="200"></p>

# Docker, DevOps, & Deployments

<!-- omit in toc -->
## Table of Contents

1. [Course Description](#course-description)
1. [Prerequisites](#prerequisites)
1. [Learning Outcomes](#learning-outcomes)
1. [Schedule](#schedule)
1. [Class Assignments](#class-assignments)
   1. [Tutorials](#tutorials)
   1. [Final Project](#final-project)
1. [Evaluation](#evaluation)
1. [Make School Course Policies](#make-school-course-policies)

## Course Description

In this course students will learn the two main flavors of Developer Operations (DevOps), one that uses containers and one that does not. Students will learn the leading container pattern with Docker and explore the pros and cons of containers by implementing them. The course will tie this pattern together with generic patterns of operation, such as environmental design, development controls, and uptime management.

## Prerequisites

- [BEW 1.1](https://make.sc/bew1-1)
- [BEW 1.2](https://make.sc/bew1-2)

## Learning Outcomes

_By the end of this course, you will be able to&hellip;_

1. Build, deploy, and orchestrate that containers in any web-based application.
1. Compare and contrast traditional and container-based deployment patterns.
1. Demonstrate proficiency for professional DevOps roles.
1. Implement and maintain a cloud infrastructure utilizing traditional DevOps techniques.

## Schedule

**Course Dates**: Monday, June 1<sup>st</sup> &mdash; Friday, July 17<sup>th</sup> 2020 _(7 weeks)_<br>
**Class Times**: Monday, Wednesday, & Friday: 1:30 &mdash; 3:30pm _(20 class sessions)_

| Class | Date         | Topics                                   |
|-------|--------------|------------------------------------------|
| 1     | Mon, June 1  | [Course Orientation]                |
| 2     | Wed, June 3  | [How Containers Work]                    |
| 3     | Fri, June 5  | [Domains & DNS]                          |
| 4     | Mon, June 8  | 🔬**Lab**: [Scripting in Bash]           |
| 5     | Wed, June 10 | [Dockerizing Web Apps]                   |
| 6     | Fri, June 12 | 🔬**Lab**: [Dockerizing Your Web App]    |
| 7     | Mon, June 15 | [Docker Compose]                         |
| 8     | Wed, June 17 |  **Lab**: [Review Worksheet]: _Containers, Orchestration, Optimization_  |
| 9     | Fri, June 19 | **❌NO CLASS - JUNETEENTH OBSERVED** |
| 10    | Mon, June 22 | [Domains & Droplets]                 |
| 11    | Wed, June 24 | [Continuous Integration] / [Alerts]                 |
| 12    | Fri, June 26 | 🔬**Lab**: Configuring CapRover |
| 13    | Mon, June 29 | [Docker Hub]                             |
| 14    | Wed, July 1  | 🔬**Lab**: Using Docker Hub      |
| -     | Fri, July 3  | **❌NO CLASS - INDEPENDENCE DAY OBSERVED** |
| 15    | Mon, July 6  | [Load Balancing & Testing]               |
| 16    | Wed, July 8  | [Multi-Stage Builds]                     |
| 17    | Fri, July 10 | 🔬**Lab**: Optimizing a Release        |
| 18    | Mon, July 13 | **1-on-1**: [Architecture Review]        |
| 20    | Fri, July 17 | [Final Presentations]                    |

## Class Assignments

### Tutorials

_Complete all 5 tutorials to pass the course_:

- Tutorial 1: [Your First Linux Containers](https://training.play-with-docker.com/ops-s1-hello)
- Tutorial 2: [Customizing Docker Images](https://training.play-with-docker.com/ops-s1-images)
- Tutorial 3: [Deploy and Manage Multiple Containers](https://training.play-with-docker.com/ops-s1-swarm-intro)
- Tutorial 4: [Docker Networking Hands-on Lab](https://training.play-with-docker.com/docker-networking-hol)
- Tutorial 5: [Docker Orchestration Hands-on Lab](https://training.play-with-docker.com/orchestration-hol)


### Final Project

_Review the [Requirements Document](Projects/FinalProject.md) to learn more about the project, including_:

- [⭐️ **Project Goals**](Projects/FinalProject.md#️-project-goals) & [**Requirements**](Projects/FinalProject.md#-project-requirements)
- [🗓 **Deliverables** & **Due Dates**](Projects/FinalProject.md#-deliverables--due-dates)
  - [1️⃣ **Proposal**: Due 6/26 @ 11:59pm](Projects/FinalProject.md#1️⃣-proposal-due-626--1159pm)
  - [2️⃣ **Architecture Review**: Due 7/13 @ 1:30pm](Projects/FinalProject.md#2️⃣-architecture-review-due-713--130pm)
  - [3️⃣ **Presentation**: Due 7/15 @ 11:59pm](Projects/FinalProject.md#3️⃣-presentation-due-715--1159pm)
  - [4️⃣ **Blog Post**: Due 7/15 @ 11:59pm](Projects/FinalProject.md#4️⃣-blog-post-due-715--1159pm)
  - [5️⃣ **Repository**: Due 7/15 @ 11:59pm](Projects/FinalProject.md#5️⃣-repository-due-715--1159pm)

## Evaluation

_To pass this course you must meet the following requirements:_

- Complete all required tutorials, challenges, and projects as listed in this syllabus.
- Turn in all deliverables on [Gradescope].
- Pass the [final project] and [architecture review] according to the rubric.
- Actively participate in class and abide by the attendance policy.
- Make up all classwork from all absences.

## Make School Course Policies

- [Program Learning Outcomes](https://make.sc/program-learning-outcomes) - What you will achieve after finishing Make School, all courses are designed around these outcomes.
- [Grading System](https://make.sc/grading-system) - How grading is done at Make School
- [Diversity and Inclusion Statement](https://make.sc/diversity-and-inclusion-statement) - Learn about Diversity and Inclusion at Make School
- [Academic Honesty](https://make.sc/academic-honesty-policy) - Our policies around plagerism, cheating, and other forms of academic misconduct
- [Attendance Policy](https://make.sc/attendance-policy) - What we expect from you in terms of attendance for all classes at Make School
- [Course Credit Policy](https://make.sc/course-credit-policy) - Our policy for how you obtain credit for your courses
- [Disability Services (Academic Accommodations)](https://make.sc/disability-services) - Services and accommodations we provide for students
- [Student Handbook](https://make.sc/student-handbook) - Guidelines, policies, and resources for all Make School students

[Course Orientation]: Lessons/CourseOrientation.md
[Code Once, Run Anywhere]: Lessons/Containers.md
[How Containers Work]: Lessons/Dockerfiles.md
[Domains & DNS]: Lessons/DNS.md
[Scripting in Bash]: https://github.com/veltman/clmystery
[Dockerizing Web Apps]: Lessons/WebServers.md
[Dockerizing Your Web App]: Labs/WebApp.md
[Docker Compose]: Lessons/Compose.md
[Domains & Droplets]: Lessons/Droplets.md
[Deployment Day]: Lessons/DeploymentDay.md
[Security]: Lessons/Security.md
[Project Kickoff]: Projects/FinalProject.md
[Continuous Integration]: https://docs.google.com/presentation/d/18DNt9UXHaPUufQogj-mThiKpvhkJzXprnPmQtaptUp8
[Alerts]: Lessons/Alerts.md
[Docker Hub]: Lessons/Hub.md
[Using Docker Hub]: Labs/Hub.md
[Load Balancing & Testing]: Lessons/LoadBalancing.md
[Multi-Stage Builds]: Lessons/Builds.md
[Optimizing a Release]: Labs/Optimize.md
[Final Project]: Projects/FinalProject.md
[Final Presentations]: Projects/FinalProject.md#Deliverables
[Architecture Review]: Projects/FinalProject?id=2%ef%b8%8f⃣-architecture-review-due-715--130pm
[Gradescope]: https://www.gradescope.com/courses/133579
[Review Worksheet _(Weeks 1-3)_]: https://www.gradescope.com/courses/133579/assignments/536592
