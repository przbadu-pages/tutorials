---
layout: post
author: Pushpa Raj Badu
title:  "Nginx reverse proxy cache"
date:   2015-07-10 17:37:49
categories: cache
description: this will helps to learn about nginx reverse proxy cache. And list of steps to make it working for ruby on rails 4 application.
---

***References:***

https://devcenter.heroku.com/articles/caching-strategies
https://mattbrictson.com/nginx-reverse-proxy-cache
https://www.packtpub.com/books/content/using-nginx-reverse-proxy
http://ghost.thekindof.me/using-varnish-v4-as-a-reverse-proxy-cache-with-rails/
https://www.codementor.io/devops/tutorial/devops-tutorial-nginx-reverse-proxy



1. ALLOW RAILS RESPONSES TO BE CACHED
----------------------------------

**Send appropriate cache headers**

    class MyController < ApplicationController
      before_filter :allow_page_caching

      # controller actions...

      private

      def allow_page_caching
        expires_in(5.minutes) unless Rails.env.development?
      end
    end

**Remove CSRF**

    <%# Remove this to allow caching %>
    <%= csrf_meta_tags %>

**Do not set session or cookie data.**


2. ENABLE THE REVERSE PROXY CACHE IN NGINX
------------------------------------------


***Finally, a nice documented nginx unicorn(or anyother webserver) file:***
https://github.com/defunkt/unicorn/blob/master/examples/nginx.conf
