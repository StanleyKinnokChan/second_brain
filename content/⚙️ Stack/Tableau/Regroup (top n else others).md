# Regroup (top n else others)

1. set up a set action with top n criteria *(let’s use top 10 countires for example)*
2. set up a cal field
    
    //C. Country Group
    
    IF [S. County - Top 10] THEN [Country] ELSE "Others" END