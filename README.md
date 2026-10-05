# CareerGhana internship tasks
Built by Christian Tetteh for his role as a full stack developer intern at CareerGhana.

Three full-stack web apps, each live, tested and documented. Each one has its own folder with its own README, and every folder keeps its full commit history from the original repo.

| Project | What it does | Live demo | Code | Video |
|---|---|---|---|---|
| **Tally** | Splits shared costs between friends. Private tabs, and nothing counts until the person charged agrees. Ghana cedis by default, US dollars optional. | [tally-splitter.vercel.app](https://tally-splitter.vercel.app) | [`tally/`](tally) | [1:50](demo-videos/tally-demo.mp4) |
| **MentorSlot** | Books sessions with mentors by field. Live availability, no double bookings, and no account needed: each booking gets a private link to view or cancel it. | [mentorslot.vercel.app](https://mentorslot.vercel.app) | [`mentorslot/`](mentorslot) | [1:46](demo-videos/mentorslot-demo.mp4) |
| **Sinew** | Tracks daily steps, water and sleep against your own goals, with a daily effort score, a weekly chart and week-on-week insights. | [sinew-fitness-tracker-7xgk.vercel.app](https://sinew-fitness-tracker-7xgk.vercel.app) | [`sinew/`](sinew) | [1:53](demo-videos/sinew-demo.mp4) |

The backends run on Render's free tier, so the first request after a quiet spell can take about 30 seconds while the server wakes up.

## Stack

All three use the same stack: a **React + Vite** frontend on **Vercel**, a **Node.js / Express** API on **Render**, and **PostgreSQL** (Render Postgres for Tally, Supabase for MentorSlot and Sinew).

## Highlights

| | Tally | MentorSlot | Sinew |
|---|---|---|---|
| Accounts | Email + password (scrypt), HttpOnly session cookie, password reset by email | None by design: signed private link per booking | Email + password (bcrypt), JWT |
| Data integrity | Integer pesewas/cents, row lock per tab, consent for every charge and payment | Database exclusion constraint makes overlapping bookings impossible | Per-user lock keeps daily totals within limits |
| Privacy | Tabs are invite-only; outsiders get the same "not found" as a missing tab | Lookup emails links and never reveals whether an address has bookings | Every query is scoped to the signed-in user |
| Automated tests | 131 backend + 34-step browser run | 208 | 127 |

## Repository layout

```
careerghana_tasks/
├── tally/          expense splitter   (backend/, frontend/, e2e/, README.md, TESTING.md)
├── mentorslot/     mentor booking     (backend/, frontend/, e2e/, README.md)
├── sinew/          fitness tracker    (backend/, frontend/, e2e/, README.md)
└── demo-videos/    a short captioned walkthrough of each app
```

To run a project locally, follow the "Running it locally" or "Set up the database" steps in that project's README. Each needs Node 18+ and a PostgreSQL database; secrets go in a local `.env` (a `.env.example` in each `backend/` lists them) and are never committed.

## Where the live apps deploy from

The live sites are built from the original per-project repos, which stay in place:
[expense-splitter](https://github.com/ChristianTetteh/expense-splitter) ·
[mentorslot](https://github.com/ChristianTetteh/mentorslot) ·
[sinew-fitness-tracker](https://github.com/ChristianTetteh/sinew-fitness-tracker).
This repository collects the same code, with the same history, for review.
