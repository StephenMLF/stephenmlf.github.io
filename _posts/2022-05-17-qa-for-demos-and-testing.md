---
layout: post 
title:  "QA for demos and testing"
date:   2022-05-17 09:00:00 +0100 
categories: evolver
---

# QA for demos and testing

### AM Update

Moved all the servers into new racks and rewired them. Pulled `feature/studio-testing` and checked that Sebastian's smoothing of skeletons worked - it did and it makes a huge difference!

Setting up QA structure and tasks that need to be completed. Also on Notion [here](https://www.notion.so/marshmallowlaserfeast/17-05-2022-e1eb36587ae34b50a7c8690dc62ed926).

|Category|Task/Test|Description|Verified|
| --- | --- | --- | ---|
|**Timeline**|Timeline Completed| Make it through the entire timeline|:heavy_check_mark:|
| |Timeline Sync|All headsets see same timeline events||
|**Particles**|Qi Particles|Visible and working as intended||
| |Particles interactable|Hand movements can influence particles||
|**Headset**|Kiosk|Automatically enter running vvvv patch and pinch disabled||
| |Tracking|Headsets do not reset tracking||
|**Game Engine**|Spectator|Sees all users and timeline events||
| |Spectator projection|GPU load and performance when projecting||
| |States|Entering Emergency mode; showing 'Raise Hand' UI||
|**Audio**|Audio|Audio coming through headset & subpac||
|**Network**|Network load|Load with 6+1 clients does not reduce performance/quality of experience||
|**Frontend**|Controller|Web requests complete/timeout rapidly (<10s)||
|**Automation**|ALVR|ALVR starting automatically||
| |Windows Update|Management of user group/policy to block updating||
| |Startup client|Startup scripts for client machines||
| |Startup server|Startup for server/docker container||
|**Quality**|ALVR Settings|Optimise quality vs performance settings|| 

