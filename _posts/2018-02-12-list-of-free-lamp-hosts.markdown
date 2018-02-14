---
layout: post
title: "List of free LAMP hosts"
date:   2018-02-12 15:41:18:00 +0000
excerpt: >
  If you don't have a LAMP account to hand, and want to give things a low-risk try,
  sign up for one of these (really) free hosts.
---

One of the criteria for testing this project was whether the deployed application would
work on free and low-cost hosting. To test that, I am assembling a number of free hosts
here that will work with Missive.

I have no axe to grind here in recommending or warning about a particular host - they
are my own experiences, and your own experience may be different. Common sense rules
apply on the internet: if you want something for free, don't give your payment card
details.

Of course, these folks only stay in business if a proportion of their userbase upgrade
to paid facilities, so if you like a host here and need more features, don't be afraid
to upgrade!

## Criteria

* Web server connection - ideally hosts will support SFTP, which is an encrypted
protocol. The older protocol of FTP does not support encryption, but most free hosts
only offer this. It really should be removed from the internet entirely, but we are
where we are!
* Sendmail - a local mail transport system that is easy to use. It does not require
a hostname, username or password, which are used in SMTP configurations only. This is
rarely offered by free hosts though, since such configurations can easily become a
spam headache for them.
* Host SMTP - whether the host offers SMTP accounts. These are usually offered on
free hosts as a paid add-on option, partly to make life harder for spammers.
* External SMTP allowed - whether external SMTP servers can be connected to. Some
hosts set up firewall rules to prevent it, in which case, customers have no option
but to use the (usually paid) host's own sending systems.

Given the above, it's worth noting that most Missive users on free hosts will need to
use SMTP mail servers. You may be able to use a free one (e.g. a Yahoo account) or
failing that, one from the host.

---

## Tested

### [000webhost.com](https://www.000webhost.com/)

| Web server connection | FTP only |
| Sendmail | Paid option |
| Host SMTP | Paid option |
| External SMTP allowed | Yes |

The free version sleeps for one hour a day, but my experience of this host has been
pretty good, and has been a useful part of my test toolkit. The online support is
more than one would expect from any hosting company. Perfectly recommended.

---

## Not presently working

### [freehostia.com](https://www.freehostia.com/)

| Web server connection | FTP only for now |
| Sendmail | Paid option |
| Host SMTP | Paid option |
| External SMTP allowed | No |

This host looks very promising, and the control panel is extensive, if rather busy for
beginners. Free users will need to configure their own domain, which is not trivial
on any host. SFTP connections are supported from an FTP client, so Missive needs a
tweak to get this working.

Unfortunately the lack of external SMTP means that no form-to-email solution will
work unless one upgrades.

## Not yet tested

* [Byet Internet Services](https://byet.host/)
