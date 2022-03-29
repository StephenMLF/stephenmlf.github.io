---
layout: post
title:  "Heartbeat"
date:   2022-03-28 16:00:00 +0100
categories: evolver
---
<link rel="shortcut icon" type="image/x-icon" href="favicon.ico">

# Heartbeats

With the timeline work last week done, the overview looks like this:

<a href="/docs/assets/images/2022-03-25-timeline.png">
<img src="/docs/assets/images/2022-03-25-timeline.png" width="600" alt="overview">
</a>

Began work to understand how to integrate the heartbeat into Evolver

<a href="/docs/assets/images/2022-03-28-heartbeat.png">
<img src="/docs/assets/images/2022-03-28-heartbeat.png" width="600" alt="heartbeat">
</a>


There are a lot of moving parts, because first the client must communicate via HTTP, then when a connection has been established and confirmed we can use ZMQ to communicate. 

We need the Heartbeat class to be capable of sending itself over HTTP, to the POST request we set up in FastAPI

We have to duplicate a bit of work here between Python and C# in order to have them agree on the data.

We also need a state machine that can handle these changes (see diagram).