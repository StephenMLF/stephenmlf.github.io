---
layout: post
title:  "State Changes"
date:   2022-04-04 09:00:00 +0100
categories: evolver
---


# State Changes

Worked with Lucas to prepare for discussing the State management within vvvv with the vvvv team. 

Loosely, we needed to show how we would expose the state held by the C# `MLFGameClient` so that they could change things inside vvvv.

First we sat down to see what mighht be causing the multiple initialisation of clients discovered at the end of last week. After introducing **a flag to allow initialisation to run only once**, it seems that we were simply sending/receiving heartbeats and their responses faster than we were processing the responses into client initialisation and state change.

After doing this, we had to get a vvvv implementation up so that we could see this `Enum` inside a `Class` and watch for it changing, so that vvvv logic can be performed on it (pictured).

<a href="/docs/assets/images/heartbeat/states (1).png">
<img src="/docs/assets/images/heartbeat/states (1).png" width="600" alt="hb sub error">
</a>

<a href="/docs/assets/images/heartbeat/states (2).png">
<img src="/docs/assets/images/heartbeat/states (2).png" width="600" alt="hb sub error">
</a>


Posted the following question to the vvvv gang with the above pictures:

Hey team - am I doing something wrong here? Having trouble with the Observable reporting the correct values just after boot.

In images:
1. Client inits as `DISCONNECTED`, reports correctly
2. When the client initialises, it sets its little internal C# timer going, firing off heartbeat messages; the first response it gets after the server has made an entry for it sets the MlfGameClient's internal state to `UNCALIBRATED` , which it then uses for sending the further Heartbeats, as can be seen below #2 in the image (i.e. the MLFGameClient's internal state is already correctly set at this point)
3. It takes until the whole patch boots up for the Observable to give the correct response, at which point it triggers and does its thing, but loooong after it's been set to `UNCALIBRATED` , meaning many heartbeat messages later.


Questions:
1. `@vvvv gang`: Under the hood, C# is ready and rolling with its HTTP response, parsing and modifications to client state, is there a way this can report in this reactive way sooner than when initial boot is finished? Am I even doing it correctly as pictured?
2. `@Lucas Moskun`: How much does this matter? We send a lot of heartbeats in that time, and an unknown number, but when will we progress to the next state? Are we planning only to request the calibration data from within vvvv after the patch has booted? What will trigger the next state change? Seems this could be really problematic if it's under the hood in C# or Python to me, but otherwise maybe not?

To be continued tomorrow...
