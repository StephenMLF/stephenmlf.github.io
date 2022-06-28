---
layout: post 
title:  "Deformations and Midnight Marauders"
date:   2022-06-28 09:00:00 +0100 
categories: [unreal, sweet-dreams, atcq]
---

# Deformations and Midnight Marauders

After Ollie's tips yesterday, managed to make a Render Target that I could write particle positions to.

<a href="/docs/assets/images/unreal/def-01.png">
<img src="/docs/assets/images/unreal/def-01.png" width="600" alt="deformations">
</a>

<a href="/docs/assets/images/unreal/def-02.png">
<img src="/docs/assets/images/unreal/def-02.png" width="600" alt="deformations">
</a>

<a href="/docs/assets/images/unreal/def-03.png">
<img src="/docs/assets/images/unreal/def-03.png" width="600" alt="deformations">
</a>

<a href="/docs/assets/images/unreal/def-04.png">
<img src="/docs/assets/images/unreal/def-04.png" width="600" alt="deformations">
</a>

Since we can now write the particle position (actually `Particles.Position - Particles.MyMeshLocation`, where MyMeshLocation is a vertex position that is updated) to a render target, we could then use that render target to plug in to the world position offset, giving us this:

I enlisted some support from both Nils and Sebastian today.

<video controls width="600">
    <source src="/docs/assets/videos/2022-06-28 09-49-03.webm" 
            type="video/webm">
</video>

After that, Nils made me some geometry where the UVs were set up so that each vertex was evenly spaced and square, like on this plane, which meant I could position the particles back onto the Render Target at specific locations with their colour, giving us this wavy plane:

<video controls width="600">
    <source src="/docs/assets/videos/2022-06-28 13-48-25.webm" 
            type="video/webm">
</video>

However, we needed a more general approach, for when UVs weren't set up as rigidly as this, as in the case of the sphere; plus needing to sort out some confusing jankiness from some unknown location. We managed the first part, which involved using the `Get Vertex UV` node, to create this:

<video controls width="600">
    <source src="/docs/assets/videos/2022-06-28 17-13-37.webm" 
            type="video/webm">
</video>

Soooo nearly there, but there seems to be some strange behaviour relating to exactly which vertex is writing/reading from the texture, causing vertices still to not line up with particle positions. 

To be continued...