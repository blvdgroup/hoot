# hoot

**All of the below is prospective. Until such point that hoot is marked "stable" and/or "ready for production," nothing from this repository should be used in a production environment. This readme, at this current point in time (17/06/25), outlines what we would like to build, not what has yet been built. With that said, if you believe in the future of education and want to aid in creating it, I invite you to contribute as outlined below.**

This is the source code for hoot. To read more about what hoot is, be, and do, please visit our website at [hoot.rocks](https://hoot.rocks). If that website is totally blank and/or worthless, it's probably because I haven't built it yet, in which case your best bet for learning more about hoot is consulting the oracle.

This readme will cover the technical aspects of running your own instance of hoot, and contributing . It's free and easy.

## Legal

hoot is entirely licensed under the Mozilla Public License 2.0. The full text of this license can be found in the LICENSE file in this repository.

Using hoot for evil is not only allowed, but highly encouraged.

## Structure

Here's a brief runthrough of the structure of this repo and how hoot works:

- _`/packages/@hoot/`_ is the heart of the thing. It contains all the packages used within hoot, and one could theoretically run hoot entirely based off of this folder and a hearty amount of chutzpah, although I cannot recommend it.
  - _`core/`_ is the core web server on which a hoot instance runs. It handles all incoming http requests and parses them using a really nice library called `micro`. By itself, it is worthless, as the other packages give hoot all of its features. It's also important to note a significant amount of setup must be done before you can actually use the core (databases and such) - much of which is avoided if you just use a Docker image, because it's 2017.
  - _`login/`_ is the single-sign-on, SAML 2.0 compliant aspect of hoot. It can be used instead of setting up your own SSO service, and it has some other nifty features too with regards to integration with the rest of the suite. All of the features described either require hoot login, or some other SSO solution to already be implemented and setup.
  - _`admit/`_ is the full admissions suite - parsing Common and Coalition applications for admissions officers, allowing peer review of applications on-site, even allowing prospective students to apply directly through your website. It is a must have if you're still dealing with applications the old, paper-based way.
  - _`class/`_ is the direct competitor to [Dominant Education Company Who Shall Not Be Named] Learn. Wikipedia refers to it as a "virtual learning environment" and "course management system" which sounds right, but to get more into the nitty gritty, this is where teacher can assign homework, upload class materials, give practice tests, and all sorts of fun stuff, and it's also where students can curse their poor judgement in not taking the practice test before the final exam.
  - _`test/`_ is the test administration suite, allowing certified computers in certified testing centers to administer tests without fear of student interference or cheating. On the server side, it's not very useful without certified computers and some setup (see below), but this does have to be enabled for testing to work at all.
  - _`enroll/`_ is the course catalog and student management system. Administrators can have fine grained control over student access to classes, manage class size and enrollment numbers quickly and efficiently, and generally just have some nice things. Students can have a fun, stress-free time enrolling in classes and prepping their schedule. (Well, I mean, stress free as this sort of thing gets.)
- _`/hardware/`_ handles non-software related stuff. This is generally called "hardware."
  - _`swipe/`_ contains full specifications for the Swipe series of hoot products. These include ID cards, ID card makers, and card readers. While we sell compatible ID card makers and card readers already, if you so choose you can go out and solder it yourself. (We won't stop you.)
- _`/software/`_ contains, well, software. There are some programs that hoot uses that aren't just webservers. Unless otherwise stated, these are all electron based applications.
  - _`test/`_ is the software used to run tests on testing center devices. The `test` package must already be enabled on the webserver as well for this to work at all. Note that no compiled binaries are provided - you must fill out certain variables and compile the binaries yourself.
- _`/Dockerfile` handles the docker environment. This allows environments to remain uniform across platforms, and makes setup and beginning to contribute on a new computer much easier. However, if you prefer not to use Docker for whatever reason, you may still set up the developer environment any way you choose. (Keeping in mind that there is absolutely no liability on our part if you break your computer while doing so.)

## Development Setup

### Easy Mode

```sh
$ git clone https://github.com/hootrocks/hoot
$ cd hoot
$ docker build .
$ docker run -p 3000:80
```

Open up `3000` in any given browser to open your personalized development environment.

### Hard Mode

**TODO**

## Production Setup

Please **contact us** if you're interested in using hoot at your school. An easy way to get started is on [our website](https://hoot.rocks).

## Contributing

We welcome contributions from all.

### Code of Conduct

Hoot contributions must be made according to the code of conduct contained within this repository, under `CONDUCT.md`. If you are the type of person who dislikes the very concept of having to adhere to a code of conduct, contributing to hoot may not be for you. Consider travelling to the nearest beach or lake, so that you might lie by the body of water and reflect.

### Issues/PRs

We're happy to accept new issues and pull requests. Before you submit an issue, please ensure an open issue does not already exist for the problem you face.

Pull requests should adhere to the cz-blvd commit message standard. (`git cz`, not `git commit`!) Please also ensure all your code meets the blvd styleguide for TypeScript. If you add functionality, be sure to add tests which test this functionality.

Our issues are best viewed in [waffle.io](https://waffle.io/), which we use to track progress.

_(Please note that, as we are in an extremely early in the development cycle, large parts will shift around you, and pull requests may become difficult to merge. Avoid pull requests, especially larger in scope, until the software reaches a more stable point in development.)_

[![forthebadge](http://forthebadge.com/images/badges/built-by-hipsters.svg)](http://forthebadge.com)
[![forthebadge](http://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com)
