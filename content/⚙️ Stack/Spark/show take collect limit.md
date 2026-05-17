---
title: show take collect limit
tags:
  - spark
---

**show**: print the row in ascii format

**take**: return rows object

**collect**: retrieved the whole distributed df from worker node back to driver node, which may be used when converting the entire df to another format like pandas df. Return rows object like take does

**limit**: a transformation step