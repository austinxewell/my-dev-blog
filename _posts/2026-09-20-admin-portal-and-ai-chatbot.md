---
layout: post
title: "Building My Portfolio Admin Portal and AI Chatbot"
date: 2026-09-20
categories:
  - personal-blog
  - public
tags:
  - portfolio
  - nuxt
  - typescript
  - ai
  - chatbot
  - llm
  - grok
  - web-development
---

I've reached another pretty significant milestone with my portfolio project: the admin portal is officially complete, and I've started working on the AI chatbot I've been wanting to add.

The admin portal has been one of those features that isn't necessarily exciting to look at from the outside, but it makes the rest of the project considerably easier to manage. Instead of hardcoding portfolio content and constantly digging through files whenever I want to make a change, I now have a centralized place to manage the content that powers the site.

With that out of the way, I could finally start playing with something a little more interesting.

## Enter the AI Version of Me

I've been kicking around the idea of adding an AI chatbot to my portfolio for a while.

The basic idea is pretty simple: instead of a portfolio being a collection of pages someone has to browse through, visitors could interact with an AI that knows about me, my experience, my projects, my skills, and the things I've worked on.

Something along the lines of:

> "What kind of projects has Austin worked on?"

or:

> "Does Austin have experience with React?"

or even:

> "Tell me about Austin's Planning Poker project."

The chatbot could answer those questions conversationally instead of forcing someone to hunt through my resume or portfolio.

I finally have a working version.

And, unsurprisingly, the first version immediately gave me another problem to solve.

## The Token Problem

The current implementation sends the information the AI needs along with the conversation.

That works.

It's also expensive in terms of tokens.

Since I'm currently experimenting with Grok's free model, the token limits become noticeable pretty quickly. Every time I send a request, I'm potentially sending a large amount of information about myself along with the user's actual question.

That's fine when testing a couple of questions.

It's not exactly ideal if I want an actual visitor to have a conversation with the chatbot.

For example, imagine the chatbot has information about:

- My professional experience
- My technical skills
- My projects
- My services
- My education
- My development experience
- My portfolio
- Personal information I'm comfortable sharing publicly

If all of that gets included with every request, the actual question might be tiny compared to the context being sent to the model.

That got me thinking about a bigger question:

**Do I really need to send all of that information every single time?**

Probably not.

## Brainstorming Possible Solutions

I haven't settled on the final architecture yet, which is actually part of what makes this interesting.

There are several approaches I could experiment with.

### Store the Information Outside the Conversation

One obvious option is to keep my portfolio data in my own database and only retrieve the pieces that are relevant to the user's question.

Instead of sending everything about me to the model, I could determine that a question is related to my professional experience and only provide the relevant information.

That would dramatically reduce the amount of unnecessary context.

It also fits nicely with the existing architecture of my portfolio because the admin portal already manages much of this information.

### Retrieval-Augmented Generation

Another option is going down the RAG route.

The basic idea would be to turn my portfolio information into searchable pieces of knowledge and retrieve the most relevant pieces whenever someone asks a question.

For example, if someone asks:

> "What frontend frameworks does Austin use?"

the system could retrieve the information related to my technical experience and provide only that context to the AI.

If they ask about one of my projects, it could retrieve that project's information instead.

This seems like a particularly interesting direction because it would let the chatbot grow without requiring the entire knowledge base to be included in every request.

### Embeddings and Vector Search

Taking RAG a step further, I could generate embeddings for my portfolio content and store them in a vector database.

Then the user's question could be converted into an embedding and compared against my stored information.

The closest matches could be passed to the model as context.

That's probably more infrastructure than I actually need for a personal portfolio, but it's also a good opportunity to learn how these systems work by building one myself.

### A Smaller Static Knowledge Base

There's also the possibility of keeping things much simpler.

My portfolio isn't exactly Wikipedia.

I have a relatively small amount of information that the chatbot actually needs to know.

I could potentially create a structured JSON document containing the important information about me and build some basic retrieval logic around it.

That might give me most of the benefits without introducing another database or service.

There's something appealing about solving the actual problem before reaching for a more complicated architecture.

## Another Question

There's also a distinction I'm still thinking about.

Do I actually need the AI to "remember" everything?

Or do I just need my application to know where to find the information?

Those are two very different problems.

Conversation history needs to be maintained so the AI understands the current conversation.

My portfolio information doesn't necessarily need to live inside that conversation.

If someone asks:

> "What projects have you worked on?"

and then follows up with:

> "Which one used Socket.IO?"

the chatbot needs to understand that "which one" refers to the projects from the previous question.

But it doesn't necessarily need to carry my entire portfolio database through every request to accomplish that.

That distinction could end up being the key to reducing the token usage.

## Where I'm At

For now, I have a working chatbot, which is a pretty good starting point.

The problem isn't that I can't get it to answer questions.

The problem is that I need to figure out how to make it do that efficiently.

That's actually one of the things I like about working on projects like this. The first version gets something working, and then immediately exposes another problem that requires me to think about the architecture.

So that's where this project is currently sitting.

The admin portal is finished.

The AI chatbot works.

Now I need to figure out the best way to give the AI access to my information without dumping my entire portfolio into every request.

I'm not sure yet whether that ends up being simple retrieval, RAG, embeddings, a structured knowledge base, or something else entirely.

Honestly, figuring that part out is probably going to be the more interesting part of the project.