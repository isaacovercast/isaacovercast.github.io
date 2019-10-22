---
title: "How to open a jupyter notebook on a compute node of your HPC"
date: 2015-09-21T13:33:30-04:00
categories:
  - blog
tags:
  - hax
---
Problem: I want to run jupyter notebooks on remote systems.

Solution: SSH tunnelling!

> **NB:** These directions are chromebook specific, but extensive ssh tunnel +
jupyter notebook documentation for mac and windows are provided on the [radcamp
jupyter notebook setup page](https://radcamp.github.io/AF-Biota/Jupyter_Notebook_Setup.html).

I have a chromebook and i'm also an avid [jupyter notebook](https://jupyter.org/)
user. I run notebook servers on remote boxes, since i obviously can't install
them locally, so normally I'll attach to my notebooks using the web interface,
which default opens on port 8888.

Two situations arise where this doesn't work: 1) Some wireless networks
disallow all traffic except http port 80 and ssh. 2) Firewalled networks (such
as hpc clusters or large campus networks) filter traffic similarly.

So, what to do to get access to my jupyter notebooks? SSH Tunneling is the
answer. In this way you can tell ssh to route traffic to the desired port on
the remote host, through the ssh connection.

* Get [Chomebook secure shell app](https://chrome.google.com/webstore/detail/secure-shell/pnhechapfaindjhompbnflcldabbghjo?hl=en)
* Type in your username and hostname for the remote system running (the box running
the notebook server)
* Add the following to the `SSH Arguments`: `-L 8888:localhost:8888`
> This is the imporant and confusing bit. 'localhost:8888' is telling the remote
server where to forward to, and the first '8888' is telling your local machine
where to access this forward.
* Open a new tab on your laptop and go to `http://localhost:8888`. Voila!

This is the best diagram on the internet (image courtesy [cyberknights.com.au](http://www.cyberknights.com.au/doc/PuTTY-tunnelling-HOWTO.html)).

![image](/assets/images/tunnel-concept-diagram.png)
