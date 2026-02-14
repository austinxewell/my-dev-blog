---
layout: post
title: "Inside a Smarter Chart Component"
date: 2026-2-10 08:00:00 -0700
categories: [personal-blog]
---

The past couple week I spent time working on a chart component that we knew from the beginning would be a meaningful and carefully planned update. While it might look simple at first glance, this work touched several areas of the application and required thinking beyond just visual output.

One of the main goals was to make the chart **adapt its layout based on the number of selected data points**. When only a few data points are selected, the chart stays clean and easy to read. As more data is added, the layout automatically adjusts so spacing, labels, and visuals remain usable instead of becoming cluttered.

Another important update was **dynamic scaling**. The chart now lets users toggle between using **min and max values provided by the backend** or automatically adjusting based on the highest and lowest values in the currently selected dataset. This allows the chart to zoom in on trends while keeping the full dataset intact.

We also added support for **custom date ranges**. Users are no longer locked into preset options and can choose exactly what time range they want to explore. To do this efficiently, we updated a previously existing chart component rather than creating something entirely new.

To avoid breaking existing features, we introduced a boolean flag called `allowsCustomDate`. This allows custom date selection only where it is explicitly supported, while keeping the current `appChart` behavior untouched elsewhere. This gives us a safe, controlled way to roll the feature out gradually across the app.

As expected, the work did not stop at the main chart. Since these charts are also used in reports, we had to update the **print formats** to match the new scaling and date logic. Keeping on screen views and printed output in sync took extra care, but it was essential for consistency.

All of this work was done in a **Nuxt 2 project using ApexCharts**, which added its own set of constraints and considerations. By the end of the week, the component felt more flexible, more predictable, and much more future ready.

This kind of work is exactly why I enjoy front end development. Thoughtful planning, incremental improvements, and solving real problems without breaking existing functionality. On to the next challenge 🚀
