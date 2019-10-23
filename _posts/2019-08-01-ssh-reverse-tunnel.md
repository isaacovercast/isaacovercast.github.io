---
title: "Accessing resources blocked by campus IT with SSH reverse tunnels"
date: 2019-08-01T13:33:30-04:00
categories:
  - blog
tags:
  - hax
---

Problem: Campus IT decides to shut down external SSH access to your lab
workstations. Solution: Reverse SSH tunnels!

## Background
We have several high-powered workstations that various members of the lab log
into to run simulations and analyses. We *used* to have SSH access to these
machines from off campus via dedicated IP addresses. Recently, the campus IT
folk decided to "harden" security by turning off all access to externally
available IPs, so now we are in a pickle. We still want terminal access to
these boxes, but how to make it happen? Reverse SSH tunnels to the rescue!

## Reverse SSH tunnel magic
The logic of reverse SSH tunnels is that you bounce traffic to the firewalled
machines off a box that you **do** have control of somewhere else on the
internet. The mechanics involve routing SSH traffic through an available port
on the external server to the SSH process on the firewalled workstation.

Here's the gist:
* Sit down at (or log into) the firewalled workstation.
* Open a reverse ssh connection from the firewalled box to the external machine.
* Establish an SSH connection to the external box to the new port and the
traffic is forwarded to the previously unavailable workstation.
* BAM! You have a terminal on the workstation inside the firewall.

## Configuring the reverse SSH tunnel

For the purposes of this tutorial let's say the firewalled workstation is called
`workstation1` and the local user account on the firewalled workstation you'd
like to log in to is "local_user". Assume that the externally available computer
lives at `remote_box.com`, has SSH enabled, and that the user you'd like to log
into on this box is `remote_user`. Here's how to establish a reverse SSH tunnel
to give you remote access to this machine:

* Sit down at `workstation1`
* Type the following command `ssh -o ServerAliveInterval=60 -fN -R \*:9666:localhost:22 remote_user@remote_box.com`
> **NB**: This will establish a reverse SSH tunnel from the `remote_box` port
port 9666, to the firewalled box port 22.
* Enter the password for the `remote_user` on the remote machine. This establishes
the reverse SSH tunnel.
* Test the setup: From any computer, anywhere on the internet type:
`ssh local_user@remote_box.com -p 9666`
> **NB:**: This will bounce traffic off the publically available `remote_box`
port 9666 to the firewalled `workstation1` default SSH port (22).

MAGIC!!!!!!



