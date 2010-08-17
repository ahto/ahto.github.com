---
layout: post
title: Using mercurial with rails
---

This post will serve as reference for my workflow with mercurial and rails3.
It is supposed to be understandable for beginners.

I will be updating this post as I find new stuff.

Setup the machine
---------------------

Update RVM

    rvm update --head

Make sure your ~/.rvmrc has at least this

    rvm_install_on_use_flag=1
    
Install latest Bundler

    gem install bundler --pre
    
Add alias to ~/.bashrc for resetting database

    alias reset_database='rake db:drop:all; rake db:create:all && rake db:migrate && rake db:seed'

Installing rails
---------------------

    gem install rails --pre

Beginning new project
---------------------

    rails new projectname -d mysql
    cd projectname
    
Add these to the projects rvmrc files

    echo "rvm 1.9.2@projectname" >> .rvmrc
    
Mercurial
------------

Above commands generates files assuming we are using git, so we need to modify them a bit.

All the .gitkeep files are ok and should be left where they are so that empty directories are kept in version control too.

Add some important folders that are empty because of the following .hgignore file

    touch log/.gitkeep tmp/.gitkeep

create new repo

    hg init

Create .hgignore file and remove the git version

    touch .hgignore
    rm .gitignore
    
And copy these in .hgignore

    syntax: glob
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
    nbproject
    

Add files and do the first commit

    hg add
    hg commit -m "Initial"
    
Go to your favorite repo site and push it to there
For example after creating new repo on (codebasehq.com)[http://www.codebasehq.com]

    hg push ssh://hg@codebasehq.com/username/project/reponame.hg
    
This is a personal preference but I like to start working always after cloning the repo so that the process is always the same.

    cd ..
    rm -Rf projectname
    hg clone ssh://hg@codebasehq.com/username/project/reponame.hg projectname
    cd projectname
    
Mysql
----------

In the gemfile, change mysql to mysql2 and run 'bundle update'.
Then in database.yml, replace "adapter: mysql" with "adapter: mysql2"

Then create the databases

    rake db:create


Doing some work for a change
----------------------------

Always start with a clone, bundle install, migrate and test run

    hg clone ssh://hg@codebasehq.com/username/project/reponame.hg projectname
    cd projectname
    bundle install
    reset_database
    rake spec:all



