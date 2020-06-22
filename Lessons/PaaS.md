<!-- Run as a slideshow: reveal-md README.md -w -->
# 🐳 Your Personal PaaS

⭐️ **GOAL**: Deploy your first application on CapRover!

<!-- omit in toc -->
## ⏰ Agenda (40m)

- [[**10m**] 📚 **TT**: Introduction to CapRover](#10m--tt-introduction-to-caprover)
- [[**05m**] 💻 **Activity**: Set Up CapRover CLI](#05m--activity-set-up-caprover-cli)
- [[**20m**] 💻 **Challenge**: Deploy Flask Application](#20m--challenge-deploy-flask-application)
- [[**05m**] ✅ **Wrap Up**: Daily Check In](#05m--wrap-up-daily-check-in)
<!-- > -->

<!-- omit in toc -->
## 🏆 Objectives

*By the end of this class, you'll be able to&hellip;*

1. Demonstrate a working, self-hosted platform as a service application available on a custom domain.
1. Use CapRover to deploy a web application written in Python and Flask.

<!-- > -->

## [**10m**] 📚 **TT**: Introduction to CapRover

Walk through the features on the [CapRover] website.

The image below walks through using [CapRover] to deploy:

<p><img src="https://caprover.com/img/captain-in-one-picture.png"></p>

<!-- > -->

## [**05m**] 💻 **Activity**: Set Up CapRover CLI

1. In order to deploy our applications successfully, we'll need to **first install the CapRover CLI**.

    ```sh
    $ npm install -g caprover
    + caprover@2.1.1
    added 196 packages from 146 contributors in 5.087s
    ```

1. Then, we'll need to **connect the CLI to our CapRover instance**:

    ```sh
    $ caprover serversetup
    Setup CapRover machine on your server...

    ? have you already started CapRover container on your server? Yes
    ? IP address of your server: 123.123.123.123
    ```

1. Finally, we're **ready to deploy** any application to our server!

<!-- > -->

## [**20m**] 💻 **Challenge**: Deploy Flask Application

1. Go to the `http://captian.dev.YOURDOMAIN.COM` in your browser.
1. From the left menu, select Apps and create a new app.
1. Name it `my-first-app`.
1. Download any of the [test apps here](https://github.com/caprover/caprover/tree/master/captain-sample-apps).
1. Unzip the content, then open a terminal and navigate to the unzipped directory.
1. Run the deploy command below. Be sure to read carefully and follow the instructions once you execute it!

    ```sh
    caprover deploy
    ```

1. Enter `my-first-app` when asked for the app name.
1. The first time you build, it'll take a few minutes. After the build is completed, visit `my-first-app.dev.YOURDOMAIN.COM`.
1. **CONGRATS! Your app is live!!** When complete, celebrate by posting the link to your working deployment on the `#bew2-2-docker` Slack channel!

<!-- > -->

## [**05m**] ✅ **Wrap Up**: Daily Check In

Check in on student progress using a Zoom poll.

<!-- > -->
<!-- do not edit below this line !-->
[Gradescope]: https://www.gradescope.com/courses/133579
[CapRover]: https://caprover.com
