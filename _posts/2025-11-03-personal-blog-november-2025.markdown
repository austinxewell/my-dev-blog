---
layout: post
title: "Personal Blog - November 2025"
date: 2025-11-03 08:00:00 -0700
categories: Personal Blog
---

# November 2025

---

### November 23, 2025

**Why Taking Breaks Actually Makes You a Better Developer** 🧘‍♂️  

I have learned that pushing myself nonstop does not make me sharper. It does not make me faster. It definitely does not make me write better code. What it does is burn me out and make simple tasks feel way harder than they should.  

Taking breaks has become a real part of my routine, and I can feel the difference. When I step away from the screen, even for a short time, my mind resets. Problems that felt stuck suddenly make sense. Bugs that I kept chasing start to reveal themselves. It is like giving my brain room to breathe.  

In my experience, breaks are not a sign of slacking. They are a sign of control. It means I understand my limits. It means I want to produce work that is clear, calm, and thoughtful instead of code that was forced out during a tired rush.  

The funniest part is that taking breaks actually makes me faster. I come back with more focus, more energy, and a better sense of direction. My decisions are cleaner. My logic is tighter. My confidence is higher.  

So I am learning to respect the reset. A short pause can save hours of frustration. A clear head will always outperform a tired one. And sometimes the smartest move you can make as a developer is to step away for a moment. ☕✨

---

### November 22, 2025

**Data Leaks and the Responsibility We Carry as Developers** 🔒  

Data leaks have always been a real threat, but the rise of AI in the development world has pushed that risk into a whole new category. AI tools are becoming a normal part of everyday work. They speed up planning, writing, debugging, and refactoring. They make development smoother and more efficient. I rely on them, and honestly, I enjoy using them.  

But here is the reality. Large language models do not know the difference between public code and sensitive logic. They do not know which parts of a system should never be exposed. If we feed the wrong information into an AI tool or copy something without reviewing it carefully, we can leak internal data without even noticing.  

I feel that this puts real responsibility on us as developers. We have to be aware of what we share, what we type into prompts, and what we allow AI to generate. We cannot rely on the model to understand the boundaries. It is on us to protect the systems we build and the information they handle.  

AI is becoming more important every day in this industry. It is a powerful tool that makes us faster and more effective. At the same time, it demands more awareness and more discipline. The convenience is incredible, but it does not erase the need for caution.  

The more we integrate AI into our workflow, the more careful we have to be. Sensitive data deserves respect, and safeguarding it starts with the decisions we make as developers. 🔐✨

---

### November 20, 2025

**Why Code Reviews Actually Matter** 🔍  

The longer I work in development, the more I realize how important real code reviews are. It is not just about catching typos or finding the obvious bugs. A good code review forces you to slow down and look at your work from another angle. It exposes blind spots you did not even know you had.  

In my experience, code reviews make the entire team better. When someone else looks at your logic, your structure, or your approach, you learn new patterns and cleaner ways to solve problems. It is easy to fall into habits, and reviews break that cycle. They push you to write code that is readable, maintainable, and clear.  

Another thing I appreciate is the accountability it creates. When you know someone else will see your work, you naturally put more care into it. You avoid shortcuts. You think through edge cases. You take pride in the final result instead of just shipping something that works for now.  

Code reviews also prevent technical debt from sneaking into the project. A second set of eyes can catch unnecessary complexity, repeated logic, or structural issues that might slow you down later. It keeps the codebase healthy instead of letting it slowly rot.  

For me, code reviews are not a formality. They are one of the strongest tools a team has to stay sharp, stay aligned, and grow together. 👌

---

### November 19, 2025

**Why Pseudocoding Matters in Complex Flows** 🧠  

The more I grow as a developer, the more I appreciate the value of pseudocoding. When a feature has a simple flow, it is easy to jump straight into the implementation. But once the logic gets deeper or the steps start branching, writing everything directly in code becomes a recipe for confusion.  

Pseudocoding fixes that. It gives me a chance to outline the entire flow before I commit to a single line of real code. I can see the structure clearly. I can adjust the logic without breaking anything. I can spot gaps in the flow long before they turn into bugs.  

In my experience, complex features become manageable when the plan is written out in plain language. It takes the pressure off. Instead of juggling a dozen scenarios in my head, I let the pseudocode guide me. It keeps everything grounded and predictable.  

Pseudocoding also saves time. It reduces rewrites. It cuts down on those moments where I realize halfway through that I missed an important branch or edge case. Once the flow is mapped, the actual coding becomes smoother and faster.  

For me, pseudocode is not optional when the logic gets heavy. It is the blueprint that keeps the entire thing from spiraling into a messy pile of fixes and guesses. A clear flow on paper turns a complex feature into something I can tackle with confidence. ✨

---

### November 14, 2025

**The Value of a Real Workflow Standard** 📊  

