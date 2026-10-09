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
