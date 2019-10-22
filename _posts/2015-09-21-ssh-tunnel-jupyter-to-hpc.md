---
title: "How to open a jupyter notebook on a compute node of your HPC"
date: 2015-09-21T13:33:30-04:00
categories:
  - blog
tags:
  - hax
---
Documenting more for the sake of posterity than for the lack of other
documentation available on the internet, also all the docs for ssh tunneling
I saw were confusing, so here's a non-confusing version.

I have a chromebook and i'm also an avid jupyter notebook user. I run tons of
notebook servers on remote boxes, since i obviously can't install it locally,
so normally I'll attach to my notebooks using the web interface, which default
opens on port 8888.

Two situations arise where this doesn't work: 1) Some wireless networks
disallow all traffic except http port 80 and ssh. 2) Firewalled networks (such
as hpc clusters or large campus networks) filter traffic similarly.

So, what to do to get access to my jupyter notebooks? SSH Tunneling is the
answer. In this way you can tell ssh to route traffic to the desired port on
the remote host, through the ssh connection.

Get Chomebook secure shell app
Type in your username and hostname for the remote system (the one with ipython notebook running)
SSH Arguments: -L 8888:localhost:8888
This is the imporant and confusing bit. 'localhost:8888' is telling the remote server where to forward to, and the first '8888' is telling your local machine where to access this forward.
Open a new tab and go to http://localhost:8888. Voila.
This is the best diagram on the internet (image courtesy http://www.cyberknights.com.au/doc/PuTTY-tunnelling-HOWTO.html)

[!png](/assets/images/tunnel-concept-diagram.png)
