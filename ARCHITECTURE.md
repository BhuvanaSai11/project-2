# Architecture Overview

## Purpose
The platform is designed to monitor household water usage, detect abnormal consumption patterns, and alert users before waste becomes expensive or damaging. The architecture is intentionally simple, reliable, and easy to deploy on a small edge device or local server environment.

## Architectural Style
The system follows a layered edge-to-cloud pattern.

This design keeps the application understandable and deployable while separating key concerns such as:

- sensing and instrumentation
- edge aggregation and filtering
- telemetry storage
- anomaly detection and scoring
- alert generation and notification

## Key Decisions

### 1. Edge-first deployment
Data is processed close to the source to reduce latency, limit bandwidth use, and support faster local anomaly detection.

### 2. Time-series data model
A lightweight storage structure records raw flow measurements and aggregated consumption windows with timestamps for later analysis.

### 3. Unsupervised anomaly detection
The system learns from routine household behavior and flags deviations without requiring a large labelled dataset of leak events.

### 4. Event-driven alerting
Once anomaly scores cross a threshold, a notification service emits a user-facing alert with timestamp, severity, and suggested checks.

## Core Components

### Sensing and telemetry
Captures water flow measurements from the sensor and streams timestamped readings to the edge device.

### Edge processing
Aggregates sensor pulses, smooths short-term noise, and builds consumption windows before forwarding the data.

### Data storage
Persists raw readings, processed usage windows, anomaly history, and alert records for retrieval and monitoring.

### Analytics engine
Applies unsupervised models such as Isolation Forests, One-Class SVMs, or Autoencoders to establish a normal usage profile and detect abnormal patterns.

### Alerting and notification
Creates homeowner alerts when abnormal water usage persists beyond a threshold or investigation window.

## Recommended Deployment Flow

1. Install the flow sensor and connect it to the edge device.
2. Start the local gateway and validate telemetry collection.
3. Store readings in the time-series data store.
4. Train or update the baseline model using historical household usage.
5. Run detection on rolling windows of consumption data.
6. Evaluate anomaly scores against configured thresholds.
7. Publish homeowner alerts when a sustained deviation is observed.
8. Monitor system health and retrain when household behavior changes.

## Summary
This architecture is built for clarity, maintainability, and reliable early leak detection. It provides a practical way to prove value quickly while preserving extensibility for future feature enhancements.
