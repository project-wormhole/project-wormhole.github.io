---
title: "Client-Server API"
description: "Wormhole Client-Server API"
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "documentation"
weight: 110
toc: true
---
## Overview
`Wormhole` server APIs are forked from [Synapse Server](https://github.com/matrix-org/synapse). We keep most of the APIs and describe the changes below.


Matrix synapse as it describes, is an ambitious new ecosystem for open federated Instant Messaging. However, we believe the need for server-side integration or modification is such a pain. We prefer to provide centralized Chat Server to reduce overhead. For example, if an app already has its own IM service, there’s nothing related to Wormhole. However, if your users want to communicate to other apps, messages will be delivered by Wormhole server via native SDK. It is worth emphasizing that all of the messages are encrypted in the native SDK, only intended recipients could decrypt the message content.

{{< img src="images/inter-intra-messaging.png" alt="`Wormhole` inter and intra service communication" caption="<em>`Wormhole` inter and intra service communication</em>" class="border-0" >}}


## Login
Currently, only Google Oauth2 is supported for login.

###  Get Google Oauth2 Redirect URL

```
GET /_matrix/client/unstable/org.matrix.msc2858/login/sso/redirect/oidc-google?redirectUrl={scheme}%3A%2F%2Fconnect&appid={appid}&access_token={access_token}
```

The client requests to login and instruct the user's browser to navigate to the responded URL.

1. `scheme` your app should monitor `scheme`://connect after the user is authenticated
2. `appid` appid provided by Wormhole
3. `access_token` access token provided by Wormhole

**Returns**:

1. `200` request was processed successfully.

