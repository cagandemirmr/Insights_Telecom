**Domain:** Telecom                                                                          **Function:** Executive Management

# ABOUT THE PROJECT
AtliQo is one of the leading telecom providers in India and launched its 5G plans in May 2022 along with other telecom providers.

However, the management noticed a decline in their active users and revenue growth post 5G launch in May 2022. AtliQo’s business director requested their analytics team to provide a comparison report of KPIs between pre and post-periods of the 5G launch.
The management is keen to compare the performance between these periods and get insights that would enable them to make informed decisions to recover their active user rate and other key metrics. 
They also wonder if they can optimize their internet plans to get more active users. 

**Task:**  

Create the comparison report based on the mock-up provided. Please note the mock-up is created by a business user who has minimal idea about dashboarding.
Hence, you need to represent the insights in a much better way.
The target audience of this dashboard is top-level management - hence the dashboard should be self-explanatory and easy to understand.
Create relevant insights not provided in the metric list/mock-up dashboard to support the cause.

# "THE" DASHBOARD

![image](https://github.com/user-attachments/assets/418177e1-7c89-4605-ade0-7633cd3d71e0)
![image](https://github.com/user-attachments/assets/d8a76752-2e39-475c-a32a-0104c4a13d1c)

Moch ups do not show nothing beacause of graphical choices such as not using legends and axis labels.And compared on average revenue,average ARPU,Monthly Active Users,
Monthly Unsubscribed Users,Monthly Trends, Market Share and Top Plans.

# DATASETS

They provided 6 CSV files:

1. dim_cities
2. dim_date
3. dim_plan
4. fact_atliqo_metrics
5. fact_market_share
6. fact_plan_revenue



Column Description for dim_cities:

1. city_code: This column represents the unique code given for each city.
2. city_name: This column represents the name of the city corresponding to the city code.



Column Description for dim_date:
1. date: This column represents the starting date of each month. 
2. month_name: This column represents the month names in abbreviated form(Example: Jan, Feb, Mar, etc). We have months starting from January to September except for May.
3. before/after_5g: This column represents the unique category based on the month. We have 2 categories, Before 5G and After 5G. January to April comes represents the period before 5G implementation and June to September represents periods after 5G implementation.
4. time_period: This column represents the unique sequence number ranging from 1 to 4. These time Periods are used to make respective months comparisons before and after 5G implementation (Example: Jan vs Jun, Feb vs Jul, Mar vs Aug and Apr vs Sep)




Column Description for dim_plan:

1. plan: This column represents the various internet plans provided by the Atliqo company to the users. 
2. plan_description: This column represents the brief description about the internet plan.



Column Description for fact_atliqo_metrics:

1. date: This column represents the starting date of each month.
2. city_code: This column represents the unique pincode code given for each city.
3. company: This column represents the company name for which the data is provided. In this dataset it's only Atliqo. 
4. atliqo_revenue_crores: This column represents the revenue that Atliqo got on that particular month in that city_code in crores(unit of currency in India - 1Crore = 10 Million) from the internet users. 
5. arpu: This column represents the average revenue per user. That means on average how much revenue Atliqo generated on single user for a given time period.
6. active_users_lakhs: This column represents the number of active users who are using Atliqo's service on that particular month in that city_code in lakhs(unit of currency in India - 1 Lakh = 100,000).
7. unsubscribed_users_lakhs: This column represents the number of unsubscribed users who unsubscribed from Atliqo on that particular month in that city_code in lakhs(unit of currency in India - 1 Lakh = 100,000). 




Column Description for fact_market_share:
1. date: This column represents the starting date of each month.
2. city_code: This column represents the unique code given for each city.
3. tmv_city_crores: This column represents the total market value of the city in that month in crores(unit of currency in India) from the internet users. 
4. company: This column represents the different competitor names in the telecom industry [Atliqo, Britel, DADAFONE, PIO, Others].
5. ms_pct: This column represents the percentage of market share gained by respective company from the total market value(tmv_city) on that particular month in that city-code. 




Column Description for fact_plan_revenue:
1. date: This column represents the starting date of each month.
2. city_code: This column represents the unique code given for each city.
3. plans: This column represents the various internet plans provided by the Atliqo company to the users.
4. plan_revenue_crores: This column represents the revenue that Atliqo got from that respective plan on that particular month in that city_code in crores (unit of currency in India - 1Crore = 10 Million).

# 3 2 1 ACTION!
First of all, i import all files into Excel.I choose Excel because its easy to share with Business Director and the sum of csv file is less than 250mb.
And I turn this data into Tables to work with.
![image](https://github.com/user-attachments/assets/1a39c80f-13b2-48d2-83bd-0de72a847e46)

Than,I check  resource data to define problems such as wrong formating data,missing values etc.
In Dim date, i find a wrong formatted data.
![image](https://github.com/user-attachments/assets/f954020f-1a24-4aff-8d3f-c9dbdf380724)

I create Agragated table to merge all information.
Then i create GB Consumption table by using IFERROR,MID and FIND functions.

=IFERROR(MID([@[Plans wto abbr]],(FIND("GB",[@[Plans wto abbr]],1)-3),5),IFERROR(MID([@[Plans wto abbr]],(FIND("MB",[@[Plans wto abbr]],1)-4),6),""))

![image](https://github.com/user-attachments/assets/26857b12-d37f-4e99-8f5a-0c16f584409f)

Than i copy values to new column and remove "(" with "" and change .5 GB values to 1.5GB values with Alter command(Control+H)
![image](https://github.com/user-attachments/assets/fe246fbb-32f8-4007-acf0-05b175bff05d) 
![image](https://github.com/user-attachments/assets/6f86fa61-159c-47e7-8d94-6e141a70eb4d)

Also Add new column based on code in Country by using XLOOKUP,
![image](https://github.com/user-attachments/assets/456516fc-6dc3-434c-8a83-06d8f0e1d023)



