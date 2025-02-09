# Day 2 - 05 Feb 2025

1) Exploring the different types of joins from [site](https://www.w3schools.com/sql/sql_join.asp)
2) Log in to [GitHub](https://github.com/)
3) checking for SSH keys in github
4) Installation of  git from the official [site](https://git-scm.com/downloads/win)
5) copy the link of ssh to ssh path to intialising keys
6) anable the ssh keys and file repository
   

## Exercise

***Get All Observations with Full Details (INNER JOIN)***

```sql
select observation.total_bill,
observation.tip,
observation.size,
sex.sex,
smoker.smoker,
day.day,
time.time
from observation observation
inner join sex sex on observation.sex_id=sex.sex_id
inner join smoker smoker on observation.smoker_id=smoker.smoker_id
inner join day day on observation.day_id=day.day_id
inner join time time on observation.time_id=time.time_id;
```
***Count the Number of Customers by Gender (JOIN with GROUP BY)***
```sql
select sex.sex, 
count(observation.sex_id) as total_customers
from Observation observation
join Sex sex on observation.sex_id = sex.sex_id
group by sex.sex
order by sex.sex desc;
```
***Get Total Revenue Grouped by Day (JOIN with SUM)e***
```sql
select day.day,
sum(observation.total_bill) as total_revenue
from observation observation
join day day on observation.day_id=day.day_id
group by day.day;
```
***Find the Average Tip Amount by Smoker Status***
```sql
select smoker.smoker, 
avg(observation.tip) as avg_tip
from Observation observation
join Smoker smoker on observation.smoker_id = smoker.smoker_id
group by smoker.smoker;
```
***Find the Most Common Dining Time (JOIN with COUNT)***
```sql
select time.time, 
count(observation.time_id) as visit_count
from Observation observation
join Time time on observation.time_id = time.time_id
group by time.time
order by visit_count desc;
```
***Find the Highest Tip Given by Each Gender (JOIN with MAX)***
```sql
select sex.sex,
avg(observation.tip) as avg_tip
from observation observation
join sex sex on observation.sex_id = sex.sex_id
group by sex.sex;
```
***Find All Tips Given on Specific Days***
```sql
select observation.total_bill, observation.tip, day.day
from Observation observation
join Day day on observation.day_id = day.day_id
where day.day in ('friday');
```
***Find All Tips Given on Weekdays***
```sql
select observation.total_bill, observation.tip, day.day
from Observation observation
join Day day on observation.day_id = day.day_id
where day.day not in ('Saturday', 'Sunday');
```
***Combine Male and Female Customer Names Without Duplicates***
```sql
select sex.sex from Sex where sex = 'Male'
UNION
select sex.sex from Sex where sex = 'Female';
```
***find the customer how are male but did give tip***
```sql
select sex.sex from  sex
where sex.sex ='Male'
except
select sex.sex from  sex 
join observation observation on sex.sex_id=observation.sex_id
where observation.tip>0;
```
***left join***
```sql
select observation.total_bill,observation.tip,s.sex
from observation observation
left join sex s on observation.sex_id=s.sex_id;
```
***having condition***
```sql
select d.day,avg(o.tip) as avg_tip
from observation o
join day d on o.day_id= d.day_id
group by d.day
having avg(o.tip)>3
order by avg_tip desc;
```
***The insert into***
```sql
insert into time (time_id,time)
values (2,'Brunch');
```
***delete row***
```sql
delete from time where time_id=3;
```
***wildcards***
```sql
SELECT * FROM Day WHERE day LIKE 'S%';
```
