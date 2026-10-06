# New Construction Explorer — data + embed

- `communities.json` — single source of truth for every new-construction community on the explorer and the community cards. Updated by the nightly audit task, never by hand.
- `audit-log.json` — append-only log of material changes and fetch failures written by the nightly audit.
- `explorer.html` — MapLibre map + filterable cards. Embedded on https://thesteel.group/new-construction/ via iframe. Reads `communities.json` next to it (or `?data=<url>`).

Served from GitHub Pages: `https://justinsteel-agent.github.io/steel-group-dashboard/new-construction/`.

- `SHOT-LIST.md` — the 7 photo slots every community gets; `media.<slot>` in `communities.json` holds the URL once a mission delivers it.
- `call-rotation.json` — Justin's daily call list (5 neighborhoods/weekday, Horry + Georgetown County **South Carolina** only). The nightly audit advances `cursor` and creates the next day's SureSend task. Unverified entries are promoted into `communities.json` only after a call or a verified fetch.

Companion systems (not in this repo): SureSend tags `VENDOR-New Construction` + `BUILDER-<name>`, builder Company records, the "New Construction – On-Site Rep Intake" automation, and the Google Drive folder "New Construction Community Database (SC)" (sheet + per-community Handouts folders).

## Rules the audit must follow
1. Unknown is `null`, rendered as "Awaiting data". Never 0.
2. A failed fetch never overwrites a known value. Keep the value, keep `last_verified`, set `stale: true` once `last_verified` is more than 7 days old.
3. Material change = starting price moves ≥ $5,000, quick-move-in count changes, incentive appears/disappears, status changes, a plan is added/removed. Each goes to `audit-log.json` with date, community, field, old, new, source URL.
4. Sources in order: `sources.primary` (NewHomeSource community page), then `sources.builder`. Add new communities only when they have ~10+ homesites or active future phases.
5. Card actions are the only outbound links: the community guide on thesteel.group and its tour form. No builder links, no directions.

6. Media slots are filled only from mission uploads (see SHOT-LIST.md). Never fill a slot with a stock or builder photo.
