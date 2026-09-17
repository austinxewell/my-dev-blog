---
layout: post
title: "I Built an Admin Panel That Nobody Can See But Me"
date: 2026-09-17 14:30:00 -0600
categories:
  - personal-blog
tags:
  - nodejs
  - authentication
  - nuxt
  - backend
---

Every time I edited my portfolio site, it went the same way: open the code, find the hardcoded string, change it, commit, deploy. For a site I touch a few times a year, that was fine. But somewhere in the last few months my portfolio stopped being a static "here's my resume" page and started turning into something I actually wanted to operate like a real app. So this week I finally did something about the editing problem. 🔧

The short version: my portfolio now has a working admin portal. The longer version is more interesting.

## The Backend Had to Grow Up First

Before any of this was possible, the backend needed actual CRUD support. I added routes for creating, updating, and deleting content, which sounds simple written out like that, but it meant rethinking what my API was actually for. It went from "serve some static data" to "manage state for a real application."

The auth flow needed the same kind of upgrade. I added refresh tokens to the login flow, because the alternative options were both bad: short-lived tokens that log me out constantly, or long-lived tokens that sit around as a bigger target if anything ever goes wrong. Refresh tokens let the access token stay short-lived while a longer-lived refresh token quietly handles renewing it in the background. Nothing revolutionary, just the standard pattern, but it's the difference between "I hacked together a login" and "I built auth I'd trust."

## Then I Actually Used It

Routes and tokens don't mean much sitting unused, so I wired all of it into the live frontend. Now I can log into a portal on my own site, and the whole authenticated flow just works: login, refreshed sessions, hitting my own API instead of editing files by hand.

That's the admin portal today. Auth that holds up, and an API that does something with it.

## What's Actually Next

Here's the part I'm most focused on right now. The portal has four sections scaffolded and doing absolutely nothing yet:

```vue
<BaseModal ref="skills">
    <h1>Modify Skills</h1>
</BaseModal>

<BaseModal ref="collaborations">
    <h1>Modify Collaborations</h1>
</BaseModal>

<BaseModal ref="services">
    <h1>Modify Services</h1>
</BaseModal>

<BaseModal ref="users">
    <h1>Modify Users</h1>
</BaseModal>
```

Modify Skills and Modify Services are first up. Those are the two sections of the site that change the most, and they're the most annoying to update by hand right now, so they get the real forms and validation first. Modify Collaborations and Modify Users come after, once the pattern is proven out on the first two.

Nobody will ever see this part of the site. That's kind of the whole point of writing about it. The public side of my portfolio is the polish. This is the part where I actually get to build the thing the way I want, without an audience watching. 👀
