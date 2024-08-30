---
title: 
tags:
---
An operator defines a single, ideally idempotent, task in your DAG.

Operators allow you to break down your workflow into discrete, manageable pieces of work. 


3 types of operator:
1. Action operators: Execute an action
2. Transfer Operators: Transfer data
3. Sensors: wait for a condition to be met (e.g. file arrivals)
	- Poke_ineterval = check condition, default 60s
	- timeout = sensor marked as failed after waiting for timeout peroid, default 7days