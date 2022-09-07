---
layout: post 
title:  "Niagara VR Limits"
date:   2022-09-06 09:00:00 +0100 
categories: [unreal]
---

## AM Update

Testing the maximum number of particles we can spawn without seeing huge performance hits this morning. 

Encountered potential (enormous) issue that Niagara may not work in VR, so tested this before progressing further by getting Nils to make a build of what we have.

## PM Update

Nils managed to get a build onto an Oculus 2 and run 200K particles plus a reduced version of the skeleton; whilst seemingly less than 1FPS, the niagara system was visible on the Quest.

Separately, 2M particles (the max for one Niagara system) ran OK on my 3070, but adding another system in (so 4M particles) took us to around 5FPS. Consulted with Sebastian and he thought that Evolver was hitting somewhere in the region of 10-12M particles in vvvv so obviously this sucks, however I have a 4GB 3070 and Evolver ran on a 12GB 3080Ti. Will try to use the demo PC at the studio to run a similar test at some point soon. 