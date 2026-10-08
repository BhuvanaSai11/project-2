# Data Model Specification

The data model supports the Sankalp hackathon submission, team formation, and judging lifecycle for Track A - Students Track.

## Core Entities & Schema

### 1. Users
* `id` (UUID, PK)
* `email` (String, Unique)
* `password_hash` (String)
* `role` (Enum: `participant`, `judge`, `organizer`, `admin`)

### 2. Events
* `id` (UUID, PK)
* `title` (String)
* `start_date` (Timestamp)
* `submission_deadline` (Timestamp)
* `tracks` (JSON / Relation)
* `track_name` (String, Example: `Track A - Students Track`)

### 3. Teams
* `id` (UUID, PK)
* `event_id` (UUID, FK)
* `name` (String)
* `invite_code` (String, Unique)

### 4. Submissions
* `id` (UUID, PK)
* `team_id` (UUID, FK)
* `event_id` (UUID, FK)
* `title` (String)
* `description` (Text)
* `repo_url` (String)
* `status` (Enum: `draft`, `submitted`)

### 5. Tracks
* `id` (UUID, PK)
* `event_id` (UUID, FK)
* `name` (String)
* `description` (Text)

## Import / Export Paths
* Database seeds can be automatically injected on startup via initialization scripts.
* Data export is supported via structured JSON/CSV dumps.

