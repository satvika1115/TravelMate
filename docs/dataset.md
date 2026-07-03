# TravelMate — Dataset Documentation

## Overview

TravelMate uses a combination of official open transit data and custom-created datasets. All raw data is processed through an in-house pipeline and stored as optimised JSON files for on-device routing — no backend server required.

---

## Datasets

### 1. Bus Routes & Stops (`frontend/src/data/bus.json`)

| Field | Description |
|-------|-------------|
| Source | TSRTC (Telangana State Road Transport Corporation) GTFS feed |
| Coverage | 1,099 bus routes · 3,676 stops |
| Fields | Route ID, route name, stop ID, stop name, stop coordinates, stop sequence |
| Processing | Generated via `scripts/processBusGTFS.js` from raw GTFS `.txt` files |
| Uniqueness | Preprocessed and indexed for O(1) direct route lookup and transfer planning |

---

### 2. Metro Lines & Stations (`frontend/src/data/metro.json`)

| Field | Description |
|-------|-------------|
| Source | Hyderabad Metro Rail GTFS feed |
| Coverage | 3 lines (Red, Green, Blue) · 57 stations |
| Fields | Line ID, station ID, station name, coordinates, GTFS shape polylines |
| Processing | Generated via `scripts/processMetroGTFS.js` |
| Uniqueness | Includes GTFS shape polylines for accurate curved route rendering on map |

---

### 3. MMTS Suburban Rail (`frontend/src/data/mmts.json`)

| Field | Description |
|-------|-------------|
| Source | MMTS (Multi-Modal Transport System) GTFS feed |
| Coverage | 20 corridors · 54 stations |
| Fields | Corridor ID, station ID, station name, coordinates, stop sequence |
| Processing | Generated via `scripts/processMmtsGTFS.js` |
| Uniqueness | Integrated into multimodal routing alongside bus and metro |

---

### 4. Fare Tables (`frontend/src/data/fares.json`)

| Field | Description |
|-------|-------------|
| Source | Official fare structures from TSRTC, Hyderabad Metro, and MMTS |
| Fields | Mode, distance slabs, base fare, per-km rate |
| Uniqueness | Custom-compiled fare table covering all three transit modes for fare estimation |

---

### 5. Bilingual Station Name Mappings (`frontend/src/translations/stationNames.js`)

| Field | Description |
|-------|-------------|
| Source | Original — manually curated by the TravelMate team |
| Coverage | 180+ station names across Bus, Metro, and MMTS |
| Fields | English name, Telugu (తెలుగు) transliteration |
| Uniqueness | Fully original dataset created for this project; not available elsewhere |

---

### 6. Safety Risk Zones (`frontend/src/data/riskAreas.json`)

| Field | Description |
|-------|-------------|
| Source | Curated from public safety reports and civic data |
| Fields | Zone name, coordinates (lat/lon boundaries), risk level |
| Uniqueness | Custom dataset mapping risk zones for commuter safety alerts along routes |

---

### 7. Hyderabad Area Zone Definitions (`frontend/src/data/hyderabadAreas.js`)

| Field | Description |
|-------|-------------|
| Source | Original — created by the TravelMate team |
| Fields | Area name, coordinates, mobility score, metro access score, bus coverage score, safety score, traffic score |
| Uniqueness | Original neighbourhood-level scoring dataset used for the analytics dashboard and transit desert identification |

---

## Data Pipeline

Raw GTFS data is processed using Node.js scripts located in `scripts/`:

```bash
npm run process:all     # regenerate all datasets
npm run process:bus     # bus only
npm run process:metro   # metro only
npm run process:mmts    # MMTS only
```

Place raw GTFS `.txt` files in:
- `data/bus_data/` for bus
- `data/metro_data/` for metro
- `data/mmts_data/` for MMTS

---

## Dataset Quality Summary

| Dataset | Unique | Relevant | Documented |
|---------|--------|----------|------------|
| Bus routes & stops | Processed form is unique | Yes | Yes |
| Metro lines & stations | Processed form is unique | Yes | Yes |
| MMTS corridors | Processed form is unique | Yes | Yes |
| Fare tables | Yes — custom compiled | Yes | Yes |
| Bilingual station names | Yes — original creation | Yes | Yes |
| Safety risk zones | Yes — custom curated | Yes | Yes |
| Area zone definitions | Yes — original creation | Yes | Yes |
