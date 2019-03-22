---
ID: 6678
post_title: >
  When you lock yourself out of Xampp
  PHPMyAdmin
author: SEO Anseo
post_excerpt: ""
layout: post
permalink: >
  https://seoanseo.ca/when-you-lock-yourself-out-of-xampp-phpmyadmin/
published: true
post_date: 2019-02-05 18:07:23
---
I've done it so many times at this point that I need to write it down!

When I create a local copy of a site and copy/paste the live files to my local machine, I often forget not to copy/paste the wp-config.php.

So...the db access get's overwritten.

Then I try to go into phpmyadmin on Xampp (ServerPress) and inevitably set a password on the root user like a dumbass and lock myself out of phpmyadmin completely.

So to save myself 45 minutes trying to figure out how to get back in the next time this happens (likely a month from now!). I'm writing this down.

1.
Go to
C:\xampplite\phpMyAdmin\config.inc.php

2.
On line 22 enter the password you set.
Change:
[php firstline="22"]$cfg['Servers'][$i]['password'] = '';[/php]
to:
[php firstline="22"]$cfg['Servers'][$i]['password'] = 'WhateverPasswordYouSet';[/php]
Now you're back in!

Best go back and reset the root user to no password and then reset it to such in config.inc.php