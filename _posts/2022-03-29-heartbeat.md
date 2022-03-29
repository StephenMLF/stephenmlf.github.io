---
layout: post
title:  "More Heartbeats"
date:   2022-03-29 11:00:00 +0100
categories: evolver
---


# More Heartbeats

<a href="/docs/assets/images/2022-03-28-heartbeat.png">
<img src="/docs/assets/images/2022-03-28-heartbeat.png" width="600" alt="heartbeat">
</a>

Today, work on:

- Work on the C# classes:
  - [ ] `MLFHeartbeat.cs`
    - [x] Add POST functionality
  - [x] `MLFHttpParams.cs`
    - [x] Just use defaults in constructor for local testing
  - [ ] `MLFGameClient.cs`
    - [ ] Do something on receive HTTP 200 after initial Heartbeat
  - [x] `EClientState.cs`
    
{% highlight csharp %}
                        public enum EClientState
                        {
                        DISCONNECTED,
                        UNCALIBRATED,
                        CALIBRATED,
                        RUNNING
                        }
{% endhighlight %}
   

  - Work on the Python side:
    - [ ] `heartbeat.py`
    - [ ] `local_client.py`
    - [ ] HTTP needs to come through to game server to manage dictionary of `local_client`s


---

Adding POST functionality to the `MLFHeartbeat.cs` class so that it can send the initial Heartbeat when a new `MLFGameClient` is made:

<a href="/docs/assets/images/heartbeat/hb_init.png">
<img src="/docs/assets/images/heartbeat/hb_init.png" width="600" alt="heartbeat">
</a>