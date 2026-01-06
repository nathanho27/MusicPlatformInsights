# MusicPlatformInsights

Cross-platform analysis of personal music listening behavior, summarizing year-long engagement, preferences, and habits using normalized Spotify and Apple Music data and Power BI visualization.

---

## Status

## In Progress

---

## Overview

MusicPlatformInsights is a user behavior analytics project that studies how individuals engage with music over time across multiple streaming platforms. Rather than treating listening activity as a collection of isolated plays, the project frames music consumption as a **behavioral pattern problem**, focusing on consistency, preference formation, and exploration dynamics over the course of a full year.

The project integrates and normalizes listening history from Spotify and Apple Music into a unified event-level schema. Platform-agnostic KPIs are then derived to summarize engagement intensity, habit stability, and preference diversity. Results are presented through a narrative-style Power BI dashboard inspired by consumer product analytics rather than traditional BI reporting.

---

## Analytical Objectives

The primary goals of the project are to:

- Summarize year-long listening behavior in a compact, interpretable format  
- Identify meaningful engagement patterns beyond simple top-N rankings  
- Compare listening habits across platforms within a unified behavioral model  
- Translate raw event data into insights that a non-technical user would understand  

The emphasis is on **interpretability and storytelling**, not algorithmic complexity.

---

## Behavioral Dimensions

Listening behavior is analyzed across several core dimensions.

### Engagement Intensity

Measures how much and how often music is consumed.

- Total minutes listened  
- Active listening days and weeks  
- Average session duration  
- Longest listening streaks  

### Consistency & Habits

Captures how regular or sporadic listening behavior is.

- Week-to-week activity stability  
- Time-of-day listening patterns  
- Weekday vs weekend behavior  
- Session frequency distributions  

### Preferences

Summarizes what the user listens to and how concentrated tastes are.

- Top artists, tracks, and genres  
- Artist loyalty vs breadth  
- Genre diversity and entropy-style measures  
- Long-term preference persistence  

### Discovery vs Repeat Behavior

Separates exploration from habitual listening.

- New artist discovery rate  
- Repeat listening concentration  
- Platform-level discovery differences  

---

## Data Sources

- **Spotify Listening History**: User-level streaming events with timestamps and track metadata  
- **Apple Music Listening History**: User-level play data exported from Apple Music  

Both sources are treated as raw inputs and transformed into a standardized listening event table to support platform-agnostic analysis.

---

## Data Modeling & Normalization

Spotify and Apple Music differ in schema, timestamp conventions, and metadata availability. To address this, all data is mapped into a **canonical listening event model** with consistent definitions for:

- Listening duration  
- Artist and track identifiers  
- Session boundaries  
- Platform attribution  

Normalization decisions are documented and prioritized for analytical consistency rather than perfect metadata reconciliation.

---

## KPI Construction

KPIs are derived exclusively from normalized listening events and are designed to be:

- Platform-independent  
- Intuitive to interpret  
- Stable across time  

Metrics are aggregated at daily, weekly, and annual levels to support both summary views and behavioral trend analysis.

---

## Visualization

Insights are delivered through a **Power BI dashboard** designed as a year-in-review experience rather than a traditional operational report.

Dashboard views include:

- High-level annual listening summary  
- Engagement and consistency breakdowns  
- Preference concentration and diversity views  
- Platform comparison insights  
- Behavioral trend timelines  

The dashboard prioritizes narrative flow and interpretability over exhaustive filtering.

---

## Project Structure

MusicPlatformInsights/
├── notebooks/
│ ├── 01_data_normalization.ipynb
│ ├── 02_kpi_construction.ipynb
│ ├── 03_behavioral_analysis.ipynb
├── data/
│ ├── raw/
│ ├── processed/
├── dashboards/
├── README.md


---

## Planned Work

Planned next steps include:

- Finalizing Spotify-first ingestion and normalization  
- Adding Apple Music as a secondary data source  
- Completing KPI definitions and validation  
- Publishing the initial Power BI year-in-review dashboard  
- Optionally adding a lightweight web presentation layer  

Work will be completed iteratively, with an emphasis on clarity and polish rather than breadth of features.

---

## Why This Project

While centered on personal music data, this project mirrors real-world analytics problems such as multi-source data integration, behavioral modeling, KPI design, and insight communication. The focus is on transforming raw event data into meaningful, user-facing insights, reflecting how modern consumer products use analytics to tell compelling stories.

