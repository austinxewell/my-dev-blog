---
layout: post
title: "A Better Way to Find Data: Object Mapping"
date: 2025-11-03 09:00:00 -0700
categories: [personal-blog, public]
tags: [frontend, javascript, performance, object-mapping]
---

Yesterday at work, I had to dig into a method that was looping through some massive arrays just to find specific data. You know the kind, `.find()` or `.filter()`, buried in a few layers of logic, running every time the function gets called. It worked, but it wasn’t pretty, and it definitely wasn’t fast.

I ended up reworking the whole thing to use an **object map** instead. That simple change cut down the lookup time to basically nothing, and it got me thinking about how underrated this approach really is.

## The Old Way

Originally, it looked something like this:

```js
const user = users.find((u) => u.id === targetId);
```

Totally fine for small data. But when you’ve got thousands (or worse, tens of thousands) of records, that linear search becomes a bottleneck. Every lookup is another full loop through the array.

## The Fix

So I built a quick map:

```js
const userMap = {};
users.forEach((u) => {
  userMap[u.id] = u;
});

// Now lookups are instant
const user = userMap[targetId];
```

Suddenly, everything felt snappy. What used to be an expensive search turned into a direct property access. Same logic, same data, just a different structure, but the difference in speed and simplicity was huge.

## Why This Stuck With Me

It’s easy to forget that data structure choices matter, even in front-end work. We get so focused on frameworks and UI layers that we overlook these small optimizations hiding in plain sight. Object mapping isn’t some new trick, it’s basic, but it’s powerful. Especially when you’re dealing with repetitive lookups or joining data from multiple sources.

Since that change, I’ve started looking at other places in the codebase where mapping could make things cleaner or faster. There’s something satisfying about turning a clunky loop into a one-line lookup.

### Takeaway:

If you find yourself looping over big data sets just to grab a single item, stop and think, "could this be a map instead?"
