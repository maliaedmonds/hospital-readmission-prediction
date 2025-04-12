# Hospital Readmission Prediction
ISTA 421 Exam 2

## Additional Resources (Part 1)

### Risk factors for all-cause hospital readmission following exacerbation of COPD: a systematic review and meta-analysis
A research paper on underlying causes of hospital readmission, particularly for patients with chronic obstructive pulmonary disease (COPD).\
Source: https://publications.ersnet.org/content/errev/29/156/190166.abstract

### Preventability of emergent hospital readmission
A research paper on potentially preventable hospital readmissions within 30 days of discharge, and the factors that may have contributed to their preventability.\
Source: https://www.sciencedirect.com/science/article/abs/pii/S0002934305800531

## Dataset Download (Part 2)
All data is downloaded from the [CMS Hospital Readmissions Reduction Program website](https://data.cms.gov/provider-data/dataset/9n3s-kdb3) using the Python pandas library.

## Initial Dataset Exploration (Part 3)
A brief exploration of the data, including descriptions of all 12 variables and their datatypes, is included in [step_3_assessment.ipynb](step_3_assessment.ipynb).

## Research Question (Part 4)
The CMS Hospital Readmissions Reduction Program provides data for many hosital facilities, including the state in which they reside and number of discharges, predicted/expected readmission rates, excess readmissions ratio, and true readmission count for each of 6 different procedures/conditions. To address expensive patient readmissions, this project addresses the following question:
> How accurately can we predict the readmission rate for a hospital based on its procedure-specific performance metrics?

## Question Significance (Part 5) 
For this problem, a hospital board is looking to assess their costs, save money, and predict patient readmissions, which tend to cost them a lot of money. By looking at how hospital characteristics affect total readmission counts, the board can begin to address underlying factors that contribute to higher readmission rates.

## Regression Algorithm (Part 6)
For this problem, I selected a boosting decision tree algorithm. The provided dataset contains a combination of quantitative and qualitative features, some of which may have non-linear relationships with the response variable. Boosting can handle these qualities well. In addition, boosting models learn slowly and attribute weight to important features, providing sufficient interpretability for the hospital board to learn from the model after it has been fitted (see [step_6_boosting_7_k-fold.ipynb](step_6_boosting_7_k-fold.ipynb)).

## Model Validation (Part 7)
Since the boosting model is a slow learner, I opted for K-Fold Cross Validation (as opposed to LOOCV) to reduce computational cost. This was performed using the scikit-learn KFold validator (see [step_6_boosting_7_k-fold.ipynb](step_6_boosting_7_k-fold.ipynb)).

## Project details (Part 8)

### Disclosures and Statements 
This project uses publicly available CMS data for academic purposes only. The predictive models are not intended to inform real-world clinical decisions and have not been validated for deployment in healthcare settings.\
Final data used for regression and interperetation in this model comes from a relatively small dataset (n=115). Predictions generated from this model may suffer from imbalance due to data availability and other biases in the original dataset.\
The DecisionTree model generated in the project was created with advice from Generative AI. All sources are included in the appropriate section of [step_6_boosting_7_k-fold.ipynb](step_6_boosting_7_k-fold.ipynb).
The scikit-learn library was used to perform K-fold cross validation and to generate partial dependency plots to interperet the model.

### Running the Model
All associated code is included in jupyter notebooks. To run the model, simply start the notebook and "Run All". To use the Boosting model separately, ensure that your predictors **X** and response **y** are both numpy arrays and run:
```
model = Boosting()
model.fit(X, y)
```
To view the loss curve for model fitting, run:
```
plt.plot(model.losses)
plt.xlabel('Iteration')
plt.ylabel('RSS')
plt.title('Boosting Training Loss Over Iterations')
plt.grid(True)
plt.show()
```
To print feature importance:
```
model.feature_importance(num_features=6, feature_names=['AMI', 'CABG', 'COPD', 'HF', 'HIP-KNEE', 'PN']) 
```

## Conclusions, Predictions, and Recommendations
Based on the generated model and the associated pdp plots, we see the bigest increase in readmission rates for higher cases of Chronic Obstructive Pulmonary Disease (COPD) and Heart Failure (HF), while we generally see a decrease from higher cases of hip/knee replacements. If reducing readmissions is truly the hospital's goal, it may be suitable for them to shift their focus to orthopedic cases like hip and knee replacements while avoiding chronic or high risk conditions like COPD and heart failure. In a more realistic sense, since it is still their goal to provide care for their patients, it would be more appropriate for them to look into what is causing readmissions in these particular COPD or HF patients (doctor performance, facility quality, associated research, etc.) and address them accordingly.