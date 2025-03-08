 Task: Predict breast-cancer chemotherapy response​

 Motivation: Deciding when to use chemotherapy​

 Data: 400 records of the patients who have undergone chemotherapy​

 Derived from ACRIN-6698 sub-study of the I-SPY 2​

 Inputs: 118 binary or real-valued features about a patient​

 Outputs:​

 pCR – Whether chemotherapy was successful​

 RFS – Time until the cancer reoccurs​

 Models: Neural Networks, Random Forests​

​Background: 

Breast Cancer is most common in females in the UK​

Chemotherapy has the potential to reduce the size of tumors, but it is toxic and not always effective.​

Predicting pCR (pathological complete response) and RFS (relapse-free survival) before treatment can improve patient stratification and outcomes.

​Data:

ACRIN-6698 Sub-study of the I-SPY 2 Trial​

Dataset Features: 118 total features (11 clinical, 107 MRI-based)​

Target Variables​

Pathological Complete Response (PCR): Binary measure (1 = positive response, 0 = no response)​

Relapse-Free Survival (RFS) Time: Time in months from chemotherapy start to cancer reappearance​

​Data Pre-processing: 

Remove entries with missing target values​

Fill in missing values with mean​

Normalize feature columns​

Apply label encoding to the categorical target column​

Feature Selection: 

Purpose: Retain on the most relevant features which will improve models accuracy. Top 10 features were selected using methods below. This number included ER, Her2 and Gene.​

Common Feature Selection Methods: Recursive Feature Elimination Wrapper Method using Random Forest Classifier and Regressor. Forward Feature Selection using Entropy and Logistic / Linear Regression and Decision Tree / Random Forest Classifier and Regressor, ANOVA.​

Classification Methods: T Test and Chi Squared.​

Regression Methods: Lasso.​

Dimensionality Reduction:

Purpose: Avoid the Curse of Dimensionality, where irrelevant features lead to increase in sparsity of data requiring more computational cost and increasing likelihood of multicollinearity and overfitting of models.​

PCA Assumes Gaussian underlying distribution and that the directions of maximum variance in the data are most important for capturing structure and pattern. Data is standardised, Covariance is calculated for observed variables and so is eigen vector / eigen value computation of covariance matrix. Eigen values are amount of variance captured by each eigenvector, larger value more important Principal Component.​

LDA seeks to maximize mean and minimize variance focusing on class separabillity. Works with Labeled data.​

Results: 

Logistic regression : pCR

Training accuracy: 0.810 ± 0.007 ​

Testing accuracy: 0.797 ± 0.075 ​

Linear regression : RFS

Training accuracy: 0.063 ± 0.006 ​

Testing accuracy: -0.024 ± 0.073 ​

Elastic-net regression: RFS

Training accuracy: 0.052 ± 0.010 ​

Testing accuracy: -0.012 ± 0.063 ​

Multi-layer perceptron (scikit):

Training accuracy pCR: 0.990 ± 0.003 ​

Testing accuracy pCR: 0.778 ± 0.054 ​

Training accuracy RFS: 0.613 ± 0.029 ​

Testing accuracy RFS: -0.196 ± 0.173 ​

Multi-layer perceptron (Keras):

Training accuracy pCR: 0.860 ± 0.046 ​

Testing accuracy pCR: 0.834 ± 0.075 ​

Training accuracy RFS: 0.215 ± 0.166 ​

Testing accuracy RFS: 0.110 ± 0.216 ​

Random forest:

Training accuracy pCR: 1.000 ± 0.000 ​

Testing accuracy pCR: 0.805 ± 0.044 ​

Training accuracy RFS: 0.858 ± 0.003 ​

Testing accuracy RFS: -0.002 ± 0.109 ​

​To Run: 

FinalTestPCR.py to generate a set of predictions for PCR from Training Data

FinalTestRFS.py to generate a set of preditions for RFS from Training Data

evaluation.py to evaluate (reads model parameters for .json files) 


