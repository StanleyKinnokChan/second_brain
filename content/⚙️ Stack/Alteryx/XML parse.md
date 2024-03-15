# XML parse

### What is XML ([w3schools.com/xml/xml_whatis.asp](http://w3schools.com/xml/xml_whatis.asp))

XML Does Not DO Anything, a XML element is a chunk of pure text wrapped by tags, while tags have no function, just a name tag

The following is the text element
```
<aside>
💡 <element>text</element>

</aside>
```

A tag can carry an attribute indicated by ‘<tag_name attribute=foo>’

A content element contains others element, here book is a content element with an attribute

```
<aside>
💡 <book category="children">

<title>Harry Potter</title>

<author>J K. Rowling</author>

<year>2005</year>

<price>29.99</price>

</book>

</aside>

The configuration of the XML parse tool consisted of two parts:

1. ‘XML element to parse’ = parse which levels of the element, also return a new column for an attribute if that exists
    - **Root:** the most outer element
    - **Auto-detect Child**: the most commonly appeared element. If all appeared once, give the first child
    - **Specific Child Name:** Literally
2. return the value of the next layer of a child inside the parent specified in 1.
    - Return child values: return the text of the next child
    - Return outer XML (XML from parents and next child elements)

Practice: weekly challenge 37

[[XML parse/Untitled.png]]
```
