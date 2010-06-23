---
layout: post
title: Scaffolding Rails Admin
---

When scaffolding namespaced controllers you need to use the following command

Do this

    rails g scaffold 'admin/post' title:string

NOT this, this will generate almost the same thing but some links don't include the namespace.

    rails g scaffold Admin::Post title:string


