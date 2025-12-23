---
layout: post
title: "Personal Blog - December 2025"
date: 2025-11-03 08:00:00 -0700
categories: Personal Blog
---

# December 2025

---

### December 22, 2025

**Learning When to Simplify Instead of Add** 🧠✨

Lately I have been catching myself doing something that used to feel productive but really was not. Adding more abstraction, more helpers, more layers, just because I could. It looked clean on the surface, but it made the system harder to reason about.

As I have grown professionally, I am realizing that good development is not about how clever the solution is. It is about how **understandable** it is six months later. Especially in front end work, where logic, state, and UI are constantly changing.

I have started asking myself a few questions before adding anything new:
- Does this actually reduce complexity?
- Will another developer understand this without context?
- Is this abstraction solving a real problem or just hiding one?

In my experience, the best solutions lately have been the boring ones. Clear computed properties instead of chained watchers. Simple components instead of over engineered systems. Explicit logic instead of magical helpers.

This mindset shift has made my reviews stronger, my code easier to maintain, and my day to day work less frustrating. It is not about writing less code. It is about writing code that respects the next person who has to touch it.

Sometimes the most professional move is choosing clarity over cleverness. 💡

---

### December 20, 2025

**My Portfolio Is Officially Full Stack** 🚀

I finally pushed a set of changes that make my online portfolio feel like a *real* application instead of just a static showcase. The front end is now fully connected to my deployed backend, and everything is wired together the way I would expect in a professional environment.

This was a big milestone for me. Not because it was difficult, but because it represents a shift in how I am building personal projects.

#### What Changed

- The portfolio is now backed by a live, deployed backend  
- Front end data is no longer mocked or hardcoded  
- API responses are driving the UI end to end  
- I started building out an **admin portal** to manage content through a proper UI  

Being able to update the database through a front end interface instead of manual changes feels like a huge step forward.

#### Admin Portal Progress

The admin portal is still early, but the foundation is there. Forms, layouts, and structure are starting to take shape, and I can already see how this will scale as I add more features.

This part of the project really highlights the overlap between my professional work and my personal growth. Clean UI, predictable flows, and maintainable logic matter just as much here as they do anywhere else.

#### CI/CD Is Live

One of the best changes I made was fully automating the project with **CI/CD**.

- Builds and deployments are automatic  
- Changes are validated before going live  
- I spend less time babysitting deployments  
- The whole workflow feels far more professional  

This alone makes the project easier to maintain and more enjoyable to work on.

#### Why This Matters

Turning this into a full stack, automated project makes it more than just a portfolio. It is now a living system that reflects how I actually build software. Clean architecture, real data, real workflows, and real responsibility.

There is still plenty to build, but this was a big checkpoint. Everything from here on out feels like forward momentum.

---

### December 19, 2025

#### Staying DRY With Computed Properties in Vue and Nuxt 🧼🧠

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

#### DRY code is easier to maintain

In my experience, the biggest benefit is maintainability. When logic lives in one computed property instead of being scattered across the component, updates are faster and safer. You fix something once and you are done.

It also makes code reviews cleaner. When logic is well named and isolated, it is easier to understand intent. That leads to better discussions and fewer bugs slipping through.

#### Cleaner components, calmer development

Computed properties force you to think about **what the UI needs**, not how many times you can repeat the same condition. That mindset keeps components smaller, clearer, and easier to reason about.

Lately I have been reminding myself that clean code is not about being clever. It is about being kind to the next developer who has to touch it. Most of the time, that next developer is future me. 😄✨

---

### December 18, 2025

##### Surfacing Unsaved Changes in Deeply Nested UI State 🧩

Recently I worked through a UI problem that looked simple on the surface but got complex fast. The goal was straightforward. Let users know when they have **unsaved changes**. The challenge was how deep those changes could live in the data.

The UI was built around nested relationships. Think something like:
- A top level parent
- Multiple children inside it
- And even more nested layers beyond that

Changes could happen anywhere in that hierarchy. A small edit at the lowest level still needed to bubble up so the user clearly understood that something was not saved.

#### Why this was harder than it sounds

In theory, you flip a boolean and call it a day. In practice, that breaks down quickly when:
- State lives at multiple levels
- Updates can happen independently
- Parent components need awareness without owning all the logic

If a change happened deep in the tree, the parent UI still needed to reflect it. Not handling that correctly leads to confusing UX and lost trust from users.

#### What I focused on

I approached this with a few priorities in mind:

- **Clear ownership of state**  
  Each layer knew whether it had changes, but it did not try to control everything.

- **Upward communication**  
  Nested components could notify their parent when something changed, without tightly coupling the logic.

- **Reusable patterns**  
  This was not a one off solution. The same approach could be reused for other complex forms later.

#### The result

The end result was a draft form system that:
- Detects changes at any level
- Communicates those changes upward
- Clearly signals to the user when something is unsaved

It was a good reminder that UI problems are often data problems in disguise. Solving them cleanly means thinking about **flow**, not just visuals.

This kind of work does not always look flashy, but it directly improves usability and trust. Those are the problems I enjoy solving the most.

---

### December 17, 2025

**Why Reusable UI Components Actually Matter (Yes, Even Modals)** 🧩✨

Lately I’ve been spending a lot of time working on UI components, especially things like **modals**, and it keeps reinforcing the same lesson over and over. Reusable and scalable UI components are not just a nice-to-have. They are a requirement if you want an application to grow without becoming a nightmare to maintain.

Modals are a great example. On the surface, they seem simple. A container, some content, maybe a close button. But once an app grows, you quickly realize how many different places need them. Forms, confirmations, warnings, previews, settings. If each one is built slightly differently, things fall apart fast.

What I’ve learned is that investing time early into **one solid modal component** pays off immediately. A reusable modal gives you:
- **Consistency** across the entire application  
- **Faster development** when new features need dialogs  
- **Cleaner code** with less duplication  
- **Easier updates** when designs or behavior change  

Scalability is the real win here. When your modal supports slots, props, and predictable behavior, it adapts to new use cases without needing to be rewritten. The same idea applies to buttons, inputs, alerts, and layout components. Build them once, build them right, and let them carry the weight of the app.

In my experience, reusable UI components change how you think about development. You stop hacking things together and start designing systems. The codebase feels calmer. Features feel easier to add. And future you spends a lot less time fixing avoidable problems.

Small components. Big impact. 🧠💡

---

### December 14, 2025

**Back At It (Ironically Enough)** 😅

It has been a few weeks since I last posted, which is funny considering one of my previous entries was literally titled **Development Fatigue**. I took that break, and then life doubled down.

Over the past month, personal and family health issues pulled my attention where it needed to be. Development took a back seat, not because of burnout, but because priorities shifted. That kind of pause is never planned, but sometimes it is necessary.

The good news is I am back, and I have things worth writing about again.

Even while I was quieter here, I was still growing professionally. I have a handful of updates that came directly out of real-world development work, problem solving, and lessons learned the hard way. Those are the posts I enjoy writing the most anyway.

Here is what is coming next:

- **Professional growth lessons** from recent work
- **Process and workflow improvements** I have been part of
- **Development decisions** that saved time and reduced friction
- More consistency and fewer long gaps between posts

This is me getting back into the habit. Writing helps me reflect, and reflection makes me a better developer. I am planning to post more routinely again and keep this blog active.

Sometimes stepping away gives you better perspective. Now it is time to put that perspective to use. 🔁💻
