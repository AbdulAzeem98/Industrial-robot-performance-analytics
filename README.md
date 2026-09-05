# Industrial Robot Performance Analytics

## Overview

A **Power BI capstone project** for analyzing industrial robot performance, health, maintenance, downtime, failures, and operational risk using custom synthetic data.

> **Note:** The dataset is synthetic and created for educational and portfolio purposes.

## Objectives

- Monitor production and operational performance
- Analyze robot health using sensor data
- Identify high-risk robots and robot types
- Analyze maintenance cost and downtime
- Identify major failure patterns
- Support data-driven maintenance decisions

## Tools & Technologies

**Power BI | DAX | Power Query | Excel**

## Dataset

The project contains four Excel datasets:

| Dataset | Purpose |
|---|---|
| `Robot_Master.xlsx` | Robot type, manufacturer, and master information |
| `Sensor_Data.xlsx` | Temperature, vibration, motor current, health score, and sensor data |
| `Production_Log.xlsx` | Production, defects, efficiency, and cycle time |
| `Maintenance_Log.xlsx` | Maintenance type, failure type, cost, and downtime |

The synthetic dataset was developed using industrial predictive-maintenance datasets on Kaggle as a reference for features and structure.

## Data Model

The Power BI model follows a **star-schema approach**.

```text
Robot_Master → Sensor_Data
             → Production_Log
             → Maintenance_Log

Date_Table   → Sensor_Data
             → Production_Log
             → Maintenance_Log

Risk_Category → Helper / Disconnected Table
```

## Key DAX Metrics

- Total Robots
- Total Units Produced
- Defect Rate
- Average Health Score
- Average Temperature
- Average Vibration
- Average Motor Current
- Total Maintenance Cost
- Total Downtime Hours
- Average Risk Score
- High / Medium / Low Risk Robot Count
- Unplanned Maintenance Rate

## Dashboard

### 1. Executive Operations

Provides an overall view of production, robot health, maintenance cost, and downtime.

**Key KPIs:** 250 Robots | ~14M Units | 2.9% Defect Rate | 47.35 Health Score | ~214M Maintenance Cost | ~20.59K Downtime Hours

### 2. Robot Health & Performance

Analyzes sensor conditions, robot health, unhealthy robots, and risk distribution.

**Key Insight:** Robot 228 recorded the lowest average health score at approximately 43.63.

### 3. Robot Risk & Reliability Analysis

Analyzes robot risk, failures, downtime, and maintenance costs.

**Key Insights:**
- Packaging had 100 high-risk robots
- Yaskawa had 27 high-risk robots
- Servo motor failure was a major downtime and maintenance-cost driver

## Business Value

The dashboard helps maintenance and operations teams:

- Identify high-risk robots
- Prioritize maintenance
- Understand failure patterns
- Reduce downtime
- Control maintenance costs
- Improve operational decision-making

## Future Scope

- Real-time IoT integration
- Machine-learning-based failure prediction
- Remaining Useful Life (RUL)
- Anomaly detection
- Automated maintenance alerts
- Maintenance optimization

## Project Structure

```text
industrial-robot-performance-analytics/
├── README.md
├── Dataset/
├── PowerBI/
├── Dashboard/
├── Presentation/
└── Documentation/
```

## Dashboard Story

- **Page 1:** What is happening?
- **Page 2:** Which robots are unhealthy?
- **Page 3:** Where should we take action?

## Disclaimer

This is an educational and portfolio project using synthetic data. It does not represent real industrial plant data.

## Author

**Abdul Azeem**

Power BI | Data Analytics | Predictive Maintenance
