---
layout: post
title: "Surfacing Unsaved Changes in Deeply Nested UI State"
date: 2025-12-18 08:00:00 -0700
categories: [personal-blog, public]
tags: [state-management, problem-solving]
---

Recently I worked through a UI problem that looked simple on the surface but got complex fast. The goal was straightforward. Let users know when they have **unsaved changes**. The challenge was how deep those changes could live in the data.

The UI was built around nested relationships. Think something like:

- A top level parent
- Multiple children inside it
- And even more nested layers beyond that

Changes could happen anywhere in that hierarchy. A small edit at the lowest level still needed to bubble up so the user clearly understood that something was not saved.

## Why this was harder than it sounds

In theory, you flip a boolean and call it a day. In practice, that breaks down quickly when:

- State lives at multiple levels
- Updates can happen independently
- Parent components need awareness without owning all the logic

If a change happened deep in the tree, the parent UI still needed to reflect it. Not handling that correctly leads to confusing UX and lost trust from users.

## What I focused on

I approached this with a few priorities in mind:

- **Clear ownership of state**  
  Each layer knew whether it had changes, but it did not try to control everything.

- **Upward communication**  
  Nested components could notify their parent when something changed, without tightly coupling the logic.

- **Reusable patterns**  
  This was not a one off solution. The same approach could be reused for other complex forms later.

## The result

The end result was a draft form system that:

- Detects changes at any level
- Communicates those changes upward
- Clearly signals to the user when something is unsaved

It was a good reminder that UI problems are often data problems in disguise. Solving them cleanly means thinking about **flow**, not just visuals.

This kind of work does not always look flashy, but it directly improves usability and trust. Those are the problems I enjoy solving the most.
