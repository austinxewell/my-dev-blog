---
layout: post
title: Getting As Above Tattoo SLC Live
date: '2026-10-11'
categories:
  - personal-blog
  - public
tags:
  - react
  - react-router
  - graphQL
  - MongoDB
  - Stripe
---
Tonight, I got the foundation of a new project, As Above Tattoo, up and running in production.

I'm building this website for a friend who owns a tattoo shop, but I also wanted to use the project as an opportunity to work with technologies I want to showcase more in my portfolio. My goal is to build something useful for the shop while getting hands-on experience with React, GraphQL, MongoDB Atlas, and Stripe.

We haven't built out the actual shop experience yet, but tonight was all about laying the groundwork.

## Building the foundation

The frontend is built with React, TypeScript, and React Router in framework mode. I'm using Tailwind CSS v4 for styling and shadcn/ui with Radix UI for accessible, reusable components.

Rather than jumping straight into building pages, I took some time to establish a design system. I created a color palette built around warm paper tones, charcoal, and antique gold, along with semantic color tokens for backgrounds, surfaces, text, borders, and accents. I also set up typography using Inter for body text and DM Serif Display for headings.

The idea is to make the design consistent from the beginning instead of scattering hardcoded colors and styling decisions throughout the application. It also gives me a foundation for supporting both light and dark themes.

## Setting up a real development workflow

I wanted this project to follow a more structured development process than simply making changes and pushing them directly to production.

The repository is hosted on GitHub, with separate `dev` and `main` branches. Both branches are protected by rulesets that require pull requests and successful CI checks before changes can be merged.

I also configured GitHub Actions to run linting and production builds for both the frontend and backend. That gives me an automated way to catch certain issues before changes make their way into the main branch.

It's a small project, but I wanted to practice the kind of workflow I'd expect to use on a team: work in a feature branch, open a pull request, let automated checks run, and merge only when those checks pass.

## Getting the site deployed

The other major milestone tonight was getting the project deployed to Netlify.

I configured the build settings and added a `netlify.toml` file so the deployment configuration lives alongside the code in the repository. The intention is to use `main` for production deployments while keeping development work separate.

Naturally, deployment wasn't completely painless.

The first production deployment resulted in Netlify's generic Page Not Found screen. After investigating the build output, I discovered that React Router's configuration had server-side rendering enabled. That didn't match the static single-page application setup I intended to deploy.

Switching `ssr` to `false` allowed the build to generate the expected `index.html` entry point. Once that configuration was corrected, the deployment could serve the application properly.

That was a good reminder that a successful build doesn't automatically mean the output is configured correctly for the hosting platform. Understanding what the framework generates, where it puts those files, and what the host expects matters just as much as getting the code to compile.

And now, it's live.

**[View As Above Tattoo SLC](https://asabovetattooslc.netlify.app/)**

## What's next?

This is just the beginning. The site currently serves as a foundation for the actual tattoo shop experience, and there is plenty left to build.

The broader plan is to develop a polished website that showcases the shop and its artists while giving me the opportunity to work through a full-stack architecture. That includes a Node.js and Express backend, GraphQL with GraphQL Yoga, MongoDB Atlas for data storage, and Stripe for payment processing when we get to that part of the project.

I also want to keep the implementation intentional. I don't want to add technologies just to check boxes on a résumé. I want to understand why each piece belongs in the architecture and how the pieces fit together.

For tonight, though, getting the foundation configured, the automated checks passing, the branches protected, and the production site live is a solid win.

There's something satisfying about taking a project from a local development environment to a real URL that someone else can open. Now I can share the site with the shop owner and continue building on top of a foundation that's already in place.

One milestone down. Plenty more to go.
