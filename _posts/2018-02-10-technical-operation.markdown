---
layout: post
title:  "Technical operation"
date:   2018-02-10 16:08:00 +0000
---

This document offers some technical detail about what happens at selected stages of
the completion of the Missive wizard.

## Web server connections

Web server credentials are required so that the Missive server can make a number of
deployments. A hostname, username and password are required. For security reasons,
web server passwords are stored temporarily for immediate use, and then thrown away.

Both encrypted (SFTP) and unencrypted (FTP) connections are supported, with encryption
being preferred if the server supports it. In general, free hosts tend to only support
FTP.

## Host check

A simple script (`host_check.php`) is deployed to the web server that returns simple
information about the web server. This helps Missive understand its capabilities,
and whether it satisfies some required and optional modules:

It returns its data in a document like this:

{% highlight json %}
{
  "ok": true,
  "modules": {
    "required": {
      "zip": true,
      "ctype": true,
      "openssl": true,
      "php": true
    },
    "optional": {
      "escapeshellcmd": false,
      "popen": false
    },
    "info": {
      "php_version": "7.1.11",
      "proceed": true,
      "warning_code": "no_sendmail"
    }
  }
}
{% endhighlight %}

The optional modules are needed for users who prefer Sendmail over SMTP. In the
example above, both of the optional modules are not satisfied by the web server, 
so the `no_sendmail` flag is also returned.

Presently this script is left on the web server, but it will probably be deleted
automatically in a future release. Users who like to keep things tidy can safely
delete this file after deployment without stopping anything working.

## Email server credentials

A page is provided to record the email credentials (hostname, username, and password).
These are in fact required only for SMTP, and if Sendmail is selected, the credentials
can be skipped.

If Sendmail is not available, SMTP is fine - you'll just need to get credentials
from your web service provider. You can often just use a free email provider like
GMail or Yahoo as well.

In a similar fashion to web server credentials, SMTP credentials are stored just
temporarily in the Missive system. This means in the unlikely event that
the system is cracked and the user database data is stolen, the value to a cracker
is rather limited.

Of course, SMTP passwords must be stored on a remote web server permanently, so
it is a good idea to use a low-value account. This means that if someone does
get a hold of your email password, the worst impact is that the account may be
used to send spam, rather than confidential material being obtained from your
Sent Items folder.

## App deployment

When deploying the form app on a web server, Missive will use a pre-compiled
compressed file called `package.zip`. It will also send an decompressor script
called `unzip.php`, which is called remotely to unzip the package, and then
self-deletes.

At this point, the remote app offers some limited remote control capabilities
to make the deployment as easy as possible. There are two sub-systems here:
"Investigator", which is used to check and test the system, and "Mailer",
which contains facilities needed for the live form.

A brief list of these features are set out below:

### Investigator

| Feature | Description
| ------- | ----------- |
| port | Check if an email server port is available |
| validate | Performs a system self-test |
| exists | Check if a PHP function is available |
| build | Returns information about the version of the deployed system |
| email | Sends a test email |
| erase | Erases the whole app |

### Mailer

| Feature | Description
| ------- | ----------- |
| field-list | Lists the available fields so they can be rendered in JavaScript |
| hello | Simple way of checking mailer script is available |
| email | Send an email |

## Test email

Sending a test mail is done before the final configuration file is deployed to
the remote server, so all the configuration is sent with the request. Test messages
may only be sent to registered email addresses on the system.

The Missive app does need the SMTP password for this operation (unless another mail
transfer system is specified), but as usual the password is deleted after the process
finishes.

For SMTP requests, a log is available, to help debugging failing send operations.

## Erase app

Users may remove the app from their server by activating the erase option, which
will remove all files that were part of the original deployment. While this should
not delete any new files added as part of a customisation, nevertheless, users are
advised to take regular backups of their web space.

## Configuration deployment

The final step is the resending of the configuration details so that the form
behaves as designed. This sends an updated `config.php` containing, amongst other
things, the contents of the emails sent when the form is completed.
