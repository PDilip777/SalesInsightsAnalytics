# Sales Insights 

Dashboard Web Link: https://app.powerbi.com/links/ejUX7izV4f?ctid=6a70f02d-5afe-4fe6-a714-3765f4461164&pbi_source=linkShare

Problem statement:

AtliQ hardware is a company which delivers computer hardware & peripheral Manufacturers to his clients, which has several branches throughout India. The sales director of the company is facing a lot of issues in terms of understanding how the business is performing and what are all the problem company is facing currently as the sales are not as expected and declining gradually. And whenever he calls the regional managers to get the current status of the sales and market, verbally telling current status and sales director he not understanding performance and regional managers sended the tons of Excel files, which made the sales director more frustrated. Humans are not comfortable in consuming numbers from excel files, which is obvious reason for the frustration.

Solution:

Sales director of the AltiQ hardware, decided to build a PowerBI Dashboard for converting the data into visual representation to make data driven decisions. So, he hired a team of data people to complete this task.

About Dataset:

The dataset provided for this project in SQL database named” SALES in this Customers Table, Markets Table, Products Table, Transactions Table”.

Steps Followed in this project:

1. Performed a high-level analysis of data in SQL to get better understanding over the data.
2. Connected the SQL data set to PowerBI.
3. Performed ETL and data cleaning on the imported data.
4. In the currency there were two types of currencies in transactions, performed currency conversion to make all the currency type same.
5. Created measure for needs and used them for creating visuals in PowerBi.
6. After the initial report reviewed by the stakeholders, made changes to the report based on the review commends.


Data Analysis (DAX):

1. Total profit Margin = Sum ([Total profit Margin]).
2. Profit Margin % = DIVIDE ([Total profit Margin], [Revenue], 0).
3. Profit Margin Contribution % = DIVIDE ([ Total Profit Margin], calculate ([Total Profit Margin], ALL ('Products Table), ALL ('Customer Table'), All ('Markets Table '))).
4. Revenue Contribution % = DIVIDE ([Revenue], CALCULATE ([Revenue], ALL ('Products Table'), All ('Customer Table'), All ('Markets Table'))).
5. Revenue Ly (Last year) = Calculate ([ Revenue], Same period last year (Date Table[date])).
6. Sales Qty = sum ([Sales Qty]).
7. Revenue = sum([Revenue]).
8. Target Diff = [Profit Margin %]- [Profit Target Value] Create Parameter for Profit Target.

=>Performed a high-level analysis of data in MYSQL to get better understanding over the data?

    ## Sales Insights Data Analysis Project

   ### Data Analysis Using MYSQL

1. Show all customer records

    SELECT * FROM customers; 

2. Show total number of customers

    SELECT count (*) FROM customers; 

3. Show transactions for Chennai market (market code for Chennai is Mark001)

    SELECT * FROM transactions where market code='Mark001’; 

4. Show distinct product codes that were sold in Chennai

    SELECT distinct product code FROM transactions where market code='Mark001’;

5. Show transactions where currency is US dollars

    SELECT * from transactions where currency="USD"

6. Show transactions in 2020 join by date table

    SELECT transactions. *, date. * FROM transactions INNER JOIN date ON transactions.order_date=date. Date where date. Year=2020; 

7. Show total revenue in year 2020,

    SELECT SUM (transactions. sales amount) FROM transactions INNER JOIN date ON transactions. order_date=date. Date where date. Year=2020 and transactions. Currency="INR\r" or transactions. Currency="USD\r”;
	
8. Show total revenue in year 2020, January Month

    SELECT SUM (transactions. sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date. Date where date. Year=2020 and date. month name="January" and (transactions. Currency="INR\r" or transactions. Currency="USD\r"); 

9. Show total revenue in year 2020 in Chennai

    SELECT SUM (transactions. sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001”; 


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column. (This is used in currency cleaning in power query.

 = Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount] *75 else [sales_amount], type any).



Dashboard or Report:
                     •	This Reports has Potential to increase revenue by at least 7% in the upcoming quarter.

![Sales Insights Dashbords-page-001](https://github.com/PDilip777/SalesInsightsAnalytics/assets/157594735/f1e93847-eb40-4326-ba55-1963055966e9)


![Sales Insights Dashbords-page-002](https://github.com/PDilip777/SalesInsightsAnalytics/assets/157594735/5b5c74fd-ac7a-4927-bc05-a6e5d4be0783)


![Sales Insights Dashbords-page-003](https://github.com/PDilip777/SalesInsightsAnalytics/assets/157594735/ce6420e7-6e2f-4f53-841d-7023b5f83792)


Tools, Software and Libraries:

1. MYSQL
2. Microsoft Power BI
3. Power Query Editor
4. DAX Language
