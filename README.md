# Olympic_Database

Our database will contain country name,country id,first and last name of player,
his/her date of birth,gender,category of sports,in which year the olypic games
was organised,various events ,medals and many more.


# RDMS Tables

- Athelete
- Country
- Disciple
- Sports
- Results
- Olympic


# SQL Query

Some sample sql queries

List all the country whose athlete participated in more than 4 sports

```bash
select country_name,Total_sports from (select country_name,count(sport_id) as Total_sports
from athlete natural join country natural join sport group by country_name)as r where Total_sports>4
```


List all the athlete palyed many discipline in any sport

```bash
select distinct fname,lname ,count ,sport_id ,country_abbrev fname,lname,count(fname) as count 
from (( select from athlete natural join result group by fname,lname )as r1 natural join
(select * from athlete natural join result ) as r2 ) where count>1 order by count desc
```

