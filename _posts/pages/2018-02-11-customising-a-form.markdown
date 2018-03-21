---
layout: post
title:  "Customising a form"
date:   2018-02-10 18:10:00 +0000
category: docs
navigation_weight: 40
permalink: /:categories/:title:output_ext
---

Forms are rendered in sections, so that each section can be overridden by custom
HTML as required. This documentation will show how to do that.

## HTML structure

Here is a form example, inside a simple HTML document. This is included
in the deployed application as `index.php`:

{% highlight php %}
<!DOCTYPE html>
<html>
    <head>
        <title>Demo of form-to-email system</title>
        <script
            src="https://code.jquery.com/jquery-3.2.1.min.js"
            integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4="
            crossorigin="anonymous"></script>
        <script type="text/javascript" src="form/js/scripts.js"></script>
        <script type="text/javascript" src="form/js/messages.js"></script>
        <link href="form/styles/styles.css" rel="stylesheet">
    </head>
    <body>
        <div id="missive-container">

            <div id="missive-message-holder"></div>

            <form id="missive-email-form">
                <div class="missive-form-section">
                    Email:
                    <input
                        type="email"
                        name="user_email"
                        value=""
                        placeholder="email@example.com">
                </div>
                <div class="missive-form-section">
                    Title:
                    <input
                        type="text"
                        name="user_title"
                        value=""
                        placeholder="Title">
                </div>
                <div class="missive-form-section">
                    Full name:
                    <input
                        type="text"
                        name="user_full_name"
                        value=""
                        placeholder="Full name">
                </div>
                <div>
                    <input
                        class="missive-send"
                        type="submit"
                        value="Send">
                    <span><img class="missive-spinner" src="spinner.gif"></span>
                </div>
            </form>
        </div>
    </body>
</html>
{% endhighlight %}

This page contains a number of features:

* A `<head>` section containing references to CDN and local assets
* An overall block `missive-container` containing the whole system
* A place to write success/error messages, in `missive-message-holder`
* The form itself, `missive-email-form`
* Form section blocks, labelled with `missive-form-section` classes
* The input elements themselves
* A submit button, `.missive-send`
* A progress spinner GIF, `.missive-spinner`

The `id` and `class` attributes may change a little, especially during the alpha
period of Missive, while I work out what CSS hooks are useful for most people.

Many cosmetic changes can be done using CSS. However, in some cases, the HTML
itself will need to be customised. Read on to see how that can be done!

## File structure

Inside the main app directory, the following directory structure is used:

    form/
        child/
            README
        default/
            assets.php
            comments.php
            container.php
            submit.php
            user_email.php
            user_first_name.php
            user_full_name.php
            user_last_name.php
            user_telephone.php
            user_title.php
        js/
            messages.js
            scripts.js
        styles/
            styles.css
        utility-funcs.php
    config.php
    index.php
    investigator.php
    mailer.php
    spinner.gif
    storage.php

The pieces that can be overridden are in the `default` directory. To replace one or
more of these with a custom version, create an identically-named file and put it in
the `child` directory. One easy way of doing this is to copy the default version of
a file to the child directory, and then modify the child copy as you wish.

As long as you keep your customisations to the child folder, they will survive
upgrades from the main control panel. However, users are still recommended to take
their own automated daily backups.

Example integration
---

In a real-world usage, a form is likely to be rendered in an existing page. As long
as that page can execute PHP code, it can integrate a Missive form.

Where any Missive code is called, it needs its libraries to be loaded. The following
code will do that, and this can be added in the PHP page itself, or in whatever
bootstrap file that is available:

{% highlight php %}
<?php
$root = __DIR__;
require_once $root . '/vendor/autoload.php';
require_once $root . '/form/utility-funcs.php';
?>
{% endhighlight %}

Of course, the root directory may need adjustment.

Next, the assets need to be loaded, which is usually done in the `<head>` of the
page in question:

{% highlight php %}
<?php renderTemplate('assets.php') ?>
{% endhighlight %}

Finally, in the appropriate place in the body, the developer can add this tag:

{% highlight php %}
<?php renderTemplate('container.php') ?>
{% endhighlight %}

Of course, for any pre-defined section, the developer can choose to add the
appropriate code into their solution without using the rendering helper. For
example, it is not necessary to use the `assets.php` script - if it is more
convenient to use `<script>` and `<link>` tags directly to load the necessary
files, that is fine.
