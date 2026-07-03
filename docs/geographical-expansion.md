# TravelMate — Geographical Expansion Plan

## Current Coverage
TravelMate currently supports public transit navigation within a single metropolitan area, covering bus, metro, and suburban rail networks.

---

## Expansion Strategy

TravelMate is built on open GTFS (General Transit Feed Specification) data standards, which most city transport authorities publish. This makes it technically straightforward to onboard any new city that provides GTFS feeds.

### Phase 1 — Neighbouring Cities
Expand to nearby cities and towns that share commuter overlap with the current coverage area, integrating their local bus and rail GTFS data.

### Phase 2 — Major Indian Cities
Onboard other major Indian cities that have published GTFS feeds and well-established metro or bus rapid transit networks (e.g., Bengaluru, Chennai, Pune, Mumbai, Delhi).

### Phase 3 — Pan-India Coverage
Partner with state transport corporations and civic tech communities across India to integrate regional bus networks, suburban rail, and upcoming metro projects.

### Phase 4 — International Expansion
Extend to cities globally that publish open GTFS data, with community contributors maintaining local transit data and translations.

---

## How Expansion Works

1. **Obtain GTFS data** — from the city's transport authority or open data portal
2. **Run the data pipeline** — process GTFS feeds using built-in scripts (`npm run process:all`)
3. **Add local language support** — translate UI strings and station names
4. **Test routing** — verify routes, stops, fares, and transfers locally
5. **Release** — deploy updated PWA and APK with new city support

---

## User Onboarding for New Cities

- **PWA** — accessible instantly via browser, no installation needed
- **APK** — distributed via F-Droid and direct download, no app store required
- **Community outreach** — engage local civic tech groups, college communities, and transit advocacy groups
- **Open source** — local contributors can independently add and maintain their city's data

---

## Key Advantage

Because TravelMate requires no backend server for routing (all computation is on-device), adding a new city does not increase infrastructure costs — making expansion low-cost and scalable.
