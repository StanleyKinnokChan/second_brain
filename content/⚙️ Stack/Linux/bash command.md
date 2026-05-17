---
title: bash command
tags:
  - linux
---
`pwd` = current directory
`df -h` = disk space
`cat <File_Name>` = print file content
`tar -cvf xxxx.tar <file_name>` = compress as the tar compress file
`tar -xvf xxxx.tar <file_name>` = decompress the tar compress file
`bash xxxx.sh` = run bash script
`chmod u+x <File_Name>` = give owner premission
`grep` = global regular expression
`tee` = often use with |, print the output and create/append a file


---
#### Pipe
- sending the output from first command to second command
- command to command
- it is useful to pass the content, because sometimes second command only accept pure string, not other command
	- e.g. `grep <pattern> <text>`
```
<command 1> | <command 2> 

# e.g.
ls -l /usr/bin | grep bash
```

---
#### Redirection Operator
- Command to File/ File to Command
```
# > symbol to write to a file
echo hello world! > hello.txt

# >> symbol append to a file
echo hello world! >> hello.txt

# < symbol feeding a file into a command
wc -w < hellow.txt

# << symbol is "Heredoc", provide a block of input directly within the script ending with a delimiter ("EOF" is common but could be any words)

cat << EOF
Here
is 
some
test
EOF
```

---
#### Conditions Evaluation

- `test` or `[ ]` can be used.
- A more modern and safer version of `[ ... ]` with additional features (e.g. pattern matching).
- There is no output in the terminal, it pass to the [[exit code]], which could be seen by `echo $?`
- there must be an space around =

```
[ 5 -eq 5 ]       # true
test 5 -eq 5      # same as above

[ "$name" = "Stanley" ]
test "$name" = "Stanley"

[ -f myfile.txt ]  # true if file exists and is a regular file

```

#### Common operators:

| Type    | Expression                               | Meaning                                         |
| ------- | ---------------------------------------- | ----------------------------------------------- |
| Integer | `-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge` | Equal, not equal, less than, etc.               |
| String  | `=`, `!=`, `-z`, `-n`                    | Equal, not equal, zero length, non-zero length  |
| File    | `-f`, `-d`, `-e`, `-r`, `-w`, `-x`       | Regular file, directory, exists, readable, etc. |
The operators defines how to evaluate the condition, e.g.:
[ 05 = 5 ]  -> string, [[exit code]] = 1
[ "a" -eq "b"] -> integer, error with exit code = 2


----
#### Argument

**Positional argument**
- $ sign followed by number (e.g. $1, $2)

**Default argument**
- positional argument + -<default_value> (e.g. ${1-dev})

**Parameter expansion **
- positional argument + two commas (e.g. ${1,,} )
- convert into lower case, esp useful for conditional evaluation

---
#### Control Operators

- `;` runs commands one after another, `$?` reflects the first command’s exit code.
- `&&` runs the next command only if the previous one succeeded (`exit 0`).
- `||` runs the next command only if the previous one failed (non-zero).

---
### Flow control

#### IF
```
if [ condition ]; then
	<statement>
elif [ condition ]; then
	<statement>
else
	<statement>
fi
```

#### Case statement
```
case word in
   pattern1 | pattern2)
      Statement(s) to be executed if pattern1 matches
      ;;
   pattern3)
      Statement(s) to be executed if pattern2 matches
      ;;
   pattern4)
      Statement(s) to be executed if pattern3 matches
      ;;
   *)
     Default condition to be executed
     ;;
esac
```

---
#### List and Loop
```
# define list variables and call the list
MY_LIST_VARIABLE = (one two three four)
echo ${MY_LIST_VARIABLE[@]}


# loop the list
for item in "${MY_LIST_VARIABLE[@]}"; do
    echo "$item"
done
```

---
#### Function
- in Bash, a function **does not need to explicitly declare parameters**
- The variables defined outside the function can be used within the function, however, the redefined the same variables within the function will change the value of the global variables. Therefore, "local" keyword is used.
- used "return 1/0" to return the exit code in a function, which can be chained with subsequent command
```
function_name(){
	local variables=value
	statement

	return 1
}

if [ $? = 1 ]; then
	echo "someone called the function"
fi
```


----
### Some useful technique

`set -e` is a shell option in `bash` that causes the script to **immediately exit** if any command returns a **non-zero error) exit status**
```
#! /bin/bash
set -e
...

```

You can set the default positional arg:
```
ENVIRONMENT=${1:-dev} # default as dev
```

---
#### General rules
- no space around = sign when defining the variables
- keep variables in upper case
- case-sensitive (e.g. X Echo but echo)
- Control structures: `if`, `then`, `fi` must be lowercase.

---
