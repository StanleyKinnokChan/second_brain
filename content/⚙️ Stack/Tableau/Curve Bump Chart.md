# Curve Bump Chart

[Data + Tableau + Me: How to Sigmoid Bump Chart (Spline?)](http://www.datatableauandme.com/2016/12/how-to-sigmoid-bump-chart-spline.html)

## Suitable dataset:

rank of group in each year

| rank | year | group (eg countries) |
| --- | --- | --- |
| 1 | 2001 | Swizterland |
| 2 | 2001 | Japan |
| 3 | 2001 | Hong Kong |
| .. |  |  |
| 1 | 2009 | Hong Kong |
| 2 | 2009 | Japan |
| 3 | 2009 | Swizterland |

## Sigmoid Curve

1. create “Path” from 1 to 49 and join it with the dataset
2. create following 8 cal. field:

//T

([Path]-25)/4

//Sigmoid

1/(1+EXP(1)^-[T])

//Year Order

[Year] - {MIN([Year])} //index across the years

//Path Order

(49*[Year Order])+[Path] //point 1-49 per year

//Year fake

([Path Order]/49) + 2000

//Rank 2 Setup
IF MIN([Path]) = 49 THEN LOOKUP(MIN([Rank]),1) END

//Rank 2

IFNULL(WINDOW_MIN([Rank 2 Setup]), MIN([Rank]))

//Curve

MIN([Rank])+(([Rank 2] - MIN([Rank]))*MIN([Sigmoid]))

1. yearfake to column; change into dimension
2. curve to row; country to & year to detail mark
3.  Table calculation of curve → nested cal. for both and rank2 setup →
Rank2: Countries > Year > Yearfake; restarting every year
rank2 setup: Countries > Year > Yearfake; restarting every countreis

## Point on the curve

1. create cal. field: 

//Dual Shape

FLOAT(MIN(IF [Path]=1 THEN [Rank] END))

1. add to row shelf and dual synchronised axis