# 🤖 Industrial Robot Performance Analytics

## Predictive Maintenance & Operational Risk Analytics using Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-Analytics-F2C811?logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Data-Excel-217346?logo=microsoftexcel&logoColor=white)
![Status](https://img.shields.io/badge/Project-Completed-success)

---

## 📌 Project Overview

Industrial robots are critical components of modern manufacturing systems. 
Unexpected robot failures can lead to production losses, increased downtime, 
higher maintenance costs, and quality problems.

This project develops an interactive **Power BI dashboard** for analyzing:

- Robot health
- Production performance
- Defect rate
- Sensor conditions
- Maintenance cost
- Downtime
- Failure types
- Robot risk
- High-risk robot groups
- Manufacturer-level risk

The objective is to transform operational and maintenance data into 
actionable business insights that can support proactive maintenance decisions.

---

# 🎯 Problem Statement

How can an organization use integrated robot, sensor, production, and 
maintenance data to identify unhealthy or high-risk robots, understand the 
major causes of downtime and maintenance costs, and support proactive 
maintenance decisions?

---

# 💡 Why This Project?

Industrial robot failures can negatively affect:

- Production continuity
- Product quality
- Maintenance expenditure
- Equipment availability
- Overall operational efficiency

A centralized analytics dashboard can help management identify where risk 
and maintenance problems are concentrated and prioritize corrective action.

---

# 🛠️ Tools & Technologies

- Microsoft Power BI
- DAX
- Microsoft Excel
- Data Modeling
- Data Visualization
- Predictive Maintenance Concepts
- Risk Analysis
- Business Intelligence

---

# 📊 Dataset

## Reference Dataset

An existing industrial predictive-maintenance dataset from Kaggle was used 
as a reference to understand the structure and variables commonly used in 
predictive-maintenance analytics.

Kaggle Reference:

https://www.kaggle.com/datasets/tatheerabbas/industrial-machine-predictive-maintenance

The Kaggle dataset was **not used as the final dashboard dataset**.

Instead, a custom synthetic dataset was created based on realistic 
industrial predictive-maintenance concepts and adapted specifically for 
industrial robot analysis.

---

# 🧩 Synthetic Dataset

The final project uses four Excel files:

### 1. Robot_Master.xlsx

Contains master information about the robot fleet.

Important fields include:

- Robot_ID
- Robot_Type
- Manufacturer

Purpose:

Provides the unique robot population and descriptive attributes used for 
filtering and grouping.

---

### 2. Sensor_Data.xlsx

Contains robot condition-monitoring data.

Important fields include:

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

Purpose:

Used to analyze robot health and relationships between sensor conditions 
and robot condition.

---

### 3. Production_Log.xlsx

Contains robot production activity.

Important fields include:

- Robot_ID
- Date
- Units_Produced
- Defect information

Purpose:

Used to analyze production volume, production trends, and defect rate.

---

### 4. Maintenance_Log.xlsx

Contains maintenance and failure information.

Important fields include:

- Robot_ID
- Date
- Maintenance_Type
- Failure_Type
- Maintenance_Cost
- Downtime_Hours

Purpose:

Used to analyze maintenance expenditure, failures, and operational downtime.

---

# 🔗 Data Model

The Power BI model connects the four main datasets using common keys.

### Main relationships

```text
                    Robot_Master
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
     Sensor_Data   Production_Log   Maintenance_Log
          │              │              │
          └──────────────┼──────────────┘
                         │
                      Date Table
