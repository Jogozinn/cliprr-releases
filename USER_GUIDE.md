# Cliprr User Guide

This guide is for people using Cliprr during the current v1 trial.

It focuses on the real current workflow.

## 1. Before you start

Cliprr is a desktop app. The current packaged flow is Windows-focused.

For the main live-monitor workflow, you should expect to need:

- a Cliprr account
- Twitch app credentials
- Twitch auth
- one starter channel to monitor

You do **not** need Google or Discord to start using the app.

Those are optional unless you want upload or delivery flows tied to them.

## 2. First launch

When you launch Cliprr:

1. Sign in or create an account
2. Go through first-time setup
3. Connect Twitch
4. Add your first channel

If the backend is healthy, you should land in the normal app flow. If the backend truly fails to start, check the local logs noted in the trial notes.

## 3. First-time setup

The setup page is meant to get you to a usable first run, not to configure every possible feature.

### Required setup

#### Twitch app + auth

This is the main required step for live monitoring.

Cliprr needs Twitch credentials and auth so it can:

- monitor live channels
- read the data it needs for clip logic
- create clips without reconnecting every session

#### Starter channel

Add one Twitch channel so Cliprr has a real target immediately after setup.

### Optional setup

#### Google upload connection

Only needed if you want Google Drive or YouTube-related flows.

#### Discord delivery

Only needed if you want test sends or delivery to a Discord server.

## 4. Create or start a monitor

After setup, go to the main monitor workspace.

This is the dense operational screen where Cliprr does the live work.

You can:

- select a streamer/channel
- set monitor values
- review confidence and trigger behavior
- start monitoring

## 5. Understand the main live workflow

The normal Cliprr loop is:

1. Start monitoring a live channel
2. Let Cliprr track confidence/activity
3. Let a trigger create a clip job
4. Let the backend process the job
5. Review outputs in the app and library

If you are new to Cliprr, focus on this loop first before exploring advanced controls.

## 6. Confidence and thresholds

Cliprr exposes more of its trigger logic than many simple clipping tools.

That means you may see things like:

- confidence values
- thresholds
- cooldown settings
- auto-threshold controls

### Beginner guidance

If you are just testing the core flow:

- start with the default settings
- avoid tuning too much immediately
- first confirm that monitoring, triggering, and processing work end to end

### Advanced guidance

If you understand the monitor well enough, you can start tuning:

- confidence targets
- cooldown timing
- threshold behavior
- AutoPilot behavior

## 7. AutoPilot and favorites

Cliprr includes a favorites/watch system that can help automate monitoring behavior.

Use this after you are comfortable with the basic manual monitor flow.

What it is good for:

- keeping a short list of streamers you care about
- tracking their live state
- starting monitoring with less manual setup

## 8. Review clips in the library

The library page is the simplest place to review saved outputs.

Use it to:

- refresh available clips
- review prior outputs
- remove clips you do not want to keep

If you are trial-testing Cliprr, the library is a good sanity-check page because it shows whether the full pipeline is actually producing outputs.

## 9. Use the VOD / longform tools

Cliprr is not limited to live monitor clipping.

The VOD page supports:

- Twitch VOD analysis
- local MP4 analysis
- hot block detection
- selected block export into clips

### Beginner guidance

Treat this as a second-phase feature after you confirm the live monitor flow.

### Advanced guidance

If you already know the app, this is one of the stronger power workflows in the product.

## 10. Settings

Use the settings page to manage:

- integrations
- routing
- account connections
- upload-related options
- license/trial status

### What is usually required

- Twitch connection

### What is often optional

- Google
- Discord
- destination-specific routing
- TikTok / Instagram paths

## 11. Dashboards

Cliprr has several dashboards.

### User dashboard

Use this for general activity and workflow visibility.

### Learning dashboard

Use this if you want to inspect or apply Cliprr’s learning-related rules and previews.

This is more advanced than the basic monitor flow.

### Admin dashboard

In the current local build, this acts as an internal operations panel for queue, metrics, test mode, and related tools.

## 12. Common issues

### Backend fails to start

If the app says the backend could not be started:

- close Cliprr completely
- relaunch the installed app, not the installer
- if it still fails, check local backend logs

### Twitch setup seems incomplete

Make sure you finished both:

- app credentials
- auth flow

### Google is not connected

That only blocks Google-related workflows. It should not stop the rest of the app from being usable.

### The app feels too advanced at first

That is normal. Start with:

1. setup
2. one monitor
3. one processed clip
4. library review

Then move into thresholds, AutoPilot, VOD, learning, and routing.

## 13. Recommended first test

If you are trialing Cliprr for the first time, do this in order:

1. complete setup
2. connect Twitch
3. save one starter channel
4. start one live monitor
5. confirm Cliprr produces at least one clip job/output
6. review the result in the library
7. then try VOD/longform tools
