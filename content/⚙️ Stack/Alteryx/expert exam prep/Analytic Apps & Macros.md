# Analytic Apps & Macros

- Create complex batch and iterative macros
• Create chained applications
• Create complex, dynamic applications with
cascading logic and conditional functionality
• Troubleshoot and optimize provided macros
• Create an analytic application from a provided
workflow

**APP:**

- List box required one row of data, one column one value
- ratio button: unconnected to detour tool if it is left
- file browse: connected to input/ output tool
- folder browse: connected to directory tool
- list/ check box is similair
- drop list: list box: To filter single value, use filter tool with expression, then use action tool to change the text within “”, no double quote need to be included
- list box: To filter multiple value, check the box of generate custom list. use filter tool - var IN (”xxxx”), then use action tool to change “xxxx”, which has to be double qoute “”

when the macro is for importing file with different schema, we can use batch macro to batch each file path streaming into dynamic input tool. then open the interface designer and config output mode as Auto configure by name/ position

- use filter tool inside a containers for radio selection (action tool formular, iif([#1),’False’,’True’)
    - need another set of filter to create the list for further drilling down
- union all output of containers
- list box won’t update in the second app, make a separate output (inside the containers ) for 2nd apps
