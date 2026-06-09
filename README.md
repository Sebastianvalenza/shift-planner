# Shift Planner (demo below)

A visual shift-coverage planner that turns a flat agent roster into a filterable view of who works when, where coverage falls short of target, and which assignments breach working-time rules — across markets, operations and a multi-week horizon.

## The Problem

Coverage for a large multi-market support team was planned in a shared spreadsheet and a paid scheduling tool. Building a week meant dragging names into cells by hand, then eyeballing whether every shift had enough people, whether anyone was rostered for too many days in a row, and whether someone finished a night shift and started again the next morning. Gaps and rule breaches were only caught after the schedule was published, and bulk changes — move ten people to mornings next week — meant editing one agent at a time.

## The Solution

Shift Planner loads the roster and presents it as an interactive planner with four views:

- **Coverage** — the working view, with a `Week · Day · Month` granularity toggle. The week grid shows every agent across seven days; each day header carries a per-shift coverage count (🌅 morning / 🌆 afternoon / 🌙 night) that turns red the moment staffing drops below target. Click any cell to reassign that agent's shift. Day zooms into a single date with target-versus-assigned per shift; Month is a heatmap of coverage against target across the whole horizon.
- **Schedule** — bulk assignment. Select any number of agents (or every agent matching the current filter), pick a shift and the weekdays, and apply across all four weeks at once. Conflicts the change creates are reported, never silently blocked.
- **Workload** — a per-agent balance sheet: days worked, rest days, hours, minimum gap between consecutive shifts, and a traffic-light on each working-time rule.
- **Analysis** — the management read: coverage %, gap-hours, days with gaps, how evenly the load is shared, and rule breaches, with coverage-versus-target and daily-gap charts.

Three working-time rules are checked live as you edit — at most five working days in any rolling seven, at least twelve hours between consecutive shifts, and one shift per day. Breaches are surfaced with an inline flag and a plain-language reason; the planner advises rather than locks you out, because the person building the rota needs to see the trade-off, not be stopped by it.

Filters for operation, market, shift and agent combine and persist in the URL, so a filtered view can be shared or bookmarked. Everything you change is saved locally and survives a refresh; one click resets to the original roster.

The planner opens on a ready-made roster — 48 agents across 4 operations, 10 markets, 3 shifts and 4 weeks — so it is usable on first load with nothing to configure, with a few coverage gaps and rule breaches deliberately left in so the validation is visible at a glance. To plan a real team, the column-mapping uploader takes an exported roster (agent, date and shift, with market and operation optional) and maps it in.

## Stack

- Vanilla **HTML + CSS + JavaScript** in a single file — no build step, no framework, no dependencies to install
- **Chart.js** for the coverage and gap-trend visualizations
- **PapaParse** for CSV parsing and automatic column detection on upload
- A seeded random generator produces the demo roster, so the sample data is identical on every load
- Runs entirely in the browser — static hosting on GitHub Pages, no backend, no credentials, and no roster data ever leaves the page

The demo roster — its agents, operations, markets and seed — is shared with the [VIP Performance Tracker](https://github.com/Sebastianvalenza/vip-performance-tracker), so an agent is the same person across both tools: two halves of one operations toolkit.

## Demo

**Live:** https://sebastianvalenza.github.io/shift-planner/

## Impact

Replaced a manual scheduling spreadsheet and a paid rota tool with a single self-serve planner — surfacing coverage gaps and working-time breaches at the moment of editing instead of after publishing, and turning a per-agent dragging exercise into one bulk action across markets and weeks.
