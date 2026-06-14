# Shift Planner

Turns a flat agent roster into a visual coverage plan that shows who works when, where staffing falls short of target, and which assignments breach working-time rules — across markets, operations and a multi-week horizon — catching gaps and breaches while you edit instead of after the rota is published.

**[Live demo](https://sebastianvalenza.github.io/shift-planner/)** · runs instantly on a ready-made roster, or upload your own.

---

## The problem it solves

Coverage for a large multi-market support team was planned in a shared spreadsheet plus a paid scheduling tool. Building a week meant dragging names into cells by hand, then eyeballing whether every shift had enough people, whether anyone was rostered too many days in a row, and whether someone finished a night shift and started again the next morning. Gaps and rule breaches only surfaced *after* the schedule was published, and a bulk change — move ten people to mornings next week — meant editing one agent at a time.

Shift Planner loads the roster and makes the answer to *is the shift covered?* visible at the moment of editing, with every working-time breach flagged inline as it happens.

## What's inside

- **Coverage** — the working view, with a `Week · Day · Month` granularity toggle. The week grid shows every agent across seven days; each day header carries a per-shift coverage count (🌅 morning / 🌆 afternoon / 🌙 night) that turns red the moment staffing drops below target. Click any cell to reassign a shift. Day zooms into a single date with target-versus-assigned per shift; Month is a heatmap of coverage against target across the whole horizon.
- **Schedule** — bulk assignment. Select any number of agents (or every agent matching the current filter), pick a shift and the weekdays, and apply across all four weeks at once. Conflicts the change creates are reported, never silently blocked.
- **Workload** — a per-agent balance sheet: days worked, rest days, hours, minimum gap between consecutive shifts, and a traffic-light on each working-time rule.
- **Analysis** — the management read: coverage %, gap-hours, days with gaps, how evenly the load is shared, and rule breaches, with coverage-versus-target and daily-gap charts.

Three working-time rules are checked live as you edit — at most five working days in any rolling seven, at least twelve hours between consecutive shifts, and one shift per day. Breaches surface with an inline flag and a plain-language reason; the planner advises rather than locks you out, because the person building the rota needs to see the trade-off, not be stopped by it.

## Use your own data

The planner opens on a ready-made roster — 48 agents across 4 operations, 10 markets, 3 shifts and 4 weeks — usable on first load with nothing to configure, with a few coverage gaps and rule breaches deliberately left in so the validation is visible at a glance. To plan a real team, the **column-mapping uploader** takes an exported roster (agent, date and shift, with market and operation optional) and maps it in. Filters for operation, market, shift and agent combine and persist in the URL, so a filtered view can be shared or bookmarked; everything you change is saved locally and survives a refresh, and one click resets to the original roster. Nothing leaves the browser.

## Part of an operations ecosystem

Shift Planner is one of five control surfaces for a single multi-hub operation, built to follow one decision down the whole chain — *from the shift being covered to the cash being collected*:

| Stage | Tool | The question it answers |
|---|---|---|
| **Capacity** | **Shift Planner** *(this tool)* | **Is the shift covered?** |
| Workflow | [Ticket Triage](https://github.com/Sebastianvalenza/ticket-triage) | Who takes what, without collisions? |
| Productivity | [Performance Tracker](https://github.com/Sebastianvalenza/performance-tracker) | Is the team performing? |
| Revenue | [Revenue Cockpit](https://github.com/Sebastianvalenza/revenue-cockpit) | Are we going to make the number? |
| Cash | [AR Cockpit](https://github.com/Sebastianvalenza/ar-cockpit) | Did the money actually land? |

All five run on the same four hubs (Madrid 🇪🇸 · Berlin 🇩🇪 · Warsaw 🇵🇱 · Dublin 🇮🇪), the same ten markets, the same seed and the same visual system — one company seen from five functions. The hubs are the same operating centres throughout: the Berlin that books deals in Revenue Cockpit is the Berlin whose support floor this tool staffs. The roster here is the same 48-agent population the Performance Tracker scores and the Ticket Triage queue assigns — staff a shift in this tool and you are staffing the people those tools measure. Same world, different layer of the business.

## Stack

Single-file `index.html` — no backend, no build step, no framework — deployable to GitHub Pages as-is. Vanilla JavaScript for the roster model and live rule-checking, Chart.js for the coverage and gap-trend visualizations, PapaParse for CSV parsing and column detection. A seeded generator (`mulberry32`) produces the demo roster, so the sample data is identical on every load. State persists to local storage; dark and light themes, persisted locally. Fully client-side — no credentials, no roster data leaving the page.

## Notes

All data is synthetic. No real agents, schedules or company names appear anywhere in this repository. Names, markets and figures are randomly generated for demonstration.

---

*[linkedin.com/in/sebastianvalenza](https://linkedin.com/in/sebastianvalenza)*
