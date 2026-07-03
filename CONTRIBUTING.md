# Contributing to TravelMate

Thank you for your interest in contributing to TravelMate! This document outlines how to get started, report issues, and submit changes.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Ways to Contribute](#ways-to-contribute)
- [Getting Started](#getting-started)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)
- [Development Workflow](#development-workflow)
- [Commit Message Guidelines](#commit-message-guidelines)
- [Submitting a Merge Request](#submitting-a-merge-request)
- [Code Style](#code-style)
- [Adding Transit Data](#adding-transit-data)
- [Adding Translations](#adding-translations)

---

## Code of Conduct

Be respectful, inclusive, and constructive. Harassment or discrimination of any kind will not be tolerated.

---

## Ways to Contribute

- Report a bug
- Suggest a new feature or improvement
- Fix an existing issue
- Improve documentation
- Add or correct transit data (routes, stops, fares)
- Add translations for new languages

---

## Getting Started

1. Fork the repository on GitLab
2. Clone your fork locally
3. Set up the development environment:

```bash
cd frontend
npm install
npm run dev
# App runs at http://localhost:3000
```

4. Create a new branch for your change (see [Development Workflow](#development-workflow))
5. Make your changes, test them, and submit a Merge Request

---

## Reporting Bugs

Open an issue on the GitLab repository:
**`https://code.swecha.org/CivicTech/manaprayanam/-/issues`**

Include:
- A clear title describing the problem
- Steps to reproduce
- Expected vs actual behaviour
- Device and browser/OS version
- Screenshots if applicable

---

## Suggesting Features

Open an issue with the label `enhancement`. Describe:
- What problem it solves
- Who benefits from it
- Any implementation ideas you have

---

## Development Workflow

### Branch Naming

| Type | Format | Example |
|------|--------|---------|
| Bug fix | `fix/short-description` | `fix/metro-transfer-crash` |
| Feature | `feat/short-description` | `feat/night-bus-filter` |
| Data update | `data/short-description` | `data/update-bus-routes` |
| Documentation | `docs/short-description` | `docs/update-readme` |

### Steps

1. Always branch off from `main`
2. Keep your branch focused on a single change
3. Test on both web (PWA) and Android if your change affects UI or routing
4. Run a build before submitting to catch errors:

```bash
cd frontend
npm run build
```

---

## Commit Message Guidelines

Use the format: `type: short description`

| Type | When to use |
|------|-------------|
| `fix` | Bug fix |
| `feat` | New feature |
| `data` | Transit data update |
| `docs` | Documentation change |
| `refactor` | Code restructure, no behaviour change |
| `style` | CSS or UI-only changes |
| `chore` | Build, config, or dependency updates |

**Examples:**
```
fix: correct MMTS fare calculation for long routes
feat: add night bus filter to route strategies
data: update bus routes with June 2025 GTFS feed
docs: add CONTRIBUTING.md
```

---

## Submitting a Merge Request

1. Push your branch to your fork
2. Open a Merge Request against the `main` branch of the main repository
3. Fill in the MR description:
   - What change does this MR make?
   - Why is it needed?
   - How was it tested?
   - Reference the related issue number (e.g. `Closes #42`)
4. Wait for review — a maintainer will respond within a few days

---

## Code Style

- **React components** — functional components with hooks only; no class components
- **CSS** — plain CSS per component; no inline styles for layout
- **Naming** — camelCase for variables/functions, PascalCase for components
- **No unused imports** — clean up before submitting
- **No console.log** — remove debug logs before submitting
- **Keep it simple** — avoid adding abstractions or dependencies beyond what the task requires

---

## Adding Transit Data

To update or add transit data for a city or mode:

1. Place GTFS `.txt` files in the appropriate folder:
   - `data/bus_data/` for bus routes
   - `data/metro_data/` for metro
   - `data/mmts_data/` for MMTS
2. Run the pipeline:

```bash
# From repo root
npm run process:all
```

3. Verify the output JSON files in `frontend/src/data/`
4. Test routing with the new data before submitting

---

## Adding Translations

Translation files are in `frontend/src/translations/`:

- `en.js` — English strings
- `te.js` — Telugu strings
- `stationNames.js` — bilingual station name mappings

To add a new language:
1. Copy `en.js` and rename it (e.g. `hi.js` for Hindi)
2. Translate all string values — do not change the keys
3. Register the new language in `frontend/src/contexts/LanguageContext.jsx`
4. Add station name mappings to `stationNames.js` where applicable

---

## License

By contributing, you agree that your contributions will be licensed under the same **GPL-3.0-only** license as this project.
