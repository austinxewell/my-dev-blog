---
layout: post
title: I Gave My Portfolio a Voice (Mine)
date: '2026-09-25'
categories:
  - personal-blog
  - public
tags:
  - ai
  - portfolio
  - artificial intelligence
---
Portfolio sites have a problem: **nobody reads them.**

Recruiters skim. Clients scroll to the pricing. Hiring managers jump straight to the projects. And that carefully written About section you spent three hours perfecting?

Yeah. Nobody read it. 😂

So I decided to do something about it.

I added a chatbot to my portfolio that can answer questions about me, as me.

Ask it what I'm good at, what I've built, what technologies I use, what it's like to work with me, or even why you should hire me, and it answers in the first person like you're talking directly to me.

And honestly, building it has been one of the more fun things I've added to my portfolio.

Here's how it works under the hood, what I learned along the way, and why I deliberately kept the architecture simpler than some of the "proper" AI solutions out there.

## 🤖 The stack

Nothing particularly exotic here:

- **Frontend:** Nuxt + TypeScript, using the same Pinia store + service layer pattern as the rest of the site
- **Backend:** Node/Express on Railway, talking to MySQL
- **Model:** `openai/gpt-oss-20b`, served through Groq's free tier

Why Groq?

Honestly... money. 😂

I already pay for an AI chat subscription. I wasn't about to put a metered API bill behind a portfolio chatbot that anyone on the internet can poke at.

Groq's free tier gives me a fast model without adding another monthly expense. The obvious downside is rate limits, which I'll get to later.

For a portfolio project, free + fast + good enough is a pretty compelling combination.

## 💬 How a message gets answered

The entire request flows through a single Express route:

1. The frontend POSTs the user's message to `/chat`.
2. The backend validates it. It has to be a string and can't exceed 1,000 characters.
3. The backend determines what information is actually relevant to the question.
4. It builds a custom system prompt using data from my database.
5. That prompt and the user's message get sent to Groq.
6. The response comes back to the frontend.

The interesting part isn't really sending a message to an LLM.

That's the easy part.

The interesting part is figuring out **what the LLM actually needs to know**.

## 🧠 Context without a vector database

The chatbot needs to know quite a bit about me.

Skills. Projects. Services. Experience. Background. Recommendations. Even project images.

Fortunately, all of that information already exists in my MySQL database because it powers the rest of my portfolio.

My first instinct could have been to just dump everything into the system prompt on every request.

Technically, that works.

It also feels a little like handing someone my entire résumé, tax returns, and childhood diary because they asked what JavaScript frameworks I know.

A smaller model also has more opportunities to get distracted when you give it a mountain of context it doesn't actually need.

The more "proper" solution would be something like RAG with embeddings and a vector database.

And maybe I'll get there eventually.

But this is a portfolio, not ChatGPT 2.0.

I wanted something simpler.

So I built keyword routing.

Every request pulls the relevant data from the database, then decides what should actually be included based on the question:

```
const includeSkills =
    matchesAny(skills.map((s) => s.name).join(' '), userMessage)
    || /skill|tech|stack|know|experience|expert|framework|tool/.test(query)
```

Skills, services, background, and colleague recommendations each have their own triggers.

Ask:

> "What's your tech stack?"

The skills section gets included.

Ask:

> "What's it like working with you?"

The recommendation gets included.

Ask about images?

Relevant project thumbnails get attached.

It's not some groundbreaking AI retrieval system.

It's a few practical rules that solve the problem I actually have.

And that's been one of my favorite parts of this project.

### 🎯 Finding the right projects

Projects needed a little more than a simple yes/no keyword check.

I built a small scoring function that compares words from each project's:

- Name
- Description
- Technology tags

against the user's question.

It skips short words and a small list of common `stopwords`, gives matches a score, and sends the top three projects to the model.

If nothing matches, it falls back to the first three projects.

Is it clever?

No.

Does it work?

Yep.

And for a portfolio with a relatively small number of projects, I don't need a distributed retrieval architecture with seventeen services and a Kubernetes cluster just to figure out which three projects are related to "Nuxt."

Sometimes boring software is good software. 😎

## 🗄️ The database became the source of truth

One of the things I really like about this approach is that I didn't create a completely separate knowledge base for the chatbot.

The portfolio's database is already the source of truth.

That means when I update a project through my admin portal, the chatbot knows about it immediately.

No retraining.

No re-indexing.

No remembering to update a second system because I changed something in the first one.

I also calculate my years of experience from start dates rather than hardcoding the number.

So the chatbot isn't going to be telling people I have "3 years of experience" forever because I forgot to update a prompt.

That's the kind of little thing that makes a project feel finished instead of just functional.

## 🧪 Prompting a smaller model

