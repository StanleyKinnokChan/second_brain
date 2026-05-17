---
title: HEAD
tags:
  - git
---


HEAD is a reference to the last commit in the currently checked-out branch.

---

A _detached HEAD_ is the situation you end up in whenever you check out a _commit_ (or tag) instead of a branch. The commit can exist in multiple branch and when you checkout the commit there is no specific branch specified (switcted to headless modes), you are in the middle of nowhere. 

In this case, you have to imagine this as a _temporary branch_ without a name; so instead of having a named branch reference, we _only_ have HEAD. It will still allow you to make commits (which will update HEAD), so the above short definition is still true if you think of a detached HEAD as a temporary branch without a name.

Checking out the branch again will switch back to head mode pointing to the latest commit of that branch

