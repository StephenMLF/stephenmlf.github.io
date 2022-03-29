---
layout: post
title:  "More Heartbeats"
date:   2022-03-29 11:00:00 +0100
categories: evolver
---

<meta property="og:image" content="/docs/assets/images/heartbeat/hb_init.png" />


# More Heartbeats

<a href="/docs/assets/images/2022-03-28-heartbeat.png">
<img src="/docs/assets/images/2022-03-28-heartbeat.png" width="600" alt="heartbeat">
</a>

Today, work on:

- Work on the C# classes:
  - [ ] `MLFHeartbeat.cs`
    - [x] Add POST functionality
    - [x] Trigger POSTing from constructor
  - [x] `MLFHttpParams.cs`
    - [x] Just use defaults in constructor for local testing
  - [ ] `MLFGameClient.cs`
    - [ ] Do something on receive HTTP 200 after initial Heartbeat:
      - if internal state is DISCONNECTED and receive 200:
        - set up zmq and bind to heartbeat topic
    - [ ] Internal state management per client
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
      - [x] make clientID a string (and any necessary changes this requires)
      - [x] HTTP needs to come through to game server to manage dictionary of `local_client`s
    - [ ] `local_client.py`
      - ~~is this necessary? we already have `heartbeat_dictionary` which is storing most recent heartbeats in the following format: `heartbeat_dictionary.update({clientID: unpacked_json})` .~~
        - yes this is totally necessary, see image


<a href="/docs/assets/images/heartbeat/hb_client_dict.png">
<img src="/docs/assets/images/heartbeat/hb_client_dict.png" width="600" alt="heartbeat client dict">
</a>
    


---

🎉 Adding POST functionality to the `MLFHeartbeat.cs` class so that it can send the initial Heartbeat when a new `MLFGameClient` is made: 🎉

<a href="/docs/assets/images/heartbeat/hb_init.png">
<img src="/docs/assets/images/heartbeat/hb_init.png" width="600" alt="heartbeat">
</a>

---

The afternoon had been spent focusing on and changing the logic around for this section specifically:

<a href="/docs/assets/images/heartbeat/hb_client_init.png">
<img src="/docs/assets/images/heartbeat/hb_client_init.png" width="600" alt="heartbeat client init">
</a>

i.e. The flow needs to be:
- [x] `MLFGameClient` sends heartbeat over HTTP
- [x] Python returns `200` 
- [x] `MLFGameClient` opens ZMQ ports and binds to `OnStateChangeTopic`
- [x] `MLFGameClient` send ZMQ message `GetClientState` with client ID
- [ ] Python has a dictionary of `{clientid : local_client_class}`
  - [ ] so python needs a `local_client_class` containing
    - client id 
    - current heartbeat (see below)
    - current state
    - and a zmq client
    - function for binding to state messages from `MLFGameClient`
    - function for sending current state over zmq
    - function for updating the local client's heartbeat
  - [ ] and therefore needs to have a `heartbeat` class that contains
    - client id
    - delegate
    - actual heartbeat values
    - function for timebomb (countdown, after which delegate is fired with client id)
    - function for updating heartbeat values
    - function for resetting timebomb (when a heartbeat is updated)
  - [x] and an `Enum` (matching C#) of the client states
- [ ] Python returns state of client; since it just made an entry, it will be its initialised value of `UNCALIBRATED`
- [ ] `MLFGameClient` parses the result and updates its state according to the result