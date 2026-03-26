# Cliprr Technical Overview

This document is for developers, collaborators, and advanced testers who want a real map of the current Cliprr implementation.

## 1. Stack

Cliprr currently uses:

- Electron for the desktop shell
- React for the frontend UI
- FastAPI for the local backend
- local file storage plus a local database under the Cliprr user-data folder
- Electron Builder for packaging
- a packaged backend binary for Windows distribution

## 2. High-level runtime model

Cliprr is not a frontend-only app.

The current product is a local desktop application with three main runtime layers:

1. Electron main process
2. React renderer
3. local FastAPI backend

### Electron main process responsibilities

- startup flow
- backend launch
- preload bridge
- settings read/write bridge
- local trial/license gate
- packaged-path resolution

Key files:

- [main/main.js](./main/main.js)
- [main/preload.js](./main/preload.js)

### React frontend responsibilities

- auth UI
- first-time setup
- monitor workspace
- settings
- dashboards
- library
- VOD/longform screens

Key files:

- [frontend/cliprr/src/App.js](./frontend/cliprr/src/App.js)
- [frontend/cliprr/src/AppRouter.js](./frontend/cliprr/src/AppRouter.js)
- [frontend/cliprr/src/AuthContext.js](./frontend/cliprr/src/AuthContext.js)

### FastAPI backend responsibilities

- auth and user APIs
- monitoring
- queueing
- processing
- integrations
- dashboards/admin endpoints
- learning/title endpoints
- VOD/longform endpoints

Key file:

- [backend/main.py](./backend/main.py)

## 3. Frontend map

Main screens:

- [HomePage.js](./frontend/cliprr/src/HomePage.js)
- [LoginPage.js](./frontend/cliprr/src/LoginPage.js)
- [RegisterPage.js](./frontend/cliprr/src/RegisterPage.js)
- [SetupLitePage.js](./frontend/cliprr/src/SetupLitePage.js)
- [MainClipInterface.js](./frontend/cliprr/src/MainClipInterface.js)
- [SettingsPage.js](./frontend/cliprr/src/SettingsPage.js)
- [UserDashboard.js](./frontend/cliprr/src/UserDashboard.js)
- [LearningDashboard.js](./frontend/cliprr/src/LearningDashboard.js)
- [AdminDashboard.js](./frontend/cliprr/src/AdminDashboard.js)
- [LibraryPage.js](./frontend/cliprr/src/LibraryPage.js)
- [vodPage.js](./frontend/cliprr/src/vodPage.js)

## 4. Backend map

Important backend modules:

- [backend/main.py](./backend/main.py)
  - route layer
  - startup wiring
  - admin, monitor, longform, learning, auth, library, and integration endpoints

- [backend/clip_monitor.py](./backend/clip_monitor.py)
  - monitor bot logic
  - confidence/trigger handling

- [backend/process_pipeline.py](./backend/process_pipeline.py)
  - clip processing workflow
  - transcription/caption/title/upload handoff

- [backend/queue_manager.py](./backend/queue_manager.py)
  - job queue and persisted spool state

- [backend/longform_pipeline.py](./backend/longform_pipeline.py)
  - longform/VOD analysis and clip generation

- [backend/title_engine.py](./backend/title_engine.py)
- [backend/title_generator.py](./backend/title_generator.py)
- [backend/title_llm.py](./backend/title_llm.py)
  - title generation and related title context logic

- [backend/upload_routing.py](./backend/upload_routing.py)
  - routing decisions for destinations/accounts

- [backend/google_drive_utils.py](./backend/google_drive_utils.py)
  - Google Drive and related Google upload logic

- [backend/autopilot.py](./backend/autopilot.py)
  - favorites/watch automation behavior

- [backend/license.py](./backend/license.py)
  - backend-side license verification hooks

## 5. Startup flow

Current packaged startup flow:

1. Electron starts
2. user-data paths are set
3. main window is created hidden
4. backend is launched
5. Electron waits for backend health
6. local trial/license gate runs
7. tokens are reloaded/refreshed
8. window is shown

The app is intentionally backend-backed even in desktop mode.

## 6. Auth and setup flow

### Auth

- login/register is handled through backend auth endpoints
- frontend stores access token in localStorage or sessionStorage
- `AuthContext` resolves `/auth/me` on startup

### Setup

The setup page is a guided checklist around:

- Twitch app credentials
- Twitch auth
- starter channel
- optional Google connection
- optional Discord webhook

## 7. Live monitor data flow

The main live path is:

1. frontend starts a monitor
2. backend monitor bot begins watching a streamer
3. confidence/trigger logic runs
4. clip jobs are created
5. jobs enter the queue/spool
6. processing pipeline handles clip output
7. logs, dashboards, and library reflect results

## 8. Longform / VOD flow

The longform path is separate from live monitoring:

1. user supplies a Twitch VOD or local MP4
2. backend analyzes the source
3. candidate blocks are returned
4. user selects blocks
5. backend generates clips from those selections
6. results are logged and surfaced back to the frontend

## 9. Storage model

Important runtime storage lives under the Cliprr user-data area.

That includes:

- settings
- database
- logs
- processed output data
- queue/spool data
- trial/license state

Electron also injects storage-related env vars so the backend reads and writes the right user-local locations in both dev and packaged builds.

## 10. Integrations

Current real integration areas:

- Twitch
- Google
- Discord
- TikTok
- Instagram

The first three are the clearest current product story.

TikTok and Instagram exist in code, but should be treated as more careful areas during trial.

## 11. Internal strengths that are easy to miss

- Cliprr has a real persisted queue/spool layer
- the app has a separate AutoPilot/watch system, not just a manual monitor screen
- title and learning flows are richer than a single “generate title” button
- the product includes both live and longform workflows

## 12. Trial/license model

The current model is a local desktop gating system with:

- trial state
- Gumroad verification
- local protected state
- Electron-enforced startup checks

This is hardened for MVP packaging, but it is still a local-first desktop model rather than a full server-side licensing platform.

## 13. Extension points

The cleanest extension points later are likely:

- monitor heuristics and trigger logic
- title generation/ranking
- upload routing rules
- learning/rule application
- dashboard metrics/logging
- setup and onboarding clarity

## 14. Current caution areas

Do not oversell these without more testing:

- TikTok upload reliability
- Instagram path maturity
- learning/prompt-context systems as beginner-facing features
- anything that assumes a full SaaS/cloud model
