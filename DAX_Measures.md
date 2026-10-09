# Dynamic DAX Measures and Data Modeling

This document provides the technical reference for custom DAX measures used in the Clinical Analytics Power BI Dashboard. These measures handle dynamic benchmarking and context transition overrides.

## Comparative Age Benchmark (vs Avg Age)

Calculates the average age of the current filter context against the entire dataset average using ALL table scope.

```dax
vs Avg Age = 
VAR _CurrentAge = AVERAGE(health_dataset[Age])
VAR _OverallAge = CALCULATE(AVERAGE(health_dataset[Age]), ALL(health_dataset))
VAR _Diff       = _CurrentAge - _OverallAge

RETURN
    SWITCH(
        TRUE(),
        _Diff > 0, UNICHAR(9650) & " " & FORMAT(_CurrentAge, "0.0"),
        _Diff < 0, UNICHAR(9660) & " " & FORMAT(_CurrentAge, "0.0"),
        FORMAT(_CurrentAge, "0.0")
    )
```
## Comparative BMI Benchmark (vs Avg BMI)

Calculates the average BMI of the current filter context against the entire dataset average using ALL table scope.
```
vs Avg BMI = 
VAR _CurrentBMI = AVERAGE(health_dataset[BMI])
VAR _OverallBMI = CALCULATE(AVERAGE(health_dataset[BMI]), ALL(health_dataset))
VAR _Diff       = _CurrentBMI - _OverallBMI

RETURN
    SWITCH(


        TRUE(),
        _Diff > 0, UNICHAR(9650) & " " & FORMAT(_CurrentBMI, "0.0"),
        _Diff < 0, UNICHAR(9660) & " " & FORMAT(_CurrentBMI, "0.0"),
        FORMAT(_CurrentBMI, "0.0")
    )
```
## Age Group Calculated Column / Measure

Categorizes individual patient ages into standardized clinical demographic brackets.

```dax
Age Group = 
SWITCH(
    TRUE(),
    health_dataset[Age] >= 18 && health_dataset[Age] <= 28, "18–28",
    health_dataset[Age] >= 29 && health_dataset[Age] <= 38, "29–38",
    health_dataset[Age] >= 39 && health_dataset[Age] <= 48, "39–48",
    health_dataset[Age] >= 49 && health_dataset[Age] <= 58, "49–58",
    health_dataset[Age] >= 59 && health_dataset[Age] <= 68, "59–68",
    health_dataset[Age] >= 69, "69+",
    "Unknown"
)
