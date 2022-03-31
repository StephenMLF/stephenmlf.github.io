---
layout: post
title:  "Pulsating Hearts"
date:   2022-03-31 09:00:00 +0100
categories: evolver
---


# Pulsating Hearts

### AM update:

[Yesterday had a great moment]({% post_url 2022-03-30-heartbeat %}) of completing the first back and forth between game client and server.

<a href="/docs/assets/images/heartbeat/hb_comms.png">
<img src="/docs/assets/images/heartbeat/hb_comms.png" width="600" alt="heartbeat comms">
</a>

So everything up to that dashed box is now complete! 

We (game client) told the server we existed, and it sent us a `200`, so we opened up a zmq connection and started listening for state changes from the server. 

The server kept track of us and made an instance of the local game client class, where it set us to be `UNCALIBRATED`, and bound to a ZMQ topic, expecting the client to request what state it is in from the server. 

Since we are still set to `DISCONNECTED` but received a `200` from the server, we can send a ZMQ message requesting our state on that topic. 

The server receives that message, and fires a callback, reporting the status of that client by sending a message _back_ over ZMQ on the topic we bound to - _et voila!_ - the Game Client receives which state it should be in, and can process it further.

---

Today, we need to add the 'process it further' bit to the C# side - adding Parsing and Updating our state functionality.

- [x] Make some python classes that implement adding clients from heartbeat
- [x] Make timebomb that can be called manually which removes clients
  - Testing passing the function through to the heartbeat to have a timebomb remove client from the dictionary: [https://www.mycompiler.io/view/GFgnwn7jOdB](https://www.mycompiler.io/view/GFgnwn7jOdB)
- [x] Make timebomb functionality actually timer based
- [x] Add zmq receiving and updating
- [x] Add zmq sending 
- [x] Add receiving to C# side
  - [x] Receiving
  - [ ] ~~Parsing~~
  - [x] Updating
- [ ] **NEW:** Actually implement some kind of state machine so that e.g. when in `UNCALIBRATED` we can perform actions, like requesting the `calibration.json` via HTTP GET (as in diagram).

---

We also need to tick some more stuff off on the Python end, like updating the current heartbeat _values_ and writing out to a file, plus actually implementing the consistent firing of the heartbeat up to the server so that we don't hit our timebomb...  

- [x] `MLFGameClient` sends heartbeat over HTTP
- [x] Python returns `200`
- [x] `MLFGameClient` opens ZMQ ports and binds to `OnStateChangeTopic`
- [x] `MLFGameClient` send ZMQ message `GetClientState` with client ID
- [x] Python has a dictionary of `{clientid : LocalClient}`
  - [x] so python needs a `LocalClient` containing
    - [x] client id
    - [x] current heartbeat (see below)
    - [x] current state (init with `UNCALIBRATED`)
    - [x] and a zmq client
    - [x] function for binding to state messages from `MLFGameClient`
    - [x] function for sending current state over zmq
    - [x] function for updating the local client's heartbeat
      - [x] this needs to be called when receiving heartbeat
  - [x] and therefore needs to have a `ClientHeartbeat` class that contains
    - [x] client id
    - [x] 'delegate' for killing clients
    - [x] actual heartbeat values
    - [x] function for timebomb (countdown, after which delegate is fired with client id)
    - [x] function for updating heartbeat values
    - [x] function for resetting timebomb (when a heartbeat is updated)
  - [x] and an `Enum` (matching C#) of the client states
- [x] Python returns state of client; since it just made an entry, it will be its initialised value of `UNCALIBRATED`
- [x] `MLFGameClient` parses the result and updates its state according to the result


<video controls width="600">
    <source src="/docs/assets/videos/2022-03-31 11-52-00-1.webm" 
            type="video/webm">
</video>

### PM Update:

Worked with Lucas on a super annoying bug that when we passed the state through as a reference, it did not update as it is an Enum. We had to solve this by adding a wrapper class for the enum, so that we are pointing at the class, and modifying its value instead of assigning a new Enum. 

This means there is a stop-gap in the code right now, where when we serialise to JSON we serialise an Enum whose value is set by the current value of the one inside the wrapper class like so:

<a href="/docs/assets/images/heartbeat/hb_stop_gap.png">
<img src="/docs/assets/images/heartbeat/hb_stop_gap.png" width="600" alt="hb stop gap">
</a>

which is dumb and ugly. So I need to work out how to get Newtonsoft.JSON to serialise the class with the correct name as expected in the JSON at the other end.

