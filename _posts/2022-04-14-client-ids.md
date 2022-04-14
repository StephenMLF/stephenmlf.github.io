---
layout: post
title:  "Client IDs"
date:   2022-04-14 17:00:00 +0100
categories: evolver
---

# Client IDs

Hefty bit of work including a bunch of refactoring over in vvvv world today with big help from Sebastian.

Effectively, we need to synchronise the IDs the game client is using for communication with the game server, and internally, so that we can perform associated logic on it, such as destroying it and re-establishing connections in the future.

We need to do something like this:

<a href="/docs/assets/images/ids/ids.png">
<img src="/docs/assets/images/ids/ids.png" width="600" alt="ids">
</a>

During lots of head scratching, we moved all of the things to do with Client IDs up to the Network level instead of within TrackingData.

This whole process took pretty much the whole day, but the result is the following:

<a href="/docs/assets/images/ids/id-sync.png">
<img src="/docs/assets/images/ids/id-sync.png" width="600" alt="id-sync">
</a>

- vvvv GET requests an ID from the server, reported back in the console (`2` in image)
- vvvv uses that ID to construct/init an `MLFGameClient`
- `MLFGameClient` begins sending heartbeat(s) with that ID
- After some time, we stop the game client
- This triggers the timebomb _for the appropriate client_ on the game server, and its entry is destroyed

Nils is now testing this in studio, but it appears to be working back to back when starting/stopping the patch repeatedly.

