---
title: Snowflake - Semi-structured data
tags:
  - snowflake
---

| fx()                                                          | Usage                                                                                       |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| TO_JSON                                                       | Converts a VARIANT value to a string containing the JSON representation of the value.       |
| PARSE_JSON                                                    | Interprets an input string as a JSON document, producing a VARIANT value.                   |
| OBJECT_CONSTRUCT( [<key>, <value> [, <key>, <value> , ...]] ) | Builds a JSON-like object (`OBJECT`, which is a subtype of `VARIANT`) from key-value pairs. |
| TO_VARIANT                                                    | Converts any value to a VARIANT value or NULL (if input is NULL).                           |

![[Sowflake semi-structure data.png]]