---
layout: post
title: "Optimizing Fetch Requests"
date: 2025-11-04 08:00:00 -0700
categories: [personal-blog, public]
tags: [frontend, api, javascript, optimization]
---

Today at work, my QA developer flagged something while implementing an access-level feature on a deployed project. While the main goal was access control, he noticed what he thought was a bug: an unnecessary API call that was slowing down the dashboard load times ⚡

After digging in, I found the culprit. The API call was necessary, but it was wrapped in an `async/await` method where it didn’t need to be. This request could happen behind the scenes without making the user wait. I refactored the required API calls into a `Promise.all([])` setup and removed the request that wasn’t relevant to the user experience. The result? Load times improved by almost **85%** 🚀

Here’s an example of the refactor:

```javascript
await Promise.all([
  fetchUserData(),
  fetchDashboardStats(),
  // Removed unnecessary API call here
]);
```

This got me thinking about **intent** in development. There’s a huge difference between writing code that works and writing code with purpose. The feature wasn’t broken, it did exactly what it was supposed to, but optimizing with intent made a measurable difference. Every line of code contributed to a smoother experience, letting the user get what they need faster **without losing functionality** ✨
