---
layout: post
title: First Real Test File
date: "2026-09-21"
categories:
  - personal-blog
tags:
  - automation
  - tool
  - tooling
  - problem-solving
---

I have had a bottleneck when it comes to writing my own blog posts.

Because I'm using Jekyll, I have to open my IDE, create a file, write the Markdown, preview it separately, and then push it to GitHub. None of those steps are particularly difficult, but together they create just enough friction to make me talk myself out of posting from time to time.

Then I had a realization...

> Hey, I'm a developer. I can fix this bottleneck.

### The Solution

I knew it wouldn't be overly difficult to create a local tool that I could use on my machine to display the Markdown next to what I'm typing. That way, I could see my blog post rendered in real time while I write it.

I also knew that creating a basic terminal command could allow me to push the finished file directly to my cloned repository. From there, GitHub would handle the rest and automatically deploy the post to my website.

That sounded a lot better than manually opening my IDE every time I wanted to write something.

So that's where I started.

I created a very basic application with a structure that looked something like this:

```text
public/
  index.html
server.js
.env
package.json
```

Nothing fancy. Just a basic UI, a small server, and the pieces I needed to start experimenting with the workflow.

The goal at this stage wasn't to build some polished blogging platform. I just wanted to remove the friction between having an idea for a post and actually publishing it.

And honestly, that's exactly what this is about.

I'm looking at the first true blog post created using this new UI.

The tool is still extremely basic, and there is plenty I want to improve. But that's kind of the point. I identified a problem in my own workflow, realized I had the skills to solve it, and started building a solution instead of continuing to work around the problem.

Now I can write my posts, see the rendered Markdown in real time, and eventually publish them without ever needing to leave the tool.

Party time! 🥳
