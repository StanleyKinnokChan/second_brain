---
title: 
tags:
  - Linux
---
Each time we type a command and press the Enter key, bash performs several substitutions upon the text before it carries out our command. The process that makes this happen is called expansion.

Tilde Expansion (~)
- point to home
```
echo ~bob # /home/bob
```

Arithmetic Expansion ( $((expression)) ) 
- evaluate expression
```
echo $((2 + 2)) # 4
```

Brace Expansion
- create multiple test strings
```
echo Front-{A,B,C}-Back # BackFront-A-Back Front-B-Back Front-C-Back

echo Number_{1..5} # Number_1 Number_2 Number_3 Number_4 Number_5
```

Parameter Expansion ($)
```
echo $parameter # parameter_value
```

Command Substitution ( $(command) )
```
ls -l $(echi cp)
```


---
#### Quoting

Double Quote
- not suppress expansion
Single Quote
- suppress all expansion

#### Escaping Characters
