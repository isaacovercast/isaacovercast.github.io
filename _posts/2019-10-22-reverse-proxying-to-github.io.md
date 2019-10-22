---
title: "Configuring apache2 as a reverse proxy for HTTP/HTTPS"
date: 2019-10-22T13:33:30-04:00
categories:
  - blog
tags:
  - hax
---

Problem: I have a vm running on 'the cloud', which is useful for various things, including
having my `www.isaacovercast.com` domain pointed at it. Now, nobody wants to run their own
http server anymore because IT IS A DRAG. Using a `github.io` page for personal sites is
definitely in fashion these days, and it makes a lot of sense. I still want to be able to 
ssh into my vm, but I want http/https requests to go to my `isaacovercast.github.io` site.
Hm?

Solution: Bounce requests for ports 80 and 443 off `isaacovercast.com` to the github.io page
by using apache as a reverse proxy. Cribbed the general directions from [here](https://devops.ionos.com/tutorials/configure-apache-as-a-reverse-proxy-using-mod_proxy-on-ubuntu/). Now, the only reason this is a good idea
and worked for me is because I already had apache2 installed, so just had to reconfigure
it a bit. If you _don't_ have apache2 installed there's probably a smarter way of doing this.

Edit your `/etc/apache2/sites-available/000-default.conf` and make it look like this
```
<VirtualHost *:80>
    # A simple redirect for http traffic
    ServerName www.isaacovercast.com
    Redirect / https://isaacovercast.github.io
</VirtualHost>

<VirtualHost *:443>
    # Somewhat fancier for https
    ServerName www.isaacovercast.com
    SSLEngine On
    SSLCertificateFile /etc/apache2/ssl/ca.crt
    SSLCertificateKeyFile /etc/apache2/ssl/ca.key
    Redirect / https://isaacovercast.github.io
</VirtualHost>
```

Restart your apache2 server (`sudo service apache2 restart`) and you're done.
