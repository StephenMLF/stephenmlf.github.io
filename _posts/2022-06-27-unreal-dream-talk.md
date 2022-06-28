---
layout: post 
title:  "Unreal Dream Talk"
date:   2022-06-27 09:00:00 +0100 
categories: [unreal, dream]
---

# Unreal Dream Talk

Talk from Ollie at All Seeing Eye taking us through Dream and its many moving parts in Unreal.

Notes:

- DataProvider as an actor for controlling/recording all data; using Sequencer & TakeRecorder
- Offline Mocap system
- Show control over OSC
- MPCs for Materials
- Editor Utility Widget hooked into a blueprint actor for control over level sequences
- Unreal Sequencer has ability to 'trigger all intermediate events' so you don't miss keyframes when scrubbing
- UE Subsystems (like UE singletons)
- Interfaces also using Messages to communicate through interfaces without caring about whether it is implemented or not

Ollie also pointed me in the direction of [this article](https://cesium.com/learn/unreal/unreal-procedural-foliage/) which may contain the answer to solving the Render Target problem in the quest for deformations.