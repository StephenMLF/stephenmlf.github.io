---
layout: post 
title:  "Unity Camera Rigging"
date:   2022-09-09 09:00:00 +0100 
categories: [unreal, unity]
---

## Camera Rigging in Unity

Spent the majority of the day working on a more complete system of Camera movement manipulation with Nils in order to create a system that can have:

- [x] A camera whose parent object can be changed (keyframe-able) so that it can orbit around its parent (simply by rotating the parent) - `Orbit Mode`
  - [x] Whilst in Orbit Mode, the camera's position can be moved with rotation, but its distance to the orbit point should be able to be changed with a `DepthToOrbitPoint` parameter
- [x] A camera whose world position can be manipulated and keyframed - `Non Orbit Mode`
- [x] A camera whose view direction can be controlled by the position of a `Point Of Interest` object

This took some time because the camera itself reports its position to Unity's inspector in local space, and when switching parent Unity remembers that local position and applies it to the object with reference to its new parent.

We needed to make a script where we could switch parent without the camera instantly jumping, and switch in and out of Orbit Mode without jumping.

## Approach to VR hands & Niagara

The latter part of the day was spent researching how we could achieve VR hands influencing a Niagara system, and I collated some useful links here on the associate notion card [here](https://www.notion.so/marshmallowlaserfeast/Interaction-of-VR-Hands-Niagara-systems-3c33c1e4e5fa47e5abaea66004b90fc8).

There are a couple of approaches, but to start with, using a sphere collider as a way of adding velocity to particles seems to make the most sense, and will be where I can pick up next.

