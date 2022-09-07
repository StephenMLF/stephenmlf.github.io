---
layout: post 
title:  "Tornado & Journal Security"
date:   2022-09-07 09:00:00 +0100 
categories: [unreal, houdini, website]
---

## AM Update

Spent the morning making a tornado. [Video link](https://drive.google.com/file/d/1IOK-_8eC_oF8qKTnHBQ5-DiPB16OQGWx/view?usp=sharing).

1. Created a series of helix splines in Houdini
2. [Made the splines into a HDA](https://www.youtube.com/watch?v=G39ttn4_hp8) for getting them into UE
3. Needed to link Houdini to UE, so needed to install the correct Houdini Plugin for UE and follow [these steps](https://www.reddit.com/r/Houdini/comments/kan3tu/failed_to_start_the_houdini_engine_session_unreal/).
4. Followed the approach in [this video](https://www.youtube.com/watch?v=bHhbi0kyQ7w) to make existing (tweaked) particle system follow a spline
5. Simply modified it to take in six splines, and use Particle ID to select which spline to adhere to.

Spent time with Joy on a call to get her Niagara system spawning on a mesh correctly, and to have it so that it respected changes to the mesh's Transform.

## PM Update

Spent a while looking into the options available for making this journal (a) more private, and (b) using Google Drive links for media so they can be accessed more easily by others.

Ended up using [StatiCrypt](https://robinmoisson.github.io/staticrypt/) to encrypt the landing page, which took some setup.

I also used [this approach](https://github.com/nathancy/jekyll-embed-video) to embedding videos which works in theory, but since I don't have full control to make videos visible to anyone on the internet who has the GDrive link, people visiting are greeted with a `503`. It mentions using Youtube instead of Google Drive to get around this. Another step.

I am not a fan of Google Sites' incredibly bland offering, and no custom CSS is able to be used site wide, but I guess I will switch to this if necessary, since the Github Pages sites are inherently public and remain so unless your account is an expensive Enterprise one.