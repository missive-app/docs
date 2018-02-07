Set-up notes for the Missive Docs
===

Installation
---

There seems to be several ways to get Jekyll installed on Ubuntu. I used the following:

    sudo apt-get install jekyll bundler

The recommended "quick" way in the manual did not seem to work - there were a number
of Ruby build errors. This can be fixed with installing some Ruby dev dependencies,
but installing Jekyll from the Ubuntu repo just seems more straightforward.

Local serving
---

The site can be served locally using this command:

    bundle exec jekyll serve

Remote site
---

The site is published on the GitHub CDN at https://missive-app.github.io/.
