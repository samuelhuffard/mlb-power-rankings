# MLB Power Rankings

A weekly MLB power-rankings site with a custom scoring model, backed by a Google Sheet instead of a database.

Every Sunday, a scheduled job pulls fresh standings, hitting, and pitching data from the MLB Stats API, runs it through a weighted scoring model (FIP, WAR, strength of schedule, and park-adjusted splits), and writes the results straight into a Google Sheet. This site reads that sheet and renders it.

## Features

- **Power rankings** for all 30 teams, with a full score breakdown per team (not just a final number — the components that produced it)
- **AI-generated verdicts** — a short, Claude-written take on each team's ranking, cached for a week so it doesn't regenerate on every page load
- **Series predictor** — matchup analysis and a projected outcome for a team's next series
- **Team roster views** with individual player stats

## Why a spreadsheet

The scoring model and the site are two different programs (a Node scheduler and this Next.js app) that need to agree on the same data without talking to each other directly. A Google Sheet is a free, human-readable system of record — I can open it and sanity-check the raw numbers behind any ranking without touching code.

## Stack

Next.js 16, React 19, Tailwind, Google Sheets API, Anthropic Claude (for verdicts), MLB Stats API.
