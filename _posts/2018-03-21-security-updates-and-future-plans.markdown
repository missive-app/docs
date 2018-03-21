---
layout: post
title:  "Security updates and news"
date:   2018-03-21 16:30:48 +0000
category: blog
excerpt: >
  An update on current development.
---

A few weeks ago, I asked a number of folks to offer some early feedback on my alpha version
of Missive. I've collected some great feedback, including how end-users perceive the
security risk of trusting third party tools, and I've been sent some various notes on
UX and usability.

One of the important considerations for building Missive is its security, so for the
past couple of weeks I've been working on a data validation system, which examines
every piece of data entered into the web application, and rejects any data that does
not look right. That is now deployed.

The blog and documentation site has been revamped to make it easier to follow.

One of my alpha users has suggested that some users may be wary of supplying
their web server credentials to a third-party service they don't know, so I have been
giving some consideration to that issue. My current thinking is to allow users to
upload an installer package to their server manually, which would circumvent the need
to supply any credentials at all.

This might look something like this tabbed interface, offering the new mechanism by
default:

![Package deployment](/assets/web-server-self-deploy.png)

This will use an existing remote-control system (of limited capability) to carry out
new deployment actions (e.g. installing a new config file).

The existing password-based system would still be available, in a secondary tab:

![Credential deployment](/assets/web-server-credentials.png)
