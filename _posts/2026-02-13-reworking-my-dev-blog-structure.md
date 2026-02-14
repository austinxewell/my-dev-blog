---
layout: post
title: "Reworking My Dev Blog Structure (and Why It Was Necessary)"
date: 2026-2-13 08:00:00 -0700
categories: [personal-blog]
---

Yesterday I finally fixed something that had been bugging me for a while: how my personal dev logs were structured.

Originally, my “personal blog” was basically a dumping ground. One long post per month, multiple dates jammed together, zero real structure. It worked when I started, but it didn’t scale, and it wasn’t pleasant to navigate or maintain.

So I rebuilt it. 🔨

## 🧱 The New Structure

I split my content into two clear tracks:

- **🧠 Personal logs** — time-based, chronological, meant for reflection and ongoing work
- **📚 Everything else** — standalone technical posts, guides, and write-ups

For personal logs, I moved to a hierarchy that actually makes sense:

```sql
Personal Logs
└── Year
    └── Month
        └── Daily entries
            └── Individual post
```

Instead of one bloated monthly post, each entry now lives on its own. That gives me:

- ✨ Cleaner URLs
- 🧭 Better navigation
- 🔗 Easier linking
- ✂️ Smaller, focused posts instead of walls of text

If I want to reference a specific day or idea later, I can. No more scrolling through a thousand words to find one paragraph.

## 🏷️ Using Categories to Separate Concerns

Next, I separated personal logs from the rest of my content using categories.

Anything tagged as `personal-blog` is intentionally **not** part of the main blog feed. Those posts still exist, they’re still linked, but you have to navigate into them on purpose.

That was the goal.

My dev blog shouldn’t feel like a journal unless you’re explicitly looking for that. Technical posts, experiments, and write-ups stay visible. Personal logs stay organized and tucked away. 📦

## 🔍 Smarter Related Posts Logic

The last piece was fixing related posts.

I created a custom `_includes/related-posts` partial that ignores relationships based purely on the `personal-blog` category.

Here’s the behavior I wanted:

- A post tagged `[personal-blog, jekyll]`
  - 🚫 **Should not** show related posts that are _only_ `[personal-blog]`
  - ✅ **Should** show related posts that share meaningful categories like `[jekyll]`

In other words:

- Shared _context_ is not the same as shared _content_
- “Personal log” is a container, not a topic

This keeps related posts actually relevant instead of noisy. 🔇

## 🎯 Why This Matters

This wasn’t about aesthetics. It was about long-term maintainability.

- ✍️ I can write personal logs freely without polluting the main blog
- 🔎 Technical posts stay discoverable
- 🧠 Navigation reflects intent, not just chronology
- 🤝 Related posts now help instead of distract

It’s still simple. Still Jekyll. Still static.

Just finally structured in a way that respects how I actually use the site.

And now I won’t dread adding the next post. 🚀
