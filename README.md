# Steam Game Engagement Analysis
### What makes players keep coming back to a Steam game?

---

## Problem Statement

Steam has a lot of games in their storefront. But the general pattern is that players will most likely spend some time with a specific game, then move on towards the next. However, there are games that break this pattern wherein no matter how old the game is, they are still playing that game.

This project investigates what separates games with lasting player communities from those that spike and die, using publicly available data from Steam and third-party sources.

---

## Research Question

> **What game characteristics are most associated with high sustained player engagement on Steam?**

"Sustained engagement" is measured using two complementary signals:

- **Active engagement rate** — the ratio of current concurrent users (`ccu`) to estimated total owners. A game with 1M owners and 50K active players right now is retaining more of its audience than one with the same owners but only 1K active.
- **Retention drop-off** — for a curated subset of games, the ratio of average monthly players at the 6-month mark to their peak player count at launch, sourced from historical Steam Charts data. This captures how well a game holds its audience after the initial hype fades.

---

## Why This Matters

**Target audience:** Indie game developers and small studios deciding where to invest — genre, pricing, content update cadence, language support — when building or shipping a game on Steam.

---

## Data Sources

| Source | What it provides | Method |
|---|---|---|
| [SteamSpy API](https://steamspy.com/api.php) | Owner estimates, concurrent users, review counts, tags, genre, price, language count | REST API (free, no key required) |
| [Steam Store API](https://store.steampowered.com/api/appdetails) | Release date, description, supported platforms, Metacritic score, DLC count | REST API (free, no key required) |
| [Steam Charts](https://steamcharts.com) | Monthly average and peak player counts (historical, per game) | Web scraping (BeautifulSoup / requests) |

---

## Features (Planned)

These are the independent variables I plan to investigate:

- **Genre / Tags** — e.g., RPG, FPS, Survival, Multiplayer
- **Price** — free-to-play vs. paid, price tier
- **Review score** — positive review ratio
- **Number of supported languages** — proxy for localization investment
- **Release recency** — age of the game at time of data collection
- **Platform support** — Windows only vs. cross-platform
- **Metacritic score** — critic reception

---

## Project Scope

- **Dataset size:** Not sure. We'll see along the way
- **Filters:** Games only (excluding DLC, soundtracks, tools); minimum 500 owners to exclude abandoned/empty listings
- **Time of data collection:** Static snapshot collected during ingestion (not a live feed)
- **Exclusions:** Games with zero `ccu` and zero reviews will be flagged and reviewed before dropping. Only games published on steam will be covered.

---

