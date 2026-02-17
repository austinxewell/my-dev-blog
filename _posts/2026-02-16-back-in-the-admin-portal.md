---
layout: post
title: "Back in the Admin Portal: Auth, Environments, and Complex Project Flows"
date: 2026-02-16
categories: [personal-blog]
tags:
  [frontend, backend, authentication, ssr, cookies, api, ux-ui, database, sql]
---

Today I jumped back into developing the admin portal for my online portfolio. This is one of those projects that’s been quietly sitting there, _mostly_ complete, waiting for me to come back and finish the harder parts.

Spoiler: it’s going well.

## Environment-Agnostic Backend Setup

One of the first things I tackled was cleaning up how the backend handles environments. I updated the BE so it works in both production and local development **without changing the code**.

If `API_BASE_URL` is not provided, the logic now defaults to localhost—backend included. That means I can develop and test features locally without worrying about accidentally impacting production behavior.

This kind of setup removes friction. Less config juggling. Fewer “why is this broken locally?” moments. Just run it and go.

## Improving the Auth Flow with SSR in Mind

On the frontend, I reworked the login flow to behave like a real application instead of a client-only shortcut.

The auth token is now stored in cookies so it can be validated at the **server level** during SSR. That opened the door to properly securing the admin portal instead of just hoping the UI behaves.

I added frontend middleware (`admin-auth.ts`) that does the following:

- Calls a `validateToken` method
- Passes authorization headers
- Returns the logged-in user if the token is valid
- Blocks access entirely if the user is not authenticated
- Routes the user back to the login page

This ensures users without valid credentials never even reach the admin UI. No flashing content. No half-loaded pages. Just a clean denial.

Exactly how it should be.

## Building the Project Creation Flow (The Hard Part)

I also started updating the flow for creating a project, which is where things get interesting and complicated.

This isn’t a single request. It’s a sequence of linked operations across multiple tables:

1. Create the base project record
2. Associate tags from the tags table
3. Select **three primary tags**
4. Upload images into the database
5. Link those images back to the project

All of this logic already exists in the backend. I can run every step via **SQL** prompts or **Postman** without issues.

The remaining work is on the frontend: building the payloads correctly and wiring the UI to the backend endpoints.

The good news?

The UI/UX for this entire flow is essentially complete. A few minor tweaks remain, but structurally it’s done. What’s left is implementation, not design, which is the part where you get that warm fuzzy feeling seeing the fruits of your labor post a finished product.

## A Quick Reality Check on Context Switching

Coming back to this project was a reminder of something every developer learns the hard way:

You can be super organized when you start a project and still get lost when you return later.

It took a bit to reorient myself. Not because the code was bad, but because _context fades_. That moment of “okay… where exactly was I?” is unavoidable.

It was also a solid reminder of why clean code, documentation, and repo organization matter, even when you’re working solo. Future-you is still another developer, and future-you does not remember everything.

## Momentum Feels Good

Overall, I’m genuinely excited about how this is shaping up. The foundations are solid, the architecture is doing its job, and I’m past the vague phase and back into concrete progress.

Now it’s just execution; and that’s a good place to be. 🚀
