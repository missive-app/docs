---
layout: post
title:  "Email app system requirements"
date:   2018-02-10 18:10:00 +0000
category: docs
navigation_weight: 20
permalink: /:categories/:title:output_ext
excerpt: >
  Here are the server requirements for the deployable mailer app, including
  minimum PHP version, required extensions and optional extensions.
---

Missive works by deploying an app to the user's own account on a dedicated or
shared web hosting server. This means that there are some minimum requirements
the server must meet in order for the Missive deployments to work on it.

The present requirements are:

* Linux or Unix-like operating system
* Apache web server
* PHP version 5.5.9 or above
* PHP `zip` extension
* PHP `ctype` extension
* PHP `openssl` extension

The following are optional but not mandatory:

* `escapeshellcmd` function (often disabled on free hosts)
* `popen` function (often disabled on free hosts)

These are likely to change as the product matures.

With regard to the PHP version, it is recommended that only versions that are within
security support should be used. A good rule of thumb is that if a major version
[appears on the PHP website](https://php.net/) in the sidebar, then it is safe to use.
