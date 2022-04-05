---
layout: post
title:  "Beat Mergin'"
date:   2022-04-04 09:00:00 +0100
categories: evolver
---


# Beat Mergin'

[Yesterday's question]({% post_url 2022-04-04-state-changes %}) was answered pretty easily: the reason for the delay in update of the status is simply because the patch is not initialised yet. After running _everything_ in `Create`, vvvv will then move on to the main loop.

<a href="/docs/assets/images/heartbeat/states (3).png">
<img src="/docs/assets/images/heartbeat/states (3).png" width="600" alt="hb state">
</a>

This also is not really an issue, as the vvvv team will be exposing some kind of event when the patch has finished booting whereupon we can trigger construction of a GameClient and have it update. 

It's also not really a problem to send many heartbeats in any given state as state changing will be decoupled from (for example) how many messages it has sent - the very first HB message is an exception.

🥂 This means we have a working Heartbeat/States 🥂

Today I am working half a day, so just big fat code cleanup and commenting, and getting each repo merged up to `develop`, though I may not have time to do that with the main Evolver repo.

Also helped Nils a little to get set up with running the game server locally so he can hit it with WebRequests from React.

