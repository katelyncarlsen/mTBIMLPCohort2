# mTBIMLPCohort2 - External Cohort

Multi-layer Perceptron developed for Cohort 2 of the metabolic biomarker data provided by Fiandaca et al., 2019.  
In the dataset, the value '0' indicates a control (no mTBI), and the value '1' indicates a test (positive mTBI). Per Fiandaca and colleagues, all data was collected at various times post-injury (no control for data collection; see file: "ExternalTBIData.csv").

# How It's Made

**_Language_**
- Python v3.9.21
  
**_IDE_**
- Jupyter Notebook
  
**_Libraries Used_**
- Pandas - data organization/cleaning
- NumPy - support for dataframe
- scikit-learn - basis of network (training/testing split, declaration, performance report)
- PyTorch - data management post-VAE
- MatPlotLib - data visualization
- seaborn - data visualization
- imblearn - imported for SMOTE (Synthetic Minority Undersampling Technique)


# Workflow
- Importing/pre-processing/cleaning data
     - NOTE: Original dataset included a misspelling; "OriiginalGroupID", hence the misspelling in the code.
- VAE Implementation -- due to the fact the original dataset contained very few datapoints
     - Declaration and training
     - Yielded 20 new samples (identified through cross-validation optimization for best accuracy)
- SMOTE Implementation -- due to the fact that this dataset was extremely imbalanced (more control than positive cases), which can impact the performance of a model
- Implementation of LASSO for feature selection and overfitting reduction
- Training/testing split -> 80/20
- Output of performance metrics (see below)

# Performance Metrics at a Glance  
__Testing Metrics__  
<img width="300" height="690" alt="image" src="https://github.com/user-attachments/assets/025f21b2-13dd-486a-8e66-5f9e3a7cf538" />  
Accuracy: 0.88  

__AUC/ROC Curve__  
<img width="300" height="403" alt="image" src="https://github.com/user-attachments/assets/1adb4b45-e20b-4736-b6f2-b833f58dd752" />  
Interpretation: A curve closer to the upper-left corner indicates a higher AUC-ROC, which is desirable. AUC-ROC measures the model's ability to distinguish between a positive and negative case. A higher AUC-ROC indicates the model has a better ability at distinguishing between the two groups based on the data. An AUC-ROC above 0.80 indicates good/excellent model performance.  

__Confusion Matrix__  
<img width="300" height="318" alt="image" src="https://github.com/user-attachments/assets/9618e4d7-c8bc-443d-999f-d1f737251936" />  
Notes: Upper left corner: true positive; upper right corner: false positive; lower left corner: false negative; lower right corner: true negative.  
# Final Notes  
Future developments and expansions of this MLP should seek to increase accuracy whilst maintaining precision and recall. Type II errors should be minimized, which can be done through the optimization of precision (however, recall should also be balanced in order to reduce the risk of Type I errors). Additionally, future steps should be taken to confirm external validity of the model. The workflow in Cohort 2 was not identical, so future research could seek to replicate the workflow seen here more accurately in Cohort 2's model.  

Link to Datasets:
https://datadryad.org/dataset/doi:10.5061/dryad.559907q  
Link to study where networks deployed:
https://docs.google.com/document/d/1jEtMAgtlKWKamzhPKkx_7q6fxsLvOcL7hpjEeVZ624Y/edit?usp=sharing
