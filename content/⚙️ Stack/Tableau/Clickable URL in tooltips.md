# Clickable URL in tooltips

In Tableau, you can add a clickable URL to tooltips by using a calculated field. Here are the steps to do so:

1. Create a calculated field that returns the URL as a string. To do this, go to the Analysis menu, select "Create Calculated Field", and enter a formula that returns the URL. For example:
    
    **`"<a href='" + [URL Field] + "'>" + [URL Field] + "</a>"`**
    
2. Make sure that the data type of the calculated field is "String".
3. Add the calculated field to the Tooltip card in the Marks card. You can do this by right-clicking the Tooltip card and selecting "Edit Tooltip".
4. In the Tooltip dialog box, select the calculated field and add it to the Tooltip.
5. Preview the view and hover over the marks to see the URL in the tooltip. You should be able to click on the URL to open it in a web browser.

Note: The URL in the calculated field must be properly formatted for it to be clickable in the tooltip. The format should be: **`<a href='URL'>Link Text</a>`**.