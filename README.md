## Pizza Sales Analysis Project

### Overview
This data analyst portfolio project explores pizza sales data to uncover valuable insights regarding weekly and monthly trends, quantities ordered, and the identification of the best and worst-selling pizzas etc. The project aims to demonstrate proficiency in data analysis using SQL for data manipulation and Power BI for data visualization.

### Data Sources
The analysis utilizes a dataset sourced from kaagle. This dataset contains comprehensive information on pizza sales, including pizza types, quantities, prices, and dates etc.

### Tools and Technologies
MS SQL Server
- **Ms SQL Server**:Ms SQL Server was employed for data extraction, transformation, and analysis, enabling efficient querying of the dataset to derive meaningful insights.
- **Power BI**: Power BI was utilized for creating interactive and visually appealing reports and dashboards to communicate the analysis results effectively.
- **Ms Excel** : Microsoft Excel played a crucial role in data preprocessing and cleaning, ensuring the dataset's accuracy and completeness.


### Analysis Steps
1. **Data Preprocessing**: The initial step involved data cleaning and transformation to ensure the dataset's accuracy and completeness.
2. **Exploratory Data Analysis (EDA)**: Exploratory data analysis was performed to gain insights into the dataset, including summary statistics, data distribution, and identifying potential outliers.
3. **Weekly and Monthly Trends Analysis**: This section of the analysis focuses on identifying sales trends over different time periods, such as weekly and monthly patterns in pizza orders and revenue.
4. **Best and Worst Seller Pizza Analysis**: Through careful analysis, we determined the best-selling and worst-selling pizzas based on various criteria, such as quantity sold or revenue generated.

### Visualizations
Visualizations were created using Power BI to provide a clear and interactive representation of the analysis findings. The Power BI report includes charts, graphs, and tables that facilitate the understanding of trends and pizza performance.

### Key Findings
Some of the key findings from this analysis include:
- Identification of the top-selling pizza varieties.
- Insights into peak ordering times and days of the week.
- Understanding the impact of pricing strategies on sales.

### How to Use This Project
To replicate or explore this project:
1. Access the datasetwhich I have add in the repository.
2. Follow the SQL queries and analysis steps detailed in this repository.
3. Download and open the Power BI report to interact with the visualizations and explore the findings.

### Contact Information
For questions, feedback, or collaboration opportunities, please feel free to reach out:
- Arockia Pauline A
- Email: arockiapauline2@gmail.com
- LinkedIn: [(6) Arockia Pauline | LinkedIn](https://www.linkedin.com/in/arockia-pauline/)

### Future Improvements
Potential enhancements for this project include:
- Incorporating additional data sources for a more comprehensive analysis.
- Implementing machine learning models for sales forecasting.
- Creating a web-based dashboard for real-time tracking of pizza sales.



**Problem Statement
KPI’s Requirement**
1.	Total Revenue
2.	Average total order value
3.	Total pizza sold
4.	Total orders
5.	Average pizzas per order
   
**Chart Requirement**
1.	Daily trend for total orders – bar chart
2.	Monthly trend for total orders – line chart
3.	Percentage of sales by pizza category – pie chart
4.	Percentage of sales by pizza size – pie chart
5.	Total pizzas sold by pizza category – funnel chart
6.	Top 5 best sellers from revenue, total orders and  quantity 
7.	Bottom 5 sellers from revenue, total orders and  quantity 

**Softwares Used**
MS excel
MS Sql Server
Power Bi



**Kpi**
**1.total revenue**
 select sum(total_price) as total_revenue from pizza_sales
 

**2.Average order value**
 select (sum(total_price)/ count(distinct(order_id))) as avg_order_value from pizza_sales
 
3.Total Pizza Sold
select * from pizza_sales
 select (sum(quantity)) as total_pizza_sold from pizza_sales
 
**4. Total orders**
select * from pizza_sales
 select count(distinct(order_id)) as total_orders from pizza_sales
 
**5.Average pizzas per order**
select * from pizza_sales;
select cast(cast(sum(quantity) as decimal(10,2))/
cast(count(distinct(order_id)) as decimal(10,2)) as decimal(10,2)) as avg_pizza_per_order from pizza_sales

 




**Problem statement**
**1.	Daily trends for total orders**
select * from pizza_sales;
select datename(dw, order_date) as order_day, count(distinct order_id) as total_orders
    from pizza_sales group by datename(dw,order_date)
	 

**2.	Monthly trend for total orders**

select * from pizza_sales;
select datename(month, order_date) as month_name, count(distinct order_id) as total_orders from pizza_sales 
group by datename(month ,order_date)
order by total_orders desc
 

**3.	Percentage of pizza sales by its category**

select * from pizza_sales;
select pizza_category, sum(total_price) as total_sales, sum(total_price)*100/ (select sum(total_price) from pizza_sales where month(order_date)=1) as toal_percentage
from pizza_sales
where month(order_date)=1
group by pizza_category
 
**4.	Total pizza sold by pizza category**
select pizza_size, cast(sum(total_price) as decimal(10,2)) as total_sales,cast( sum(total_price)*100/
(select sum(total_price) from pizza_sales where datepart(quarter, order_date)=1) as decimal(10,2))  as sales_percent
from pizza_sales
where datepart(quarter, order_date)=1
group by pizza_size
order by sales_percent desc
 

**5.	Top 5 pizzas by revenue**

select top 5 pizza_name, sum(total_price) as total_revenue from pizza_sales 
group by pizza_name 
order by total_revenue desc
 

**6.	Bottom 5 pizzas by revenue**

select top 5 pizza_name, sum(total_price) as total_revenue from pizza_sales 
group by pizza_name 
order by total_revenue
 

**7.	Top 5 best sellers by quantity**

select top 5 pizza_name, sum(quantity) as total_quantity from pizza_sales 
group by pizza_name 
order by total_quantity desc
 



**8.	bottom 5  sellers by quantity**
select top 5 pizza_name, sum(quantity) as total_quantity from pizza_sales 
group by pizza_name 
order by total_quantity asc
 


**9.	total orders of top 5 best selling pizzas**

select top 5 pizza_name, count(distinct order_id) as total_orders from pizza_sales 
group by pizza_name 
order by total_orders desc
 

**10.	total orders of bottom 5  selling pizzas**

select top 5 pizza_name, count(distinct order_id) as total_orders from pizza_sales 
group by pizza_name 
order by total_orders asc
 
