# DAX Measures — Industrial Robot Performance Analytics

This document lists the main DAX measures used in the Power BI dashboard.

> **Note:** Measure names and formulas should match the final PBIX. The formulas below document the project metrics used in the dashboard; adjust a column name only if the final PBIX uses a different field name.

## Robot_Master

### Total Robots
```DAX
Total Robots =
DISTINCTCOUNT(Robot_Master[Robot_ID])
```

### Total Maintenance Cost
```DAX
Total Maintenance Cost =
SUM(Maintenance_Log[Maintenance_Cost])
```

### Total Downtime Hours
```DAX
Total Downtime Hours =
SUM(Maintenance_Log[Downtime])
```

## Production_Log

### Total Units Produced
```DAX
Total Units Produced =
SUM(Production_Log[Units_Produced])
```

### Total Defective Units
```DAX
Total Defective Units =
SUM(Production_Log[Defective_Units])
```

### Defect Rate
```DAX
Defect Rate =
DIVIDE(
    [Total Defective Units],
    [Total Units Produced],
    0
)
```

### Average Efficiency
```DAX
Average Efficiency =
AVERAGE(Production_Log[Efficiency])
```

## Sensor_Data

### Average Health Score
```DAX
Average Health Score =
AVERAGE(Sensor_Data[Health_Score])
```

### Average Temperature
```DAX
Average Temperature =
AVERAGE(Sensor_Data[Temperature])
```

### Average Vibration
```DAX
Average Vibration =
AVERAGE(Sensor_Data[Vibration])
```

### Average Motor Current
```DAX
Average Motor Current =
AVERAGE(Sensor_Data[Motor_Current])
```

### Average Risk Score
```DAX
Average Risk Score =
AVERAGE(Sensor_Data[Robot Risk Score])
```

## Maintenance_Log

### Total Maintenance Events
```DAX
Total Maintenance Events =
COUNTROWS(Maintenance_Log)
```

### Average Maintenance Cost
```DAX
Average Maintenance Cost =
AVERAGE(Maintenance_Log[Maintenance_Cost])
```

### Average Downtime
```DAX
Average Downtime =
AVERAGE(Maintenance_Log[Downtime])
```

### Unplanned Maintenance Rate
```DAX
Unplanned Maintenance Rate =
DIVIDE(
    CALCULATE(
        [Total Maintenance Events],
        Maintenance_Log[Maintenance_Type] = "Unplanned"
    ),
    [Total Maintenance Events],
    0
)
```

## Risk Analysis

The dashboard uses a risk score to classify robots into:

- **High Risk**
- **Medium Risk**
- **Low Risk**

### High Risk Robot Count
```DAX
High Risk Robot Count =
CALCULATE(
    DISTINCTCOUNT(Sensor_Data[Robot_ID]),
    Sensor_Data[Risk Category] = "High Risk"
)
```

### Medium Risk Robot Count
```DAX
Medium Risk Robot Count =
CALCULATE(
    DISTINCTCOUNT(Sensor_Data[Robot_ID]),
    Sensor_Data[Risk Category] = "Medium Risk"
)
```

### Low Risk Robot Count
```DAX
Low Risk Robot Count =
CALCULATE(
    DISTINCTCOUNT(Sensor_Data[Robot_ID]),
    Sensor_Data[Risk Category] = "Low Risk"
)
```

> If the final PBIX calculates risk category through a measure rather than a `Sensor_Data[Risk Category]` column, keep the existing PBIX risk measures and use this section as documentation of the intended classification.

## Key Dashboard Metrics

The final dashboard highlights these metrics:

| Metric | Purpose |
|---|---|
| Total Robots | Overall robot population |
| Total Units Produced | Production volume |
| Defect Rate | Production quality |
| Average Health Score | Robot condition |
| Average Temperature | Thermal condition |
| Average Vibration | Mechanical condition |
| Average Motor Current | Motor/load condition |
| Total Maintenance Cost | Maintenance spending |
| Total Downtime Hours | Lost operating time |
| Average Risk Score | Overall operational risk |
| High Risk Robot Count | Robots requiring priority attention |
| Maintenance Events | Maintenance workload |

## Risk_Category Helper Table

`Risk_Category` is a small helper/disconnected table containing:

- High Risk
- Medium Risk
- Low Risk

Its purpose is to provide a clean categorical structure for risk-distribution visuals such as the funnel and donut chart. The actual risk level is derived from the project's risk logic.

## Modeling Notes

The model uses:

- `Robot_Master` as the robot dimension.
- `Date_Table` as the date dimension.
- `Sensor_Data`, `Production_Log`, and `Maintenance_Log` as operational/fact-style tables.
- `Risk_Category` as a helper table for risk-category visualization.

The model is designed to support interactive filtering by date, robot type, and manufacturer.
