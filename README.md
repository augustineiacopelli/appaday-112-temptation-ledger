# AppADay 112 - Temptation Ledger

Part of [AppADay](https://augustineiacopelli.github.io/appaday/), a daily discipline project by Augustine Iacopelli: one complete, functional, mobile-friendly web app shipped every day.

## What it does

A private accountability ledger for the moment a temptation hits. Name the trigger or site pulling at you and a short reason it feels pressing, then sit through a sixty-second pause that redisplays the reason while it counts down. Once the pause expires you choose honestly: close and hold, or proceed anyway. The choice writes one entry to the ledger and the screen resets to a blank page. A streak of consecutive held entries sits at the top, and an Insights section turns the accumulated history into a held-vs-yielded ratio, a 14-day trend, a ranked breakdown by trigger or site, and a time-of-day pattern, so the shape of the struggle becomes visible over time instead of staying anecdotal.

## How it works

The pause is timestamp-based rather than a simple tick counter, so it stays accurate even if the tab loses focus or the device sleeps: the countdown and its SVG ring are both computed from the difference between now and a stored end time, checked every 250ms. The proceed and close buttons stay disabled until that difference reaches zero. There is no separate streak variable in storage; the streak, and every chart in Insights, is recomputed fresh from the history array on every render, the same pattern the project uses elsewhere to avoid state drifting out of sync with the log. All four visualizations are hand-built, two as proportional HTML bars and two as inline SVG bar charts, with no charting library involved.

## Tech

Single self-contained `index.html`. No frameworks, no build step, no external dependencies beyond Google Fonts. All data lives in one `localStorage` key, read and written inside try/catch. Not AI-powered; no API calls are made.

## Category

Productivity (P)

## Live

https://augustineiacopelli.github.io/appaday-112-temptation-ledger/
