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
