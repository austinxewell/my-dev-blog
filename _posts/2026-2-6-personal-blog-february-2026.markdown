---
layout: post
title: "Personal Blog - February 2026"
date: 2026-2-06 08:00:00 -0700
categories: Personal Blog
---

# February 2026

---

### February 11, 2026

**When Your Database Looks Dead but Isn’t: Lessons from Railway**

As a developer, few things are as alarming as seeing your backend throw **ETIMEDOUT** errors on every request. Today, I ran into that exact situation with my Node.js portfolio running on Railway.

At first glance, it looked like MySQL had completely stopped:

**Database deployment:** stopped

My heart sank. Had I broken something? Had I lost all my data?

**Spoiler:** no. The database was fine. The problem was Railway. Ironically, I'm thankful it was just a Railway outtage.

**What actually happened**

Railway crashed in certain areas and this created my connection to MySQL and my back end deployment to crash. Whats really tricky is Railway shows a deployment status that isn’t always trustworthy. The logs told me:

```yaml
2026-02-11 22:59:51.262288Z 0 [System] /usr/sbin/mysqld: ready for connections. Version: '9.4.0' port: 3306
```

That line alone means MySQL started successfully and is accepting connections. Everything else, the UI badge, the scary “stopped” label, was misleading.

**Why this happens:**

1. **Deployment status does not equal process running.** Railway interprets the container lifecycle differently from MySQL.
2. **Restarting vs. redeploying.** If you restart a DB, Railway may still mark the last deploy as stopped even though the container is alive.
3. **Dashboard lag.** Railway sometimes takes minutes to reflect the real state.

**Lessons learned**

1. **Logs are your source of truth.** Ignore the stopped badge. If the logs say ready for connections, your DB is up.
2. **Handle DB outages in your backend.** Even after MySQL restarted, my Node.js backend was still timing out because it held dead connections. **Fix:** poll the DB before starting the server until a simple query succeeds.
3. **Auto-restart is non-negotiable.** Enable Railway’s “Restart on failure” for database services. Don’t rely on the platform to magically revive your container.
4. **Internal hostnames matter.** Your backend should always use Railway’s internal DB host, not localhost or public IPs.
5. **Plan for ephemeral infrastructure.** Even on a paid plan, Railway can send SIGTERM, rotate containers, or recycle hosts. Build for failure.

**Thankfully It Wasn't A Bad Day**

Im so thankful that this was a simple fix despite it having my head spinning. I was super afraid that I would have had to restart my MySQL deployment and restructure my database with a back up. Todays been really busy at work so it was not something I would have been able to get to right away.

### TL;DR

- ETIMEDOUT errors don’t always mean your DB is dead.
- Railway UI is misleading; logs and network tests are the truth.
- Add DB readiness checks in your backend.
- Enable auto-restart for your DB service.
- Keep connection pools small and use retries.
- Appreciate the little victories, even if they don't start as victories.

With these safeguards, even Railway’s quirks stop being scary. ✅

---

### February 10, 2026

**Inside a Smarter Chart Component 📊**

The past couple week I spent time working on a chart component that we knew from the beginning would be a meaningful and carefully planned update. While it might look simple at first glance, this work touched several areas of the application and required thinking beyond just visual output.

One of the main goals was to make the chart **adapt its layout based on the number of selected data points**. When only a few data points are selected, the chart stays clean and easy to read. As more data is added, the layout automatically adjusts so spacing, labels, and visuals remain usable instead of becoming cluttered.

Another important update was **dynamic scaling**. The chart now lets users toggle between using **min and max values provided by the backend** or automatically adjusting based on the highest and lowest values in the currently selected dataset. This allows the chart to zoom in on trends while keeping the full dataset intact.

We also added support for **custom date ranges**. Users are no longer locked into preset options and can choose exactly what time range they want to explore. To do this efficiently, we updated a previously existing chart component rather than creating something entirely new.

To avoid breaking existing features, we introduced a boolean flag called `allowsCustomDate`. This allows custom date selection only where it is explicitly supported, while keeping the current `appChart` behavior untouched elsewhere. This gives us a safe, controlled way to roll the feature out gradually across the app.

As expected, the work did not stop at the main chart. Since these charts are also used in reports, we had to update the **print formats** to match the new scaling and date logic. Keeping on screen views and printed output in sync took extra care, but it was essential for consistency.

All of this work was done in a **Nuxt 2 project using ApexCharts**, which added its own set of constraints and considerations. By the end of the week, the component felt more flexible, more predictable, and much more future ready.

This kind of work is exactly why I enjoy front end development. Thoughtful planning, incremental improvements, and solving real problems without breaking existing functionality. On to the next challenge 🚀

---

### February 8, 2026

**Laying Out a Game Plan for Upcoming Posts 📝**

Since I have so much going on right now, I want to write down a clear game plan for the posts I want to share next. This is as much for me as it is for anyone reading. It helps me slow down, organize my thoughts, and actually finish posts instead of letting ideas pile up.

Here’s what I want to talk about over the next stretch.

- Walkthroughs of **real features I’m building**, including what the goal was, what broke, and how I fixed it
- Stories behind **dynamic chart components**, from data shaping to UI decisions
- How I approach **print-friendly screens**, because making things look good on paper is way harder than it sounds
- Breaking down **project estimates**, how I think about scope, tradeoffs, and unknowns
- A full write-up on a **major feature rewrite** that changed how an app fundamentally works
- What it’s like jumping into **new projects and unfamiliar codebases** without panic
- Thoughts from **code reviews**, including feedback that helped and mistakes I won’t repeat

There are also a few focused topics I want to dedicate posts to because they keep coming up.

- Why **ATS-friendly resumes** actually matter for developers, even when it feels dumb
- Lessons learned while moving **JavaScript to TypeScript** in Nuxt 3 projects
- Ongoing updates to my **Planning Poker app**, especially mobile responsiveness and small quality of life improvements that add up

Some posts will be technical. Some will be more reflective. Some will just be quick notes about something I learned the hard way. The goal is to stay honest, stay consistent, and document the process as it actually happens.

Now I just need to start writing and shipping them one at a time. 🚀

---

### February 6, 2026

**Holiday Recharge and Dev Adventures 🎄**

The holidays are a great reminder of the simple things: cozy evenings, good food, and most importantly, **quality time with family**. It’s amazing how stepping away from screens for a little bit can help you hit reset and come back with fresh energy.

That said, it hasn’t been a quiet break in my dev life. Over the past few weeks, I’ve been diving into all sorts of exciting work:

- Building **dynamic chart components** that actually respond to user input
- Creating **specialized print screens** to make reports look just right
- Estimating updates for **project structure improvements**
- Completely reworking a feature that overhauled the **main function of an application**
- Adjusting to **new projects and codebases**
- Participating in **code reviews and giving feedback**

And that’s just scratching the surface.

Even with the whirlwind of activity, I’m more excited than ever to keep going. There is something so satisfying about turning complex problems into smooth solutions, and each challenge is a chance to grow.

The holidays helped me pause and appreciate the bigger picture, and now I’m ready to dive back in with renewed focus and energy. Let’s get it! 🚀
