# Canonical Listening Event Schema

Each row represents a single listening event from any supported platform.

## Fields

- event_time: Timestamp of the listening event (UTC)
- platform: Source platform (spotify, apple_music)
- artist: Artist name
- track: Track name
- duration_minutes: Minutes listened during the event
- session_id: Logical session grouping identifier (derived)

This schema is designed to support platform-agnostic behavioral analysis.
