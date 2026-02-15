---
layout: post
title: "When Your Database Looks Dead but Isn’t"
date: 2026-2-11 08:00:00 -0700
categories: [personal-blog, public]
tags: [backend, devops, nodejs, mysql, railway, database, jekyll]
---

As a developer, few things are as alarming as seeing your backend throw **ETIMEDOUT** errors on every request. Today, I ran into that exact situation with my Node.js portfolio running on Railway.

At first glance, it looked like MySQL had completely stopped:

## Database deployment: stopped

My heart sank. Had I broken something? Had I lost all my data?

**Spoiler:** no. The database was fine. The problem was Railway. Ironically, I'm thankful it was just a Railway outtage.

## What actually happened

Railway crashed in certain areas and this created my connection to MySQL and my back end deployment to crash. Whats really tricky is Railway shows a deployment status that isn’t always trustworthy. The logs told me:

```yaml
2026-02-11 22:59:51.262288Z 0 [System] /usr/sbin/mysqld: ready for connections. Version: '9.4.0' port: 3306
```

That line alone means MySQL started successfully and is accepting connections. Everything else, the UI badge, the scary “stopped” label, was misleading.

## Why this happens:

1. **Deployment status does not equal process running.** Railway interprets the container lifecycle differently from MySQL.
2. **Restarting vs. redeploying.** If you restart a DB, Railway may still mark the last deploy as stopped even though the container is alive.
3. **Dashboard lag.** Railway sometimes takes minutes to reflect the real state.

## Lessons learned

1. **Logs are your source of truth.** Ignore the stopped badge. If the logs say ready for connections, your DB is up.
2. **Handle DB outages in your backend.** Even after MySQL restarted, my Node.js backend was still timing out because it held dead connections. **Fix:** poll the DB before starting the server until a simple query succeeds.
3. **Auto-restart is non-negotiable.** Enable Railway’s “Restart on failure” for database services. Don’t rely on the platform to magically revive your container.
4. **Internal hostnames matter.** Your backend should always use Railway’s internal DB host, not localhost or public IPs.
5. **Plan for ephemeral infrastructure.** Even on a paid plan, Railway can send SIGTERM, rotate containers, or recycle hosts. Build for failure.

## Thankfully It Wasn't A Bad Day

Im so thankful that this was a simple fix despite it having my head spinning. I was super afraid that I would have had to restart my MySQL deployment and restructure my database with a back up. Todays been really busy at work so it was not something I would have been able to get to right away.

### TL;DR

- ETIMEDOUT errors don’t always mean your DB is dead.
- Railway UI is misleading; logs and network tests are the truth.
- Add DB readiness checks in your backend.
- Enable auto-restart for your DB service.
- Keep connection pools small and use retries.
- Appreciate the little victories, even if they don't start as victories.

With these safeguards, even Railway’s quirks stop being scary. ✅
