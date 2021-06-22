---
title: "Platform API"
description: "Introduction of platform APIs"
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: ["wormhole_architecture.png"]
menu:
  docs:
    parent: "documentation"
weight: 110
toc: true
---

Almost every APIs are well handled by our native SDKs, there're still APIs that allow your application server to work with accounts and data related to your Wormhole application. The API lets you create accounts, set users' token programmatically so that you can boost your login conversion rate.

## Base URL
Every application has its unique base url. For now, to join Wormhole and get an app ID, app token, and a base URL, please email to "p.wormhole.im@gmail.com". The format of the base URL used for the Platform API is
```
https://api-{app id}.wormholeim.org
```

## Headers
All of the platform APIs should include the following headers
```
Content-Type: application/json; charset=utf8
X-App-ID: {App ID}
X-App-Token: {App Token}
```

### Bulk insert accounts

```
POST /v1/accounts/
Content-Type: application/json; charset=utf8
X-App-ID: {App ID}
X-App-Token: {App Token}

{
  "user_list": [
    {
      "user_id": "{user_id}",
      "display_name": "{display_name}",
      "avatar": "{avatar_url}",
    }
  ]
}
```

The account API allows you to create multiple accounts at the same time. Note that a single call can comprise as many as `100` accounts.

1. `user_id` is the ID of the user in your app. The user_id MUST be unique within your app.
2. `display_name` should be unique within your app also to prevents users from misidentifying 
3. `avatar_url` url of avatar for the user


**Returns**:

1. `200` request was processed successfully.
2. `400` missing parameter.
3. `413` rate limit exceeded. Too many requests.

```
{
  "success": [
    {
      "user_id": "{user_id}",
      "wormhole_id": "{wormhole_id}",
      "access_token": "{access_token}"
    }
  ]
}
```
1. `user_id` is the ID of the user in your app.
2. `wormhole_id` is the user id in Wormhole
3. `access_token` is used to login Wormhole. You should pass access_token to native SDK.

### Disable User

```
PUT /v1/accounts/:wormhole_id
Authorization: Basic {basic_auth}
X-PKG-NAME: {package_name}
X-PKG-TOKEN: {package_token}

{
  "status" : "{status}"
}
```

Disable the user account by Wormhole ID. Note that you can still enable the account in the future.

1. `status` changes between `enable` and `disable`

**Returns**:

1. `200` account status successfully changed.
2. `404` account not found.

