# Healthcare Operations Intelligence
### Claims Denial Analysis, Power BI KPI Dashboard and Denial-Risk Model

> **Note:** All data in this project is synthetic. It was created for a fictional healthcare organisation, and no real patient information is used.

## The problem

A fictional healthcare organisation had too many denied claims and slow payments, and no clear view of why. This project works out where the claims process breaks down, why claims are denied, and how much money is affected. It also shows staff which pending claims to review first.

## What I did

1. **Cleaned the data in MySQL.** The raw files had mixed date formats, duplicate IDs, trailing spaces in key columns, blank diagnosis codes and negative processing days. Every fix is recorded in a cleaning log.
2. **Built a star schema.** Claims sit in the centre, linked to members, providers, insurance plans, procedures, diagnoses and a date table.
3. **Analysed denials and payments with SQL.** Denial rate by month, provider, plan, procedure and diagnosis; financial impact; processing time.
4. **Built a five-page Power BI dashboard** with DAX measures: Executive Overview, Claims Operations, Denial Analysis, Financial, and Predictive Risk.
5. **Built a denial-risk model in Python.** A logistic regression scores each pending claim so staff can review the riskiest first.

## Key findings

- **Denial rate:** About 12% of decided claims were denied. It rose from about 11% to about 14% in July 2025.
- **Cause:** On 1 July 2025, prior authorisation became required for all Behavioral Health and Rehabilitation claims and part of Evaluation claims. Missing prior authorisation is the largest single denial reason by value.
- **Money:** About $69M of billed charges were denied. Of a roughly $48M gap between allowed and paid amounts, $41M came from denied claims.
- **Operations:** Inpatient claims take the longest to process (about 21 days against 6 to 12 for other types), and paper submissions are slower than electronic ones. 1,566 pending claims are over 30 days old.
- **Risk model:** ROC-AUC of about 0.72. The highest-risk tenth of claims had an actual denial rate of about 41%, against about 4% for the lowest-risk tenth. The model scored 6,925 pending claims.

## Tools

MySQL, Power BI, DAX, Python (Pandas), logistic regression, Excel

## Repository structure

​```
Healthcare-Operations-Intelligence/
├── data/            raw and cleaned datasets, cleaning log, data dictionary
├── sql/             schema and load, validation, cleaning and analysis scripts
├── python/          cleaning, trend analysis and denial-risk model scripts
├── outputs/         risk scores and charts
├── dashboard/       screenshots of the five Power BI pages
└── docs/            case study, data model and DAX notes
​```

## How to reproduce

1. Run the scripts in `sql/` in order to create the tables, load the raw files and apply the cleaning steps.
2. Run the scripts in `python/` to rebuild the cleaned data, the trend analysis and the risk model.
3. Open Power BI, connect it to the MySQL database, and follow the notes in `docs/` to recreate the model and measures.

## Dashboard preview

![Executive Overview](dashboard/executive_overview.png)

## About me

I'm Serena Oboh, a data analyst with a Microbiology background.
LinkedIn: https://www.linkedin.com/in/serena-oboh-390260357/
