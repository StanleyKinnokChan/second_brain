---
title: 
tags:
  - Security
---
Bubble sort
- Move the largest number to the end
- loop everythings

Insert sort
- moving the number once at a time from the unsorted side and insert to sorted side
- performance similar to bubble sort, but generally faster because of the moving distance

Selection sort
- worse, because you have to sort becauseS
- swap the minimum from unsorted side with the last values

Quick sort
- randomly choose an element as "prvoting point (pp)" to split the array into two
- placeing everythings smaller to the left and larger to the right, recurrsively
- Divide-and conquer approach

Merge sort
- Divide-and conquer approach
- divided the array in half 
- keep dividing into many many small aray, then repeat sort -> merged into big array sort -> merged into big array -> until it is completely sorted

Heap sort:
- Heapify the array then build a max heap (=all parent >= children for ascending) - use O(n)
- keep remove the max root node life the leaf node, and rebuild the the map heap
- the tree will get smaller and smaller
 ![[sorting algo complexity.png]]