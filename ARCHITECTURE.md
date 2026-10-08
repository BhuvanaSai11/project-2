# Architecture Overview

## Purpose

The platform is designed to support a hackathon lifecycle from event setup to final results publication. The architecture is intentionally simple and reliable so that it can be run locally with minimal infrastructure.

## Architectural Style

The project follows a modular monolith pattern.

This approach keeps the application easier to understand and deploy while still separating key concerns such as:

- authentication and role management
- event management
- team formation
- submission handling
- judging and scoring
- result publication

## Key Decisions

### 1. Docker-based deployment
The application is designed to run locally through Docker so that it does not depend on a complex managed cloud setup.

### 2. Role-based authorization
Different user roles are enforced at the application layer to define access boundaries between participants, judges, organizers, and admins.

### 3. Relational data model
A lightweight relational database is used to manage entities such as users, teams, events, tracks, and submissions in a structured way.

### 4. Track-based event model
The platform supports multiple tracks, including the Student Track, so that event organizers can classify submissions and assign judging appropriately.

## Core Components

### Authentication and access control
Handles login, role assignment, and permission checks.

### Event management
Manages hackathon event creation, deadlines, track configuration, and event metadata.

### Team management
Handles team creation, invite code generation, and membership logic.

### Submission management
Controls project submission information, repository links, and submission status.

### Judging and scoring
Supports isolated evaluation flows, assignment of judges to projects, and score recording.

### Results and gallery
Publishes accepted or ranked results and exposes a public listing of submissions.

## Recommended Deployment Flow

1. Start the application using Docker Compose.
2. Initialize database configuration and seed data if needed.
3. Create the hackathon event and define tracks.
4. Register participants and teams.
5. Allow project submissions.
6. Close the submission milestone.
7. Assign judges and collect scores.
8. Publish results.

## Summary

This architecture is built for clarity, maintainability, and quick setup. It gives organizers a practical way to run a hackathon while preserving structure, fairness, and operational simplicity.
