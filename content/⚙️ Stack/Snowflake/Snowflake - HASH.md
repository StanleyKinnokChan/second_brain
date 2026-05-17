---
title: Snowflake - HASH
tags:
  - snowflake
---
[[Snowflake]] provides non-cryptographic hash functions, which take input value(s) and return a signed 64-bit numeric value. Hash functions are deterministic. [[Snowflake]] provides both a scalar hash function and an aggregate hash function, both of which are listed here.


1. HASH()
	- Returns a signed 64-bit hash value. Note that HASH never returns NULL, even for NULL inputs.
	- use case:
		- Convert skewed data values to values that are likely to be more randomly or more evenly distributed.
2. HASH_AGG()
	- Returns an aggregate signed 64-bit hash value over the (unordered) set of input rows. HASH_AGG never returns NULL, even if no input is provided. Empty input “hashes” to `0`.
	- usecase:
		- use for aggregate hash functions is to detect changes to a set of values without comparing the individual old and new values (e.g. difference of two lists)