---
layout: post
title:  "Server World"
date:   2022-04-26 09:00:00 +0100
categories: evolver
---

# Server World

### Yesterday

- Opened up the Unity timeline repository and attempted to get it synced with vvvv
  - Made a build and distributed to all evolver PCs
  - Managed to get it hooked up to vvvv, but it doesn't seem to respond to updates coming from the game server
  - Spent the morning getting to grips with the way in which the timeline tool has been created withing Unity, so that we can add our own DMX control output for environmental control

- Spent a big chunk of time with Lucas working out how we could optimise the game server so that it can deal with timebombs
  - ultimately, it seemed to make sense to take the responsibility for timebombing awy from each client and allow the server to manage this
  - Lucas spent time working out the nuances of Processes vs Threads in Python
  - had a look at using Background Tasks (supported by FastAPI) to run timebombing instead

- Spent a little time looking at the remaining server functionality required to integrate with Nils' controller
  - made a method and endpoint that will return the current state of a specific client


### Today

- [x] State Controls
  - [x] Send all to Lobby > POST > /State/LobbyAllClients
  - [x] Send Client to Lobby  > POST > /State>LobbyClient
  - [x] Start all clients > POST > /State/StartAllClients 
  - [x] Start one client > POST > /State/StartClient 
  - [x] Emergency all > POST > /State/EmergencyAllClients 
  - [x] Emergency client > POST > /State/EmergencyClient 
  - [x] Force all clients states > POST > /State/ForceStateAllClients 
  - [x] Force one clients state > POST > /State/ForceStateClient 