# Rasthm Desk: the control room for my AI agents

> The source code is private. This page explains what the desk is and what it is built with.

I run a small AI automation studio, Halo Automations, mostly with agents. They reply to new leads, prepare proposals, keep track of calls, and make and post Instagram reels. The desk is the one private page where I see what they are doing and step in. Everything is automatic by default, and I can override any of it by hand.

It works on a laptop and on a phone, usually opened straight from a Telegram ping.

## What it does

**Inbox**
- New leads from the website, Instagram comments and Instagram DMs, each with a reply drafted by an agent. I can approve, edit or skip it. Approved replies go out through Gmail or Instagram.
- Booked calls are pulled from Google Calendar. Moved or cancelled calls are followed, with reminders 30 and 5 minutes before.
- Proposals are drafted from call notes. Each gets a private proposal page for the client, a follow-up reminder, and approve, edit and skip buttons.

**Reels**
- Connects to Instagram.
- Each reel card has its caption and video, with Approve, Post now, Post at and Skip.
- Posting slots are in Indian time. A reel is approved automatically if I don't act in time. A missed slot moves to the next free one instead of flooding the feed.
- The reel maker on my PC ([Casper](https://github.com/rasthm/casper-showcase)) is controlled from here: on and off, the next topics, notes for the maker, and posting times.
- Weekly Instagram numbers.

**Settings and activity**
- Prices, agent switches, timings, message texts and auto modes, each one checked before it is saved.
- An activity log of everything the agents and the desk did, plus Casper's heartbeat.

**Telegram**
- Pings with one-tap approve buttons, reminders, and a login link for signing in.

## How it is built

- One Cloudflare Worker in TypeScript, with D1 (SQLite) for data and KV, and a cron job every 5 minutes that posts reels, auto-approves, auto-replies and sends reminders.
- The front end is plain HTML, CSS and JavaScript modules, with no framework and no build step.
- All timers, polls and checks are plain code, so no AI calls are spent on scheduling.
- Everything a visitor or a model wrote is shown as text, never as HTML. The page is not indexed by search engines.
- Unit tests run with Vitest.

## Integrations

Cloudflare Workers, D1 and KV · Telegram Bot API · Gmail API · Google Calendar API · Instagram Graph API (posting, comments, DMs and insights) · Casper on my PC, for sales drafts and reels.

---
© 2026 Rasthm.
