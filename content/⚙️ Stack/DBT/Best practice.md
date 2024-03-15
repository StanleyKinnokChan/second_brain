# Best practice

[https://docs.getdbt.com/guides/best-practices](https://docs.getdbt.com/guides/best-practices)

- don’t create high number of specific job → wasting time to recreate some core table
solution: start with incremental job and decide what need to be built more than once a day
    - use tags/ exposure to select those specific needs
    - build everything out from the source if the source update frequently
    - build out particular sub-directory to get all data for specific needs (eg finiance)
    - take advantage of union and intersection to select the only target models