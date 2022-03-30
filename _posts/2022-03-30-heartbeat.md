---
layout: post
title:  "❤🥁"
date:   2022-03-30 09:00:00 +0100
categories: evolver
---


# More Heartbeats

Yesterday afternoon was spent focusing on and changing the logic around for this section specifically (mentioned at the end of yesterday's post), and today work needs to continue to glue this section together:

<a href="/docs/assets/images/heartbeat/hb_client_init.png">
<img src="/docs/assets/images/heartbeat/hb_client_init.png" width="600" alt="heartbeat client init">
</a>

i.e. The flow needs to be:
- [x] `MLFGameClient` sends heartbeat over HTTP
- [x] Python returns `200` 
- [x] `MLFGameClient` opens ZMQ ports and binds to `OnStateChangeTopic`
- [x] `MLFGameClient` send ZMQ message `GetClientState` with client ID
- [x] Python has a dictionary of `{clientid : local_client_class}`
  - [ ] so python needs a `local_client_class` containing
    - [x] client id 
    - [x] current heartbeat (see below)
    - [x] current state (init with `UNCALIBRATED`)
    - [ ] and a zmq client
    - [ ] function for binding to state messages from `MLFGameClient`
    - [ ] function for sending current state over zmq
    - [ ] function for updating the local client's heartbeat
  - [ ] and therefore needs to have a `heartbeat` class that contains
    - [x] client id
    - [x] 'delegate' for killing clients
    - [x] actual heartbeat values
    - [ ] function for timebomb (countdown, after which delegate is fired with client id)
    - [ ] function for updating heartbeat values
    - [ ] function for resetting timebomb (when a heartbeat is updated)
  - [x] and an `Enum` (matching C#) of the client states (see yesterday's post)
- [ ] Python returns state of client; since it just made an entry, it will be its initialised value of `UNCALIBRATED`
- [ ] `MLFGameClient` parses the result and updates its state according to the result


---

This can be simplified a bit, or broken down into different tasks:
- [x] Make some python classes that implement adding clients from heartbeat
- [x] Make timebomb functionality to be called manually which removes clients
  - Testing passing the function through to the heartbeat to have a timebomb remove client from the dictionary: [https://www.mycompiler.io/view/GFgnwn7jOdB](https://www.mycompiler.io/view/GFgnwn7jOdB)
- [ ] Make timebomb functionality actually timer based
- [ ] Add zmq receiving and updating
- [ ] Add zmq sending 
- [ ] Add receiving to C# side
  - [ ] Receiving
  - [ ] Parsing
  - [ ] Updating

