---
layout: post
title: Using mercurial with rails
---

This post will serve as reference for my workflow with mercurial and rails3.
It is supposed to be understandable for beginners.

Beginning new project
---------------------

    rails projectname -d mysql
    cd projectname
    
This command generates files assuming we are using git, so we need to modify them a bit.

All the .gitkeep files are ok and should be left where they are so that empty directories are kept in version control too.

create new repo

    hg init

Create .hgignore file and remove the git version

    touch .hgignore
    rm .gitignore
    
And copy these in .hgignore

    syntax: glob
    #newline here
    .bundle
    config/database.yml
    config/*.sphinx.conf
    config/s3_credentials.yml
    *~
    *.cache
    *.log
    *.pid
    tmp/**/*
    .DS_Store
    db/cstore/**
    db/sphinx/**
    doc/api
    doc/app
    doc/plugins
    doc/*.dot
    coverage/*
    db/*.sqlite3
    *.tmproj
    *.sw?
    vanity.html
    .git
    *.gem
    
Keep important folders that are empty

    touch log/.gitkeep tmp/.gitkeep
    
Add files and do the first commit

    hg add .
    hg commit -m "Initial"


