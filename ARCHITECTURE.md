# Architecture Decision Record

## System Design Overview
The platform follows a modular monolith architecture designed for reliability, simplicity, and ease of self-hosting via Docker. This architecture is tailored for the Sankalp hackathon platform and supports event workflows, track-based judging, and public project discovery.

## Key Technical Decisions
1. **Containerization (Docker):** Chosen to guarantee that the application runs locally without depending on external cloud services, hosted databases, or network connectivity.
2. **Role Isolation:** Enforced at the middleware level to clearly separate permissions between Participants, Judges, Organizers, and Admins.
3. **Database Layer:** Utilizes a lightweight relational database via Docker to manage relational entities like users, teams, events, projects, and track assignments cleanly.
4. **Track-Based Event Model:** Configured to support multiple tracks, including Track A - Students Track.

## Sankalp Hackathon Scope
The platform is designed around the Sankalp 2026 hackathon flow: registration, team onboarding, project submission, evaluation, and results publication.
