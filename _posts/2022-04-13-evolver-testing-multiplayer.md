---
layout: post
title:  "Multiplayering"
date:   2022-04-13 09:00:00 +0100
categories: evolver
---

# Multiplayering

### AM Update

At the [end of yesterday]({% post_url 2022-04-12-evolver-test-setup %}), we spent a good while making sure that we could get the multiplayer up and running in the studio.

We eventually got to a stage where we were receiving data from another client as before, though the data coming in was garbage because we weren't properly inside the application on the sending side.

Today, Nils will test this setup to make sure we can have a multiplayer experience in place before tomorrow's external demos in the studio.

I'll work with him to resolve any bugs and hopefully to merge what we have in our IK branch in with other work in develop.

### PM Update

Merging vvvv files sucks. After spending all morning trying to merge `develop` into an old merge branch, with the IK work on top, we then decided to try to make a new branch from `develop` and merge in the IK branch. Every time we tested, ALVR lost connection to vvvv.

Just finished recreating _only_ the Audience Matrix Transform stuff (so all yesterday's work) in a new branch off develop, so we can isolate it from the IK stuff. Nils will test... Still haven't been able to test multiplayer.

Thankfully, the demos scheduled for tomorrow in the studio have been cancelled, so the pressure is more to deliver the audience transform work in a way that means Natan can use it.