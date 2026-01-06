# MusicPlatformInsights

Cross-platform analysis of personal music listening behavior, focusing on engagement, habits, and preferences using normalized Spotify and Apple Music data and Power BI visualization.

---

## Status

## In Progress

Data access pending. Project structure, schema design, and KPI definitions initialized.

---

## Overview

MusicPlatformInsights is a user behavior analytics project that studies how individuals engage with music over time across multiple streaming platforms. Rather than treating listening activity as a collection of isolated plays, the project frames music consumption as a **behavioral pattern problem**, emphasizing consistency, preference formation, and discovery dynamics.

The project is designed to integrate and normalize listening history from Spotify and Apple Music into a unified, platform-agnostic event model. From this foundation, a set of interpretable KPIs is derived to summarize engagement intensity, listening habits, and preference diversity. Insights are ultimately delivered through a narrative-style Power BI dashboard inspired by consumer product analytics rather than traditional BI reporting.

---

## Analytical Objectives

The primary objectives of the project are to:

- Summarize individual-level listening behavior over the available analysis window  
- Identify meaningful engagement patterns beyond simple top-N summaries  
- Compare listening habits across platforms within a unified behavioral framework  
- Translate raw event data into insights that are intuitive and user-facing  

The emphasis is on **clarity, interpretability, and storytelling**, not algorithmic complexity.

---

## Canonical Listening Event Model

All listening data is mapped into a standardized event-level schema to support platform-agnostic analysis.

Each row represents a single listening event and includes:

- `event_time`: Timestamp of the listening event  
- `platform`: Source platform (spotify, apple_music)  
- `artist`: Artist name  
- `track`: Track name  
- `duration_minutes`: Minutes listened during the event  
- `session_id`: Derived identifier grouping events into listening sessions  

This schema is intentionally minimal and designed to support behavioral analysis rather than perfect metadata reconciliation.

---

## KPI Definitions

KPIs are defined conceptually prior to data ingestion and derived exclusively from normalized listening events.

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

## Data Sources

Planned data sources include:

- **Spotify Listening History**: Exported user-level streaming events with timestamps and playback duration  
- **Apple Music Listening History**: User-level play activity exported via Apple Media Services  

Both sources will be treated as raw inputs and transformed into the canonical listening event model prior to analysis.

---

## Visualization

Insights will be delivered through a **Power BI dashboard** designed as a year-in-review style experience rather than an operational report.

Planned dashboard views include:

- High-level listening summary  
- Engagement and habit consistency breakdowns  
- Preference concentration and diversity views  
- Discovery versus repeat listening behavior  
- Cross-platform comparison insights  

The dashboard will prioritize narrative flow and interpretability over exhaustive filtering.

---

## Project Structure
```
MusicPlatformInsights/
├── notebooks/
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

- Ingesting and cleaning Spotify listening history  
- Validating the canonical schema against real event data  
- Adding Apple Music as a secondary data source  
- Implementing KPI calculations and aggregation logic  
- Publishing the initial Power BI dashboard  

Work will proceed incrementally with an emphasis on correctness, clarity, and polish.

---

## Why This Project

While centered on personal music data, this project mirrors real-world analytics problems such as multi-source data integration, behavioral modeling, KPI design, and insight communication. The focus is on transforming raw event data into meaningful, user-facing insights, reflecting how modern consumer products use analytics to understand and communicate user behavior.


