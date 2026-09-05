# Industrial Robot Performance Analytics

## Project Overview

**Industrial Robot Performance Analytics** is a Power BI capstone project designed to analyze industrial robot operations, production performance, robot health, maintenance activity, downtime, failure patterns, and operational risk.

The project uses a custom synthetic dataset based on industrial predictive-maintenance concepts and presents the results through an interactive three-page Power BI dashboard.

> **Note:** All data used in this project is synthetic and created for educational, portfolio, and demonstration purposes. It does not represent data from a real industrial plant.

## Problem Statement

Industrial robots are critical to automated manufacturing. Unexpected failures, poor robot health, excessive downtime, and high maintenance costs can reduce productivity and increase operational expenses.

This project builds a centralized analytics solution to identify:

- Overall production and operational performance
- Robot health and sensor conditions
- High-risk robots and robot types
- Major failure types
- Maintenance cost drivers
- Downtime drivers
- Areas requiring maintenance attention

## Project Objectives

1. Monitor overall robot and production performance.
2. Analyze robot health using sensor data.
3. Identify high-risk robots and robot categories.
4. Analyze maintenance cost and downtime.
5. Identify important failure types.
6. Compare robot types and manufacturers.
7. Provide actionable insights through an interactive Power BI dashboard.

## Tools & Technologies

- **Microsoft Power BI** — Data modeling, DAX, visualization, and dashboard development
- **Microsoft Excel** — Dataset storage and preparation
- **DAX** — Analytical measures and calculations
- **Power Query** — Data transformation and cleaning

## Dataset

The project uses four integrated Excel datasets.

### 1. Robot_Master.xlsx

Master information for each industrial robot.

Key fields:
- Robot_ID
- Robot_Type
- Manufacturer

### 2. Sensor_Data.xlsx

Robot condition-monitoring data.

Key fields:
- Robot_ID
- Date
- Temperature
- Vibration
- Motor_Current
- RPM
- Torque
- Energy_Consumption
- Tool_Wear
- Health_Score

### 3. Production_Log.xlsx

Production and quality information.

Key fields:
- Robot_ID
- Date
- Units_Produced
- Defective_Units
- Efficiency
- Cycle_Time

### 4. Maintenance_Log.xlsx

Maintenance and failure information.

Key fields:
- Maintenance_ID
- Robot_ID
- Date
- Maintenance_Type
- Failure_Type
- Maintenance_Cost
- Downtime
- Technician

## Dataset Reference

The synthetic dataset was developed using industrial predictive-maintenance datasets available on Kaggle as a reference for feature selection, machine-condition concepts, and dataset structure.

The final dataset in this repository is **custom synthetic data** and is not copied from real-world plant data.

## Data Model

The Power BI model follows a structured relational/star-schema approach.

```text
Robot_Master[Robot_ID]
        |
        +-- 1 : * -- Sensor_Data[Robot_ID]
        |
        +-- 1 : * -- Production_Log[Robot_ID]
        |
        +-- 1 : * -- Maintenance_Log[Robot_ID]

Date_Table[Date]
        |
        +-- 1 : * -- Sensor_Data[Date]
        +-- 1 : * -- Production_Log[Date]
        +-- 1 : * -- Maintenance_Log[Date]
```

A small **Risk_Category** helper table contains High Risk, Medium Risk, and Low Risk categories for risk-distribution visuals.

## Important DAX Metrics

The dashboard includes measures for:

- Total Robots
- Total Units Produced
- Defect Rate
- Average Health Score
- Average Temperature
- Average Vibration
- Average Motor Current
- Total Maintenance Cost
- Total Downtime Hours
- Total Maintenance Events
- Average Risk Score
- High Risk Robot Count
- Medium Risk Robot Count
- Low Risk Robot Count
- Unplanned Maintenance Rate

A calculated risk score is used to classify robots into risk categories based on condition and operational indicators.

# Dashboard

## Page 1 — Executive Operations

Provides a high-level overview of robot operations.

