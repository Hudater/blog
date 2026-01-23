---
## Hashnode
slug: networking-part-1
domain: hashnode.hudater.dev
subtitle: Understanding Network Devices
enableToc: true
saveAsDraft: false

# Cover Image URL of the post
# String | Optional
# Note: You must upload the image to Hashnode's CDN, before you can use it here.
# Ex: https://cdn.hashnode.com/res/hashnode/image/upload/v1681132538878/itnaYF1h-.png
# - To upload, Login to Hashnode and go to https://hashnode.com/uploader
#   Use the URL that is generated after the upload.
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1768907490094/TEkoHSA4S.jpg?auto=format

## Jekyll
title: "Networking Fundamentals: Understanding Network Devices (1/4)"
layout: post
date: 2026-01-21 05:30:00 +0530
categories: [networking-series, devices]
comments: true
pin: false
# tags: [servers, proxmox, homelab, hybrid cloud, architecture diagram]
tags:
  - networks
  - devices
  - homelab
image:
  path: "https://res.cloudinary.com/djsasyvfl/image/upload/v1767633860/Hudater_Homelab_v1.0_a2qotp.svg"
  alt: "Logical Network Traffic Diagram"
---

You might have used the internet (or are you a mysterious alien from Andromeda who has gained the ability to access this webpage through some magic!)

But you might not understand how it works. How can a company come and install one weird looking box with blinking lights and antennas and suddenly you can talk to your uncle sitting in another continent!

In this series of blogs, I'll take you on a journey through air to wires and at the end, you might just understand **Why Internet is Magical** and **How sometimes a Shark might just try to upload some fresh data in the undersea cable network**

## The WiFi Box Enigma

The device your [ISP](https://en.wikipedia.org/wiki/Internet_service_provider){:target="_blank"} installed does not serve a singular function, it actually entails a number of devices cramped into one functional unit.


Let’s break open this ISP-provided box and see what’s really inside.


### Modem

Modem stands for **Modulator/Demodulator**. It converts 