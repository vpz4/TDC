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


**Input & Output**
- Input: A tabular dataset in .csv or .xlsx or .JSON format.
- Output: The TDC tool generates the following reports:
  - a data quality evaluation report which summarises useful metadata and feature-level diagnostics,
  - a curated dataset which is the original dataset where the problematic fields (e.g., outliers, missing values, data inconsistencies) are highlighted using colour coding,
  - a clean curated dataset which is the curated dataset where the features with bad quality (i.e. with more than 30% missing values) are automatically removed,
  - a similarity  report which summarises the highly correlated pairs of features (if any), and
  - another similarity report which summarises the lexically similar pairs of features (if any).
  - a structured .json file which includes all the information from the previous reports in a structured way to support the work of programmers towards the development of customised front-end interfaces.


**Functionalities**
- Select your dataset (supported formats: .csv/.json/.xlsx).
- Select a method for outlier detection (mandatory).
  - z-score: A measure of how many standard deviations a data point is from the mean of its distribution.
  - z-score (mod.): A robust measure of standard deviations for data points in a sample, typically using the median and median absolute deviation instead of the mean and standard deviation, which improves resilience to outliers. Recommended option.
  - interquartile range (IQR): A measure of statistical dispersion based on the difference between the 75th and 25th percentiles.
  - Grubb’s test: A statistical test which is used to identify outliers by comparing the extreme values to the expected values under a normal distribution.
  - Local outlier factor (LOF): An algorithm that detects outliers by measuring the local deviation of a given data point with respect to its neighbours. Note: This option is sensitive to data type errors and is currently ignored.
  - Isolation Forests: An ensemble method for anomaly detection that isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature.
  - Isolation Forests (mod.): A modified feature wise application of the Isolation Forests algorithm.
- Select a method for similarity detection (optional).
  - Spearman rank-order correlation coefficient: A non-parametric measure that assesses how well the relationship between two variables can be described using a monotonic function, based on their ranked values. Recommended option.
  - Perason’s correlation coefficient: A measure of the linear correlation between two variables, giving a value between -1 and 1 inclusive, where 1 is total positive linear correlation, 0 is no linear correlation, and -1 is total negative linear correlation.
  - Kendall’s tau: A non-parametric statistic used to measure the ordinal association between two measured quantities, reflecting the similarity of the orderings of the data when ranked by each of the quantities.
  - Covariance: A measure indicating the extent to which two random variables change in tandem, showing whether increases in one variable tend to be accompanied by increases (positive covariance) or decreases (negative covariance) in the other variable.
  - None: No similarity detection is applied.
Note: The TDC tool has a built-in functionality that calculates the Jaro distance between each pair of feature labels to estimate the lexical similarity and thus input is not requested by the user.
- Select a method for data imputation (optional).


**Related publications**
- Pezoulas, Vasileios C., et al. "Medical data quality assessment: On the development of an automated framework for medical data curation." Computers in biology and medicine 107 (2019): 270-283.
- Pezoulas, Vasileios C., et al. "Enhancing medical data quality through data curation: A case study in primary Sjögren's syndrome." Clin. Exp. Rheumatology 37.3 (2019): 90-96. 
- Pezoulas, Vasileios C., et al. "Distilling knowledge from high quality biobank data towards the discovery of risk factors for patients with cardiovascular diseases and depression." 2023 IEEE EMBS International Conference on Biomedical and Health Informatics (BHI). IEEE, 2023. 
- Pezoulas, Vasileios C., et al. "A computational pipeline for data augmentation towards the improvement of disease classification and risk stratification models: A case study in two clinical domains." Computers in Biology and Medicine 134 (2021): 104520.
