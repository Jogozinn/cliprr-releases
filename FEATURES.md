# Cliprr Features

This file lists the features that are present in the current Cliprr codebase. It does not include roadmap ideas or planned features.

## How to read this file

- **Trial-ready** means the feature looks usable enough for real testing
- **Advanced** means it exists and works, but may need more explanation or careful use
- **Partial** means it exists in the product, but should not be treated as a headline promise yet

## 1. Live monitoring

### Twitch channel monitoring

Status: Trial-ready

Cliprr can monitor live Twitch channels and watch for moments worth clipping.

Includes:

- channel-based monitoring
- live confidence tracking
- clip trigger counts
- cooldown handling
- monitor status updates

### Confidence and threshold controls

Status: Trial-ready, advanced

Cliprr exposes confidence and threshold logic rather than hiding it completely.

Includes:

- confidence target setting
- auto-threshold support
- cooldown and re-arm behavior
- confidence/stat endpoints used by the live workspace

### AutoPilot and favorites

Status: Trial-ready

Cliprr has a favorites/watchlist layer that goes beyond a static saved list.

Includes:

- favorite channels
- live polling
- watch arming
- go-live monitor starting behavior

This is one of the stronger underexposed parts of the product.

## 2. Clip creation and processing

### Triggered clip creation

Status: Trial-ready

When a monitor decides a moment is worth clipping, Cliprr can kick off the clip job and push it into the processing flow.

### Durable queue and spool

Status: Trial-ready, internal strength

Cliprr uses a real queue layer with pending-job persistence.

Includes:

- in-memory queue handling
- persisted pending jobs
- restart survival for queued work

### Processing pipeline

Status: Trial-ready

Cliprr has a backend processing pipeline for clips after they are created.

Includes:

- clip acquisition/download handling
- transcription-related steps
- captioning pipeline hooks
- title generation integration
- routing/upload handoff
- logging of results

## 3. Titles and learning

### Title generation

Status: Trial-ready

Cliprr can generate multiple title candidates rather than only one fixed title.

Includes:

- title generation pipeline
- title ranking/best-title output
- test mode flows for title-focused runs

### Learning dashboard

Status: Trial-ready, advanced

Cliprr includes a learning dashboard with rule preview and apply/disable/reset controls.

This is more than a simple “AI titles” toggle.

Includes:

- learning summary
- proposed rule preview
- apply rule
- disable rule
- reset learning state

### Prompt approval and context tools

Status: Partial, internal-tool leaning

Cliprr contains prompt approval and context-dictionary plumbing that appears aimed at refining how context and title ideas are handled.

This exists, but it should be explained carefully and not treated as the main marketing story yet.

## 4. Review and storage

### Library

Status: Trial-ready

Cliprr includes a clip library for reviewing saved outputs.

Includes:

- clip listing
- refresh
- delete
- review-oriented grid/card view

### Dashboards

Status: Trial-ready

The app includes multiple dashboards:

- user dashboard
- learning dashboard
- admin dashboard

These help surface activity, metrics, queue/admin tooling, and internal system state.

## 5. Longform / VOD

### VOD analysis

Status: Trial-ready

Cliprr can analyze a Twitch VOD or local MP4 and identify hot blocks for follow-up clipping.

### Longform clip generation

Status: Trial-ready, advanced

After analysis, selected blocks can be processed into clips.

Includes:

- analyzed block retrieval
- generation streaming/logging
- local file path support

This is a real feature, but it is more power-user oriented than the main live-monitor flow.

## 6. Integrations and routing

### Twitch app and auth

Status: Trial-ready

Cliprr supports Twitch connection for clip and chat auth flows.

This is the main required integration for first use.

### Google connection

Status: Trial-ready

Cliprr supports Google OAuth and Google account storage for Drive and YouTube-related flows.

It is optional unless you want those destinations.

### Discord delivery

Status: Trial-ready

Cliprr supports Discord webhook connection and test sending.

### Multi-account routing

Status: Trial-ready, advanced

Settings and routing logic support account-aware routing for destinations such as Google and TikTok.

### TikTok upload path

Status: Partial

TikTok upload logic exists, including backend upload code and settings support, but this should be treated as a more cautious trial feature.

### Instagram upload path

Status: Partial

Instagram upload code exists, but it should not be marketed as heavily as the main Twitch/Google/Discord flows yet.

## 7. Setup, auth, and licensing

### Login and registration

Status: Trial-ready

Cliprr includes local account creation and login for the app.

### First-time setup

Status: Trial-ready

Cliprr has a guided first-time setup page focused on the minimum needed to start using the app.

Required:

- Twitch app + auth
- starter channel

Optional:

- Google upload connection
- Discord delivery

### Trial and license gating

Status: Trial-ready MVP

The desktop app includes local trial/license gating with Gumroad verification and hardened local state handling.

This is good enough for MVP packaging, but it is still a local-first desktop enforcement model.

## 8. Internal and admin systems

### Queue controls

Status: Trial-ready, advanced

Admin tooling includes queue stop/clear controls.

### Test mode

Status: Trial-ready, advanced

There is a test mode focused on titles-only runs and lower-cost validation.

### Metrics polling

Status: Trial-ready, advanced

Admin tooling includes YouTube metrics polling status and manual poll actions.

## Features to explain carefully

These are real, but need careful messaging:

- confidence and threshold logic
- AutoPilot
- learning rules
- prompt approval
- longform/VOD analysis
- TikTok upload
- Instagram upload

## Features to lead with

If you are describing Cliprr to trial users, lead with:

- Twitch monitoring
- clip triggering
- processing pipeline
- title generation
- library/review
- VOD clipping
- optional upload routing
