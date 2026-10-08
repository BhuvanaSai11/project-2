# Smart Water Leak & Abnormal Consumption Detection

An automated, edge-to-cloud monitoring system that learns normal household water usage patterns using unsupervised machine learning and flags abnormal consumption in near real time.

## The Problem
Water waste often stays invisible until utility bills arrive or physical damage occurs.

- Continuous waste: Slow, persistent leaks can run unnoticed for hours or days.
- Late discovery: Manual meter checks are infrequent, tedious, and easy to miss.

## System Architecture
The project uses a simple, reliable edge-to-cloud pipeline to transform raw flow measurements into actionable warnings.

[Flow Sensor] -> [Edge Device] -> [Data Store] -> [Anomaly Model] -> [Homeowner Alert]
(Measure)       (Aggregate)     (Timestamp)     (Score)           (Notify)

- Flow Sensor: Measures raw water flow.
- Edge Device: Aggregates telemetry locally and filters noisy pulses.
- Data Store: Stores timestamped telemetry and derived consumption windows.
- Anomaly Model: Learns ordinary household usage and computes anomaly scores.
- Homeowner Alert: Sends concise notifications when abnormal usage persists.

## Unsupervised Machine Learning Approach
Unlike traditional detection methods, this system does not require pre-labelled leak examples.

- Baseline Learning: The model studies recurring usage patterns including time of day, duration, flow rate, and recent historical behavior to establish a normal cluster.
- Anomaly Scoring: Each new consumption window is assigned an anomaly score. If the score exceeds a threshold, the system raises an investigation.
- Persistent Monitoring Example: Normal household demand typically drops near zero overnight. A steady flow rate during sleeping hours can indicate a leak or abnormal usage pattern.

## Core Components

### 1. Sensing Layer
Captures the raw flow signal from the water meter or flow sensor and produces time-series data.

### 2. Edge Processing Layer
Aggregates pulses, performs local validation, and reduces unnecessary cloud traffic.

### 3. Data and Storage Layer
Stores sensor readings, consumption windows, anomaly history, and alert metadata in a structured format.

### 4. Analytics Layer
Runs unsupervised models such as Isolation Forests, One-Class SVMs, or Autoencoders to profile expected water usage.

### 5. Alerting Layer
Triggers notifications for likely leaks or sustained abnormal activity with severity, timestamp, and suggested checks.

## Data Model Highlights
The system tracks household-level telemetry and events:

- Household: home metadata and installation context
- Sensor: meter or flow sensor identity and calibration details
- Flow Reading: timestamped raw flow measurements
- Consumption Window: aggregated usage segment for a period of time
- Anomaly Event: model output with score and threshold comparison
- Alert: homeowner notifications and resolution state

## Benefits and Limitations

### Key Benefits
- Saves water and reduces utility bills
- Detects issues much earlier than monthly billing cycles
- Adapts to each home’s unique usage profile
- Works with minimal labeled data

### Engineering Realities
- Sensor noise and calibration drift must be handled carefully
- False positives may occur during irrigation, guests, or unusual routines
- Early operation requires historical baselines
- Privacy and secure storage are important for household telemetry

## Future Scope
- Automated valve shut-off mechanisms
- Room-level sub-metering and sensing
- Weather-aware consumption models
- Community-wide water insights and benchmarking

## Summary
This project combines hardware sensing, edge processing, time-series storage, and unsupervised anomaly detection to create a practical and scalable water leak monitoring system.
