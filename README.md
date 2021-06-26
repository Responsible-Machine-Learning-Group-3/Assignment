# Model Card - Home Mortgage
## Group_3 members
Lu Li - luli@gwmail.gwu.edu
Vi Pham - vipham91@gwu.edu
Chengshu Yang - csyang6@gwu.edu
Leqi Yin - yinleqi@gwu.edu

## Introduction
### Intended Use
The model for this home mortgages data is designed to determine what specific conditions for a customer to receive high priced mortgages or not. Since the EBM model has better accuracy and more intelligibility, it could raise more revenue for real-world business companies such as insurance companies. Using this model, we could do many passes to train a small tree for many features which may be considered as potential price-affecting causes by the insurance company such as locations of the cars’ owner or years of cars. It is a very useful accurate model for large datasets with many features to analyze.
Many intended users could be homebuyers, borrowers, lenders, sellers, or insurance companies.

### Training data
The training data is taken from Home Mortgage Disclosure Act data. The folder contains two data files: hmda_train_preprocessed.zip and hmda_test_preprocessed.zip.
The training data was divided into 70% training data and 30% validation data.
There are 112253 rows and 23 columns in Train data. The validation data contains 48085 rows and 23 columns. Specific features used for model design are descripted as below:
* high priced: Binary target, whether (1) or not (0) the annual percentage rate (APR) charged for a mortgage is 150 basis points (1.5%) or more above a survey-based estimate of similar mortgages. (High-priced mortgages are legal, but somewhat punitive to borrowers. High-priced mortgages often fall on the shoulders of minority homeowners, and are one of many issues that perpetuates a massive disparity in overall wealth between different demographic groups in the US.)
* conforming: Binary numeric input, whether the mortgage conforms to normal standards (1), or whether the loan is different (0), e.g., jumbo, HELOC, reverse mortgage, etc.
* debt_to_income _ratio_std: Numeric input, standardized debt-to-income ratio for mortgage applicants.
* debt_to_income_ratio_missing: Binary numeric input, missing marker (1) for debt to income ratio std.
* income_std: Numeric input, standardized income for mortgage applicants.
* loan_amount_std: Numeric input, standardized amount of the mortgage for applicants.
* intro_rate_period_std: Numeric input, standardized introductory rate period for mortgage applicants. 1
* loan_to_value_ratio_std: Numeric input, ratio of the mortgage size to the value of the property for mortgage applicants.
* no_intro_rate_period _std: Binary numeric input, whether or not a mortgage does not include an introductory rate period.
* property_value_std: Numeric input, value of the mortgaged property.
* term 360: Binary numeric input, whether the mortgage is a standard 360 month mortgage (1) or a different type of mortgage (0)

### Evaluation data
The test data is a part of the Home Mortgage Disclosure Act data and is taken from hmda_test_preprocessed.zip,  which contains 19831 rows and 22 columns. This data set does not include the ‘high_priced’ column compared to the train data.

## Performance
### Model details
In EDM model, we select the x values as inputs which are 'debt_to_income_ratio_std', 'term_360', 'conforming', 'debt_to_income_ratio_missing', 'loan_amount_std', 'loan_to_value_ratio_std', 'no_intro_rate_period_std', 'intro_rate_period_std', 'property_value_std', 'income_std'. 
For the target y values, we use binary values in the  ‘high_priced’ column.

![Correlation](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/1.png)

The picture shows the correlations between x values and y value.
Among different interpretable models, the Explanation Boosting Machine using the ‘interpret’ package has been considered as the best remediated model because the model has the lowest test error and higher AUC.

We need to install following softwares and libraries in our machine to be able to run EBM model:
* Python - Anaconda
* InterpretML package: https://github.com/interpretml/interpret
* Installation: Python 3.6+ | Linux, Mac, Windows : pip install interpret

### Quantitative analysis
* We use AUC and AIR scores to evaluate the best remediated model (EBM).
* Our best remediated model has an AUC of 0.7752 on the training data and an AUC of 0.7709 on the validation data. AIR for Asian people vs. White people is 1.171. AIR for Black people vs. White people is 0.810. AIR for Females vs. Males is 0.955. 
* Model interpretability:
Global variable importance:

![Global variable importance](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/2.png)

Partial dependence:
![Partial dependence](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/3.png)
![Global variable importance](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/4.png)

AIR vs. AUC:
![AIR vs. AUC](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/5.png)

Variable importance for stolen model:
![Variable importance for stolen model](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/6.png)

Recession simulation results:
![Recession simulation results](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/7.png)

Global logloss residuals:
![Global logloss residuals](https://github.com/Responsible-Machine-Learning-Group-3/Assignment/blob/main/img/8.png)

* We also considered Elastic Net and Monotonic XGBoost for this project.

### Ethical considerations
#### Potential negative impacts of using EBM  model: 
* Software problems: InterpretML package has some limitations on some Python package like python 32 bit
* Larger model may take longer time to run

#### Potential uncertainties:
* Consider real-world risks: although we remediated the model, it could still discriminate against people based on their demographics.
* Uncertainty 1: for people whose race and gender are more complex (e.g. mixed race, transgender), the model might produce results that deviate from the ones we saw, which leads to uncertainties.
* Uncertainty 2: the model could be difficult to reproduce (e.g. produce the exact same AUC and predictions) unless using a virtual machine.

#### Any unexpected or results encountered during training: 
* It could give a high test error result if we are not careful about the data splitting for training and validation data. 






