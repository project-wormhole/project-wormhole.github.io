---
title: "Introduction"
description: "Wormhole is an Open Source project aimed to give an Open Standard, allowing people on different apps to communicate with each other through a secure, fast, and reliable protocol."
lead: "Wormhole is an Open Source project aimed to give an Open Standard, allowing people on different apps to communicate with each other through a secure, fast, and reliable protocol."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "documentation"
weight: 100
toc: true
---

## How does it work?
### Intra and Inter Messaging
Only inter-app messages are go through wormhole server, intra messages will have no difference. We provide client SDKs which help you to integrate with the least effort.

### Messaging
* Restful APIs is provided to register user, create chats and complete with E2EE etc.
* Websocket provides efficient messaging interface that avoids the overheads of negotiation and reduce the latency. 
* WebRTC is introduced to secure real-time voice and video calls over the web.
### Security
* Double Ratchet algorithm is used to exchange encrypted messages based on a shared secret key 
* X3DH key agreement protocol is integrated and used as the Double Ratchet's initial root key
* Sesame algorithm for managing message encryption sessions in an asynchronous and multi-device setting
### Privacy
* Profile and Picture names and pictures let people know who is messaging them. Wormhole service has no knowledge of them since they are end-to-end encrypted
* Messages are protected by E2EE that wormhole and third party does not have a means to decrypt them. Only senders and intended recipients can read the messages.
* Message Requests give you the option to block, delete, and accept messages from somebody that trying to get in touch with you.
### Open source, open standard
Wormhole is based on Signal project and plan to provide
* Open Source
  * Client SDKs ( Apache License)
  * Client reference implementation ( Android, iOS)
  * Application Server
* Open Standard
  * Inter-service communication protocol
* Standalone service
  * Production grad inter-service messaging service