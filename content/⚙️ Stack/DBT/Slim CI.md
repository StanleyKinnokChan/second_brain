---
title: 
tags:
---


Slim CI (only test/ run the model being modified, instead of full run):

1. run ***dbt compile***  to generate manifest json and move the json file to root folder
2. modified any nodes, even comment will do the work
3. run ***dbt compile*** again to generate 2nd manifest json in the target folder
4. With the help of [[select selector]], use dbt ls --select state:modified --state . to confirm the model being chanage
5. dbt run --select state:modified