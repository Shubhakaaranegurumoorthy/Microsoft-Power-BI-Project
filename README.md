# Sales Insights-Dashboard

## Problem Statement
AtliQ Hardware is a company which supplies computer hardware and he's facing a lot of challenges so the challenge is this 
the market is growing dynamically and then he's facing issues in terms of 
tracking the sales in this dynamically growing market and he's having issues 
with the insights of his business so he has this Regional Managers for North 
India South India and Central India whenever he wants to get insights in 
these three regions he would call these people and on the phone 
this local regional manager will give him some insights, the problem is the conversation which are happening they're 
all verbal and you know there is this habit that all the managers have which 
is they try to paint a rosy picture you know they don't want to look bad so 
sometimes they will lie or even if they are not lying they will try to sugarcoat 
the facts so bhavan patel who is a sales director is extremely frustrated and he wants a interactive dashboard so that he can see it anywhere and at anytime.


### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`
