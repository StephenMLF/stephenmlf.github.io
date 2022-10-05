---
layout: post 
title:  "WUND: FBX to Sphere Unit Sculptures"
date:   2022-10-03 09:00:00 +0100 
categories: [wund, houdini]
---

## FBX to Sphere Unit Sculptures

### Links
- [https://www.youtube.com/watch?v=aOisEGCA3zk](https://www.youtube.com/watch?v=aOisEGCA3zk)
- [https://www.youtube.com/watch?v=3wqpHCgrS8g](https://www.youtube.com/watch?v=3wqpHCgrS8g)
- [https://www.youtube.com/watch?v=3nA72vbMOqY](https://www.youtube.com/watch?v=3nA72vbMOqY)
- [https://www.youtube.com/watch?v=pDBGlhNC9aY](https://www.youtube.com/watch?v=pDBGlhNC9aY)

{% highlight c %}
float small = 0.5;
float medium = 0.75;
float large = 1;

if (@convexity < ch('threshold1')){
@pscale = small * ch('global_multiplier');
}
else if (@convexity < ch('threshold2')){
@pscale = medium * ch('global_multiplier');
}
else {
@pscale = large * ch('global_multiplier');
}
{% endhighlight %}

### Discussions/Process Documentation
- https://marshmallowlf.slack.com/archives/C041S7UBAEL/p1664808260543719 