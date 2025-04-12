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
> How accurately can we predict the readmission rate for a hospital based on its characteristics and procedure-specific performance metrics?

## Question Significance (Part 5) 
For this problem, a hospital board is looking to assess their costs, save money, and predict patient readmissions, which tend to cost them a lot of money. By looking at how hospital characteristics affect total readmission counts, the board can begin to address underlying factors that contribute to higher readmission rates.

