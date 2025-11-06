---
layout: post
title: "Personal Blog - November 2025"
date: 2025-11-03 08:00:00 -0700
categories: Personal Blog
---

# November 2025

---

### November 6, 2025

**Debugging Victory** 💻

Today was one of those days that reminded me why I love being a developer.

I got dropped into a new project built with Nuxt 3 and TypeScript, and almost immediately ran into a bug that completely broke the build process. It was one of those mysterious ones that points you to line 480 of a file, only for that line to be inside your CSS block. Classic.

After a good chunk of debugging and some teamwork with another dev and my front-end manager, we finally found the issue. The culprit was type assertions inside the template. Once we cleaned those up and refactored the logic, the app finally built correctly again. Pipelines passed, no more red builds, and everyone could move forward.

Even though I had help, I was the one who tracked down the root cause and verified the fix. That felt great. It reminded me how far I’ve come and how much I enjoy problem-solving.

There’s nothing quite like the moment when something that felt impossible suddenly clicks. 🔍✨

---

### November 5, 2025

**Back-End Progress** 🚀

Today I wrapped up the **basic CRUD operations** for the back-end of my online portfolio.

Along the way, I got a much deeper understanding of **SQL relationships** and what it really takes to implement a proper **login flow** on the back-end.

I implemented:

- **Hashing** for secure passwords
- **Refresh tokens** and **access tokens** for proper authentication
- The ability to **modify data safely** after login

And the best part? I successfully **deployed the API**, so it’s officially live!

Now comes the fun part: connecting all this data to my **front-end portfolio** and seeing it all come together. This is really exciting! 🎉

---

### November 4, 2025

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

---

### November 3, 2025

This is my first personal blog post! ☕

I’m sure this format will evolve as I go and as I learn more about Markdown and how Jekyll actually works under the hood. I’m excited about this setup because, if I understand it right, I’ll be able to edit posts directly from GitHub, even from my phone.

That means I can jot down quick thoughts or updates wherever I am without needing to open my code editor.

To test that theory, I’m going to add a new section below this one straight from GitHub instead of VSCode.

This is added from web browser instance of github.

This line is added from my phones GitHub app instance.

#### A Better Way to Find Data: Object Mapping

Yesterday at work, I had to dig into a method that was looping through some massive arrays just to find specific data. You know the kind, `.find()` or `.filter()`, buried in a few layers of logic, running every time the function gets called. It worked, but it wasn’t pretty, and it definitely wasn’t fast.

I ended up reworking the whole thing to use an **object map** instead. That simple change cut down the lookup time to basically nothing, and it got me thinking about how underrated this approach really is.

##### The Old Way

Originally, it looked something like this:

```js
const user = users.find((u) => u.id === targetId);
```

Totally fine for small data. But when you’ve got thousands (or worse, tens of thousands) of records, that linear search becomes a bottleneck. Every lookup is another full loop through the array.

##### The Fix

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

##### Why This Stuck With Me

It’s easy to forget that data structure choices matter, even in front-end work. We get so focused on frameworks and UI layers that we overlook these small optimizations hiding in plain sight. Object mapping isn’t some new trick, it’s basic, but it’s powerful. Especially when you’re dealing with repetitive lookups or joining data from multiple sources.

Since that change, I’ve started looking at other places in the codebase where mapping could make things cleaner or faster. There’s something satisfying about turning a clunky loop into a one-line lookup.

**Takeaway:**  
If you find yourself looping over big data sets just to grab a single item, stop and think, "could this be a map instead?"
