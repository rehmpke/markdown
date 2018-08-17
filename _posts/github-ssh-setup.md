---
layout: "post"
title: "Github SSH Setup"
date: "2018-08-17 15:49:00"
expire_date: 2018-11-07 13:00:00
image: 
news_image_alt: 'Photo of issue'
article_lead: >-
  IE issue search box . . .
video_content: false
video_link: ''
categories: server
---

# Github and other SSH Setup

Trying to make sure to remember these components of ssh setup.

I realized several things today first off I was not setup to use ssh correctly and that there is something called `ssh-add -l`, that lists out what ssh keys have been added to my [ssh-agent](https://en.wikipedia.org/wiki/Ssh-agent), a program to hold private keys which is used for public key authentication, more can be read on [OpenBSD](https://man.openbsd.org/ssh-agent). The mac has one setup that ties the agent to the keychain. this is helpful in it allows you to type your ssh into one location and just load your files.

I will clarify this shortly.

a few links I figured out this stuff at include the following:

## Permission denied (publickey). fatal: Could not read from remote repository.

-   [GitHub Error Message - Permission denied (publickey) - Stack  Overflow](https://stackoverflow.com/questions/12940626/github-error-message-permission-denied-publickey)
-   [error-permission-denied-publickey](https://help.github.com/articles/error-permission-denied-publickey/)
has a nice piece about Check that you are connecting to the correct server

        $ ssh -vT git@github.com

this lead me to a large amount of detail. I noticed it was looking for the requested key id_rsa

At that point I typed github key does it have to be id_rsa into google.
