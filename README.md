PROBLEM STATEMENT :
This project focuses on analyzing bank loan data to derive insights using Business Intelligence (BI) techniques. The primary aim is to identify trends, assess loan performance, and support strategic decision-making in banking operations.
PROCEDURE:
Tools Used:
•	Microsoft Excel – For initial data handling and cleaning.
•	SQL Server – To execute queries for summarization, transformation, and data validation.
•	Power BI – To build dynamic dashboards with charts, KPIs, and visuals.
Steps Followed:
1.	Data Extraction
Raw loan data was imported into Excel and SQL Server.
2.	Data Cleaning
Null values, duplicates, and inconsistencies were handled using Excel functions and SQL queries.
3.	Transformation
SQL queries were used to generate calculated fields such as DTI, interest rate %, and monthly totals. These results were validated before visualization.
4.	Validation
SQL results were compared with Power BI outputs to ensure accurate visual representation before finalizing dashboards for reporting.
5.	Preprocessing and Building Relationships To ensure accurate and flexible time-based analysis, performed structured preprocessing steps and built data model relationships in Power BI:
STEP 01: Load Dataset
Import the dataset directly from SQL Server into Power BI using the “Get Data” option.
STEP 02: Check Data Quality
Go to Transform Data → View → Column Quality to identify columns with errors, empty values, or duplicate entries.
STEP 03: Create Calendar Table (Date Table)
Create a new table using DAX to generate a continuous range of dates based on the issue_date field:
Date Table = CALENDAR(MIN(bank_loan_data[issue_date]), MAX(bank_loan_data[issue_date]))
STEP 04: Add Month Column
In the Date Table, create a new column to extract the month name:
Month = FORMAT('Date Table'[Date],"mmmm")
STEP 05: Build Relationships
Navigate to Model View and create a relationship between 
DateTable[Date] and bank_loan_data[issue_date].
STEP 06: Configure Relationship
Set the relationship as One-to-Many (1:*), with DateTable[Date] as the Primary Key and bank_loan_data[issue_date] as the Foreign Key.
DASHBOARD 1: SUMMARY
Objective: Provide a high-level overview of key loan KPIs and classify loan status as Good or Bad.
Key KPIs:
1.	Total Loan Applications – Including Month-to-Date (MTD) and Month-over-Month (MoM) trends.
2.	Total Funded Amount – Analyzing how much has been disbursed and its MoM changes.
3.	Total Amount Received – Monitoring loan repayments with MTD and MoM variations.
4.	Average Interest Rate – Including MoM changes to assess lending cost trends.
5.	Average Debt-to-Income (DTI) Ratio – To evaluate borrower financial health.
Loan Status Grid View:
•	Good Loan KPIs:
o	Good Loan Application Percentage
o	Good Loan Applications
o	Good Loan Funded Amount
o	Good Loan Total Received Amount
•	Bad Loan KPIs:
o	Bad Loan Application Percentage
o	Bad Loan Applications
o	Bad Loan Funded Amount
o	Bad Loan Total Received Amount
DASHBOARD 2: OVERVIEW
Objective: Provide visual insights into trends, borrower behavior, and regional activity using charts and maps.
Charts Used:
1.	Monthly Trends by Issue Date (Line Chart) – To observe seasonal patterns.
2.	Regional Analysis by State (Filled Map) – For understanding regional loan activity.
3.	Loan Term Analysis (Donut Chart) – To display distribution by loan terms.
4.	Employment Length (Bar Chart) – To analyze borrower stability.
5.	Loan Purpose Breakdown (Bar Chart) – To identify reasons for borrowing.
6.	Home Ownership (Tree Map) – To see how ownership influences lending.
Metrics Displayed:
•	Total Loan Applications
•	Total Funded Amount
•	Total Amount Received
DASHBOARD 3: DETAILS
Objective: Deliver a granular, detailed grid-based view of all loan-related data in one place. This dashboard serves as a consolidated interface to explore borrower profiles, individual loan metrics, and performance indicators.
SQL QUERIES EXAMPLES:
KPI’s:
Total Loan Applications
SELECT COUNT(id) AS Total_Applications FROM bank_loan_data
 
MTD Loan Applications
SELECT COUNT(id) AS Total_Applications FROM bank_loan_data
WHERE MONTH(issue_date) = 12
 
PMTD Loan Applications
SELECT COUNT(id) AS Total_Applications FROM bank_loan_data
WHERE MONTH(issue_date) = 11



 

