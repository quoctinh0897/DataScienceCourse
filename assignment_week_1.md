### SQL
#### Problem 1

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.
**Input Format**
```
select sum(c.population) from city as c left join country as ctr on c.countrycode = ctr.code
where ctr.continent = 'Asia';
```
