---
layout: post
title: "Staying DRY With Computed Properties in Vue and Nuxt"
date: 2025-12-19 08:00:00 -0700
categories: [personal-blog, public]
tags: [frontend, vue, nuxt]
---

Lately I have been paying a lot more attention to **DRY code**, both in my own development updates and during code reviews. It is one of those principles that sounds obvious, but it is surprisingly easy to drift away from when features start piling up.

One area where this shows up fast is in **Vue and Nuxt components**. It is tempting to repeat logic in templates, watchers, or methods just to get something working. The problem is that repetition always comes back to bite you.

This is where **computed properties** really shine.

#### Why computed properties matter

Computed properties help keep logic:

- **Centralized**
- **Readable**
- **Reusable**
- **Easy to change later**

Instead of calculating the same value in multiple places, you define it once and let Vue handle the rest. When the data changes, the computed value updates automatically. No extra glue code. No copy and paste logic.

## DRY code is easier to maintain

In my experience, the biggest benefit is maintainability. When logic lives in one computed property instead of being scattered across the component, updates are faster and safer. You fix something once and you are done.

It also makes code reviews cleaner. When logic is well named and isolated, it is easier to understand intent. That leads to better discussions and fewer bugs slipping through.

## Cleaner components, calmer development

Computed properties force you to think about **what the UI needs**, not how many times you can repeat the same condition. That mindset keeps components smaller, clearer, and easier to reason about.

Lately I have been reminding myself that clean code is not about being clever. It is about being kind to the next developer who has to touch it. Most of the time, that next developer is future me. 😄✨
