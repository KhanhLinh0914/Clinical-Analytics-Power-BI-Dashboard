# Clinical Analytics and Organ Health Power BI Dashboard

An executive-grade, interactive Power BI analytics suite designed to evaluate patient health outcomes, lifestyle impacts such as smoking duration versus intake intensity, and cardiovascular metrics across organ conditions and age cohorts.

## Executive Summary

This analytics framework evaluates multi-organ cohorts including Heart, Lungs, Kidneys, Liver, and Overall Human Body sliced dynamically by physiological health status Damaged versus Healthy.


<img width="1218" height="737" alt="image" src="https://github.com/user-attachments/assets/b7f0b97d-e2a1-4acb-9756-9ff812db48e0" />


### Key Clinical Takeaways

1. Severe Smoking Prevalence: Over 70% to 78.8% of patients exhibiting organ damage across all primary organ groups have a current or former smoking history.
2. Obesity as a Critical Accelerant: Patients with damaged organs consistently present elevated BMI levels ranging from 28.6 to 30.7, reaching Obese Class I status in cardiac (30.7) and pulmonary (30.2) cohorts.
3. Early Onset in Vital Organs: Lung-damaged patients skew youngest among all cohorts (50.8 years), followed by Liver-damaged patients (51.7 years), driven by intense daily cigarette consumption (CPD) in young adulthood (18–28 and 29–38).
4. Universal Cardiovascular Strain: High-risk Blood Pressure and Cholesterol profiles remain uniformly distributed across all age groups from 18–28 through 69+.

## Comparative Cohort Analysis Matrix

| Target Organ / Cohort | Health Status | Total Patients | Avg Age vs Baseline | Avg BMI vs Baseline | Primary Behavioral and Clinical Drivers |
| :--- | :---: | :---: | :---: | :---: | :--- |
| Heart | Damaged | 105 | 53.6 Lower | 30.7 Higher | 78.8% Ever Smoked; highest overall BMI cohort. |
| Heart | Healthy | 183 | 52.0 Lower | 30.0 Higher | 75.9% Ever Smoked; lower severe duration exposure. |
| Human Body (Overall) | Damaged | 96 | 58.2 Higher | 29.0 Lower | Skews significantly older; reflects cumulative aging. |
| Human Body (Overall) | Healthy | 178 | 53.9 Lower | 29.9 Higher | Highest concentration of non-smoking control group (26.96%). |
| Lungs | Damaged | 90 | 50.8 Lower | 30.2 Higher | 70.2% Ever Smoked; youngest pathology cohort. |
| Lungs | Healthy | 181 | 54.7 Higher | 30.0 Higher | Baseline control group. |
| Kidney | Damaged | 105 | 53.9 Lower | 29.3 Lower | 69.5% Ever Smoked; steady BP risk across ages. |
| Kidney | Healthy | 159 | 54.6 Higher | 30.2 Higher | Baseline control group. |
| Liver | Damaged | 123 | 51.7 Lower | 28.6 Lower | High fraction of former smokers (27.54%). |
| Liver | Healthy | 176 | 53.7 Lower | 28.2 Lower | Baseline control group. |

## Detailed Clinical and Biomarkers Analysis


### 1. Dual Impact of Age and Body Mass Index (BMI)

Clinical obesity (BMI >= 30.0) emerges as one of the most prominent risk factors accelerating the degradation of vital organs, with the highest susceptibility observed in Cardiac and Pulmonary systems.

The damaged Heart cohort records the highest average BMI across all segments at 30.7, exceeding the Class I Obesity threshold. Similarly, the damaged Lung cohort exhibits a mean BMI of 30.2.

Notably, patients presenting with pathology in these two vital organs skew younger than the overall dataset average (Heart average age: 53.6 years; Lung average age: 50.8 years).

In contrast, patients exhibiting general system-wide damage (Human Body) reflect natural physiological aging, with an average age reaching 58.2 years. This distinction highlights that the compound interaction between elevated BMI and unhealthy lifestyle behaviors accelerates severe organ damage prematurely (in early 50s) long before natural age-related degeneration occurs.

### 2. Smoking Dynamics: Intake Duration (YOS) vs Intake Intensity (CPD)

