### SQL
#### Problem 1

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

**Input Format**

The **CITY** table is described as follows:

| Field | Type |
|:----:|:---:|
| ID | NUMBER |
| NAME | VARCHAR2(17) |
| COUNTRYCODE | VARCHAR2(3) |
| DISTRICT | VARCHAR2(20) |
| POPULATION | NUMBER |
The **COUNTRY** table is described as follows:

| Field | Type |
|:----:|:---:|
| CODE | VARCHAR2(3) |
| NAME | VARCHAR2(44) |
| CONTINENT | VARCHAR2(13) |
| REGION | VARCHAR2(25) |
| SURFACEAREA | NUMBER |
| INDEPYEAR | VARCHAR2(5) |
| POPULATION | NUMBER |
| LIFEEXPECTANCY | VARCHAR2(4) |
| GNP | NUMBER |
| GNPOLD | VARCHAR2(9) |
| LOCALNAME | VARCHAR2(44) |
| GOVERNMENTFORM | VARCHAR2(44) |
| HEADOFSTATE | VARCHAR2(32 |
| CAPITAL | VARCHAR2(4) |
| CODE2 | VARCHAR2(2) |

**Solution**

```
select sum(c.population) from city as c left join country as ctr on c.countrycode = ctr.code
where ctr.continent = 'Asia';
```

#### Problem 2

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

**Input Format**

The **CITY** table is described as follows:

| Field | Type |
|:----:|:---:|
| ID | NUMBER |
| NAME | VARCHAR2(17) |
| COUNTRYCODE | VARCHAR2(3) |
| DISTRICT | VARCHAR2(20) |
| POPULATION | NUMBER |
The **COUNTRY** table is described as follows:

| Field | Type |
|:----:|:---:|
| CODE | VARCHAR2(3) |
| NAME | VARCHAR2(44) |
| CONTINENT | VARCHAR2(13) |
| REGION | VARCHAR2(25) |
| SURFACEAREA | NUMBER |
| INDEPYEAR | VARCHAR2(5) |
| POPULATION | NUMBER |
| LIFEEXPECTANCY | VARCHAR2(4) |
| GNP | NUMBER |
| GNPOLD | VARCHAR2(9) |
| LOCALNAME | VARCHAR2(44) |
| GOVERNMENTFORM | VARCHAR2(44) |
| HEADOFSTATE | VARCHAR2(32 |
| CAPITAL | VARCHAR2(4) |
| CODE2 | VARCHAR2(2) |

**Solution**

```
select c.name from city as c left join country as ctr on c.countrycode = ctr.code
where ctr.continent = 'Africa';
```

#### Problem 3

Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

**Input Format**

The **CITY** table is described as follows:

| Field | Type |
|:----:|:---:|
| ID | NUMBER |
| NAME | VARCHAR2(17) |
| COUNTRYCODE | VARCHAR2(3) |
| DISTRICT | VARCHAR2(20) |
| POPULATION | NUMBER |
The **COUNTRY** table is described as follows:

| Field | Type |
|:----:|:---:|
| CODE | VARCHAR2(3) |
| NAME | VARCHAR2(44) |
| CONTINENT | VARCHAR2(13) |
| REGION | VARCHAR2(25) |
| SURFACEAREA | NUMBER |
| INDEPYEAR | VARCHAR2(5) |
| POPULATION | NUMBER |
| LIFEEXPECTANCY | VARCHAR2(4) |
| GNP | NUMBER |
| GNPOLD | VARCHAR2(9) |
| LOCALNAME | VARCHAR2(44) |
| GOVERNMENTFORM | VARCHAR2(44) |
| HEADOFSTATE | VARCHAR2(32 |
| CAPITAL | VARCHAR2(4) |
| CODE2 | VARCHAR2(2) |

**Solution**

```
select ctr.continent,floor(avg(c.population)) from country as ctr inner join city as c on c.countrycode = ctr.code group by ctr.continent;
```
#### Problem 4

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

**Input Format**

| Colunm | Type |
|:----:|:---:|
| A | Integer |
| B | Integer |
| C | Integer |

**Sample Input**

| A | B | C |
|:----:|:---:|:---:|
| 20 | 20 | 23 |
| 20 | 20 | 20 |
| 20 | 21 | 22 |
| 13 | 14 | 30 |

**Sample Output**

```
Isosceles
Equilateral
Scalene
Not A Triangle
```

**Solution**

```
select case
when A + B <= C then 'Not A Triangle' when A = B AND B = C then 'Equilateral' when A = B or B = C or A = C then 'Isosceles' when A != B or B != C or A != C then 'Scalene' end from TRIANGLES;
```
#### Problem 5

Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeroes removed), and the actual average salary.

Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.

**Input Format**

The EMPLOYEES table is described as follows:

| Colunm | Type |
|:----:|:---:|
| Id | Integer |
| Name | String |
| Salary | Integer |


**Solution**

```
select ceil(avg(salary) - avg(replace(salary,'0',''))) from employees
```
#### Problem 6

We define an employee's total earnings to be their monthly  worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as  space-separated integers.

**Input Format**

The Employee table containing employee data for a company is described as follows:

| Colunm | Type |
|:----:|:---:|
| Employee_id | Integer |
| Name | String |
| Months | Integer |
| Salary | Integer |


**Solution**

```
select salary*months as total, count(*) as cnt from employee
where salary*months = (select max(salary*months) from employee)
group by total
```

#### Problem 7

Query the total population of all cities in CITY where District is California.

**Input Format**

| Colunm | Type |
|:----:|:---:|
| ID | Integer |
| Name | String |
| CountryCode | String |
| District | String |
| Population | Integer |

**Solution**

```
select sum(population) from city
where district = 'California'
```

#### Problem 8

Query the average population for all cities in CITY, rounded down to the nearest integer.

**Input Format**

| Colunm | Type |
|:----:|:---:|
| ID | Integer |
| Name | String |
| CountryCode | String |
| District | String |
| Population | Integer |

**Solution**

```
select floor(avg(population)) from city
```

#### Problem 9

Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of 2 decimal places.
The sum of all values in LONG_W rounded to a scale of 2 decimal places.

**Input Format**

The STATION table is described as follows:

| Colunm | Type |
|:----:|:---:|
| ID | Integer |
| City | String |
| State | String |
| lat_n | Integer |
| long_w | Integer |

**Solution**

```
select round(sum(lat_n),2),round(sum(long_w),2) from station
```

#### Problem 10

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345 . Round your answer to 4 decimal places.

**Input Format**

The STATION table is described as follows:

| Colunm | Type |
|:----:|:---:|
| ID | Integer |
| City | String |
| State | String |
| lat_n | Integer |
| long_w | Integer |

```
select round(long_w,4) from station
where lat_n < 137.2345
order by lat_n desc
limit 1
```
