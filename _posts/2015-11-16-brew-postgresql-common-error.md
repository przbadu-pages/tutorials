---
layout: post
author: Pushpa Raj Badu
title:  Brew Postgresql common error
date:   2015-11-16 17:37:49
categories: brew postgresql
description: Fix brew and postgresql error "Is the server running locally and accepting connections ...."
---


`brew` postgresql error for rails migrations:
----------------------------------------------

      could not connect to server: No such file or directory
          Is the server running locally and accepting
          connections on Unix domain socket "/tmp/.s.PGSQL.5432"?

I was frequently having this problem in my `yosemite` when I was trying to migrate my database in rails application. I have installed postgresql with `Home Brew` package manager.

The problem was a `pid` file was blocking postgres from starting up.

I found this solution, which works perfectly for me:

      $ rm /usr/local/var/postgres/postmaster.pid
