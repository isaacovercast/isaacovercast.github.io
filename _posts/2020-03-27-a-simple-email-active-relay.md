---
title: "Setting up a simple email active relay"
date: 2020-03-27T13:33:30-04:00
categories:
  - blog
tags:
  - hax
---

Problem: I use gmail as my primary email client (sue me). I have several email addresses
and I use "Check mail from other accounts" and POP3 to fetch external email into gmail.
Everything's all in one place so I don't have to go checking 20 different email accounts
all day long (annoying). So! At my current (nameless) employer I set this up and it worked
just fine, but then I got snippy email from IT about how I shouldn't do this because
"security". Apparently they have POP enabled? But you shouldn't use it? And they monitor it?
Ok.... 

Solution: Set up an active relay to poll and fetch email using the 'authorized' method
and forward to gmail. Again I'll use my always-on DigitalOcean droplet at
`isaacovercast.com` to run a very simple daemon process to accomplish this.
I'm going to use fetchmail to check my external account, and then procmail to
forward any emails it finds. First I edit the `~/.fetchmailrc`:

```
#### .fetchmailrc

 # Run fetchmail as a background process and poll every 300 seconds
 set daemon 300
 # Where to write logging, you should clean this up every once in a while.
 set logfile /home/isaac/tmp/fetchmail.log

 # Should be obvious
 poll pop.biologie.ens.fr proto POP3 uidl
  user "overcast" pass "xxxxxxx"
  ssl
  # Don't delete seen messages from server 
  keep
  # Don't rewrite the headers
  no rewrite
  # What to do with new mail -> make procmail deal with it
  mda "/usr/bin/procmail -f %F -d %T";
```

and `~/.procmailrc` (essentially tell procmail to forward everything it sees):
```
VERBOSE=yes
:0
! isaac.overcast@gmail.com
```

Run `fetchmail` and you're done. If the droplet goes down I have to remember to
restart this, so I add a line to `/etc/rc.local` (Ubuntu):

```
su isaac -c 'fetchmail'
```

Who knows if it works, because I don't want to cycle my box to test it. But it
__should__ work ;p.
