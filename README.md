# Admission Scores vs. Academic Performance in Higher Education
### An Exploratory Educational Data Analysis of Public and Private University Cohorts in Egypt

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Data Analysis](https://img.shields.io/badge/Data%20Analysis-EDA-blue)
![Statistics](https://img.shields.io/badge/Statistics-Descriptive%20Analysis-green)
![Status](https://img.shields.io/badge/Status-Exploratory-orange)

## 📌 Project Overview

Does a student's secondary-school admission score relate to their academic performance three years later?

This project explores that question through an analysis of two third-year university cohorts in Egypt: a public university medicine cohort and a private university cohort.

The reported admission thresholds differ substantially:

- **Public university cohort:** Alexandria University's Faculty of Medicine, with a reported admission threshold of 92.93% in the General Secondary Education Certificate.
- **Private university cohort:** A private university cohort with a reported minimum admission requirement of 50%.

The study investigates differences in the available academic outcomes, including percentage distributions, grade classifications, GPA statistics, and student-level performance patterns.

One of the most striking descriptive observations is that the public medicine dataset contains a large proportion of students classified as *Excellent*, while the preliminary overall GPA analysis of the private cohort classified no students in the *A* category.

The central objective is to investigate whether the observed differences are associated with admission requirements, while recognizing that university type, academic discipline, curriculum, assessment methods, and grading systems may also contribute to the differences.

**This is an exploratory observational study, not a causal evaluation of public versus private higher education.**

## 🎯 Research Objectives

1. Explore the relationship between university admission requirements and subsequent academic performance.
2. Analyze the distribution of third-year academic outcomes in each cohort.
3. Compare measures of central tendency and variability where the underlying measures are comparable.
4. Examine grade distributions and the prevalence of high academic achievement.
5. Investigate the differences between the cohorts without treating their grading systems as equivalent by default.
6. Identify the limitations of using admission thresholds to explain academic performance.
7. Establish a reproducible workflow for educational data collection, cleaning, analysis, and visualization.

## ❓ Research Questions

- How are academic outcomes distributed within each cohort?
- What differences are visible in the mean, median, and variability of student results?
- How common are high grades in each cohort under its own grading system?
- Do the available data support a meaningful comparison between the cohorts?
- Can differences in admission thresholds be linked to later academic outcomes using the available evidence?
- What additional student-level data would be needed to test the relationship between individual admission scores and university performance?

## 📊 Dataset Description

### Dataset A: Public Medicine Cohort

| Attribute | Description |
|---|---|
| Institution | Alexandria University |
| Institution type | Public |
| Faculty | Medicine |
| Academic level | Third year |
| Initial records | 501 |
| Records with valid final percentages | 484 |
| Reported admission threshold | 92.93% |
| Final percentage scale | 0–100% |
| Main outcome | Third-year final percentage and recorded grade |

The examination results were collected from an online source using **web scraping** and organized into a structured dataset for analysis.

Link : https://med.alexu.edu.eg/results/level_results.php?level_id=237

The dataset includes student identifiers, subject-level examination components, total marks, final percentages, recorded grades, and credit-related fields.

#### Public Cohort: Validated Descriptive Results

| Metric | Result |
|---|---:|
| Records in source dataset | 501 |
| Students with valid final percentages | 484 |
| Mean final percentage | 88.41% |
| Median final percentage | 89.98% |
| Standard deviation | 6.08 percentage points |
| Minimum final percentage | 65.62% |
| 25th percentile | 84.93% |
| 75th percentile | 92.96% |
| Maximum final percentage | 97.24% |
| Students with at least 92.93% in third-year results | 122 |
| Percentage at or above 92.93% | 25.21% |

#### Public Cohort: Recorded Grade Distribution

| Recorded grade | Students | Percentage of 484 valid-percentage records |
|---|---:|---:|
| Excellent | 362 | 74.79% |
| Very Good | 104 | 21.49% |
| Good | 18 | 3.72% |
| **Total** | **484** | **100.00%** |

The grade counts above are based on records with valid final percentages. The separate source file contains additional records with administrative or incomplete-result statuses.

#### Public Cohort: Percentage Bands

| Final percentage band | Students | Percentage |
|---|---:|---:|
| Below 50% | 0 | 0.00% |
| 50%–below 60% | 0 | 0.00% |
| 60%–below 70% | 3 | 0.62% |
| 70%–below 80% | 52 | 10.74% |
| 80%–below 90% | 187 | 38.64% |
| 90%–100% | 242 | 50.00% |

These bands are descriptive categories for analysis and do not replace the university's official grade classifications.

#### Public Cohort: Record Validation

The original file contains 501 records. Of these, 484 have valid numeric percentages and 17 contain nonnumeric final-result or administrative statuses.

| Recorded status among the 17 records | Count |
|---|---:|
| راسب | 10 |
| incomplete | 4 |
| غ ب | 2 |
| غ | 1 |
| **Total** | **17** |

These statuses must not automatically be treated as equivalent. In particular, an incomplete result or an administrative absence code is not necessarily the same as a confirmed final failure.

The final failure rate requires a validated definition of failure and an appropriate denominator.

### Dataset B: Private University Cohort

| Attribute | Description |
|---|---|
| Institution type | Private |
| Academic level | Third year |
| Students | 59 |
| Reported minimum admission requirement | 50% |
| Subjects in the source dataset | 12 |
| Main recorded outcomes | Letter grades and result statuses |
| Overall analysis | Credit-weighted GPA and letter-grade classification |

The private cohort dataset contains letter grades and result statuses for 12 subjects. The analysis uses a grade-point mapping and credit-weighted calculations to derive a provisional overall GPA.

#### Preliminary Private Cohort GPA Results

The following results come from the initial GPA analysis and should be treated as provisional until all subject credits and grade-classification rules have been validated.

| Metric | Preliminary result |
|---|---:|
| Students | 59 |
| Credits included in the initial calculation | 24 |
| Mean GPA | 2.173 |
| Median GPA | 2.305 |
| Minimum GPA | 0.000 |
| Maximum GPA | 3.278 |
| Students classified as A | 0 |
| Students classified as B | 5 |
| Students classified as C | 24 |
| Students classified as D | 14 |
| Students classified as E | 11 |
| Students classified as F | 5 |

**Important:** The initial calculation omitted Diagnosis Radiology from the credit-weighted GPA because its credit value had not been incorporated. The complete credit structure has since been verified, but the figures above must be recalculated using that verified structure before being presented as final results.

The private cohort's *A* classification is also not automatically equivalent to the public cohort's *Excellent* classification.

## 🔍 Methodology

### 1. Data Collection

- Obtain publicly available third-year examination results for the public medicine cohort.
- Use web scraping to extract and structure the available examination records.
- Load the private cohort's student-grade dataset for analysis.
- Preserve the original recorded grades and result statuses for validation.

### 2. Data Cleaning and Validation

- Standardize column names and whitespace.
- Inspect missing values, duplicates, and data types.
- Convert final percentages to numeric values where valid.
- Separate valid academic results from incomplete and administrative statuses.
- Validate student counts and summary statistics.
- Review the relationship between final percentages and recorded grade categories.

### 3. Feature Preparation

Prepare student-level variables, including:

- Final percentage.
- Recorded final grade.
- Overall GPA for the private cohort.
- Subject-level grades and result statuses.
- Subject credit hours.
- Indicators derived from validated academic outcomes.

Derived features must retain clear definitions and must not be interpreted as official university classifications unless they match the source's rules.

### 4. Exploratory Data Analysis

The exploratory analysis includes:

- Mean, median, standard deviation, minimum, and maximum.
- Percentile analysis.
- Histograms of final percentages.
- Box plots for distribution and outlier inspection.
- Grade-frequency tables.
- Percentage-band distributions.
- Subject-level grade-point and failure-rate analysis for the private cohort.
- Validation of the final-result records.

### 5. Cross-Cohort Comparison

A fair comparison requires a careful assessment of whether the outcome measures are comparable.

The analysis should distinguish between:

- Raw percentages from the public medicine cohort.
- Letter grades and credit-weighted GPA from the private cohort.
- Official grade classifications.
- Descriptive categories created for analytical purposes.

Where a defensible common measure is unavailable, the results should be reported separately rather than combined into an artificial common scale.

### 6. Statistical Analysis

Depending on the availability and comparability of the underlying data, further analysis may include:

- Distribution comparisons.
- Confidence intervals for descriptive estimates.
- Appropriate two-sample statistical tests.
- Effect sizes.
- Nonparametric comparisons when their assumptions are appropriate.
- Student-level correlation analysis if individual admission scores and subsequent academic outcomes become available.

Statistical significance alone would not establish that admission scores or university type caused the observed outcomes.

## 📈 Visualizations

The project includes or is designed to include:

1. **Final Percentage Distribution** — a histogram of the public cohort's final percentages.
2. **Percentage Box Plot** — a view of the median, spread, and potential outliers.
3. **Final Grade Distribution** — counts and percentages of recorded grade categories.
4. **Percentage Bands** — the number of students within defined percentage ranges.
5. **Percentages by Recorded Grade** — a comparison of the distribution of percentages within each grade.
6. **Private Cohort GPA Distribution** — a histogram of credit-weighted GPAs after final credit validation.
7. **Private Cohort Subject Analysis** — subject-level average grade points and validated pass/fail rates.
8. **Cross-Cohort Comparison Charts** — to be produced only after the comparison metrics and grading definitions have been validated.

All charts should include clear titles, axis labels, units, and sample sizes where relevant.

## 🧠 Preliminary Findings

### Finding 1: A high concentration of Excellent grades in the public cohort

Among the 484 public medicine records with valid final percentages, 362 students (74.79%) are classified as Excellent in the source data.

This is a substantial descriptive feature of the observed cohort.

### Finding 2: A high proportion of public cohort students achieved at least 90%

A total of 242 students (50.00% of the valid-percentage records) achieved a third-year final percentage of at least 90%.

### Finding 3: The public cohort's mean and median differ

The mean final percentage is 88.41%, while the median is 89.98%.

The median being higher than the mean suggests that lower-performing observations may be pulling the mean downward. This is a descriptive interpretation, not a conclusion about the causes of the distribution.

### Finding 4: The private cohort's preliminary GPA analysis contains no A classifications

The initial analysis classified no students in the overall A category. This finding must be recalculated after applying the verified credit structure and checking the grade-point mapping and overall classification thresholds.

### Finding 5: The cohorts cannot be compared by headline grade counts alone

The public cohort's Excellent category and the private cohort's overall A classification come from different grading systems and academic programmes.

The difference is worth investigating, but a direct comparison of these percentages would be misleading without a defensible harmonization method.

## ⚠️ Limitations

1. **Different academic disciplines:** The cohorts study different subjects and may have different curricula, assessments, and academic expectations.
2. **Different grading systems:** Percentages and credit-weighted GPAs are not directly interchangeable.
3. **Admission thresholds are not individual scores:** The reported minimum admission thresholds do not reveal each student's actual secondary-school score.
4. **Different cohort sizes:** The public cohort has 484 valid-percentage records, while the private cohort contains 59 students.
5. **Incomplete or administrative records:** Some public cohort records have no valid numeric final percentage. Their final status must be validated.
6. **GPA validation:** The private cohort's preliminary GPA statistics require recalculation using the complete verified credit structure.
7. **Selection effects:** Students choose or enter different programmes for many reasons, and the observed groups may differ in more than admission thresholds.
8. **No causal identification:** A comparison of two cohorts cannot isolate the effect of admission requirements or university type.
9. **Data provenance:** The public results were collected from an online source through web scraping. The source, extraction date, and transformation process should be documented in the project.
10. **Privacy:** Student identifiers should be removed or anonymized in public datasets and visualizations unless publication is authorized and appropriate.

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- Web Scraping
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Descriptive Statistics
- Data Visualization
- Statistical Analysis

## 📂 Suggested Repository Structure

```text
admission-vs-academic-performance/
│
├── data/
│   ├── README.md
│   └── processed/
│
├── notebooks/
│   ├── 01_public_cohort_data_cleaning.ipynb
│   ├── 02_public_cohort_eda.ipynb
│   ├── 03_private_cohort_eda.ipynb
│   └── 04_cross_cohort_comparison.ipynb
│
├── src/
│   ├── data_cleaning.py
│   ├── feature_engineering.py
│   └── analysis.py
│
├── visualizations/
│
├── reports/
│
├── requirements.txt
└── README.md
```

## 🚀 Future Work

- Recalculate the private cohort's GPA using the complete verified credit structure.
- Confirm all grade-point mappings and overall grade thresholds.
- Validate public cohort result statuses and the final failure rate.
- Document the online source and web-scraping workflow.
- Remove or anonymize student identifiers.
- Compare only defensible common outcome measures.
- Obtain individual admission scores where legally and ethically available.
- Test student-level associations between admission scores and subsequent academic outcomes.
- Use appropriate statistical tests, confidence intervals, and effect sizes.
- Extend the study to additional cohorts and academic programmes.

## 📝 Conclusion

This exploratory study investigates whether substantial differences in university admission thresholds are associated with differences in later academic outcomes.

The public medicine cohort shows a high proportion of Excellent classifications in the recorded third-year results. The private cohort's preliminary GPA analysis shows a different overall grade distribution, but its statistics require final recalculation and validation.

The results provide a useful starting point for educational data analysis. However, they do not establish that admission scores or university type alone explain the observed differences.

**The key research challenge is to determine whether the observed differences remain meaningful after accounting for grading systems, academic disciplines, cohort characteristics, and other relevant factors.**

---

**Project focus:** Educational Data Analysis · University Admissions · Academic Performance · Python · Web Scraping · Statistical Reasoning
