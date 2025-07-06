# KMS-SQL-case-study
select *
from [KMS Sql Case Study1]


--- Which product category that has the highest 

select top 1 [Product_Category],count ([Product_Category])as [Product Count]
from [KMS Sql Case Study1]
group by Product_Category
order by [Product Count] desc


--- what are the top 3 and buttom 3 region in terms of sales 

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] desc

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] asc

----- what were  the Total Sales of applicants in ontario?

select Region, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
where Region='ontario'
Group by Region

--------Advice the management of KMS on what to do to increase the revenue from the buttom 10 customer 

Select top 10 [Customer_Name], SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Customer_Name
order by [Total Sales] asc

------KMS incurred the Most shipping cost using which shipping method ?

Select Top 1 [Ship_Mode], SUM([Shipping_Cost]) as [Total Shipping Cost]
from [KMS Sql Case Study1]
group by Ship_Mode
order by [Total Shipping Cost] desc

----Who are the most valuable customer, and what products or services did they typically purchase?

select [Customer_Name],Product_Name, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
Group by Customer_Name,Product_Name
order by [Total Sales] desc

-----Which small business customer have the highest sales ?

select top 1 Customer_Name,Customer_Segment, SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
where Customer_Segment ='small Business'
group by Customer_Name,Customer_Segment
order by [Total Sales] desc

---Which corporate customer placed the most number of orders in 2019 -2012?

select top 1  Customer_Name,Customer_Segment, count([Order_ID]) as [Total order]
from [KMS Sql Case Study1]
where Customer_Segment ='corporate' and Order_Date between '2009' and '2012'
group by Customer_Name,Customer_Segment
order by [Total order] desc

---  Which consumer customer was the most profitable one?

select top 1 Customer_Name,Customer_Segment, sum([Profit]) as [Total profit]
from [KMS Sql Case Study1]
where Customer_Segment ='Consumer'
group by Customer_Name,Customer_Segment
order by [Total profit] desc

----Which customer returned items, and what segments do they belong to?
select Customer_Name,Customer_Segment,[Status]
from [KMS Sql Case Study1]
join [dbo].[Order_Status]
on [KMS Sql Case Study1].Order_ID = [dbo].[Order_Status].[Order_ID]

/* If the delivery truck is the most economical but the lowest shipping method and express air is the fastest.
but the most expensive one, did you think the company appropriately spent shipping costs based on the order priority */

Select Order_Priority, Ship_Mode,
    COUNT([Order_ID]) AS [order count],
    SUM(sales - profit) AS [Estimated shipping cost],
    AVG(DATEDIFF(DAY, [Order_Date], [Ship_Date])) AS [Avg ship date]
from  [KMS Sql Case Study1] 
group by Order_Priority,Ship_Mode
order by  Order_Priority,Ship_Mode desc       
     
/* No, KMS did not appropriately spend shipping costs based on the order of  priority.
They overused delivery trucks, which are best for bulk or non-urgent orders and 
underused express air, which is meant for urgent deliveries. 
This shows a misalignment between shipping cost,speed and order priority leading to inefficient spending and wasted cost .*/


select Customer_Segment, SUM(sales) as [total sales]
from [KMS Sql Case Study1]
group by Customer_Segment
order by [total sales] desc


select *
from [KMS Sql Case Study1]


--- Which product category that has the highest 

select top 1 [Product_Category],count ([Product_Category])as [Product Count]
from [KMS Sql Case Study1]
group by Product_Category
order by [Product Count] desc


--- what are the top 3 and buttom 3 region in terms of sales 

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] desc

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] asc

----- what were  the Total Sales of applicants in ontario?

select Region, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
where Region='ontario'
Group by Region

--------Advice the management of KMS on what to do to increase the revenue from the buttom 10 customer 

Select top 10 [Customer_Name], SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Customer_Name
order by [Total Sales] asc
/* To boost sales from the bottom 10 customers, the company should focus on strengthening relationships 
through customized promotions, puchasing behaviours, reaching out directly through calls,text or emails to their customers to understand their past experience,
Give discounts on their most viewed or previously purchased products, Upsell and Cross-sell Offers,
Offer faster delivery, better after-sales support, or dedicated account managers for small businesses and  Survey to Understand 
the Needs of the customers, what would make them again and why they havent been coming frequently*/

------KMS incurred the Most shipping cost using which shipping method ?

Select Top 1 [Ship_Mode], SUM([Shipping_Cost]) as [Total Shipping Cost]
from [KMS Sql Case Study1]
group by Ship_Mode
order by [Total Shipping Cost] desc

----Who are the most valuable customer, and what products or services did they typically purchase?

select [Customer_Name],Product_Name, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
Group by Customer_Name,Product_Name
order by [Total Sales] desc

-----Which small business customer have the highest sales ?

select top 1 Customer_Name,Customer_Segment, SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
where Customer_Segment ='small Business'
group by Customer_Name,Customer_Segment
order by [Total Sales] desc

---Which corporate customer placed the most number of orders in 2019 -2012?

select top 1  Customer_Name,Customer_Segment, count([Order_ID]) as [Total order]
from [KMS Sql Case Study1]
where Customer_Segment ='corporate' and Order_Date between '2009' and '2012'
group by Customer_Name,Customer_Segment
order by [Total order] desc

---  Which consumer customer was the most profitable one?

select top 1 Customer_Name,Customer_Segment, sum([Profit]) as [Total profit]
from [KMS Sql Case Study1]
where Customer_Segment ='Consumer'
group by Customer_Name,Customer_Segment
order by [Total profit] desc

----Which customer returned items, and what segments do they belong to?
select Customer_Name,Customer_Segment,[Status]
from [KMS Sql Case Study1]
join [dbo].[Order_Status]
on [KMS Sql Case Study1].Order_ID = [dbo].[Order_Status].[Order_ID]

/* If the delivery truck is the most economical but the lowest shipping method and express air is the fastest.
but the most expensive one, did you think the company appropriately spent shipping costs based on the order priority */

Select Order_Priority, Ship_Mode,
    COUNT([Order_ID]) AS [order count],
    SUM(sales - profit) AS [Estimated shipping cost],
    AVG(DATEDIFF(DAY, [Order_Date], [Ship_Date])) AS [Avg ship date]
from  [KMS Sql Case Study1] 
group by Order_Priority,Ship_Mode
order by  Order_Priority,Ship_Mode desc
