# AWS Student Community Day — IGDTUW

A single-file HTML prototype for a one-day AWS Cloud Club event at IGDTUW: a programme of talks and workshops, session detail pages, a 3-step registration flow, a personal "My day" schedule, and a resources page.

This is a front-end-only prototype. There is no backend or server — everything runs in the browser off an in-file dataset.

## Files

- `aws-community-day.html` — the entire app (markup, styles, and JavaScript in one file)

## Running it

Open `aws-community-day.html` directly in any modern browser. No build step, no server, no dependencies to install.

## Views

- **Home** — masthead with the day's status, a full time-ordered rail of the schedule, and three featured sessions
- **Programme** (`Events`) — all sessions as colour-coded cards, searchable and filterable by format (Talk / Workshop / Panel / Networking)
- **Session detail** — overview, takeaways, and what to bring for a single session, plus star / calendar actions
- **Register** — 3-step form (details → interests → review) with inline validation
- **My day** — appears after registering: a ticket stub, live countdown to the event, and a personal schedule built from starred sessions
- **Resources** — recordings, workshop code, learning paths, and certificate; locked until the event start date

## Data & state

- Session content (`SESSIONS`) and the fixed schedule blocks (`FIXED`) are hardcoded at the top of the `<script>` block — edit them there to change the programme.
- User state (registration details, starred sessions, registered flag) is persisted to `localStorage` under the key `ascd_state`, so it survives a page reload but is local to one browser.
- `EVENT_DATE` / `EVENT_END` control the live countdown and the upcoming/live/past status shown across the site.

## Calendar downloads

The "Add to calendar" (.ics) buttons call `claude.use('downloads')`, a capability only available when this file is opened as a **published Claude artifact**. Opened as a plain local file, `claude` is undefined and those two buttons will fail silently — everything else works normally. Ask if you'd like this swapped for a plain `Blob` + `<a download>` so it works outside the artifact viewer too.

## Design notes

Palette, typography and layout were built specifically for this brief rather than using generic SaaS-dashboard defaults — see the design rationale in the conversation this file came from if you want the reasoning behind specific choices (colour system, the schedule rail, the ticket-stub dashboard card, etc).
