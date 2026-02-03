# Healthcare Analytics: Hospital Readmissions Analysis

## Project Overview

This project analyzes patient outcomes and identifies key factors affecting hospital **readmissions** for diabetic patients across 130 US hospitals from 1999-2008.

---

## Dataset Information

**Source:** [UCI Machine Learning Repository - Diabetes 130-US hospitals](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)

**Alternative Source:** [Kaggle Dataset](https://www.kaggle.com/datasets/brandao/diabetes/data)

### Dataset Description

The dataset contains hospital admission records for diabetic patients with three possible readmission outcomes:

1. **No readmission** - Patient was not readmitted
2. **Readmission < 30 days** - Early readmission (potentially indicates inadequate initial treatment)
3. **Readmission > 30 days** - Late readmission (may be related to patient condition rather than treatment quality)

### Dataset Dimensions

- **Total Records:** 101,766 patient encounters
- **Features:** 50 variables including:
  - Patient demographics (age, gender, race)
  - Clinical information (diagnoses, procedures, medications)
  - Hospital stay details (admission type, discharge disposition, length of stay)
  - Laboratory and medical procedures
  - Medication management
  - Readmission status (target variable)

---

## Data Characteristics

### Numerical Features Summary

Key statistics from the dataset:

| Feature | Mean | Std | Min | 25% | 50% | 75% | Max |
|---------|------|-----|-----|-----|-----|-----|-----|
| **time_in_hospital** | 4.40 days | 2.99 | 1 | 2 | 4 | 6 | 14 |
| **num_lab_procedures** | 43.10 | 19.67 | 1 | 31 | 44 | 57 | 132 |
| **num_procedures** | 1.34 | 1.71 | 0 | 0 | 1 | 2 | 6 |
| **num_medications** | 16.02 | 8.13 | 1 | 10 | 15 | 20 | 81 |
| **number_diagnoses** | 7.42 | 1.93 | 1 | 6 | 8 | 9 | 16 |
| **number_outpatient** | 0.37 | 1.27 | 0 | 0 | 0 | 0 | 42 |
| **number_emergency** | 0.20 | 0.93 | 0 | 0 | 0 | 0 | 76 |
| **number_inpatient** | 0.64 | 1.26 | 0 | 0 | 0 | 1 | 21 |

### Categorical Features

The dataset includes various categorical features such as:
- Race (Caucasian, AfricanAmerican, Hispanic, Asian, Other)
- Gender (Male, Female)
- Age groups (in 10-year brackets: [0-10), [10-20), etc.)
- Admission type, discharge disposition, admission source (mapped via IDS_mapping.csv)
- Medication changes and diabetes medication status
- Multiple medication-related features (insulin, metformin, etc.)

### Missing Data Handling

- **Weight column:** Contains significant missing values marked as "?"
- **Dimensional mapping:** Some categorical IDs require mapping from the IDS_mapping.csv file for proper interpretation

---

## Key Insights from EDA

### Hospital Stay Patterns

- **Average hospital stay:** 4.4 days (median: 4 days)
- Most patients stay between 2-6 days
- Hospital stays range from 1 to 14 days

![Average hospital stay](/images/time_in_hospital.png "Time in Hospital")


### Medical Complexity

- **Laboratory procedures:** Patients undergo an average of 43 lab procedures
- **Medications:** Average of 16 medications per patient encounter
- **Diagnoses:** Patients typically have 7-8 concurrent diagnoses
- High variation in number of medications (1-81) suggests diverse patient complexity

### Prior Healthcare Utilization

- **Inpatient visits:** Average of 0.64 prior admissions
- **Emergency visits:** Average of 0.20 prior emergency encounters  
- **Outpatient visits:** Average of 0.37 prior outpatient encounters
- Most patients (50th percentile) have no prior emergency or outpatient visits

### Treatment Patterns

- **Procedures:** Median of 1 procedure per stay
- 25% of patients have no procedures performed
- Maximum of 6 procedures observed

---

## Clinical Implications

### Early Readmission Risk (< 30 days)

Early readmissions may indicate:
- Inadequate initial treatment
- Premature discharge
- Insufficient patient education or follow-up care
- Need for treatment protocol adjustments

### Late Readmission Considerations (> 30 days)

Late readmissions may reflect:
- Natural disease progression
- Chronic condition management challenges
- Patient-specific health factors rather than treatment quality

---

## Dimensional Reference Tables

The dataset uses coded IDs for certain categorical variables. These mappings are available in the **IDS_mapping.csv** file and include:

1. **admission_type_id** - Type of hospital admission (Emergency, Urgent, Elective, etc.)
2. **discharge_disposition_id** - Patient discharge destination (Home, SNF, Hospice, etc.)
3. **admission_source_id** - Origin of hospital admission (Physician referral, Emergency, Transfer, etc.)

Reference: [Original UCI Data Source](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)

---

## Research Questions Addressed

This analysis supports investigation of:

1. **Primary Objective:** Identifying patients at risk of readmission
2. **Treatment Optimization:** Understanding factors that can be modified to reduce readmissions
3. **Resource Allocation:** Patterns in healthcare utilization and medical complexity
4. **Outcome Prediction:** Developing models to predict readmission likelihood

---

## Analysis Approach

The exploratory data analysis includes:

1. **Data Understanding**
   - Dataset structure and dimensions review
   - Feature type identification (numerical vs categorical)
   - Data quality assessment

2. **Data Preprocessing Preparation**
   - Missing value identification
   - Data type validation
   - Feature scale assessment
   - Categorical variable mapping requirements

3. **Descriptive Statistics**
   - Distribution analysis of numerical features
   - Summary statistics computation
   - Identification of data ranges and outliers

4. **Pattern Recognition**
   - Hospital stay duration patterns
   - Medical complexity indicators
   - Prior healthcare utilization trends
   - Treatment intensity variations

---

## Tools & Technologies

- **Python 3** for data analysis
- **pandas** for data manipulation
- **numpy** for numerical operations
- **matplotlib** & **seaborn** for visualization
- **scipy.stats** for statistical testing (ANOVA, Chi-square)
- Statistical methods: gaussian_kde, f_oneway, chi2_contingency

---

## Next Steps

Potential extensions of this analysis:

1. **Feature Engineering**
   - Create interaction features
   - Aggregate medication categories
   - Encode categorical variables appropriately

2. **Statistical Analysis**
   - Hypothesis testing for readmission factors
   - Correlation analysis between features
   - Survival analysis for time-to-readmission

3. **Predictive Modeling**
   - Build classification models for readmission prediction
   - Compare model performance across different algorithms
   - Feature importance analysis

4. **Treatment Insights**
   - Identify modifiable risk factors
   - Develop intervention strategies
   - Create clinical decision support tools

---

## Data Ethics & Considerations

- Patient privacy maintained through de-identification
- Historical data (1999-2008) may not reflect current medical practices
- Geographic and demographic representation should be considered
- Analysis should support clinical decision-making, not replace it

---

## Repository Structure

```
healthcare-analytics/
│
├── healthcare_analytics.ipynb    # Main analysis notebook
├── diabetic_data.csv             # Primary dataset
├── IDS_mapping.csv               # Dimensional mapping file
└── README.md                     # This file
```

---

## Contact & Contributions

For questions, suggestions, or contributions to this analysis, please open an issue or submit a pull request.

---

## License & Citation

When using this dataset, please cite:
- Original UCI ML Repository source
- Beata Strack, et al. (2014). "Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records"

---

**Last Updated:** February 2026
