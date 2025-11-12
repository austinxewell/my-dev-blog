---
layout: post
title: "Personal Blog - November 2025"
date: 2025-11-03 08:00:00 -0700
categories: Personal Blog
---

# November 2025

---

### November 11, 2025

**Tailwind Love... Until Tables Come Around** 🎨  

I’ll say it... I love using **Tailwind CSS**. The speed, flexibility, and control it gives when building UIs is unmatched. Being able to rapidly style and adjust components without leaving my markup has completely changed how I approach front-end development.  

That said, there is one area where Tailwind really starts to show its limits: **tables**.  

When it comes to consistent table design like spacing, alignment, alternating row colors, hover states, or handling responsive layouts, utility classes can start to feel clunky. It is one of those places where using Tailwind alone ends up being more painful than productive.  

After building multiple table-heavy features across different applications at work, I have realized that **SCSS still wins** for structured table styling. Nesting selectors, handling breakpoints with mixins, and keeping the table formatting logic contained just makes more sense.  

So while I will keep using Tailwind for most of my UI, tables are one place where I am perfectly fine going back to SCSS. Sometimes the older and more reliable tools still fit the job better. 🧠💡

---

### November 10, 2025

**Building for the Future: The Importance of Componentizing Features** ⚙️  

One of the biggest lessons I’ve learned in front-end development is the importance of **componentizing features**. When you’re building an app, it’s easy to start stacking logic, UI, and functionality all in one place. It works at first, but as soon as you scale or revisit that code, it becomes a tangled mess.  

Breaking your features into **reusable components** is how you future-proof your project. Each component should do one thing well. The more isolated and predictable your components are, the easier it becomes to extend, refactor, or debug your application.  

Scalability isn’t just about performance. It’s also about **maintainability**. A well-structured component system lets your project grow naturally without collapsing under its own weight.  

Today I spent time rethinking how some of my front-end features fit together, and it reminded me that clean architecture is what separates a fast MVP from a product that can actually last. 🧩✨

---

### November 8, 2025

**Development Fatigue** 😩

It's been a super busy week at work, combined with long nights working on my online portfolio. Today I finalized the **dummy flow** for creating a project and I am really happy with how it turned out.

I try to get some type of development in daily, but between long work days and long personal nights, I think I am going to take a well-deserved (mostly) day off.

That said, I _did_ wake up early to finalize the **Create Project** feature in my **Admin Portal** for my personal portfolio. 💤☕🖥️

---

### November 7, 2025

Today I dove into connecting the backend I built for my online portfolio with a front-end interface. It's always exciting to see personal projects evolve, especially when professional growth starts showing in the details.

Here's what I accomplished today:

- ✅ **Login page** – fully functional and styled
- ✅ **Admin portal** – initial structure set up
- ✅ **Form modal** – ready to hold multi-step forms

One feature I'm particularly proud of is the **form step tracker**. It's something I used to overlook in simple multi-step forms, but seeing it implemented now adds a huge boost to usability. It's a small detail, but it really enhances the user experience.

It's moments like this where you notice how much your development skills have grown over time. Where your professional knowledge finally is merging into personal projects. 🛠️✨

Can't wait to keep building and polishing this portfolio interface.

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
