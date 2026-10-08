# Sankalp Hackathon Platform

A simple and reliable platform for organizing hackathon events, managing participant teams, collecting project submissions, and supporting judging and result publication.

## Overview

This project helps organizers run a hackathon end-to-end without relying on complex external systems. It supports:

- event creation and configuration
- participant registration
- team formation through invite links
- project submission with deadlines
- track-based project organization
- judging and scoring
- public gallery and results publishing

The system is designed for local deployment using Docker and is intended to be easy to run and maintain.

## Core Features

### For organizers
- Create and manage hackathon events
- Configure submission deadlines and tracks
- Review submission statuses
- Publish results
- Manage access for judges and admins

### For participants
- Register and sign in
- Join or create a team
- Submit project information and repository links
- View public project listings

### For judges
- Access assigned tracks or projects
- Score submissions based on defined criteria
- Submit evaluations without changing admin settings

## User Roles

The platform separates responsibilities by role:

- Participant
- Judge
- Organizer
- Admin

This role separation helps maintain access control and keeps evaluation fair and auditable.

## Workflow

1. An organizer creates an event and configures tracks.
2. Participants register and form teams.
3. Teams submit their project details before the deadline.
4. Judges review the submissions in their assigned track.
5. Scores are recorded and normalized.
6. Results are published to participants and organizers.

## System Design

The platform follows a modular monolith design with clear responsibilities. It is built to be:

- reliable
- easy to self-host
- easy to deploy locally
- scalable enough for a hackathon use case

## Local Setup

1. Clone the repository.
2. Open the project folder.
3. Start the services with Docker Compose:

```bash
docker compose up
```

4. Open the application in the browser at the configured local port.

## Project Files

- `README.md` - project overview
- `ARCHITECTURE.md` - technical design and decisions
- `DATA-MODEL.md` - database entities and relationships
- `JUDGING..md` - judging and scoring process
- `docker-compose.yml` - local container setup

## Notes

This project is designed for a hackathon environment and focuses on a clear, structured user flow, role isolation, and a straightforward deployment model.