A 20B model is fast and inexpensive, but it still needs some guardrails.

A language model will happily fill in the blanks if you give it room to do so.

That is exactly what I don't want on a portfolio.

I don't need my AI assistant deciding that I have five years of Kubernetes experience because that sounds plausible.

So the system prompt ended up with some very specific rules:

- **Use only the information provided. No guessing.** If it doesn't know something, it says so with a canned, lighthearted response that points people toward the real me.
- **Use plain conversational text and keep answers short.** Chat bubbles and giant walls of markdown don't exactly mix.
- **For "Why should I hire you?" questions, pick 2–3 strong points.** Otherwise, it tries to dump my entire résumé into one response.
- **Copy dates exactly as written.** This rule exists because the model kept shifting dates by a month. Apparently, dates are optional suggestions to some LLMs. 😂
- **Pair education with experience.** If someone asks about my education, it can mention the University of Utah bootcamp, but it should also put that alongside my production experience.

I also run the model at:

```
temperature: 0.3
max tokens: 450
```

This isn't a creative writing partner.

It's a portfolio assistant.

I'd much rather have it be a little boring and accurate than incredibly creative and completely wrong.

## 🚦 Surviving on a free API

Running on a free API means there are two sets of rate limits to worry about:

**Mine.**

And **Groq's.**

My own limit is handled with `express-rate-limit`:

```
10 requests per 15 minutes per client
```

That keeps a single visitor, bot, or overly enthusiastic portfolio reviewer from burning through my Groq quota.

Groq's limits are a different story.

If Groq returns `rate_limit_exceeded`, my backend reads the `retry-after` header and gives the user a friendly message explaining that the chatbot is running on a free plan and roughly how long they need to wait.

No mysterious:

> "Something went wrong."

No pretending everything is fine.

And no dumping some ugly API error into the UI.

Other upstream failures return a `502`, while the actual error details stay in my server logs.

It's a small thing, but I think good error handling is one of those details people notice without realizing they're noticing it.

## 🛠️ How I built it

I'm proud of this project.

And yes, I used AI heavily while building it.

Those two statements aren't contradictory.

A lot of the implementation was AI-assisted. I used AI to help write code, explore approaches, work through implementation details, catch problems, and move faster.

But AI didn't decide what I wanted to build.

I did.

I designed the overall architecture around the systems I already had. I decided what information the chatbot needed, how that information should be retrieved, what constraints the model needed, how requests should be validated, how rate limiting should work, and what the experience should feel like.

Then I tested the hell out of it.

I asked it questions that should trigger different parts of my portfolio.

I asked vague questions.

I asked about specific projects.

I asked about skills.

I asked about experience.

I asked about education.

I asked what it's like to work with me.

I asked why someone should hire me.

And, perhaps most importantly, I asked questions specifically designed to make it screw up.

Every time it did something weird, I had a decision to make.

Was the prompt wrong?

Was I sending the wrong context?

Was I sending too much context?

Did I need another piece of data?

Did the model need a stricter rule?

Or was I trying to solve a problem that didn't actually need solving?

That's how the current system evolved.

Keyword routing came from realizing that every question doesn't need every piece of my portfolio.

Project scoring came from realizing that simply including every project wasn't useful.

The prompt rules came from watching the model make mistakes.

Token limits came from watching how much information it actually needed.

Rate limiting came from remembering that the internet is full of people who will absolutely click a button 47 times just because they can. 😂

That's the part of AI-assisted development that I think gets overlooked.

Using AI to write code doesn't eliminate the engineering.

You still have to understand the problem, make architectural decisions, evaluate the output, test the system, find the failures, and decide what should happen next.

In this project, AI helped me move faster.

It didn't remove the need for me to think.

And honestly, that's part of what makes this project fun for me. I got to take a technology that is becoming increasingly common, figure out how to actually integrate it into something I had already built, and make it solve a real problem on my own site.

That's a lot more interesting to me than simply making another todo app with an LLM API attached to it.

## 🔮 What's next

The chatbot is still very much a work in progress.

Right now, every message is handled independently.

There's no conversation history, so if you ask:

> "Which project are you most proud of?"

and then follow up with:

> "Tell me more about that one."

the chatbot doesn't have enough context to know what "that one" means.

That's probably the biggest feature I'd like to tackle next.

I'd also like to experiment with Nuxt UI v4's chat components on the frontend and continue looking for ways to reduce token usage without sacrificing response quality.

Eventually, I could see this growing into something much more interesting than a chatbot sitting in the corner of my portfolio.

For now, though, it does exactly what I wanted it to do.

It gives people a way to interact with my portfolio instead of making them dig through it.

And if you're curious what it thinks about me...

Go ahead and give it a try.

Just remember: if it tells you something completely wrong about me, that's a bug report. 😅
