---
layout: post
title: "List of SMTP providers"
date:   2018-02-26 23:28:54:00 +0000
category: docs
navigation_weight: 60
permalink: /:categories/:title:output_ext
excerpt: >
  If your host allows external SMTP connections, you might be able to use one of
  these mail hosts.
---

Some external mail providers such as Google and Microsoft operate at the sort of scale
where it can be assumed they know what they are doing, and as such their services are
probably going to be of good quality. Equally, some mail services from smaller web
hosts will not always be up to scratch, which may be a reason to try connecting to an
external service.

Note that many [free web hosts]({% post_url 2018-02-12-list-of-free-lamp-hosts %}) do not permit
external SMTP connections, in an effort to make it harder for anonymous customers to
send spam. Other that 000webhost, all the others I tried blocked the mail ports at their
firewall. However, if you are on a paid account, you will normally be fine.

If you already use a provider below for your personal or business email, I recommend
you get a separate one for your Missive form app. That way, if your password becomes
compromised, the amount of security damage will be minimal.

### GMail

This works very well. The settings are as follows:

| Encryption | TLS |
| Host | smtp.gmail.com |
| Username | your.account@gmail.com |
| Password | your.gmail.password |

You have to make one additional setting change in GMail, which is thus:

* Go to the cog icon in the top-right
* Click on the [Settings](https://mail.google.com/mail/#settings/general) menu entry
* Click on the [Accounts and Import](https://mail.google.com/mail/#settings/accounts) tab
* Get to the [Google Accounts](https://myaccount.google.com/u/0/?hl=en) section
* Find the [Apps With Account Access](https://myaccount.google.com/u/0/security?hl=en#connectedapps) section
* Turn on "Allow less secure apps"

Even though it sounds slightly alarming, I take the view that this feature is perfectly
safe to use. Google does offer other authentication systems which do not need this
switch (particularly OAuth2) - seeing if that can be integrated is on
[the roadmap]({% post_url 2018-02-09-roadmap %}).

### Other providers

I'll test some more of these in the future. I imagine free accounts from any of the
following would be just fine:

* [Microsoft](https://signup.live.com/)
* [Yahoo](https://login.yahoo.com/account/create)
* [Zoho](https://www.zoho.eu/workplace/pricing.html)