### Main KPIs

- Total Robots: **250**
- Total Units Produced: **~14M**
- Defect Rate: **2.9%**
- Average Health Score: **47.35**
- Total Maintenance Cost: **~214M**
- Total Downtime: **~20.59K hours**

### Main Analysis

- Production trend over time
- Maintenance cost by robot type
- Average health by robot type
- Temperature versus robot health
- Maintenance events by type
- Maintenance cost and downtime trend

### Key Insight

Overall production is strong, but maintenance cost and downtime represent significant opportunities for improvement.

## Page 2 — Robot Health & Performance

Focuses on robot condition and sensor-based health analysis.

### Main KPIs

- Average Health Score: **47.35**
- Average Temperature: **54.32**
- Average Vibration: **3.89**
- Average Motor Current: **15.02**

### Main Analysis

- Health score by robot type
- Temperature versus health
- Bottom 10 robots by health
- Vibration versus health
- Motor current versus health
- Robot risk distribution

### Key Insight

Condition-monitoring data helps identify unhealthy robots and supports early maintenance prioritization.

The lowest-health robot identified was **Robot 228**, with an average health score of approximately **43.63**.

## Page 3 — Robot Risk & Reliability Analysis

Focuses on risk, failures, downtime, maintenance cost, and reliability.

### Main KPIs

- Average Risk Score: **50.10**
- High Risk Robot Count: **121**
- Average Health Score: **47.35**
- Total Downtime: **~20.59K hours**

### Main Analysis

- Risk category by robot type
- Downtime by failure type
- High-risk robots by manufacturer
- Overall robot risk distribution
- Maintenance cost by failure type
- Average risk score by robot type

### Key Insights

- **Packaging** has the highest number of high-risk robots: **100**.
- **Yaskawa** has the highest absolute high-risk robot count: **27**.
- **Servo motor failure** is a major contributor to downtime and maintenance cost.
- **Robot 210** was identified as the highest robot for both downtime and maintenance cost.

> High-risk counts by manufacturer should be considered together with the number of robots from each manufacturer. A high-risk percentage would provide a fairer comparison.

## Business Value

The dashboard can help operations and maintenance teams:

- Identify high-risk robots
- Prioritize maintenance activities
- Monitor robot health
- Understand major failure patterns
- Reduce unexpected downtime
- Control maintenance costs
- Monitor production quality
- Support data-driven maintenance decisions

## Future Improvements

The current project is a predictive-maintenance analytics prototype. Future enhancements could include:

- Real-time IoT sensor integration
- Machine-learning-based failure prediction
- Remaining Useful Life (RUL) prediction
- Anomaly detection
- Automated maintenance alerts
- Maintenance scheduling optimization
- Root-cause analysis
- Manufacturer reliability percentages
- Cost-saving and ROI analysis
- Integration with enterprise maintenance systems

## Project Structure

```text
industrial-robot-performance-analytics/
│
├── README.md
│
├── Dataset/
│   ├── Robot_Master.xlsx
│   ├── Sensor_Data.xlsx
│   ├── Production_Log.xlsx
│   └── Maintenance_Log.xlsx
│
├── PowerBI/
│   └── Industrial_Robot_Performance.pbix
│
├── Presentation/
│   └── Industrial_Robot_Performance_Capstone_Presentation.pptx
│
└── Documentation/
    ├── Data_Model.png
    └── DAX_Measures.md
```

## Dashboard Story

> **Page 1 tells us what is happening.**  
> **Page 2 tells us which robots are unhealthy.**  
> **Page 3 tells us where the risk, downtime, and maintenance cost require action.**

## Disclaimer

This project was created as an educational and portfolio capstone project.

All operational data is synthetic and should not be interpreted as real production or maintenance data from any specific company.

## Author

**Abdul Azeem**

**Project:** Industrial Robot Performance Analytics  
**Domain:** Robotics | Predictive Maintenance | Business Intelligence  
**Primary Tool:** Microsoft Power BI
