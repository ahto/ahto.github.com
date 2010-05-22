---
layout: post
title: Quick debugging mail server
---

When you are testing emails, a very quick way is to run the following command and when you send emails through smtp://localhost:8025 the email is printed out in the terminal.

Brilliant!

    python /usr/lib/python2.6/smtpd.py -n -c DebuggingServer localhost:8025
