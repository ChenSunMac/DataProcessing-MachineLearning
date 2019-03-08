---
description: 'Examination and Cleaning, Transformation, Data Reduction'
---

# Data Preprocessing

### Data Examination

Examine the data to correct for missing values, outliers, noise etc.

#### Histograms for Outlier Detection

Histogram is a bar plot of values vs frequency, values divided into bins \(range of values\)



### Normalization

Normalization is a mapping from $$x_0, x_1... x_n$$ of the attribute A to a new value in the interval \[0, 1\]. 

**Min-Max Normalization:** $$x'_i = \frac{x_i - \min_i x_i}{max_i x_i - \min _i x_i}$$ 

_**PRO:**_ This makes the values invariant to rigid displacement of coordinates. 

_**CON:**_ It will encounter an out-of-bounds error if a future input case for normalization falls outside of the original data range for A

**Subtract the mean:** $$x'_i = (x_i' - \bar A)$$ 

**Z-Score Normalization \(**_**standardization**_**\):** $$x'_i = (x_i' - \bar A)/\sigma_A$$ 

Scale by mean and standard deviation, Positive means value is above the mean, Negative means it is below the mean. Data is modified so that it now has the aggregate properties of a standard normal distribution μ = 0 and σ = 1.

Many analysis and machine learning algorithms benefit from normalizing your data \(decision tree methods are the main exception\)

_**Pro:**_ This method of normalization is useful when the actual minimum and maximum of attribute A are unknown, or when there are outliers that dominate the min-max normalization. Could be a good thing if you don’t mind similar points treated the same \(grades\)

**Con:  Z-score** Normalization may or may not be desirable in some cases. It may make samples that are dispersed in space closer to each other and hence are difficult to separate. This could be unacceptable when small differences matter - safety, money in millions