As I keep growing in my development career, one thing is becoming very clear to me. A fast growing environment with multiple teams and multiple projects needs a real workflow standard. Without it, everything feels scattered. Everyone has their own style, their own process, their own interpretation of what “done” means.  

In my experience, that lack of uniformity hits hardest when you try to track development statistics or measure progress. I have seen how painful it gets when you attempt to gather meaningful data from teams that all operate differently. The numbers stop being useful because they are not measuring the same thing. It becomes more frustration than insight.  

I feel that a strong workflow standard is not about locking people into rigid rules. It is about giving everyone a shared baseline. It creates clarity. It reduces confusion. It makes it possible for teams to work in sync instead of drifting in separate directions.  

When everyone follows a predictable workflow, you can actually trust the data you collect. You can find patterns, improve weak spots, and build healthier processes. You get real visibility instead of noise.  

The more I work across different setups, the more obvious it becomes. A unified workflow is not just helpful. It is essential for any environment that wants to grow without falling apart. 🧭✨

---

### November 13, 2025

#### User Avatar Components

If you’ve ever logged into a site and saw your little circle with your face (or initials) staring back at you, you’ve met a **user avatar**. Seems simple, right? But building one that’s flexible, reliable, and visually polished is deceptively tricky.  

Here’s my personal reflection on crafting a solid avatar component in a front-end project.

#### 1. Size Matters

Not all avatars are created equal. Sometimes you need a tiny circle for a chat sidebar, other times a big one for a profile page. A good avatar component lets you **set the size with a simple prop**. For example:

- `sm` → sidebar chats  
- `md` → navigation bars  
- `lg` → profile pages  

Keeping these sizes consistent avoids tiny inconsistencies that subtly make an app feel sloppy.  

####  2. Loading Gracefully

Ever clicked on a profile and saw a flicker of blank gray before the image loaded? That’s a missed opportunity.  

A neat trick: **use a pulsing placeholder** while the image loads. It’s a small touch, but it makes the interface feel alive rather than static. Kind of like saying, “Hey, I see you’re coming, hold on!”  

#### 3. Fallback Initials

Not everyone uploads a profile picture. That’s why **initials are your friend**. A simple rule:

- Take the first letter of the first name  
- Take the first letter of the last name  
- Display them in a clean circle  

💡 Tip: Filter out extra spaces and weird edge cases so `"  John   Doe  "` still becomes `JD`. No surprises, just clean fallback.  

#### 4. A Bit of Personality

A user avatar isn’t just functional, it can carry **visual charm**:

- Rounded circles feel friendly  
- Pulsing loaders add motion  
- Consistent text sizes make initials readable  

Even a tiny component like this communicates care for details in your app.  

#### 5. Keep it Flexible

The real secret to a good component? **Flexibility without over-complication**. Props for:

- `src` → profile picture  
- `name` → fallback initials  
- `size` → easy resizing  

…plus some smart defaults, and you’ve got a component that works everywhere without constant tweaking.  

#### TL;DR

A user avatar is tiny, but it’s mighty. Handle loading elegantly, fallback smartly, size consistently, and sprinkle a little personality on top. It’s a small piece of UI, but it can make your app feel more thoughtful, polished, and alive.  

Next time you see a little circle with someone’s face (or letters) in an app, give it a wink. Someone, somewhere, wrote that component with care.  

---

### November 12, 2025

**The Reality of Agile Development** 🔁  

Agile is one of those things that every developer ends up having an opinion about. After working within Agile environments for a while, I can see why it is such a common approach. When done right, it keeps teams aligned, communication flowing, and progress visible. When done wrong, it can feel like endless standups and planning sessions that slow everything down.  

Here is how I see the balance:  

#### 👍 The Pros  
- **Flexibility:** Agile makes it easier to adapt to change. Priorities shift, requirements evolve, and the process allows for it.  
- **Visibility:** Everyone knows what is being worked on and what is next. It is transparent and helps keep momentum.  
- **Collaboration:** Frequent check-ins force communication and help teams catch issues early instead of weeks later.  
- **Incremental Progress:** Shipping in small iterations keeps projects moving forward without waiting for one massive release.  

#### 👎 The Cons  
- **Meeting Overload:** Too many ceremonies can eat into actual development time. Not every task needs a retrospective.  
- **Scope Creep:** Constant change can lead to never-ending "just one more feature" cycles.  
- **Surface-Level Productivity:** It is easy to look busy in Agile without making meaningful progress if priorities are unclear.  
- **Burnout Risk:** The constant push for deliverables in short sprints can wear teams down fast.  

In the right hands, Agile is a great framework for building software efficiently. In the wrong hands, it becomes a checklist of rituals that lose all purpose.  

For me, the key is finding a balance. Keep the principles, drop the fluff, and make sure the process serves the product, not the other way around. ⚙️

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
