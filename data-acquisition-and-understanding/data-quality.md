# Data Quality

For data quality, we care about 


* **Accuracy:** incorrect, inaccurate, transmission error, duplicates
* **Completeness:** not recorded, not available...
* **Consistency:** outliers, inconsistent data...
* **Interpretability:** how easily the data can be understood

Examining the data to correct for **missing values**, **outliers** and **noise**

  **Detection **:
  
- Use histogram to detect outliers
- Use difference between mean, mode, median to indicate outliers
- Use clustering to detect outliers
- Observe fluctuation in values


### Data Cleaning: 

 **Fixing **:
 
- Filling in Missing data
- Remove samples that are way out of range
- Use logic to  correct inconsistency
- Use prediction methods or fitting

##### Data Smoothing

Smoothing with bin (sort & replace by median/mean) or smoothing with a window (1-D filtering)



##### Normalization (Feature Scaling)
map the values of the attribute to a new value in the interval of [0,1] or any other range.

一般是把数据限定在需要的范围，比如一般都是[0, 1]，从而消除了数据量纲对建模的影响

- Min-Max:
  + 好处是make the value invariant to rigid displacement of coordinates, which is a simple linear transformation
  + 缺陷是encouter out of bounds error if future input fall outside of range, 可能会因数值范围的扩大需要重新regularization
- Z-score,zero mean normalization,归一化，也是standardization: x'=(x-mean)/std
  + 将数据正态化，使平均值0方差为1, data is modified so it has the aggregate properties of a standard normal distribution
  + Although many machine learning algorithms benefit from normalizing, decision tree method may not
  + 好处是当最大最小值未知时，或者有outlier时比较方便
  + 坏处：Normalization may not be desirable in some cases and it make samples that are dispersed in space closer to each other and hence are difficult to separate.
  + 尤其是当small differences matter, e.g. safety, money in millions
 

##### Data Reduction

Goal: improve performance without hurting accuracy too much

* Numerosity Reduction
  - regression: replace pints with function or smaller number of predictions
  - clustering:




