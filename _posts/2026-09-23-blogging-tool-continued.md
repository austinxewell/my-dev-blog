---
layout: post
title: Blogging Tool Continued...
date: '2026-09-23'
categories:
  - personal-blog
tags:
  - tool
  - tooling
  - problem-solving
---
Yesterday, I started a small project to make writing and publishing my blog posts a little less annoying.

The idea was pretty simple: build a local tool where I could write a post, submit it, and have it committed to my GitHub Pages repository without having to jump through all of the little hoops I normally have to go through.

1) Open my IDE.

2) Create a Markdown file.

3) Add the front matter.

4) Write the post.

5) Make sure it's in the right directory.

6) Start Jekyll.

7) Open the local site.

8) Check the formatting.

9) Go back and fix something.

10) Commit everything.

11) Push it.

None of those steps are particularly difficult, but when you put them all together, it creates just enough friction to make me think, "Eh... I'll write it later." 😅

And we all know how that usually goes.

## From Testing to Actually Being Useful

Yesterday's post was intentionally pretty generic because, honestly, it was partly an excuse to test the tool itself.

I wanted to make sure I could get the basic workflow working before I started making it more useful.

Today, I expanded on that idea.

One of the first things I added was a `.bat` file that handles the initial setup for me.

Now I can have a shortcut sitting right on my desktop. I click it, and it opens the project, starts the local server, opens the browser to localhost, and gets everything ready for me.

That's it.

No terminal.

No manually starting the dev server.

No digging through folders.

No remembering which localhost port I'm using.

I just open the shortcut and start writing. 🚀

Once I'm finished, I hit submit and the tool takes care of the rest.

But I didn't stop there.

## One Less File to Think About

There was another small piece of my blogging workflow that I realized I was still handling manually.

Every month, I have a monthly update file that needs to be created for the new month.

Normally, I'd have to remember to create that file myself.

Not anymore.

I added some automation that checks whether a new month has been pushed. If it has, the tool automatically creates the new monthly update file for me.

It's a tiny feature.

Like... *really* tiny.

But that's kind of the point. 😄

It's one more thing I don't have to remember to do.

The goal isn't to automate everything just because I can. It's to automate the repetitive little things that don't really provide any value.

I don't need to spend my time thinking, "Oh yeah, it's a new month. I need to make that file."

The system can figure that out.

And now it does.

## From Multiple Steps to One

With these changes, what was previously a multiple-step process is now basically:

**Open → Write → Submit.**

And honestly, that's pretty satisfying.

I started this project yesterday because I wanted an easier way to write blog posts.

A day later, I've got a desktop shortcut that launches everything, automatic monthly file creation, a writing interface, and the ability to commit the finished post without leaving the tool.

For a project that started as a way to test an idea, it's becoming surprisingly useful.

## It Doesn't Need to Be Complicated

This little project reminded me of something I've learned throughout my time in development.

Sometimes it's not about how advanced your project is.

It's not about how many technologies you're using.

It's not about whether you built some incredibly complicated architecture that makes people say, "Whoa, that's impressive."

Sometimes it's just about solving a problem.

That's something I think is easy to lose sight of as a developer.

There's always another framework to learn. Another design pattern to understand. Another technology that everyone says you should be using.

But at the end of the day, software exists to solve problems.

This tool isn't particularly complicated. It probably isn't going to impress anyone looking at my GitHub repository.

And that's okay.

It doesn't need to.

I had a problem.

I figured out why I was running into that problem.

Then I built something to remove the roadblock.

Problem solved. 🤷‍♂️

## Small Problems Still Matter

I think there's also something to be said for solving the small problems you encounter in your own life.

I could have just kept telling myself that creating a blog post isn't that difficult.

I already know Markdown.

I already know Jekyll.

I already know Git.

I already know how to push changes to GitHub.

None of that was the problem.

The problem was the **friction between having an idea and actually publishing it.**

That distinction matters.

A process can be technically easy and still be annoying enough that you avoid doing it.

So instead of forcing myself to keep working around that friction, I decided to eliminate it.

And that's probably my favorite part of this project.

It isn't impressive because it's complicated.

It's useful because it solves a problem I actually had.

## Build What Gets in Your Way

I think that's one of the most valuable lessons I've picked up as a developer.

You don't always need to build something huge.

You don't always need to prove that you can solve the hardest problem in the room.

Sometimes you just need to look at something that's getting in your way and think:

**"I could probably make this easier."**

Then go make it easier.

That's exactly what this project is.

A small tool built to remove a bunch of small roadblocks.

And now, instead of thinking about everything I have to do before I can write a blog post, I can click a shortcut, start typing, and get the idea out of my head.

That's a win in my book. 👍
