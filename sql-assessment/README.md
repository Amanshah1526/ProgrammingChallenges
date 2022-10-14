# SQL Challenge

The database contains two tables, store_revenue and marketing_data.  Refer to the two CSV
files, store_revenue and marketing_data to understand how these tables have been created.

store_revenue contains revenue by date, brand ID, and location:

 >  create table store_revenue (
 >     id int not null primary key auto_increment,
 >    date datetime,
 >    brand_id int,
 >    store_location varchar(250),
 >    revenue float  
 >  );

marketing_data contains ad impression and click data by date and location:

> create table marketing_data (
>  id int not null primary key auto_increment,
>  date datetime,
>  geo varchar(2),
>  impressions float,
>  clicks float
> );

### Please provide a SQL statement under each question.

* Question #0 (Already done for you as an example)
 Select the first 2 rows from the marketing data
​
>  select *
>  from marketing_data
> limit 2;
​
*  Question #1
 Generate a query to get the sum of the clicks of the marketing data
 
> SELECT SUM(clicks)
> FROM Marketing_data;

​
*  Question #2
 Generate a query to gather the sum of revenue by store_location from the store_revenue table
 
> SELECT SUM(revenue)
> FROM Store_revenue
> GROUP BY store_location;

​
*  Question #3
 Merge these two datasets so we can see impressions, clicks, and revenue together by date
and geo.
 Please ensure all records from each table are accounted for.
 
> select m.impressions, m.clicks, s.revenue, m.geo 
> from marketing_data m inner join store_revenue s 
> on s.date=m.date 
> order by m.geo;
 
​
* Question #4
 In your opinion, what is the most efficient store and why?
 
> According to my opinion, California at record number #23 is the most effecient store.
  As it has the highest revenue even with the tax deductions and considering no loss.
 
​
* Question #5 (Challenge)
 Generate a query to rank in order the top 10 revenue producing states
 
> SELECT geo, SUM(revenue) as TSUM 
> FROM store_revenue
> GROUP BY store_location
> ORDER BY TSUM DESC limit 10;
​
