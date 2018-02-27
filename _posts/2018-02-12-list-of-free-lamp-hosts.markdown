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
to upgrade. Paid services are also more likely to be of better quality - a number of
hosts I tried were way more trouble than they were worth.

## Criteria

* Web server connection - ideally hosts will support SFTP or FTPS, which are encrypted
protocols. The older protocol of FTP does not support encryption, but most free hosts
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

| Web server connection | FTPS, FTP |
| Sendmail | Paid option |
| Host SMTP | Paid option |
| External SMTP allowed | Yes |

The free version sleeps for one hour a day, but my experience of this host has been
pretty good, and has been a useful part of my test toolkit. The feature-set is somewhat
limited, but that makes this host much easier to set up than many others I tried.

The online support is more than one would expect from any hosting company, and they
even delve into programming problems, which hosts normally don't want to touch. I
am happy to recommend this host.

---

## Not presently working

### [awardspace.com](https://www.awardspace.com/)

| Web server connection | FTP |
| Sendmail | Works occasionally |
| Host SMTP | Paid option |
| External SMTP allowed | No |

The paid options for this host would probably be fine, but the free tier is a slog to
use. External SMTP is not permitted, and support confirmed for me that their own SMTP
does not work with free accounts. I got Sendmail sort-of working, but it did not feel
reliable.

There was a lot of extra set-up required with this host. To use their SMTP servers,
you'll need to use your own domain or subdomain, which means editing DNS records with
your DNS provider. You then need to add a sub-domain in the web interface, and then
finally set up an email account for the SMTP.

When exploring the SMTP options in the free tier, I found that only port 25 was
open, and the server certificates are unfortunately self-signed, so encryption and
Auto TLS need to be disabled. However, it is possible the paid accounts have
a better configuration.

### [freehostia.com](https://www.freehostia.com/)

| Web server connection | FTPS, FTP |
| Sendmail | Paid option |
| Host SMTP | Paid option |
| External SMTP allowed | No |

This host looks very promising, and the control panel is extensive, if rather busy for
beginners. Free users will need to configure their own domain, which is not trivial
on any host.

Unfortunately the lack of external SMTP connectivity means that no form-to-email
solution will work unless one upgrades.

### [byet.host](http://byet.host/)

| Web server connection | FTP |
| Sendmail | ? |
| Host SMTP | ? |
| External SMTP allowed | ? |

Nope, nope, nope. The host sets their own cookies and inject this JavaScript:

{% highlight html %}
<html><body><script type="text/javascript" src="/aes.js" ></script><script>function
toNumbers(d){var e=[];d.replace(/(..)/g,function(d){e.push(parseInt(d,16))});return e}
function toHex(){for(var d=[],d=1==arguments.length&&arguments[0].constructor==Array?
arguments[0]:arguments,e="",f=0;f<d.length;f++)e+=(16>d[f]?"0":"")+d[f].toString(16);
return e.toLowerCase()}var a=toNumbers("f655ba9d09a112d4968c63579db590b4"),b=
toNumbers("98344c2eee86c3994890592585b49f80"),c=toNumbers(
"a9c4a3be9b84420c1cf732936c18da0d");document.cookie="__test="+toHex(
slowAES.decrypt(c,2,a,b))+"; expires=Thu, 31-Dec-37 23:55:55 GMT; path=/";
location.href="http://missive-demo.byethost5.com/host_check.php?i=1";</script>
<noscript>This site requires Javascript to work, please enable Javascript
in your browser or use a browser with Javascript support</noscript></body>
</html>
{% endhighlight %}

Aside from behaving like malware, this corrupts the JSON answers from the various
scripts deployed by Missive, and so is probably unusable. I contacted their support
channel, and they said this is "caused by our anti bot / spam protection that is
mandatory on free hosting". They say their premium offering does not do this.

I couldn't get any further than the Script Location tab with this host, which is
where the first host test script is deployed.

### [heliohost.org](https://www.heliohost.org/)

| Web server connection | SFTP |
| Sendmail | No, doesn't allow `popen()` |
| Host SMTP | ? |
| External SMTP allowed | ? |

This service is volunteer run and looks pretty good on the surface, including full
cPanel provision. However I've had some difficulties with accounts locking on a
very sensitive wrong-password trigger, as well as periods of server downtime. The
default server for new users, "Johnny", has an uptime of around 90%, and is really
for testing only.

Presently this service needs file permission adjustments before they will run,
so I'm regarding it as unsuitable for now. I will happily look again though in
the future, in case the situation changes.
