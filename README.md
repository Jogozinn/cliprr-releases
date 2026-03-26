# Cliprr

Cliprr is a Windows desktop app for turning Twitch streams into shortform content workflows.

It combines a local Electron app, a local FastAPI backend, Twitch monitoring, clip processing, title generation, review tools, and optional upload routing into one packaged tool.

## Current status

Cliprr v1 is complete and now in trial use.

That means:

- the core workflow is real and usable
- trial users should expect a practical tool, not a polished SaaS platform
- some advanced integrations and internal tools exist, but not every area should be treated as equally mature

## Who Cliprr is for

Cliprr is built for people who want to catch Twitch moments faster and spend less time manually clipping, titling, and routing content.

It is best suited for:

- streamers
- editors
- solo content operators
- testers helping validate the workflow during the trial phase

## What Cliprr does

Cliprr currently supports five main jobs:

1. Monitor live Twitch channels and trigger clips
2. Process clips into usable shortform outputs
3. Generate and review titles
4. Route outputs to connected destinations
5. Review saved clips and cut longform/VOD content

## Core workflow

1. Install and launch Cliprr
2. Create an account or sign in
3. Complete first-time setup
   - Twitch app + auth is required for live monitoring
   - Google is optional unless you want Drive or YouTube-related flows
   - Discord is optional
4. Start a monitor for a Twitch channel
5. Let Cliprr watch for moments and trigger clips
6. Process, title, review, and route outputs
7. Use the library and longform tools for follow-up work

## Product areas

### Live monitoring

- live Twitch monitor
- confidence and threshold controls
- cooldown and trigger behavior
- AutoPilot and favorites watchlist

### Clip processing

- queued clip jobs
- durable spool/pending-job handling
- transcription and caption pipeline
- title generation
- output logging

### Review and organization

- local clip library
- user dashboard
- learning dashboard
- admin dashboard

### Longform

- VOD and local MP4 analysis
- hot block detection
- clip generation from selected blocks

### Integrations

- Twitch auth
- Google auth for Drive and YouTube-related flows
- Discord webhook delivery
- TikTok and Instagram paths exist, but should be treated more carefully during trial

## Trial-first reality

Cliprr already does a lot, but the trial phase should focus on the strongest flows first:

- first-time setup
- live monitoring
- clip processing
- library and review
- longform/VOD workflow

Advanced or rougher areas should be tested, but not over-marketed yet.

## Architecture at a glance

- Electron main process: app startup, backend launch, preload bridge, local trial/license gate
- React frontend: login, setup, monitor, settings, dashboards, library, VOD tools
- FastAPI backend: auth, monitoring, queueing, processing, routing, integrations, logging
- Local user data: settings, database, logs, queue state, processed outputs

## Install and run basics

### Packaged app

The current packaged flow is Windows-focused.

- install Cliprr
- launch the installed app
- complete setup

### Source/dev flow

- backend is launched locally by the Electron app in dev
- frontend runs from the React app
- packaging is handled through Electron Builder and a packaged backend binary

## Documentation

- [FEATURES.md](./FEATURES.md)
- [USER_GUIDE.md](./USER_GUIDE.md)
- [TRIAL_NOTES.md](./TRIAL_NOTES.md)
- [TECHNICAL_OVERVIEW.md](./TECHNICAL_OVERVIEW.md)

## What to read next

- Start with [USER_GUIDE.md](./USER_GUIDE.md) if you want to use Cliprr
- Read [TRIAL_NOTES.md](./TRIAL_NOTES.md) if you are testing the current build
- Read [TECHNICAL_OVERVIEW.md](./TECHNICAL_OVERVIEW.md) if you are working on the codebase
