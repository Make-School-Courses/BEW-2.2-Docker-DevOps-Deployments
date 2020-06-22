<!-- Run as a slideshow: reveal-md README.md -w -->
# 🐳 Domains & Droplets

⭐️ **GOAL**: Create and configure a CapRover DO droplet for use in following class sessions.

<!-- omit in toc -->
## ⏰ Agenda (60m)

- [[**10m**] ☀️ **Warmup**: SSH Keys](#10m-️-warmup-ssh-keys)
- [[**20m**] 📚 **TT**: So, You're Ready to Deploy&hellip;](#20m--tt-so-youre-ready-to-deploy)
  - [💬 [**05m**] **Discuss**: Decide What BEW 2.2 Should Use](#-05m-discuss-decide-what-bew-22-should-use)
  - [💻 [**05m**] **Activity**: Register Hosting Account on DigitalOcean](#-05m-activity-register-hosting-account-on-digitalocean)
- [[**20m**] 💻 **Challenge**: Set Up Your Personal PaaS](#20m--challenge-set-up-your-personal-paas)

<!-- > -->
<!-- omit in toc -->
## 🏆 Objectives

*By the end of this class, you'll be able to&hellip;*

1. Define _"virtual private server"_ and their role in deploying web applications.
1. Contrast and compare DigitalOcean droplets to hosted Platform as a Service (PaaS) used in prior courses.
1. Use DigitalOcean to set up a virtual private server in the cloud.
1. Apply A records in order to connect a new server to an existing domain name.

<!-- > -->

## [**10m**] ☀️ **Warmup**: SSH Keys

**IMPORTANT**: This warmup is required to complete today's challenges and finish your final project!

Check to see if you've already generated an SSH key with the default filename by running the following command in your terminal:

```sh
test -f ~/.ssh/id_rsa || test -f ~/.ssh/id_rsa.pub && echo "Default SSH keys not found. Use the following guide to create them before proceeding: https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent.
```

- **IF NO KEYS**: Break out and follow the [Generating a New SSH Key and Adding it to the SSH Agent] tutorial linked in your terminal.
- **IF KEYS EXIST**: Break out to read [TODO: Quick intro to SSH]. We will be discussing it later in class.

## [**20m**] 📚 **TT**: So, You're Ready to Deploy&hellip;

<!-- > -->

<!-- omit in toc -->
### How to Host

<!-- > -->

#### Hosting Options

| Category | Description | Examples |
| :-: | - | :-: |
| **Dedicated** | Hardware responsible for hosting all websites and servers. | - |
| **VPS** | Many virtual server instances running on a physical dedicated server. | [DigitalOcean] |
| **Cloud** | VPS enhanced with on-demand application scaling; flexible pricing based on usage. | [AWS] |
| **PaaS** | Develop, run, and manage applications without the complexity of building and maintaining infrastructure typically associated with developing and launching an app. | [Heroku] |

These are the major offerings available for backend web developers. To learn more, read [8 Different Types of Web Hosting Services](https://www.thebalancesmb.com/types-of-web-hosting-services-2532072).
<!-- > -->

### 💬 [**05m**] **Discuss**: Decide What BEW 2.2 Should Use

Review the [Course Learning Outcomes] on the syllabus and decide Which type of hosting you'd choose for projects in this course.

Justify your answer.

<!-- > -->

### 💻 [**05m**] **Activity**: Register Hosting Account on DigitalOcean

1. Click the following link to create a free DigitalOcean account: [$100 Free Credit].
1. Click the verification link DigitalOcean sent to your email.

We'll be using DigitalOcean heavily the next few weeks! Be sure to sign up now.

<!-- > -->

<!-- omit in toc -->
### Modify DNS Records

Once the droplet is running, copy it's IP address to your clipboard. Navigate to your domain name registar's website, log in, and an A record.

Here are some helpful guides from common registrars:

- [Namecheap]
- [Techdomains]
- [Name.com]

<!-- > -->

<!-- omit in toc -->
### Access Your Server

1. **Copy your SSH key to your server** by running:

    ```sh
    ssh-copy-id -i ~/.ssh/id_rsa root@captain.dev.YOURDOMAIN.COM
    ```

1. Test it by **logging in**:

    ```sh
    ssh root@captain.dev.YOURDOMAIN.com
    ```

1. **Exit the SSH session**:

    ```sh
    exit
    ```

<!-- > -->

<!-- omit in toc -->
### Deploy Application

**Typical deployment strategies include**:

- **MANUAL**: Upload the files that need updated using a browser, `ftp`, `scp`, or other file transfer protocol.
- **MANUAL**: Use `git` to clone the repo on the server, manually pull when code needs updated.
- **AUTOMATED**: Use [continuous integration] platforms like TravisCI, CircleCI, or GitHub Actions.
- **AUTOMATED**: Container-based self-hosted platform as a service applications.

_We'll practice how to upload files manually, as well as how to take advantage of automated systems, in our next lesson on creating and maintaining a self-hosted [Platform as a Service] application._

<!-- > -->

## [**20m**] 💻 **Challenge**: Set Up Your Personal PaaS

**Follow the steps in order to complete today's challenge!**

1. Click this link to create a droplet using the [CapRover One-Click App] on DigitalOcean.
1. Configure the droplet with the following settings:
    - CPU: `1`
    - RAM: `1 GB`
    - Location: `San Francisco, CA`
1. Upload your SSH key to DigitalOcean.
1. Once the droplet is running, copy it's IP address to your clipboard. **Write down the IP address in your notes, you'll need it later on!**
1. Visit your domain name registrar's website and log in.
1. Add an A record pointing `*.dev` to your new droplet's IP address.
1. Visit `http://IP_ADDRESS:3000` in your browser.
1. Follow the instructions to complete the CapRover installation. **Be sure to use a very secure password.**
1. **Submit your new droplet's IP address on [Gradescope] to complete this activity**.

**NOTE**: From now on, access the CapRover dashboard by visiting `https://captain.dev.YOURDOMAIN.com`.

**In the [next section], we'll deploy an application via CapRover to our new personal PaaS**!

<!-- do not edit below this line -->
[Gradescope]: https://www.gradescope.com/courses/133579
[DigitalOcean]: https://make.sc/digitalocean
[SSDNodes]: https://www.ssdnodes.com
[Heroku]: https://www.heroku.com
[AWS]: https://aws.amazon.com
[Wikipedia: Platform as a Service]: https://en.wikipedia.org/wiki/Platform_as_a_service
[Namecheap]: https://www.namecheap.com/support/knowledgebase/article.aspx/319/2237/how-can-i-set-up-an-a-address-record-for-my-domain
[Techdomains]: https://get.tech/faq#headingNine
[Name.com]: https://www.name.com/support/articles/115004893508-Adding-an-A-record
[Generating a New SSH Key and Adding it to the SSH Agent]: https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
[$100 Free Credit]: https://make.sc/digitalocean
[Course Learning Outcomes]: https://make.sc/bew2.2#Learning-Outcomes
[continuous integration]: https://docs.google.com/presentation/d/18DNt9UXHaPUufQogj-mThiKpvhkJzXprnPmQtaptUp8
[Docker Hub]: https://hub.docker.com
[Platform as a Service]: PaaS.md
[CapRover One-Click App]: https://marketplace.digitalocean.com/apps/caprover
[next section]: PaaS.md
