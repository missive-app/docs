---
layout: post
title: "Alpha testing and feedback"
date:   2018-02-11 17:18:00 +0000
excerpt: >
  An introduction to folks interested in the alpha version of Missive. It works,
  but there's probably bugs...
---

Welcome! You're probably reading this because I've been talking about
[Missive](https://missive-test.jondh.me.uk/) in a chat channel, Reddit, or some other
forum. This is a prototype project that's been a labour of love for a number of months,
and I'd love some feedback on it, both good and bad.

I want the system to have a solid free offering, so that people can deploy useful
forms from the web wizard free of charge. Once this becomes reliable, I'll consider
adding for-fee add-ons.

So, feel free to kick the tyres, and send me your unvarnished thoughts `:-)`

## Rationale

A common problem I see in programmer's forums is folks struggling with setting up
a contact form. The main problems I see are:

* Using PHP's `mail()` feature despite its problems and inflexibility;
* Security problems, such as a lack of rate-limiting and header injection;
* SMTP authentication failures (or bumping into rate-limiting after a large number
of failures);
* Not having any visibility on what part of a send is failing

Put simply, sending email programmatically, and doing it safely, is something
that looks easy and actually isn't. Thus, I found myself wondering back in July 2017
whether I could make this easier.

## Similar projects

Every now and again I see form builder systems, such as:

* [TypeForms](https://www.typeform.com/)
* [FormKeep](https://formkeep.com/)
* [FormGet](https://www.formget.com/)
* [PageClip](https://pageclip.co/)

If you know of any others, do let me know! Being aware of what else is available in this
space is very useful.

I have not found any that are self-hosted though, and especially not with
automated deployments. Of course, I will have to make a good effort to see
how useful that is in practice, given the overhead involved of maintaining it. However,
given how much I see people struggle with this task, I think it is helpful.

## Areas of feedback

My questions at this stage are what features this project needs to gain some traction.
I think it is already useful, but then I am biased! I am also interested in how I
can show it is secure enough to use, given that I am handling people's security
credentials.

There are a number of broad areas I would like to look at:

* Documentation (what do people need?)
* Support channels (Twitter? Chat widget? Discourse? Slack?)
* Features (what do users actually want? See also [the roadmap](/2018/02/09/roadmap.html))
* Pricing for future add-ons

## What you will need

Since the point of this project is to deploy software onto your own server, you will
need a web server with an FTP or SSH account. A shell account on a VPS or dedicated
server is probably fine, as long as you have an web folder and PHP support. cPanel
accounts are normally ideal as well.

Finally, if you don't have an account to hand,
[free accounts are available](/2018/02/12/list-of-free-lamp-hosts.html).

## Feedback forum

Feedback is welcome via any channel you can reach me:

* Whatever channel I've spoken to you on
* A related blog or Reddit post ([such as this one](https://talk.birmingham.io/t/contact-form-email-deployment-project/3507))
* The chat widget on the application home page
* Or, failing that, drop me a line at `missive-feedback.ws@jondh.me.uk`

## About the author

My name's Jon, and I am a contract software engineer in
[Birmingham](https://en.wikipedia.org/wiki/Birmingham)
([map](https://www.openstreetmap.org/#map=14/52.4788/-1.8909)), specialising in PHP.
I can be found on [Stack Overflow here](https://stackoverflow.com/users/472495/halfer)
and I [blog rather sporadically here](https://blog.jondh.me.uk/).

I also post over at [CircleCI](https://discuss.circleci.com/u/halfer) and
tech forum [Birmingham.IO](https://talk.birmingham.io/u/halfer).
