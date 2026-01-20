# MusicPlatformInsights

Cross-platform analysis of personal music listening behavior, integrating Spotify and Apple Music data into a unified event-level model to study engagement patterns, habit consistency, preference diversity, and discovery behavior through interpretable KPIs and Power BI visualization.

---

## Status

## In Progress

Spotify and Apple Music listening history has been ingested, normalized into a canonical event schema, sessionized, and stored in a unified SQLite database. Apple Music artist metadata has been partially enriched using library data. KPI modeling and dashboard development are in progress.

---

## Overview

MusicPlatformInsights is a user behavior analytics project that studies how individuals engage with music over time across multiple streaming platforms. Rather than treating listening activity as a collection of isolated plays, the project frames music consumption as a **behavioral pattern problem**, emphasizing listening habits, session behavior, and preference formation.

Listening history from Spotify and Apple Music is ingested from raw user exports, normalized into a shared event-level schema, and stored in a single SQLite database. From this foundation, a set of interpretable KPIs is derived to summarize engagement intensity, consistency, and discovery dynamics. Insights are delivered through a narrative-style Power BI dashboard inspired by consumer product analytics rather than traditional BI reporting.

---

## Analytical Objectives

The primary objectives of the project are to:

- Normalize heterogeneous streaming data into a single, platform-agnostic event model  
- Summarize individual-level listening behavior over time  
- Identify engagement patterns beyond simple top-N summaries  
- Compare listening habits across platforms within a unified framework  
- Translate raw event data into intuitive, user-facing insights  

The emphasis is on **clarity, interpretability, and storytelling**, not algorithmic complexity.

---

## Canonical Listening Event Model

All listening data is mapped into a standardized event-level schema shared across platforms.

Each row represents a single listening event and includes:

- `event_time`: Timestamp of the listening event (UTC)  
- `platform`: Source platform (`spotify`, `apple_music`)  
- `artist`: Artist name (best-effort for Apple Music)  
- `track`: Track name  
- `duration_minutes`: Minutes listened during the event  
- `session_id`: Derived identifier grouping events into listening sessions  

This schema is intentionally minimal and designed to support behavioral analysis rather than perfect metadata reconciliation.

---

## Data Ingestion & Normalization

### Spotify

- Listening history ingested from exported Spotify Streaming History JSON files  
- Timestamps localized to the user’s local timezone and converted to UTC  
- Play durations converted from milliseconds to minutes  
- Very short plays filtered using a minimum duration threshold  
- Session IDs generated based on inactivity gaps  

### Apple Music

- Listening history ingested from Apple Music Play Activity CSV exports  
- Timestamps parsed and normalized to UTC  
- Play durations converted from milliseconds to minutes  
- Session IDs generated using the same logic as Spotify  
- Artist metadata partially enriched via a left join with the Apple Music Library Tracks export  

Due to Apple Music data limitations, some events (e.g. radio, autoplay, editorial content) do not resolve to library tracks and remain unmatched. This behavior is expected and documented.

---

## KPI Definitions

KPIs are defined conceptually and derived exclusively from the normalized event table.

Core metrics include:

- **Total Listening Time**: Sum of minutes listened over the analysis window  
- **Active Day**: Any calendar day with at least one listening event  
- **Active Week**: Any calendar week with at least one listening event  
- **Listening Session**: A sequence of events separated by no more than a fixed inactivity threshold  
- **Session Length**: Total listening time within a session  
- **Discovery Event**: First-time listen to an artist  
- **Repeat Listening Rate**: Share of listening attributed to previously encountered artists  

Definitions are designed to remain stable across platforms.

---

## Data Storage

All normalized listening events are stored in a single SQLite database:

- Database: `MusicPlatformInsights.db`  
- Table: `listening_events`  

Spotify events initialize the table. Apple Music events are appended after enrichment, replacing prior Apple rows to avoid duplication.

---

## Visualization

Insights are delivered through a **Power BI dashboard** designed as a year-in-review style experience rather than an operational report.

Planned dashboard views include:

- High-level listening summaries  
- Engagement and habit consistency metrics  
- Session behavior and listening intensity  
- Preference concentration and diversity  
- Discovery versus repeat listening behavior  
- Cross-platform comparison insights  

The dashboard prioritizes narrative flow and interpretability over exhaustive filtering.

---

## Project Structure

```
MusicPlatformInsights/
├── notebooks/
│ ├── LoadSpotifyData.ipynb
│ ├── LoadAppleData.ipynb
│ ├── AddAppleArtists.ipynb
├── data/
│ ├── raw/
│ ├── processed/
├── dashboards/
├── docs/
│ ├── canonical_schema.md
│ ├── kpi_definitions.md
├── README.md
```

---

## Planned Work

Next steps include:

- Implementing KPI calculations on the unified event table  
- Validating session-level and longitudinal metrics  
- Building and publishing the Power BI dashboard  
- Refining cross-platform comparison insights  
- Optional v2 enrichment for Apple Music metadata  

---

## Why This Project

While centered on personal music data, this project mirrors real-world analytics problems such as multi-source data integration, behavioral modeling, KPI design, and insight communication. The focus is on transforming raw event data into meaningful, user-facing insights, reflecting how modern consumer products use analytics to understand and communicate user behavior.
