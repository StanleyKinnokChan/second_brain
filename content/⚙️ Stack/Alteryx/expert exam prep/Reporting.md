# Reporting

- Create and output dynamic, batched reports
with the following elements:
o Headers and footers
o Tables and charts
o Images and text
o Specific layout criteria
o Report maps

Note:

- union by position rather than name
- overlay tool to put legend on map
- report map tool: the data tab set up the field that affect the style, but the style needed to be set in layers tab
- header tool: connect the tool after making the report, then render final report with render tool

**Read all tab in excel**

1. use input tool, import only the list of sheet names
2. use dynamic input tool
    1. output file names as field = full path
    2. field: sheet names
    3. action: change file/ table name
3. regex .*\|\|\|(.*) to get sheet name for each row
4. build batch macro (attach sheet name col to the row of report snippet)
5. macro output will be render group by sheet name