A granular evaluation of smoking duration (Years of Smoking - YOS) against consumption intensity (Cigarettes Per Day - CPD) deconstructs the pathological mechanisms of organ damage:

Cumulative Exposure (YOS): Total years of smoking adhere strictly to natural biological progression, scaling proportionally with age and peaking among elderly cohorts (59–68 and 69+ age groups).

Early Acute Damage driven by Consumption Intensity (CPD): Conversely, daily intake rate (CPD) peaks heavily among younger and middle-aged cohorts (18–28, 29–38, and 39–48). In Pulmonary and Hepatic cohorts, intense daily consumption during youth acts as an acute catalyst, breaching organ defense mechanisms long before cumulative age exposure (YOS) matures.

Gender Disparity: Across all damaged organ cohorts, male patients dominate both Current and Former smoking status categories. Female patients are predominantly concentrated within the Never smoked control group.

### 3. Comprehensive Cardiovascular Risk Profile (Hypertension and Cholesterol)

Demographic-Wide Risk Distribution: Cardiovascular risk metrics (Hypertension and High Cholesterol) are no longer exclusive to elderly populations. Distribution analysis in the Cholesterol and Hypertension Risk chart shows that the High-Risk segment maintains a consistent, uninterrupted volume across all age brackets, starting as early as the 18–28 group up to 69+.

Early Metabolic Degeneration: The fact that young adult cohorts present elevated risk profiles comparable to senior demographics confirms that metabolic degeneration occurs synchronously with high early daily smoking intensity (CPD) during youth.

### 4. Organ-Specific Pathological Footprints

Pulmonary (Lungs): Represents the most immediate casualty of smoking exposure. Patients with damaged lungs are the youngest among all surveyed cohorts (50.8 years average age).

Cardiovascular (Heart): Highly sensitive to weight burden. The distinct BMI gap between damaged heart patients (30.7) and healthy heart controls (30.0) establishes body mass index as a decisive variable for cardiac resilience.

Hepatic (Liver) and Renal (Kidney): Patients with Liver damage (51.7 years average age, BMI 28.6) and Kidney damage (53.9 years average age, BMI 29.3) show noticeably lower BMI figures compared to Heart/Lung cohorts. This delivers a critical clinical insight: Liver and Kidney damage are primarily driven by chemical toxicity (smoking, alcohol, diet) and metabolic filtration overload, rather than physical structural strain from excess adipose mass (BMI).

## Dynamic DAX Measures 

The dashboard relies on custom DAX measures for dynamic cohort benchmarking and context transition overrides using ALL table scope.

Full calculations and formulas are documented separately in [DAX Measures Documentation](DAX_Measures.md).

## Data Architecture and Modeling

The reporting framework utilizes a Star Schema data model designed to optimize filter propagation and support dynamic cross filtering across organ dimensions, health conditions, and clinical metrics.


<img width="871" height="687" alt="Screenshot 2026-10-08 231747" src="https://github.com/user-attachments/assets/8218d12e-acff-4e17-9e9a-6c88c7a9cbfb" />


### Entity Relationship Details

* Fact Table: `health_dataset` contains patient level clinical telemetry, demographic profiles, smoking intensity indicators, and cardiovascular risk attributes.
* Dimension Table: `condition` provides normalized organ condition classifications mapped one to many into the central fact dataset.
* Dimension Table: `Organs` contains standardized organ categorization mapped one to many into the fact table and visual assets.
* Dynamic Visual Mapping: `Image Dataset` functions as a supporting reference table maintaining dynamic URLs mapped to organ and condition combinations for adaptive report rendering.

## Clinical Strategy and Preventive Interventions

Synthesized data demands a paradigm shift in clinical intervention strategies:

1. Lower Screening Age Thresholds: Preventive screening programs for Cholesterol and Hypertension must lower their priority age threshold to include young adults (18–28), targeting high daily consumption smokers (CPD).
2. Targeted Weight Management: Implement BMI reduction programs (BMI < 30.0) as a primary non-pharmacological intervention for patients diagnosed with early cardiac or pulmonary risk.
3. Primary Behavioral Risk Metric: Daily cigarette consumption (CPD) should be prioritized over cumulative years (YOS) as an immediate early warning indicator for acute organ pathology.
