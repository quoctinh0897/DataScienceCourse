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
---

### Python
#### Problem 1

Task

Raghu is a shoe shop owner. His shop has N number of shoes.
He has a list containing the size of each shoe he has in his shop.
There are X number of customers who are willing to pay  amount of money only if they get the shoe of their desired size.

Your task is to compute how much money Raghu earned.

**Input Format**

The first line contains , the number of shoes.
The second line contains the space separated list of all the shoe sizes in the shop.
The third line contains , the number of customers.
The next  lines contain the space separated values of the  desired by the customer and , the price of the shoe.

**Output Format**

Print the amount of money earned by Raghu.

Sample Input

```
10
2 3 4 5 6 8 7 6 5 18
6
6 55
6 45
6 55
4 40
18 60
10 50
```

***Sample Output***

200
Explanation

Customer 1: Purchased size 6 shoe for $55.
Customer 2: Purchased size 6 shoe for $45.
Customer 3: Size 6 no longer available, so no purchase.
Customer 4: Purchased size 4 shoe for $40.
Customer 5: Purchased size 18 shoe for $60.
Customer 6: Size 10 not available, so no purchase.

***Solution***

```
from collections import Counter

numShoe = input()
money = 0
counterShoe = Counter(list(input().split(' ')))
numBill = int(input())
for i in range(numBill):
    bill = list(input().split(' '))
    if(bill[0] in counterShoe.keys() and counterShoe[bill[0]] > 0):
        counterShoe[bill[0]] -= 1
        money += (int(bill[1]))
print(money)
```
