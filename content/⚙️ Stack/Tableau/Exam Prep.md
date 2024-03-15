# Exam Prep

Tableau feature

1.1 choose an appropriate data source

- structured
- 1 column for same measure

1.1.2 live connection or extract

- tableau language

![Untitled](Exam%20Prep%20f2224f30622f4217adf96cef0c56800e/Untitled.png)

Assess data quality (on data source page: right click the field and describe)

- Completeness: no null
- Consistency: name and structure are same all time
- accuracy: the data are correct all the time/ no spelling mistake

Clean operations:

- pivot, split, change data type, rename field….

difference between data source and connections

- data source has its own panel, link between your source data and Tableau
- connection allows building your own data model

Full refresh extract vs incremental refresh extract 

- incremental refresh only add new rows to data,
- full refresh update all data

discrete and continuous; dimension and measure

- In summary, discrete and continuous data refer to the nature of the values that can be taken by a variable, while dimensions and measures refer to the type of data used to describe a dataset.
- dimension split out the view, measure create axis

download options in server

![Untitled](Exam%20Prep%20f2224f30622f4217adf96cef0c56800e/Untitled%201.png)

**Function:**

**Count**

first: 0 to -n

last: n to 0

index: 1 to n

**ranking for (6,9,9,14)**

rank: 1,2,2,4

rank_dense: 1,2,2,3 

rank_modified: 1,3,3,4

rank_unique: 1,2,3,4

**Color mark type:**

- discrete measure create categorical palettes
- continuous measure create color range

**Annotation:**

- mark - follow the object
- point - fixed position
- area - a whole area

Moving average is 3 month (2 previous monthes + current month)

**USE TABLE TO DO THE COMPARISON**

Spotlighting is **a technique for showing discrete thresholds based on the values of a measure**

Dates are typically treated as dimensions

**pills:** 

- color= discrete vs continuous
- aggregation method = measure vs dimension

**LOGIC CAN MULTIPLE THE VALUE**

Before you can query a data source with Ask Data, a Tableau author must first create a lens(Link opens in a new window) that specifies the subset of data fields the lens uses.

Q26 - MDX, which stands for Multidimensional Expressions, is a query language for OLAP databases. With MDX calculated members, you can create more complex calculations and reference both measures and dimensions. (True/ False)

- When working with dates, Tableau retrieves date formats automatically from the data source.
- When using a cube, we cannot take extracts
- the reason for a cube's speed is that all its aggregations and hierarchies are pre-built.
- Cubes are very powerful and can return information very quickly, often much more quickly than a relational data source.

dimension= any field containing qualitative, categorical information

If Tableau Server is running HTTPS and you use HTTP in the URR for an web page object, browser won't be able to display the web page

calculation with all the item with a set (eg top 10)

DA-F-L-1060