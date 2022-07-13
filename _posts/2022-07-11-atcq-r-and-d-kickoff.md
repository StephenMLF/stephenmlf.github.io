---
layout: post 
title:  "ATCQ R&D Kickoff"
date:   2022-07-11 09:00:00 +0100 
categories: [unreal, atcq]
---

# Beginning R&D

Spent the day collating, collecting, ingesting and digesting relevant and useful information for the A Tribe Called Quest Midnight Marauders project over on Miro [here](https://miro.com/app/board/uXjVOoqtOWY=/?moveToWidget=3458764528968613180&cot=14).

Was mostly focusing on the techniques that might need to be implemented to achieve both deepfaking with Metahumans and facial morphing between two characters (person x -> Steve Biko), and spent a little time experimenting with the results of StyleGAN-NADA; an update to NVIDIA's StyleGAN2 process.

<video controls width="600">
    <source src="/docs/assets/images/atcq-r-d/rep-01.webm" 
            type="video/webm">
</video>

<video controls width="600">
    <source src="/docs/assets/images/atcq-r-d/rep-02.webm" 
            type="video/webm">
</video>

<a href="/docs/assets/images/atcq-r-d/rep-collage.jpg">
<img src="/docs/assets/images/atcq-r-d/rep-collage.jpg" width="600" alt="stylegan-nada collage">
</a>

Though this is designed as a general AI capable of style transfer, its movement through latent space is guided by CLIP so it can be told to arrive at a text prompt from an image, such as arriving at 'Steve Biko' from 'Person':

<a href="/docs/assets/images/atcq-r-d/steve-original.png">
<img src="/docs/assets/images/atcq-r-d/steve-original.png" width="600" alt="stylegan-nada steve">
</a>

<a href="/docs/assets/images/atcq-r-d/steve-biko.png">
<img src="/docs/assets/images/atcq-r-d/steve-biko.png" width="600" alt="stylegan-nada steve">
</a>

These results are after 250 iterations, it took about 400 to reach something more passable, but still skin tone was a problem for a GAN whose dataset is largely trained on Caucasian people.