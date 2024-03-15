---
title: 
tags:
---

Evaluates an expression in a context modified by filters.

The function copied original filter context to prepare the new filter context 

The new filter context undergone 1 out of 3 of the following actions:
1. Adding additional filters (independent condition)
2. Overriding filters (USERELATIONSHIP, CROSSFILTER, ALL, ALLEXCEPT, ALLSELECTED, and ALLNOBLANKROW)
3. Context transition (can be removed by all)

Every filter argument can be either a filter removal (such as ALL, ALLEXCEPT, ALLNOBLANKROW), a filter restore (ALLSELECTED), or a table expression returning a list of values for one or more columns or for an entire expanded table.

