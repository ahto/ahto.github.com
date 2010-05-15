---
layout: post
title: Rubinius in Ubuntu 10.04
---

Requirements
------------

I have a system that has compiled MRI 1.8.7 and MRI 1.9.2-head succesfully so the only thing I added was texinfo.

    sudo aptitude install texinfo

    
Install
-------

    rvm install rbx
    
And that's it.


Usage
-----

I'm wating for [mysql2 gem to work on it](http://github.com/evanphx/rubinius/issuesearch?state=open&q=mysql2#issue/296) before starting any testing.
