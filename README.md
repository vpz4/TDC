# TDC
Tabular data curation (TDC) tool

**Structure of the TDC folder**
- hosted: a folder where the server temporarily stores the input dataset (it is removed after the execution).
- results: a folder where the results are stored.
- sample_datsets: includes a test input dataset (for demonstration purposes) in .xlsx, .csv and .json formats.
- static: includes a subfolder “images” which contains the HTML logos (from EUCAIM and from FORTH).
- .gitignore: this is needed when pushing unnecessary updates to github.
- templates: a folder which includes the HTML script (index.html) along with the logos (from EUCAIM and FORTH).
- app.py: the main script of the TDC tool.
- DockerFile: the file for building the dockerized application.
- README.md: a readme document which is needed for the GitHub repository.
- requirements.txt: the versions of the required python libraries that are necessary when building the docker.

**Functionalities**
- Select your dataset (supported formats: .csv/.json/.xlsx).
- Select a method for outlier detection (mandatory).
  - z-score: A measure of how many standard deviations a data point is from the mean of its distribution.
-- z-score (mod.): A robust measure of standard deviations for data points in a sample, typically using the median and median absolute deviation instead of the mean and standard deviation, which improves resilience to outliers. Recommended option.
-- interquartile range (IQR): A measure of statistical dispersion based on the difference between the 75th and 25th percentiles.
-- Grubb’s test: A statistical test which is used to identify outliers by comparing the extreme values to the expected values under a normal distribution.
-- Local outlier factor (LOF): An algorithm that detects outliers by measuring the local deviation of a given data point with respect to its neighbours. Note: This option is sensitive to data type errors and is currently ignored.
-- Isolation Forests: An ensemble method for anomaly detection that isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature.
-- Isolation Forests (mod.): A modified feature wise application of the Isolation Forests algorithm.
- Select a method for similarity detection (optional).
-- Spearman rank-order correlation coefficient: A non-parametric measure that assesses how well the relationship between two variables can be described using a monotonic function, based on their ranked values. Recommended option.
-- Perason’s correlation coefficient: A measure of the linear correlation between two variables, giving a value between -1 and 1 inclusive, where 1 is total positive linear correlation, 0 is no linear correlation, and -1 is total negative linear correlation.
-- Kendall’s tau: A non-parametric statistic used to measure the ordinal association between two measured quantities, reflecting the similarity of the orderings of the data when ranked by each of the quantities.
-- Covariance: A measure indicating the extent to which two random variables change in tandem, showing whether increases in one variable tend to be accompanied by increases (positive covariance) or decreases (negative covariance) in the other variable.
-- None: No similarity detection is applied.
Note: The TDC tool has a built-in functionality that calculates the Jaro distance between each pair of feature labels to estimate the lexical similarity and thus input is not requested by the user.
- Select a method for data imputation (optional).
-- Average/median: Imputes missing values using the average (mean) or median of the observed data points in the same variable, which is useful for maintaining the central tendency of the dataset.
-- Random: Fills missing entries with zeros, which can be appropriate for datasets where a zero can represent the absence of an attribute or a neutral baseline, but may skew data distributions if zero is not a meaningful value for the variable.
-- Zeros: Fills missing entries with zeros, which can be appropriate for datasets where a zero can represent the absence of an attribute or a neutral baseline, but may skew data distributions if zero is not a meaningful value for the variable.
-- None: No imputation method is applied. Recommended option.
