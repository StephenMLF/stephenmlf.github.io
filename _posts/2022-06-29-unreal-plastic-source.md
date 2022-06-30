---
layout: post 
title:  "Unreal Source on Plastic"
date:   2022-06-29 09:00:00 +0100 
categories: [unreal, sweet-dreams, atcq]
---

# Unreal Source on Plastic

Had catchups with Nils, and with Lucas and Maria to talk about the upcoming work, and to set things up a little ahead of Monday when we will be doing the ATCQ Onboarding.

## With Nils

- With Nils we were attempting to get Unreal building an apk that the Quest 2 could run, just with the VR demo, to iron out some of the kinks in the various Android SDK/JDK/NDK etc etc settings that need to be understood before getting into production proper. This took a long time.
- The goal of this was to see if we can get any of the work we have produced so far into a headset and see what we need to optimise for VR so we can have an understanding of what we cannot accomplish in a headset.

## With Lucas and Maria

- Had a preliminary chat with the backend gurus about the technical landscape of the ATCQ project, and how it will define some prerequisites of the project; they had produced a [Miro board](https://miro.com/app/board/uXjVOpo50DA=/) looking at it.
- Defining any kind of relatonship that implies a gap between a timeline (Sequencer) **Conductor** and **Follower(s)** suggests that it would make sense to run Unreal as a [Dedicated Server](https://docs.unrealengine.com/5.0/en-US/setting-up-dedicated-servers-in-unreal-engine/):

> To follow the steps in this how-to, your project needs to satisfy the following requirements:
> - You must be using a source build of Unreal Engine, which you can download from the Epic Games Github.
>   - If your project is using a binary build from the Epic Games Launcher, you will need to migrate it to a Github source build.
> - You must have a C++ project that can support server-client multiplayer gameplay.
>   - If you are using a Blueprint project, you will need to convert it to a C++ project before you can proceed.



- This meant we need our own repository to house the Unreal Engine source, simple enough to fork into a github repo, but we aren't in the practice of using github internally, so I needed to explore other options:
  - Spent a good amount of time trying to fork the repo out to our Bitbucket account, but Bitbucket refused to accept pushes of over 2GB and repos of over 10GB, both of which were failures I had to discover through a series of esoteric command line git issues. This took ages.
  - Eventually after a chat with Mike looked into forking into a new Plastic repo instead. The instructions on actually doing this were pretty lacking, though a [good bit of documentation exists about the concept of Gitsync itself](https://www.plasticscm.com/documentation/gitsync/plastic-scm-version-control-gitsync-guide). Eventually, I found [a video in Japanese where someone actually did it](https://youtu.be/B0a3H3_-VKc?t=1229), and set it running. Since it's such an enormous repo with such a huge commit history, and Plastic effectively converts the entire git history to a Plastic-friendly one, I started it at 1630 and it's still going right now at 1000 the next day...   