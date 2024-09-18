
HEAD is a reference to the last commit in the currently checked-out branch.

---

There is a small exception to this, which is the detached HEAD. A _detached HEAD_ is the situation you end up in whenever you check out a _commit_ (or tag) instead of a branch. In this case, you have to imagine this as a _temporary branch_ without a name; so instead of having a named branch reference, we _only_ have HEAD. It will still allow you to make commits (which will update HEAD), so the above short definition is still true if you think of a detached HEAD as a temporary branch without a name.