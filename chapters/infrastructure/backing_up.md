---
layout: recipe
title: Backing Up
chapter: Infrastructure
---

# Backing Up Production

To backup the production database from Heroku, run the following commands:

    heroku pgbackups:capture --app teamleada
    curl -o latest.dump `heroku pgbackups:url --app teamleada`

Then, to restore into your local database for development purposes, run the following:

    rake db:drop
    rake db:create

    pg_restore --verbose --clean --no-acl --no-owner -h localhost -U mark -d teada_development latest.dump

    rake db:migrate
    rake db:seed

