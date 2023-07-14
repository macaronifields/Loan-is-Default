# Loan-is-Default

## Data Source
https://tianchi.aliyun.com/competition/entrance/531830/information

The data is from a credit platform's loan records, with a total data volume of over 1.2 million entries and 47 columns of variable information. Among these columns, 15 are anonymous variables. 800,000 entries will be randomly selected as the training set **train.csv**, 200,000 entries as test set A **testA.csv**, and another 200,000 entries as test set B. Additionally, sensitive information such as employmentTitle, purpose, postCode, and title will be anonymized for privacy reasons.

| Field  | Description |
| ------------- | ------------- |
| id  | Unique credit certificate identifier assigned to loan listings  |
| loanAmnt  | Loan Amount  |
| term | Loan Term(years) |
| interestRate| Loan Interest Rate |
| installment | Installment Amount |
| grade | Loan Grade |
| subGrade | Subgrade within Loan Grade|
| employmentTitle | Employment Title|
| employmentLength | Employment Length(years) |
| homeOwnership |Home Ownership Status provided by the borrower at the time of registration|
|annualIncome | Annual Income|
|verificationStatus| Verification Status|
|issueDate| Month of Loan Issuance|
|purpose| Loan Purpose Category specified by the borrower during the loan application|
|postCode| First 3 digits of the Postal Code provided by the borrower in the loan application|
|regionCode| Region Code|
|dti| Debt-to-Income Ratio|
|delinquency_2years| Number of delinquency events (30+ days past due) in the borrower's credit history within the past 2 years|
|ficoRangeLow| Lower boundary of the FICO range the borrower belongs to at the time of loan issuance
|ficoRangeHigh| Upper boundary of the FICO range the borrower belongs to at the time of loan issuance|
|openAcc| Number of open credit lines in the borrower's credit history|
|pubRec| Number of derogatory public records|
|pubRecBankruptcies| Number of public record bankruptcies|
|revolBal| Total credit revolving balance|
|revolUtil| Revolving line utilization rate, or the amount of credit the borrower is using relative to the total available revolving credit|
|totalAcc| Total number of credit lines currently in the borrower's credit history|
|initialListStatus| Initial listing status of the loan|
|applicationType| Indicates whether the loan application is an individual application or a joint application with two co-borrowers|
|earliestCreditLine| Month the earliest reported credit line was opened|
|title| Loan title provided by the borrower|
|policyCode| Publicly available policy code, where 1 indicates the loan is publicly available and 2 indicates the loan is not publicly available as a new product|
|n-series anonymous features| Anonymous features n0-n14, representing processed count features related to borrower behavior|

## Model Evaluation w/ AUC
|Model | AUC|
|----|----|
|Logistic Regression | 0.6177|
|Random Forest| 0.7093|
|XGBoost| 0.7430|
|LightGBM | 0.7422|
|CatBoost| 0.7429|
|Mean(XGB,CBT)|0.7438|
|Mean(XGB,LGB,CBT)| 0.7437|
|Sqrt(XGB\*LGB\*CBT)| 0.7439|

## Prediction
Based on the AUC above, we used multiplication of squared results from three models(*XGBoost*, *LightGBM*, *CatBoost*) to make predictions shown in **predict.csv**.


