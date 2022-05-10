---
layout: post
title:  "More QA"
date:   2022-05-10 09:00:00 +0100
categories: evolver
---

# More QA


### AM Update

Spent the first half of the day trying to get more work into the Lateral Movement issue. We found a bunch of things:

- We were previously getting 20+ms for Encoder latency which is now down to around 8ms with some heavy tweaking and i think with our GPU priority setting
- We were getting consistent 50+ms spikes for Send/Receive which took a while to figure out... seems like there was an OOA network running in the studio which we have disabled
- We were losing packets to Fec(?), and at the top just generally. More tweaks means we are reporting no packet loss now
- Sending at 72Hz, we seem to have a stable movement left to right on one headset.

<a href="/docs/assets/images/debugging/alvr (1).png">
<img src="/docs/assets/images/debugging/alvr (1).png" width="600" alt="post_calibration">
</a>

<a href="/docs/assets/images/debugging/alvr (2).png">
<img src="/docs/assets/images/debugging/alvr (2).png" width="600" alt="post_calibration">
</a>

<a href="/docs/assets/images/debugging/alvr (3).png">
<img src="/docs/assets/images/debugging/alvr (3).png" width="600" alt="post_calibration">
</a>

### PM Update

Managed also to test Sebastian's work:

- Spent some time with Nils mapping the playspace in the studio, and then transferring to vvvv Seb's Calibration tool
- This meant we got `calibration.json` info for the position of the pillar and also the outline of the space
- Verified that we could trigger them by having our heads/hands collide with their edges