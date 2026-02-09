# Data Preprocessing and Statistical Analysis Solutions

This document contains step-by-step solutions for a set of data mining and statistical analysis problems, including normalization, outlier detection, and data smoothing.

---

## Table of Contents
1. [Problem 8: Min-Max Normalization (Distances)](#problem-8-min-max-normalization-distances)
2. [Problem 9: Min-Max Normalization (Prices)](#problem-9-min-max-normalization-prices)
3. [Problem 10: Outlier Detection - IQR (Visitors)](#problem-10-outlier-detection---iqr-visitors)
4. [Problem 11: Outlier Detection - Z-Score (Weights)](#problem-11-outlier-detection---z-score-weights)
5. [Problem 12: Outlier Detection - IQR (Electricity)](#problem-12-outlier-detection---iqr-electricity)
6. [Problem 13: Data Smoothing - Mean Binning](#problem-13-data-smoothing---mean-binning)

---

## Problem 8: Min-Max Normalization (Distances)

**Question:**
The distances (in km) covered by five runners are 2, 4, 6, 8, 10. Apply Min–Max normalization to scale the data between 0 and 1.

**Formula:**
$$v' = \frac{v - min_A}{max_A - min_A} (new\_max_A - new\_min_A) + new\_min_A$$
*Since the target range is [0, 1], the formula simplifies to:*
$$v' = \frac{v - min}{max - min}$$

**Parameters:**
- **Min:** 2
- **Max:** 10
- **Range (Max - Min):** 8

**Solution:**
| Original Value ($v$) | Calculation ($\frac{v - 2}{8}$) | Normalized Value ($v'$) |
| :---: | :--- | :---: |
| 2 | $(2 - 2) / 8 = 0 / 8$ | **0.00** |
| 4 | $(4 - 2) / 8 = 2 / 8$ | **0.25** |
| 6 | $(6 - 2) / 8 = 4 / 8$ | **0.50** |
| 8 | $(8 - 2) / 8 = 6 / 8$ | **0.75** |
| 10 | $(10 - 2) / 8 = 8 / 8$ | **1.00** |

---

## Problem 9: Min-Max Normalization (Prices)

**Question:**
The prices (in ₹ hundreds) of five products are 5, 10, 15, 20, 25. Apply Min–Max normalization to scale the data between 0 and 1.

**Parameters:**
- **Min:** 5
- **Max:** 25
- **Range (Max - Min):** 20

**Solution:**
| Original Value ($v$) | Calculation ($\frac{v - 5}{20}$) | Normalized Value ($v'$) |
| :---: | :--- | :---: |
| 5 | $(5 - 5) / 20 = 0 / 20$ | **0.00** |
| 10 | $(10 - 5) / 20 = 5 / 20$ | **0.25** |
| 15 | $(15 - 5) / 20 = 10 / 20$ | **0.50** |
| 20 | $(20 - 5) / 20 = 15 / 20$ | **0.75** |
| 25 | $(25 - 5) / 20 = 20 / 20$ | **1.00** |

---

## Problem 10: Outlier Detection - IQR (Visitors)

**Question:**
The following dataset shows the daily number of visitors to a website over 8 days. Identify the outliers using the Interquartile Range (IQR) method.
**Data:** 45, 48, 50, 47, 46, 43, 44, 90

**Step 1: Sort the Data**
43, 44, 45, 46, 47, 48, 50, 90

**Step 2: Calculate Quartiles**
- **Q1 (25th percentile):** Median of first half (43, 44, 45, 46) = $\frac{44 + 45}{2} = 44.5$
- **Q3 (75th percentile):** Median of second half (47, 48, 50, 90) = $\frac{48 + 50}{2} = 49$

**Step 3: Calculate IQR**
$$IQR = Q3 - Q1 = 49 - 44.5 = 4.5$$

**Step 4: Determine Fences**
- **Lower Fence:** $Q1 - 1.5 \times IQR = 44.5 - 6.75 = 37.75$
- **Upper Fence:** $Q3 + 1.5 \times IQR = 49 + 6.75 = 55.75$

**Result:**
The value **90** is greater than the Upper Fence (55.75).
**Outlier:** 90

---

## Problem 11: Outlier Detection - Z-Score (Weights)

**Question:**
The weights (kg) of 8 students are: 45, 50, 52, 48, 47, 49, 46, 80. Identify outliers using the z-score method.

**Step 1: Calculate Mean ($\mu$)**
$$\mu = \frac{45+50+52+48+47+49+46+80}{8} = \frac{417}{8} = 52.125$$

**Step 2: Calculate Standard Deviation ($\sigma$)**
$$\sigma \approx 11.48$$

**Step 3: Calculate Z-Scores**
Formula: $Z = \frac{x - \mu}{\sigma}$

Checking the suspected outlier (80):
$$Z = \frac{80 - 52.125}{11.48} \approx 2.43$$

**Result:**
Typically, a Z-score greater than +3 (or sometimes +2 for small datasets) is considered an outlier. The value 80 has a Z-score of 2.43, which is significantly higher than the rest of the data (which cluster around 0).
**Outlier:** 80

---

## Problem 12: Outlier Detection - IQR (Electricity)

**Question:**
The dataset below shows the daily electricity consumption (in units) for 8 days. Use the Interquartile Range (IQR) method to identify outliers.
**Data:** 110, 115, 112, 118, 113, 109, 108, 150

**Step 1: Sort the Data**
108, 109, 110, 112, 113, 115, 118, 150

**Step 2: Calculate Quartiles**
- **Q1:** Median of (108, 109, 110, 112) = $\frac{109 + 110}{2} = 109.5$
- **Q3:** Median of (113, 115, 118, 150) = $\frac{115 + 118}{2} = 116.5$

**Step 3: Calculate IQR**
$$IQR = 116.5 - 109.5 = 7$$

**Step 4: Determine Fences**
- **Lower Fence:** $109.5 - (1.5 \times 7) = 109.5 - 10.5 = 99$
- **Upper Fence:** $116.5 + (1.5 \times 7) = 116.5 + 10.5 = 127$

**Result:**
The value **150** is greater than the Upper Fence (127).
**Outlier:** 150

---

## Problem 13: Data Smoothing - Mean Binning

**Question:**
The daily temperatures (°C) recorded over a week are: 23, 45, 12, 18, 50, 27, 30. Use mean binning with a bin size of 3 to smooth the data.

**Step 1: Sort the Data**
12, 18, 23, 27, 30, 45, 50

**Step 2: Partition into Bins (Bin Size = 3)**
- **Bin 1:** {12, 18, 23}
- **Bin 2:** {27, 30, 45}
- **Bin 3:** {50}

**Step 3: Calculate Bin Means**
- **Mean 1:** $\frac{12+18+23}{3} = 17.67$
- **Mean 2:** $\frac{27+30+45}{3} = 34$
- **Mean 3:** $50$

**Step 4: Smooth the Data**
Replace all values in a bin with the bin mean.

**Final Smoothed Data:**
17.67, 17.67, 17.67, 34, 34, 34, 50