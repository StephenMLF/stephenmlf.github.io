---
layout: post 
title:  "WUND Creative Development #05"
date:   2022-10-04 09:00:00 +0100 
categories: [wund, houdini]
---

## Customising Sphere Scattering & Growth

### Links
- [Controlling shortest path growth](https://www.youtube.com/watch?v=siL-sbLTGe8&t=312s)
- [Using curvature of mesh as input to scatter density](https://www.youtube.com/watch?v=oeN5KgvWHfs)
- [Quick curvature calcs (reverse AO method)](https://www.sidefx.com/docs/houdini/nodes/sop/labs--measure_curvarture-2.0.html)

### Discussions/Process Documentation

[Discussion #1](https://marshmallowlf.slack.com/archives/C041S7UBAEL/p1664878579932259)
- Scattering points on geometry based on thickness of geometry
- Density of points (i.e. total number) controllable with slider
- Using curvature (convexity) of geometry to select from one of three sizes of unit (small, medium, large)
- Controlled using thresholds to determine at what levels of convexity different sizes should be selected
- Global control of size of all units
- (FBX Export of resulting geometry)
 
### PM Update

[Discussion #2](https://marshmallowlf.slack.com/archives/C041S7UBAEL/p1664899545383679)
Process:
1. Generate/use reference Geometry (pictured is just a sphere-y thing)
2. Grow branches according to reference geometry
3. Tweak existing system for taking geometry and describing it using 3 different sizes of spheres