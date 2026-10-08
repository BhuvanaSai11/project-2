# Data Model Specification

The data model supports household water telemetry, anomaly detection, and user alert workflows for the Smart Water Leak detection system.

## Core Entities & Schema

### 1. Households
* `id` (UUID, PK)
* `name` (String)
* `address` (String, nullable)
* `created_at` (Timestamp)

### 2. Users
* `id` (UUID, PK)
* `household_id` (UUID, FK)
* `email` (String, Unique)
* `password_hash` (String)
* `role` (Enum: `owner`, `admin`, `viewer`)

### 3. Sensors
* `id` (UUID, PK)
* `household_id` (UUID, FK)
* `sensor_name` (String)
* `device_type` (String)
* `calibration_factor` (Decimal)
* `status` (Enum: `active`, `inactive`, `faulty`)

### 4. Flow Readings
* `id` (UUID, PK)
* `sensor_id` (UUID, FK)
* `timestamp` (Timestamp)
* `flow_rate` (Decimal)
* `pulse_count` (Integer)
* `source` (String)

### 5. Consumption Windows
* `id` (UUID, PK)
* `household_id` (UUID, FK)
* `window_start` (Timestamp)
* `window_end` (Timestamp)
* `total_volume` (Decimal)
* `avg_flow_rate` (Decimal)
* `peak_flow_rate` (Decimal)

### 6. Baseline Profiles
* `id` (UUID, PK)
* `household_id` (UUID, FK)
* `time_bucket` (String)
* `expected_flow_mean` (Decimal)
* `expected_flow_stddev` (Decimal)
* `updated_at` (Timestamp)

### 7. Anomaly Events
* `id` (UUID, PK)
* `household_id` (UUID, FK)
* `window_id` (UUID, FK, nullable)
* `score` (Decimal)
* `threshold` (Decimal)
* `status` (Enum: `open`, `investigating`, `resolved`)
* `created_at` (Timestamp)

### 8. Alerts
* `id` (UUID, PK)
* `household_id` (UUID, FK)
* `anomaly_event_id` (UUID, FK)
* `severity` (Enum: `low`, `medium`, `high`)
* `message` (Text)
* `channel` (Enum: `sms`, `email`, `push`)
* `sent_at` (Timestamp)

## Relationships
- One household can have many users.
- One household can have many sensors.
- One sensor can produce many flow readings.
- One household can have many consumption windows and baseline profiles.
- One anomaly event can trigger one or more alerts.

## Storage Notes
- Raw flow readings should be stored in a time-series-friendly structure.
- Aggregated usage windows are ideal for model scoring and dashboard analysis.
- Alert records should remain immutable once sent for audit and troubleshooting.
