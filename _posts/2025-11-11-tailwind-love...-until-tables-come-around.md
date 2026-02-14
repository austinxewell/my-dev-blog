---
layout: post
title: "Tailwind Love... Until Tables Come Around"
date: 2025-11-11 08:00:00 -0700
categories: [personal-blog]
---

I’ll say it... I love using **Tailwind CSS**. The speed, flexibility, and control it gives when building UIs is unmatched. Being able to rapidly style and adjust components without leaving my markup has completely changed how I approach front-end development.

That said, there is one area where Tailwind really starts to show its limits: **tables**.

When it comes to consistent table design like spacing, alignment, alternating row colors, hover states, or handling responsive layouts, utility classes can start to feel clunky. It is one of those places where using Tailwind alone ends up being more painful than productive.

After building multiple table-heavy features across different applications at work, I have realized that **SCSS still wins** for structured table styling. Nesting selectors, handling breakpoints with mixins, and keeping the table formatting logic contained just makes more sense.

So while I will keep using Tailwind for most of my UI, tables are one place where I am perfectly fine going back to SCSS. Sometimes the older and more reliable tools still fit the job better. 🧠💡
