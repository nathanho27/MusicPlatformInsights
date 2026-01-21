# MusicPlatformInsights

Cross-platform analysis of personal music listening behavior, integrating Spotify and Apple Music data into a unified event-level model to study engagement patterns, habit consistency, preference diversity, and discovery behavior through interpretable KPIs and Power BI visualization.

---

## Status

## In Progress

Spotify and Apple Music listening history has been ingested, normalized into a canonical event schema, sessionized, and stored in a unified SQLite database. Apple Music artist metadata has been partially enriched using library data. Core behavioral KPIs have been implemented and exported for dashboarding. Power BI dashboard development is in progress.

---

## Overview

MusicPlatformInsights is a user behavior analytics project that studies how individuals engage with music over time across multiple streaming platforms. Rather than treating listening activity as a collection of isolated plays, the project frames music consumption as a **behavioral pattern problem**, emphasizing listening habits, session behavior, and preference formation.

Listening history from Spotify and Apple Music is ingested from raw user exports, normalized into a shared event-level schema, and stored in a single SQLite database. From this foundation, a set of interpretable, behavior-focused KPIs is derived to summarize engagement intensity, habit consistency, preference diversity, and discovery dynamics. Insights are delivered through a narrative-style Power BI dashboard inspired by consumer product analytics rather than traditional BI reporting.

---

## Analytical Objectives

The primary objectives of the project are to:

- Normalize heterogeneous streaming data into a single, platform-agnostic event model  
- Summarize individual-level listening behavior over time  
- Model engagement patterns beyond simple top-N summaries  
- Compare listening habits across platforms within a unified analytical framework  
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
- Timestamps localized and converted to UTC  
- Play durations converted from milliseconds to minutes  
- Very short plays filtered using a minimum duration threshold  
- Session IDs generated based on inactivity gaps  

### Apple Music

- Listening history ingested from Apple Music Play Activity CSV exports  
- Timestamps parsed and normalized to UTC  
- Play durations converted from milliseconds to minutes  
- Session IDs generated using the same logic as Spotify  
- Artist metadata partially enriched via a left join with the Apple Music Library Tracks export  

Due to Apple Music data limitations, some events (e.g. radio, autoplay, editorial content) do not resolve cleanly to library tracks and remain unmatched. This behavior is expected and documented.

---

## Engagement KPIs

Behavioral KPIs are derived exclusively from the normalized event table in a dedicated analysis notebook. KPIs are computed at the appropriate level of aggregation and exported as clean tables for visualization.

Implemented metrics include:

- **Listening Intensity**
  - Total listening time by platform  
  - Daily listening minutes  

- **Habit Consistency**
  - Active listening days  
  - Active listening weeks  

- **Session Behavior**
  - Session length (minutes)  
  - Tracks per session  
  - Average and median session duration  

- **Preference Diversity**
  - Unique tracks per day  
  - Unique artists per week  

- **Discovery Behavior**
  - Discovery events (first listen to an artist)  
  - Discovery rate by platform  

Deduplication is applied intentionally at the KPI level rather than globally.

---

## Data Storage

All normalized listening events are stored in a single SQLite database:

- Database: `MusicPlatformInsights.db`  
- Table: `listening_events`  

Spotify events initialize the table. Apple Music events are appended after enrichment, replacing prior Apple rows to avoid duplication.

Derived KPI tables are exported as CSVs for use in Power BI.

---

## Visualization

Insights are delivered through a **Power BI dashboard** designed as a year-in-review style experience rather than an operational report.

Planned dashboard views include:

- High-level listening summaries  
- Engagement and habit consistency trends  
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
│ ├── EngagementKPIs.ipynb
│ ├── ExportToPowerBI.ipynb
├── data/
│ ├── raw/
│ ├── processed/
│ └── kpis/
├── dashboards/
├── docs/
│ ├── canonical_schema.md
│ ├── kpi_definitions.md
├── README.md
```

---

## Planned Work

Next steps include:

- Finalizing Power BI dashboard layout and storytelling flow  
- Refining cross-platform comparison insights  
- Adding optional v2 Apple Music metadata enrichment  
- Documenting KPI rationale for interview and portfolio use  

---

## Why This Project

While centered on personal music data, this project mirrors real-world analytics problems such as multi-source data integration, behavioral modeling, KPI design, and insight communication. The focus is on transforming raw event data into meaningful, user-facing insights, reflecting how modern consumer products use analytics to understand and communicate user behavior.
