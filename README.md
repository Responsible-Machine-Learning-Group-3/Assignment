# Model Card
### Group_3 members
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
• high priced: Binary target, whether (1) or not (0) the annual percentage rate (APR) charged for a mortgage is 150 basis points (1.5%) or more above a survey-based estimate of similar mortgages. (High-priced mortgages are legal, but somewhat punitive to borrowers. High-priced mortgages often fall on the shoulders of minority homeowners, and are one of many issues that perpetuates a massive disparity in overall wealth between different demographic groups in the US.)
• conforming: Binary numeric input, whether the mortgage conforms to normal standards (1), or whether the loan is different (0), e.g., jumbo, HELOC, reverse mortgage, etc.
• debt_to_income _ratio_std: Numeric input, standardized debt-to-income ratio for mortgage applicants.
• debt_to_income_ratio_missing: Binary numeric input, missing marker (1) for debt to income ratio std.
• income_std: Numeric input, standardized income for mortgage applicants.
• loan_amount_std: Numeric input, standardized amount of the mortgage for applicants.
• intro_rate_period_std: Numeric input, standardized introductory rate period for mortgage applicants. 1
• loan_to_value_ratio_std: Numeric input, ratio of the mortgage size to the value of the property for mortgage applicants.
• no_intro_rate_period _std: Binary numeric input, whether or not a mortgage does not include an introductory rate period.
• property_value_std: Numeric input, value of the mortgaged property.
• term 360: Binary numeric input, whether the mortgage is a standard 360 month mortgage (1) or a different type of mortgage (0)

### Evaluation data
The test data is a part of the Home Mortgage Disclosure Act data and is taken from hmda_test_preprocessed.zip,  which contains 19831 rows and 22 columns. This data set does not include the ‘high_priced’ column compared to the train data.

