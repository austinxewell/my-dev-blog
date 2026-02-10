---
layout: post
title: "Personal Blog - February 2026"
date: 2026-2-06 08:00:00 -0700
categories: Personal Blog
---

# February 2026

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
