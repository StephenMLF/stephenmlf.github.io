---
layout: post 
title:  "Evolver Support"
date:   2022-09-13 09:00:00 +0100 
categories: [evolver]
---

## Cinemachine Camera

Spent the morning with Nils investigating Cinemachine as an alternative Camera Rig that can be controlled with Unity's timeline. Long story short: this officially supported plugin with years of dev behind it is better than the couple of scripts we wrote in a few days. Not only that, but setting camera blends means we can have multiple shots that the Main Camera blends between. This means I only had to write a very simple script to relay the `transform.position`, `transform.forward` and `transform.up` to the vvvv property connector for us to see results in vvvv. This put Nils in a position to be able to set up new camera moves with Barney.

## MLFGameClient ID

Had a call with Lucas and Maria, investigating the difficulties involved in appending `MLFGameClient` `ClientID` to the GET request url when requesting calibration, so that different calibration files can be served up on a per-user basis. We ended up having to do a bunch of digging through the Evolver patch to see if we could make that happen at a patch level, but eventually it seemed somewhat easier to expose a function to return the `ClientID` (which is assigned in C# using the client's IP) up to the patch, where it can then form part of the URL.

## Building Evolver

After this, Nils and I began the long process of getting Evolver to build on his machine. It was long because there were a lot of clashing dependencies, most notably we needed to manually upgrade the `System.Numerics` nuget to `v4.5.0` instead of `v4.4.0`. This means that Nils is able to run a build on a studio PC and control timelining from his PC in the Unity Timeline app. 
