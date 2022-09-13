---
layout: post 
title:  "Niagara Forces & Unity Cameras"
date:   2022-09-12 09:00:00 +0100 
categories: [unreal, unity, niagara]
---

## Influencing Niagara

Managed to get an external actor to influence Niagara systems of two different kinds [[VIDEO](https://drive.google.com/file/d/1H8XM0arRUoaVDsCwOV040i3dH3Qktk32/view?usp=sharing)]:
- The tornado is the spline following system which is lerping between sticking directly to the splines and a noise-influenced position; the RightHandSphere object is the position for a point force on the system, and the particles move back nice and smoothly when the force no longer impacts them.
- The orange sphere is a Niagara system where particles update their positions based on a baked point cache from Houdini, meaning they are sticking to where they are told to be pretty religiously. As a result, after the RightHandSphere interacts with them in the same way, they move back to their positions from the point cache a little less 'naturally'.

Notes: The video is wayyyy choppier than what it actually was like in real life for some reason. Also the radius of influence and force strength are cranked way up to make the effect visible at these distances, and can be tweaked til kingdom come.

## PM Update

Spent a good chunk of time with Nils trying to figure out kinks in the Camera rig system we created. Although the system worked perfectly in the Editor, as soon as we timelined elements, there were big issues, since there was figting between the positions as calculated by our script and those that were being determined by keyframes in the Animation window. We tried many things, including moving the script calculations to `LateUpdate()` but no dice. Ultimately paused due to time, but this is a high priority task to be addressed tomorrow.