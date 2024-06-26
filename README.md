# Credit_Card_Financial_Dashboard
## Power BI dashboard
### Project Objective:
To develop a comprehensive credit card weekly dashboard that provides real time insights into key performance metrics and trends, 
enabling stakeholders to monitor and analyze credit card operations effectively.

### Import data to SQL Database:
1. Prepare CSV Files
2. Create new database in SQL
3. Import csv files into SQL tables

### DAX Queries:
- Revenue = 'Credit Card Detail'[Annual_Fees] + 'Credit Card Detail'[Total_Trans_Amt] + 'Credit Card Detail'[Interest_Earned]

- AgeGroup = SWITCH(
  TRUE(),
  'customer_detail'[Customer_Age]<30,"20-30",
  'customer_detail'[Customer_Age]>=30 && 'customer_detail'[Customer_Age]<40, "30-40",
  'customer_detail'[Customer_Age]>=40 && 'customer_detail'[Customer_Age]<50, "40-50",
  'customer_detail'[Customer_Age]>=50 && 'customer_detail'[Customer_Age]<60, "50-60",
  'customer_detail'[Customer_Age]>=60,"60+",
  "unknown")

- Week_num2 = WEEKNUM('Credit Card Detail'[Week_Start_Date])

- Current_Week_Revenue = CALCULATE(
              SUM('Credit Card Detail'[Revenue]),
              FILTER(
                  ALL('Credit Card Detail'),
                  'Credit Card Detail'[Week_num2] = MAX('Credit Card Detail'[Week_num2])))

- Previous_Week_Revenue = CALCULATE(
             SUM('Credit Card Detail'[Revenue]),
             FILTER(
                 ALL('Credit Card Detail'),
                 'Credit Card Detail'[Week_num2] = MAX('Credit Card Detail'[Week_num2])-1))

### Project Insights: Week 53(31 Dec):

Week over Week Change:
1. Revenue increased by 28.8%
2. Total Transaction Amount and count increased by 35% and 3.4%
3. Customer count increased by  12.8%

Overview YTD:
1. Overall revenue is 57M
2. Total interest is 8M
3. Total transaction amt is 46M
4. Male customers are contributing more in revenue 31M, female 26M
5. Blue & Silver credit card are contributing 93% of overall transactions
6. TX, NY & CA is contributing to 68%
7. Overall activation rate is 57.5%
8. Overall Deliquent rate is 6.06%
