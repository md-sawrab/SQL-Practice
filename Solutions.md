**Select everything from sales table**

```sql
    select * from sales;
```

**Show just a few columns from sales table**

```sql
  select SaleDate, Amount, Customers from sales;
  select Amount, Customers, GeoID from sales;
```
**Adding a calculated column with SQL**

```sql
  Select SaleDate, Amount, Boxes, Amount / boxes  from sales;
```

**Naming a field with AS in SQL**

```sql
  Select SaleDate, Amount, Boxes, Amount / boxes as 'Amount per box'  from sales;
```

**Using WHERE Clause in SQL**

```sql
  select * from sales
  where amount > 10000;
```
**Showing sales data where amount is greater than 10,000 by descending order**
```sql
  select * from sales
  where amount > 10000
  order by amount desc;
```
**Showing sales data where geography is g1 by product ID & descending order of amounts**

```sql
  select * from sales
  where geoid='g1'
  order by PID, Amount desc;
```
**Working with dates in SQL**

```sql
  Select * from sales
  where amount > 10000 and SaleDate >= '2022-01-01';
```
**Using year() function to select all data in a specific year**

```sql
  select SaleDate, Amount from sales
  where amount > 10000 and year(SaleDate) = 2022
  order by amount desc;
```
**BETWEEN condition in SQL with < & > operators**

```sql
  select * from sales
  where boxes >0 and boxes <=50;
```
**Using the between operator in SQL**

```sql
  select * from sales
  where boxes between 0 and 50;
```
**Using weekday() function in SQL**

```sql
  select SaleDate, Amount, Boxes, weekday(SaleDate) as 'Day of week'
  from sales
  where weekday(SaleDate) = 4;
```
**Working with People table**

```sql
  select * from people;
```
**OR operator in SQL**

```sql
  select * from people
  where team = 'Delish' or team = 'Jucies';
```
**IN operator in SQL**

```sql
  select * from people
  where team in ('Delish','Jucies');
```
**LIKE operator in SQL**

```sql
  select * from people
  where salesperson like 'B%';

  select * from people
  where salesperson like '%B%';

  select * from sales;
```
**Using CASE to create branching logic in SQL**

```sql
  select 	SaleDate, Amount,
  		case 	when amount < 1000 then 'Under 1k'
  				when amount < 5000 then 'Under 5k'
                  when amount < 10000 then 'Under 10k'
  			else '10k or more'
  		end as 'Amount category'
  from sales;
```
**Join**
```sql
  	select * from sales;
  	
  	select * from people;
  	
  	select s.SaleDate, s.Amount, p.Salesperson
  	from sales as s
  	join people as p on p.SPID = s.SPID;
```

**Left Join**	
```sql
  	select s.SaleDate, s.Amount, pr.Product
  	from sales as s
  	left join products as pr on pr.PID = pr.PID;
  	
  	select s.SaleDate, s.Amount, p.Salesperson,pr.product,p.Team
  	from sales as s
  	join people as p on p.SPID = s.SPID
  	join products as pr on pr.PID = pr.PID;
	
```
