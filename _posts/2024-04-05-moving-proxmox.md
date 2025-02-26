---
title: "Moving Proxmox to New Subnet"
date: 2024-04-05 22:40
author: tiff
description: Moving Proxmox to new subnet poses challenges.
excerpt: Moving Proxmox to new subnet poses challenges.
tags: [networking]
category: [Homelab, Proxmox]
---

I've been wanting to get my Proxmox cluster plugged into my UDM Pro for at least a year now. A few issues were:

- Accessing the cluster from a different subnet
- Updating the IP address of each node in the cluster
- Keeping old LXC containers and VMs in tact
- Keeping HDD and SSD mountpoints in tact

## Wait. Why?

You may be asking, "tiff, why move the cluster at all?" This is a fair thing to ask because it was a headache and a half to get this working. The juice that made it worth the squeeze: The Unifi Network Application.

Being able to monitor what is coming in and out of those nodes on my network is important to me.

A few months back my Synology got hit with a barrage of bot attacks from someone scanning for open ports in Shodan or something. The only reason I knew was because I'd logged in to do something and noticed thousands of notifications DSM fly by each second. Luckily for me I'd hardened the security on my Synology well enough to withstand the days long barrage of bots but it would have been nicer to know ahead of time and, with more data at my disposal, know what to do about it, where the failure points were so I could mitigate something like that in the future.

For my Proxmox cluster, this is especially critical because of the services I host on it. I am still learning as well so security is something I am implementing as I know more about how to lock down your services exposed to the web and having that data could be a useful tool in progressing with this.

## How I solved the issue

There are a few steps I took that I will link below. In the first GitHub gist,

<script src="https://gist.github.com/twhite96/2ed4c6f3d50ed0009947c69e7bded6ca.js"></script>

This was fine but I still couldn't get three of my nodes to properly resolve the new IP addresses.

I followed this Reddit post for guidance:

<blockquote class="reddit-embed-bq" style="height:316px" data-embed-height="316"><a href="https://www.reddit.com/r/Proxmox/comments/avk2gx/help_cluster_not_ready_no_quorum_500/">Help! Cluster not ready - no quorum? (500)</a><br> by<a href="https://www.reddit.com/user/cjalas/">u/cjalas</a> in<a href="https://www.reddit.com/r/Proxmox/">Proxmox</a></blockquote><script async="" src="https://embed.reddit.com/widgets.js" charset="UTF-8"></script>

Response to OP that I used:
<br>

> The following steps will unlink your cluster. You can create a new cluster of course. I'm just warning you.
> {: .prompt-danger }

<br>

<blockquote class="reddit-embed-bq" data-embed-height="436"><a href="https://www.reddit.com/r/Proxmox/comments/avk2gx/comment/ehg0gg2/">Comment</a><br> by<a href="https://www.reddit.com/user/cjalas/">u/cjalas</a> from discussion<a href="https://www.reddit.com/r/Proxmox/comments/avk2gx/help_cluster_not_ready_no_quorum_500/"><no value=""></no></a><br> in<a href="https://www.reddit.com/r/Proxmox/">Proxmox</a></blockquote><script async="" src="https://embed.reddit.com/widgets.js" charset="UTF-8"></script>
