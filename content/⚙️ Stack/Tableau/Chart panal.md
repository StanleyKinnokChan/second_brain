# Chart panal

1. put x-var and y-var on the column and row shelf; put group on detail mark

1. create cal. field and convert them into discrete pills

//panel columns
(INDEX()-1)%(ROUND(SQRT(SIZE())))

//panel rows
INT((INDEX()-1)/(ROUND(SQRT(SIZE()))))

1. Tableau tal for these two pill
For each group and x, at the level of group