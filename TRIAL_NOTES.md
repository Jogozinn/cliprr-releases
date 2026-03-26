# Cliprr Trial Notes

This file is for current testers and early users.

## Trial phase goal

The goal of the trial is to confirm that Cliprr’s real workflows hold up in normal use:

- setup
- monitoring
- triggering
- processing
- review
- longform clipping

This is not a UI-only beta. The important thing is whether the workflows behave reliably.

## What to focus on first

Please test these first:

1. first-time setup
2. Twitch connection
3. starter channel save/load
4. live monitor startup
5. clip processing pipeline
6. library visibility of saved outputs
7. VOD / longform flow

## Areas that appear strongest right now

- guided setup
- live Twitch monitor
- queue-backed processing flow
- library/review
- VOD analysis and clip generation
- Discord and Google as optional add-ons rather than blockers

## Areas that still need careful feedback

- confidence and threshold tuning clarity
- AutoPilot behavior and expectations
- learning dashboard understanding
- prompt approval/context workflows
- TikTok and Instagram paths
- advanced routing expectations

## What kind of feedback helps most

Please report:

- what you were trying to do
- what screen/page you were on
- what you expected
- what actually happened
- whether the issue was one-time or repeatable
- any relevant logs or screenshots

## Useful feedback examples

Good examples:

- “Setup saved Twitch values but did not reflect completion until restart.”
- “Monitor started, but no clip jobs appeared even though confidence spiked.”
- “VOD analysis found blocks, but generation failed at export.”
- “Library shows the clip but title/result metadata looks wrong.”

Less useful examples:

- “It feels weird.”
- “The app is broken.”

## What is optional during trial

You do not need to test every destination or advanced system immediately.

It is fine to skip:

- Google if you are not testing Drive/YouTube flows
- Discord if you are not testing delivery
- TikTok/Instagram if you are focused on the core product loop

## Known product reality during trial

Cliprr v1 already contains advanced systems, but the simplest success path is still:

1. connect Twitch
2. monitor a channel
3. process clips
4. review results

If that path is not solid, that matters more than whether an advanced settings edge case looks polished.

## Logs and local debug locations

If startup or backend issues happen, the most useful local files are usually under:

- `%APPDATA%\\Cliprr\\`
- `%APPDATA%\\Cliprr\\logs\\`

Common useful files:

- `backend.log`
- settings and local runtime state under the Cliprr app-data folder

## What not to assume

- Google is not required for first use
- Discord is not required for first use
- Not every advanced screen is meant to be a beginner entry point
- The installer EXE is not the normal launcher after install

## Best trial pass checklist

If you only have a short testing window, use this:

1. install the packaged app
2. launch the installed app
3. register/login
4. complete required setup
5. start a monitor
6. confirm a clip is triggered and processed
7. confirm it appears in the library
8. try one VOD/longform run
9. report anything that breaks, hangs, or silently fails
