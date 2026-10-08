Smart Water Leak & Abnormal Consumption Detection

An automated, edge-to-cloud system that learns normal household water usage patterns using unsupervised machine learning and flags abnormal consumption in near real time.

The Problem
Water waste often stays invisible until utility bills arrive or physical damage occurs.

* Continuous Waste: Slow, persistent leaks can run unnoticed for hours or days.


* Late Discovery: Manual meter checks are infrequent, tedious, and easy to miss.



System Architecture
The project utilizes a simple, efficient edge-to-cloud pipeline to transform raw flow measurements into actionable warnings:

[Flow Sensor] -> [Edge Device] -> [Data Store] -> [Anomaly Model] -> [Homeowner Alert]
(Measure)       (Aggregate)     (Timestamp)     (Score)           (Notify)

* Flow Sensor: Measures raw water flow.


* Edge Device: Aggregates telemetry data locally.


* Data Store: Logs and timestamps consumption records.


* Anomaly Model: Analyzes windows of data and computes anomaly scores.


* Homeowner Alert: Sends concise mobile notifications when abnormal usage persists.



Unsupervised Machine Learning Approach
Unlike traditional methods, this system requires no pre-labelled leak examples.

* Baseline Learning: The model studies recurring usage patterns including time of day, duration, flow rate, and recent historical data to establish a normal cluster.


* Anomaly Scoring: Each new consumption window is assigned an anomaly score. If the score exceeds a predefined threshold, an investigation is triggered.


* Persistent Monitoring Example: Normal household demand typically drops near zero overnight (00:00 to 04:00). A continuous baseline anomaly (such as an 18 L/h flow rate during sleeping hours) creates a clear, persistent anomaly that gets immediately flagged.



Team Division of Labor

Teammate 1: Machine Learning & Data Intelligence

* Model Design & Training: Develops the unsupervised anomaly detection model (e.g., Isolation Forests, One-Class SVMs, or Autoencoders) to profile normal consumption clusters.


* Feature Engineering: Extracts and structures features from raw data, incorporating variables like time of day, usage duration, rolling flow rates, and historical baselines.


* Threshold Tuning & Evaluation: Optimizes anomaly scoring thresholds to minimize false positives caused by unusual routines or guests while ensuring real leaks are caught.



Teammate 2: Hardware, Edge & Backend Pipeline

* Hardware & Edge Integration: Configures the flow sensor and programs the edge device to accurately measure and aggregate water pulse/flow data.


* Data Pipeline & Storage: Sets up the backend data store to securely timestamp and log incoming time-series telemetry.


* Alerts & Notifications: Builds the real-time notification system to deliver mobile alerts featuring timestamp, severity, and suggested checks.



Benefits & Limitations

* Key Benefits: Saves water, lowers utility bills, moves discovery from monthly bills to timely alerts, and adapts locally to each home's unique rhythm.


* Engineering Realities: Must account for sensor noise/drift, potential false positives from irrigation or guests, cold-start history requirements, and data privacy.



Future Scope

* Automated valve shut-off mechanisms.


* Room-level sub-metering and sensing.


* Weather-aware consumption models.


* Community-wide water insights.
