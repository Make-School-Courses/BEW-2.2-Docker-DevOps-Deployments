<!-- Run as a slideshow: reveal-md README.md -w -->
# 🐳 DNS & Domain Names `🚧 WIP`

⭐️ **GOAL**: Learn about the domain name system and register your very own domain for use throughout the course.

|**Time**  | **Activity**              |
 --------- | ------------------------- |
| 5 MIN     | 🏆 Learning Objectives    |
| 15 MIN    | 📚 Review DNS Comic   |
| 10 MIN    | 🔥 Trace a request   |
| 30 MIN    | 🗣️ Register a Domain Name + Link to GitHub   |
| 10 MIN    | 🛏️ BREAK                     |
| - MIN     | 💪 Tutorial Q&A + Work Time      |

<!-- > -->

### 🏆 Learning Objectives

By the end of this class you will be able to...
1. explain the role of DNS and domain names 
2. trace a request using the `traceroute` command
3. register a domain name + link to GitHub Pages
4. be fully prepared for the next set of Docker lessons

<!-- > -->

### 📚 Review DNS Comic

Students should go through this [DNS comic which explains with graphics how DNS systems work and communicate!](https://howdns.works)

Take notes on the vocabulary term that comes up in each page and "trace" the example ping from the comic.

<!-- > -->

### 🔥 Trace a request 

Instructor demo usage of the `traceroute` command.

Use the `traceroute` terminal command with the following websites and explore the output:
- google.com
- makeschool.com
- nsa.gov

Discussion questions:
- what happens if we paste the IP addresses found in the route into a web browser?
- How does the route change with a VPN?
- What about something like a TOR browser?

Can we truly mask our activity?

<!-- > -->

### 🗣️ Register a Domain Name + Link to GitHub

-- Instructor Demo --

A .xyz domain name can be purchased from [namecheap.com for ~$1.](namecheap.com)

Reference materials:
- Great guide to [connect a namecheap.com domain to GitHub Pages](https://dev.to/pauljwil/connect-github-pages-to-your-namecheap-domain-4gjj)
- Documentation from GitHub that specifies current IP address to use for your domains `A Records`.
- Troubleshooting [tips from GitHub for ideas to use when things don't work](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/troubleshooting-custom-domains-and-github-pages#cname-errors)
-- NOTE: dropping the CNAME certificate and then readding seems to be the best quick debugging fix for namecheap.com

Demonstrate a working set of `CNAME` and `A Record` properties using the `dig` command. As of June 2021, it should include four `A Records` and one `CNAME`.

EX:
```
 ~ dig www.jaylowe.xyz +nostats +nocomments +nocmd                                                  ✔  at 14:59:35 

www.jaylowe.xyz.	1799	IN	CNAME	ogjaylowe.github.io.
ogjaylowe.github.io.	3600	IN	A	185.199.108.153
ogjaylowe.github.io.	3600	IN	A	185.199.111.153
ogjaylowe.github.io.	3600	IN	A	185.199.109.153
ogjaylowe.github.io.	3600	IN	A	185.199.110.153
```


<!-- > -->

### 🛏️ BREAK   

<!-- > -->
### 💪 Tutorial Q&A + Work Time 

Use this time to ask questions about the tutorials and/or complete them in preperation for the upcoming Docker lessons.

<!-- do not edit below this line !-->
[View]: https://make-school-courses.github.io/BEW-2.3-Web-Security/Slides/00-LESSON_NAME_TODO
[Gradescope]: https://www.gradescope.com/courses/133579
[Link]: https://en.wikipedia.org/wiki/HTTP_404
