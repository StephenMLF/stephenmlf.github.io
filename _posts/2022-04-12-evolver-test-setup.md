---
layout: post
title:  "IK 🐇 Hole"
date:   2022-04-12 09:00:00 +0100
categories: evolver
---

# 🦾🐰 IK

### AM Update

Given yesterday's tests seemed to run in the studio OK, it's time to check out the IK stuff properly. 

Christian mentioned the fact that some IK matrices are only being applied when the patch has connection to the game server, so that's the first port of call.

### PM Update

Worked with Sebastian to implement two elements of robustness to the `TrackingSystem`.

First, I added a fallback/default `calibration.json` that would mean we have something to work with even if we can't GET the file from the http server. When the GET _does_ complete, we switch to using that data instead. 

<a href="/docs/assets/images/ik/ik-1.png">
<img src="/docs/assets/images/ik/ik-1.png" width="600" alt="ik">
</a>

Next, we made it so that every user has an `Audience Transform Matrix` by moving it inside `TrackingData` and applying it as it used to be, i.e.: `Model Matrix = Audience Matrix * Calibration Matrix * Transform Matrix Multiplier`

<a href="/docs/assets/images/ik/ik-2.png">
<img src="/docs/assets/images/ik/ik-2.png" width="600" alt="ik">
</a>

...then used the `Model Matrix` instead of the old `Transform Matrix Multiplier`...

<a href="/docs/assets/images/ik/ik-3.png">
<img src="/docs/assets/images/ik/ik-3.png" width="600" alt="ik">
</a>

...created a method to set the matrix for all users in the user dictionary...

<a href="/docs/assets/images/ik/ik-4.png">
<img src="/docs/assets/images/ik/ik-4.png" width="600" alt="ik">
</a>

...and made an operation that called that method with a given matrix...

<a href="/docs/assets/images/ik/ik-5.png">
<img src="/docs/assets/images/ik/ik-5.png" width="600" alt="ik">
</a>

...that we could expose at the top level of the patch for manually manipulating and testing the results!

<a href="/docs/assets/images/ik/ik-6.png">
<img src="/docs/assets/images/ik/ik-6.png" width="600" alt="ik">
</a>


### Bugfix

Spent a long time debugging why these minor changes caused a significant CPU load vs Sebastian's branch. 

Ultimately, I had at some stage moved all the MLFGameClient creation into an `If` loop, and then back out which had forced all the nodes into `Update` instead of `Create` meaning we were creating a new MLFGameClient every frame.

<a href="/docs/assets/images/ik/ik-7.png">
<img src="/docs/assets/images/ik/ik-7.png" width="600" alt="ik">
</a>