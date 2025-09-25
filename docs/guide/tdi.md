# TDI

TDI stands for Tree Data Interface.

At its core, the TDI language is a calculator that allows you to analyze data in your MDSplus trees. There are now 400+ built-in functions; in addition to constants and standard calculator operators, there are _____________ that let you pull . Users may also write their own functions to suit their needs (see below). 


The fact that it's a calculator might not sound like a big deal, but this was written from scratch back when this sort of thing was rare, and as it turns out, you would actually be hard-pressed to write a better one today, even with all of the computer science advancement in the last four decades.


TDI is mostly not case sensitive. There are exceptions.
The TDI reference page will be simply list every function and what it does.

TODO: reference thin client

## VSCode extension

You can add this extension to your VSCode so that TDI code is highlighted in different colors to improve legibility.

https://marketplace.visualstudio.com/items?itemName=MDSplus.mdsplus-tdi-language-support

## Operators
### Binary Operators
A, B are literals/variables in the examples below

| description | example | built-in |
|-----|-----|------|
|addition| `A + B` | `add(A, B)` |
|subtraction| `A - B` | `subtract(A, B)`|
|multiplication| `A * B` | `multiply(A, B)`|
|division| `A / B` | `divide(A, B)` |
|modulus (remainder)| `A % B` | `mod(A, B)` |
|concatenation| `A // B` | `concat(A, B)` |


### Unary Operators
Where A is a variable,
for Built-ins, only variables can be used

| description | example | built-in|
|-----|-----|---|
|post-increment| `A++` | `post_inc(_A)`|
|pre-increment| `++A` |`pre_inc(_A)`|
|post-decrement| `A--` |`post_dec(_A)`|
|pre-decrement| `--A` |`pre_dec(_A)`|


### Comparison Operators

A, B are literals/variables in the examples below
Only the C-style is recommended. 
>TODO: we'll probably slim down the table and all the non recommended stuff in reference or something

| description | C-style | fortran-style | built-in |
|-------------|---------|---------------|----------|
|equals| `A == B` | `A.EQ.B` | `equals(A, B)`|
|not equals | `A != B` or `A <> B`|`A.NEQ.B` |  `neq(A, B)` |
|greater than| `A > B` |`A.GT.B` | `gt(A, B)`|
|greater than or equal to| `A >= B` |`A.GE.B` | `ge(A, B)`|
|less than | `A < B` |`A.LT.B` | `le(A, B)`|
|less than or equal to | `A <= B` |`A.LE.B` | `le(A, B)` |
| Boolian and | `A && B` | `A.AND.B` |  `iand(A, B)` |
| Boolian or | `A \|\| B` | `A.OR.B` | `ior(A, B)` |


### Bitwise Operators

A, B are literals/variables in the examples below

| description | example |
|-----|-----|
|bitwise AND| `A & B` |
|bitwise OR| `A \| B` |
|bitwise XOR | `A ^ B` |
|bitwise NOT | `~A` |



how to terminate a line: each line must end with a semi-colon.





```Mark's personal notes
add 4 + 5
increment (post) 4++
increment (pre) ++4


_x = 4 + 5
# _x = 9

_x++
# _x = 10

++_x
# _x = 11

# buuuuuut...

# so this returns what _x is then increments _x
_y = _x++
# _y = 11
# _x = 12

# and this increments _x then returns the result
_y = ++_x
# _y = 13
# _y = 13

# backtick
TODO: ask Stephen if this belongs here

```





## Variables

* Variables must be prefixed with an underscore
* Variables not case sensitive

```tdi
# You can set it to numbers!
_x = 4

# You can set it to math!
_x = 4 + 5

# You can include units!
_x = build_with_units(60, "Hz")

# You can set it to the result of functions!
_x = myfunction()

```

### Scope
TODO: Tim

so this is like when there's a variable inside a for loop...when the for loop is over, is that variable still accessible?

Unlike Python, where you can just tab it over, curly braces {} are required for tdi functions

## Control Flow

### For Loop
### While Loop
### If Statement

## Built-Ins

### Write

### Read


## Functions


These are the two ways to add to TDI functionality
* Writing a .fun file.
* Writing a .py file.

For `MDS_PATH` (link to heading in environment variables)

### External Functions/Shared libraries

```tdi
# This will call `MyFunction` in `libMyLib.so`/`MyLib.dll`
MyLib->MyFunction()

```


### Status Codes

### Comments

```
# Single line comment

/*
Block
comment
*/
```


### Writing a .fun file.
To write a .fun file called `something`, put a file called `something.fun` on your `$MDS_PATH`. In that file, you make a function called `something`. 


`helloworld.fun`
```tdi
public fun helloworld()
{
        write(*, "Hello world");
        return(1);
}
```

Todos: Keyword `public`, `in`, `out`, `optional`

### `optional`
it's a keyword, perpended to an argument to a function that makes the argument optional 
to check to see if the argument was specified or passed, use the `present()` built-in.

## Python Integration
### Python from TDI 
Py()
TODO: organization

### TDI from Python