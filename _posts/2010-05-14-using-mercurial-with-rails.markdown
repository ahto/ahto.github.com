---
layout: post
title: Using mercurial with rails
---

This post will serve as reference for my workflow with mercurial and rails3.
It is supposed to be understandable for beginners.

I will be updating this post as I find new stuff.

Beginning new project
---------------------

    rails projectname -d mysql
    cd projectname
    
This command generates files assuming we are using git, so we need to modify them a bit.

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
    

Add files and do the first commit

    hg add
    hg commit -m "Initial"
    
Go to your favorite repo site and push it to there
For example after creating new repo on (http://www.codebasehq.com)

    hg push ssh://hg@codebasehq.com/username/project/reponame.hg
    
This is a personal preference but I like to start working always after cloning the repo so that the process is always the same.

    cd ..
    rm -Rf projectname
    hg clone ssh://hg@codebasehq.com/username/project/reponame.hg projectname


Doing some work for a change
----------------------------

Always start with a clone, bundle install, migrate and test run

    hg clone ssh://hg@codebasehq.com/username/project/reponame.hg projectname
    cd projectname
    bundle install
    rake db:migrate
    rake spec:all



