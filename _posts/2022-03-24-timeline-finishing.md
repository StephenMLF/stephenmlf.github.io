---
layout: post
title:  "Finished up timeline"
date:   2022-03-24 18:00:00 +0100
categories: evolver
---

# Timeline finished!

The timeline that will run Evolver is now operational.

It is integrated into the FastAPI REST server and can be interacted with via HTTP requests.

<video controls width="600">
    <source src="/docs/assets/videos/2022-03-24 15-36-38.webm" 
            type="video/webm">
</video>

- HTTP server is booted
- Timeline `phase_config.json` is loaded
- Using FastAPI we can test drive running commands on the timeline
- The server prints out any relevant data and returns to the HTTP client
- The timeline outputs data every x seconds (default is 0.5) and when receiving any HTTP request
- Worked with Lucas and Sebastian to integrate zmq through to vvvv
- Timeline message is output through MLF SDK ZMQ client & intermediary
- Incoming message in vvvv is put into a class, an instance of which is then updated
- The incoming message is split according to relevant JSON markers and feeds the Timeline Debug Tool
- Timeline Debug Tool is integrated into the main Evolver patch for testing and handover to vvvv team