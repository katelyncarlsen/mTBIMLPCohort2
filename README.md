# mTBIMLPCohort1

Multi-layer Perceptron developed for Cohort 1 of the metabolic biomarker data provided by Fiandaca et al., 2019.  
In the dataset, the value '0' indicates a control (no mTBI), and the value '6' indicates a test (positive mTBI). Only data collected 6 hours post injury were used (see file: "AthleteTBIData.csv".

# How It's Made

**_Language_**
- Python v3.9.21
  
**_IDE_**
- Jupyter Notebook
  
**_Libraries Used_**
- Pandas
- NumPy
- scikit-learn
- PyTorch
- MatPlotLib
- seaborn


# Workflow
- Importing/pre-processing/cleaning data
     - NOTE: Original dataset included a misspelling; "OriiginalGroupID", hence the misspelling in the code.
- VAE Implementation -- due to the fact the original dataset contained very few datapoints
     - Declaration and training
     - Yielded 20 new samples (identified through cross-validation optimization for best accuracy)
- Implementation of LASSO for feature selection and overfitting reduction
- Implementation of PCA for reduction of redudant features
- Training/testing split -> 80/20
- Output of performance metrics (see below)

# Performance Metrics at a Glance
__Training Metrics__  
<img width="300" height="690" alt="image" src="https://github.com/user-attachments/assets/fe39ba21-4969-4307-ac9f-783d9bd47371" />  
Accuracy: 0.89  

__Testing Metrics__  
<img width="300" height="690" alt="image" src="https://github.com/user-attachments/assets/d41c1d8f-2097-4302-99ea-121ba13adfdb" />  
Accuracy: 0.80  
Note: The decrease in accuracy seen here is likely due to overfitting of the model, where the machine instead simply 'memorizes' the data, rather than actually learning from it. In order to combat this in the future, steps should be taken to ensure high volume and high-quality datasets be used.  

__AUC/ROC Curve__  
<img width="300" height="403" alt="image" src="https://github.com/user-attachments/assets/75848887-19ef-4047-8734-64a12c80a0aa" />  
Interpretation: A curve closer to the upper-left corner indicates a higher AUC-ROC, which is desirable. AUC-ROC measures the model's ability to distinguish between a positive and negative case. A higher AUC-ROC indicates the model has a better ability at distinguishing between the two groups based on the data. An AUC-ROC above 0.80 indicates good/excellent model performance.  

__Confusion Matrix__  
<img width="300" height="318" alt="image" src="https://github.com/user-attachments/assets/5a8af044-0402-4a74-badb-3edc5e9c247f" />  
Notes: Upper left corner: true positive; upper right corner: false positive; lower left corner: false negative; lower right corner: true negative. Future developments should seek to minimze the number of Type II errors;  this may be achieved through a higher quality of dataset.

# Final Notes  
Future developments and expansions of this MLP should seek to increase accuracy whilst maintaining precision and recall. Type II errors should be minimized, which can be done through the optimization of precision (however, recall should also be balanced in order to reduce the risk of Type I errors). Additionally, future steps should be taken to confirm external validity of the model. The workflow in Cohort 2 was not identical, so future research could seek to replicate the workflow seen here more accurately in Cohort 2's model.  

Link to Datasets:
https://datadryad.org/dataset/doi:10.5061/dryad.559907q  
Link to study where networks deployed:
https://docs.google.com/document/d/1jEtMAgtlKWKamzhPKkx_7q6fxsLvOcL7hpjEeVZ624Y/edit?usp=sharing
