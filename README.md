# CAPSTONE PROJECT: Predicting CMS Cincinnati physician reimbursement payments for 2020 (during COVID) based on historical payment information  

### Problem Statement:
Is it possible to predict CMS payments for 2020 made to physicians in Cincinnati Ohio for the top 10 most reimbursed drugs or biologics based on historical CMS payments to those physicians from 2013 through 2019?

Using the 2013-2020 General Payments data files from the Centers for Medicare and Medicaid Services (https://www.cms.gov/OpenPayments/Data/Dataset-Downloads), is it possible to use time series forecasting to predict 2020 CMS Cincinnati physician payments for these ten historically most reimbursed drugs/biologics:  Xarelto, Victoza, Humira, Levemir, Invokana, Entresto, Farxiga, Chantix, Myrbetriq and Toujeo?

Stakeholders for this analysis are drug manufacturers who need to make sales predictions and identify raw materials needs for upcoming orders.

### Executive Summary:
Can time series models do a good job of predicting 2020 CMS Cincinnati physician payments based on 2013-2019 historical CMS Cincinnati physician payments for the top 10 most common drugs/biologics?

The data for this project was pulled from the general payments data files for each year of 2013- 2020 found at the CMS website (https://www.cms.gov/OpenPayments/Data/Dataset-Downloads) for the state of Ohio.  The Cincinati years of 2018-2020 were pulled directly from the yearly general payments data file, while the Cincinnati years 2013-2017 were pulled from the Ohio data files.  All years were merged into one dataset for Cincinnati.  Variables were created for each of the top 10 most common drugs/biologics:  Xarelto, Victoza, Humira, Levemir, Invokana, Entresto, Farxiga, Chantix, Myrbetriq and Toujeo.

Payments to teaching hospitals were dropped, as were payments that represented bundled transactions.

Data representing daily payments to Cincinnati physicians were then summarized at the daily, weekly and monthly levels by date for time series analysis for each of the top 10 most common drugs/biologics.

Immediately it was noticed that there was no 2020 data for Victoza, Levemir and Toujeo, so no models were built for these insulin/diabetic drugs/biologics.

Then, 11 time series models were built for each of the remaining 7 drugs/biologics at the aggregated daily payment level.  While the RMSEs for these models were significantly lower than those models built using the aggregated weekly and monthly payments, there was not strong differentiation between the "best" model and the baseline (mean) times series model for each drug/biologic.

This pattern also held true for the 10 time series models built for each of the 7 drugs/biologics using the aggregated weekly payments as compared to the aggregated monthly payments for each of the 7 drugs/biologics. 

Eighteen models were built for the monthly aggregated payments for each of the 7 most common drugs/biologics.  These included a simple mean baseline model, a simple expontential smoothing model, 4 seasonal baseline shift models based on 4,6, 12, and 18 time periods, 4 Holt-Winters multiplicative models built on those same 4 time periods, 4 Holt-Winters additive models built on those same 4 time periods, and 4 SARIMA models built on those 4 time periods.

Humira, an immunosuppressive biologic, had high RMSEs and 2020 payments were not well predicted by time series models based on 2013-2019 historical data.  It would probably be better to predict payments based on the COVID rates during those time periods and other data.

Xarelto, a blood thinning drug, had high RMSEs and 2020 payments were not well predicted by time series models based on 2013-2019 historical data.  This drug is normally given to people who have knee and hop replacements to prevent blood clots.  Since elective surgeries were shut down during 2020, it makes sense that historical times series predictions were not great for this drug.  It would probably be better to predict payments based on the expected knee and hip surgeries and other data.

Farxiga, a drug to treat Type 2 diabetes and heart failure and chronic kidney disease in some people, also had high RMSEs and 2020 payments were not well predicted by time series models based on 2013-2019 historical data.  This is because Farxiga was considered to be a potential lifesaving treatment for COVID and payments spiked during 2020 compared to previous years.

Invokana (a 3rd line drug to treat diabetes), Entresto (a fixed dose drug to treat heart failure), Chantix (a smoking cessation drug) and Murbetriq (an overactive bladder control drug)  all had lower model RMSEs that the former 3 drugs and had somewhat better predictions for 2020 payments.  However, it is recommended that other machine learning models be built with other types of data (including other drug payments/presences) to do a more accurate job of future predictions.

#### Folders:
I: Ohio
- Please start with these files to replicate this analysis.  These files are the building blocks for the analysis.  For more details, see the immediate next section.

#### Files & Reproducing This Analysis:
Please start with the files located in the Ohio folder, with the number "00xxx".  You will need to download the respect year's general payments file from the CMS website listed under Data Source to gather Ohio data to build the analytical file.  I recommend only downloading one file at a time from the CMS website and zipping it or deleting it after you are finished to conserve space on your computer.

After you have completed downloading the data and have obtained data for Ohio, you can continue to run the files in the numbered order that they appear in this main directory (outside of the Ohio folder, where this README file is located).
#### Data Source:
The data for this project was pulled from the general payments data files for each year of 2013- 2020 found at the Centers for Medicare and Medicaid Services website (https://www.cms.gov/OpenPayments/Data/Dataset-Downloads).  These data files had most recently been updated as of 1/21/22.  The data for 2021 will not be released until June 2022.

#### Data Dictionary:
The data dictionary can be found here: ( https://www.cms.gov/OpenPayments/Downloads/OpenPaymentsDataDictionary.pdf )

#### Merging Data:
Data was pulled from each of the general payments files for 2013 through 2020 for Ohio and then from Ohio for Cincinnati.  Teaching hospitals and bundled payments were excluded from the analysis.

#### Cleaning Data:
Outliers were dropped at the indidivual physician payment date level before the data was aggregated.

#### EDA Learnings
Victoza, Levemir and Toujeo had no 2020 Cincinnati physician payments and were excluded from the analysis.

Farxiga had a huge spike in 2020 payments because it was considered a potential treatment for COVID to prevent major organs in the body from shutting down.

Please see the Capstone Presentation.pdf for graphs showing the time series distributions for each of the 7 most common drugs/biologics.

### Modeling
Eleven time series models were built for the daily aggregated payments for each of the 7 most common drugs/biologics.  These models were not deemed to be as good as the models based on the monthly aggregated payments, and so will not be discussed.

Ten time series models were built for the weeky aggregated payments for each of the 7 most common drugs/biologics.  These models were not deemed to be as good as the models based on the monthly aggregated payments, and so will not be discussed.

Eighteen time series models were built for the monthly aggregated payments for each of the 7 most common drugs/biologics.  These included a simple mean baseline model, a simple expontential smoothing model, 4 seasonal baseline shift models based on 4,6, 12, and 18 time periods, 4 Holt-Winters multiplicative models built on those same 4 time periods, 4 Holt-Winters additive models built on those same 4 time periods, and 4 SARIMA models built on those 4 time periods.

Please see the Capstone Presentation.pdf for the RMSE details of the final 18 models for each of the 7 most common drugs/biologics.

#### Limitations
COVID radically impacted medical behavior and medical supply chains and healthcare services.  Therefore, using historical payment data is not the most optimal method to predict 2020 Cincinnati CMS physician payments.

#### Conclusion
It is recommended that other types of machine learning models be explored with additional data, possibly including other types of drugs to see if 2020 Cincinnati CMS physician payments can be better predicted.
