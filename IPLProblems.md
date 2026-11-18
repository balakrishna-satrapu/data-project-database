# IPL problems

## Problem 1: Number of matches played per year of all the years in IPL.

**Query**

select season, count(*)\
from matches\
group by season\
order by season;

**Output**

| season | count |
|---|---:|
| 2008 | 58 |
| 2009 | 57 |
| 2010 | 60 |
| 2011 | 73 |
| 2012 | 74 |
| 2013 | 76 |
| 2014 | 60 |
| 2015 | 59 |
| 2016 | 60 |
| 2017 | 59 |

## Problem 2: Number of matches won of all teams over all the years of IPL.

**Query**

select winner, count(*) as matches_won\
from matches\
group by winner\
having winner is not null\
order by matches_won desc;

**Output**

| winner | matches_won |
|---|---:|
| Mumbai Indians | 92 |
| Chennai Super Kings | 79 |
| Kolkata Knight Riders | 77 |
| Royal Challengers Bangalore | 73 |
| Kings XI Punjab | 70 |
| Rajasthan Royals | 63 |
| Delhi Daredevils | 62 |
| Sunrisers Hyderabad | 42 |
| Deccan Chargers | 29 |
| Gujarat Lions | 13 |
| Pune Warriors | 12 |
| Rising Pune Supergiant | 10 |
| Kochi Tuskers Kerala | 6 |
| Rising Pune Supergiants | 5 |

## Problem 3: For the year 2016 get the extra runs conceded per team.

**Query**

select d.bowling_team as bowling_team, sum(d.extra_runs) as extra_runs\
from matches m\
join deliveries d\
on d.match_id = m.id\
and m.season = 2016\
group by d.bowling_team\
order by extra_runs desc;

**Output**

| bowling_team | extra_runs |
|---|---:|
| Royal Challengers Bangalore | 156 |
| Kolkata Knight Riders | 122 |
| Rising Pune Supergiants | 108 |
| Sunrisers Hyderabad | 107 |
| Delhi Daredevils | 106 |
| Mumbai Indians | 102 |
| Kings XI Punjab | 100 |
| Gujarat Lions | 98 |


## Problem 4: For the year 2015 get the top economical bowlers.

**Query**

select d.bowler as bowler, round((6.0 * (sum(batsman_runs) + sum(d.wide_runs) + sum(d.noball_runs)) / (count(\
    case\
		when d.wide_runs = 0 and d.noball_runs = 0\
		then 1 \
	end))), 2) as economy\
from matches m\
join deliveries d\
on d.match_id = m.id\
and m.season = 2015\
group by d.bowler\
order by economy\
limit 5;

**Output**

| bowler | economy |
|---|---:|
| RN ten Doeschate | 4.00 |
| J Yadav | 4.14 |
| V Kohli | 5.45 |
| R Ashwin | 5.85 |
| S Nadeem | 6.14 |