# TDI Reference

## Contents
We'll probably do a table of all the each category, with simlinks to each heading


## Constants

### `$A0` (Opcode 1)

The BOHR Radius Constant of 52.9177E-12m, with a margin of error of 1168.02E-21

|||
|-|-|
| TDI Syntax | `$A0` |
| C Syntax | `Tdi3A0()` |
| Python Syntax | `MDSplus.dA0` |
| Java mdsplus-api Syntax | `CONST.dA0()` |


### `$2PI` (Opcode number: 372)

Two times pi, or equivalent to circumference of a circle divided by its radius (approx 6.2831853072)

|||
|-|-|
|TDI Syntax | `$2PI`|
|C Syntax   | `Tdi32Pi` |
|Python Syntax| `MDSplus.d2pi`|






## Functions

 ### `ADD` (Opcode 38)

Numeric Elemental. Add numbers.

Arguments A and B must be numeric.

**WARNING**: integer overflow is ignored.

Example: `[2,3,4] + 5.0` is `[7.0,8.0,9.0]`. 

>TODO: figure out whether it makes sense to have this in a more centralized place. This tells you what happens when you add two signals together, or add two numbers with different units (should be different with add/subtract vs multiply/divide, for example)

|||
|-|-|
|TDI Syntax| `A + B` or `ADD(A, B)`|
|C Syntax| `Tdi3ADD(A, B)`|
|Python Syntax| `MDSplus.ADD(A, B)`|
|Signals| Single signal or smaller data.|
|Units| Single or common units, else bad.|
|Form| Compatible form of A and B.|
|Result|The element-by-element sum of objects A and B.|

### `BUILD_WITH_UNITS` (Opcode 88)

MDS Operation. Make a describe data with units.

Example: `_S = BUILD_WITH_UNITS($VALUE*6,'m/s^2')` can be used in a `BUILD_SIGNAL(_S,BUILD_WITH_UNITS(5./1024*raw_node,'V'`) or similar. Note this could also have been `BUILD_WITH_UNITS(BUILD_SIGNAL($VALUE*6, BUILD_WITH_UNITS(5./1024*raw_node,'V')),'m/s^2')`. |

|||
|-|-|
| TDI syntax | `BUILD_WITH_UNITS(arg0,arg1)` |
| C Syntax | `Tdi3BuildWithUnits(arg0,arg1)` |
| Python Syntax | `MDSplus.BUILD_WITH_UNITS(arg0,arg1)` TODO: Confirm |
| Min Arguments | 2 |
| Max arguments | 2 |
|**Arguments**||
|DATA | any expression that DATA(this) will be valid. |
|UNITS | character string. See the primary section on "Units".|
|Result | Class-R descriptor. <BR> Use `BUILD_xxx` for immediate structure building. <BR> Use `MAKE_xxx` in FUNs for evaluated non-PUBLIC variables.|



### `MAKE_WITH_ERROR` (Opcode 447)

MDS Operation. Make a data with error structure.

Example: `_A0 = Build_With_Error(52.9177E-12, 2400E-21)`

|||
|-|-|
|TDI syntax | MAKE_WITH_ERROR(arg0,arg1)|
|C Syntax| `Tdi3MakeWithError` |
|Python Syntax| `Mdsplus.TdiMakeWithError(arg0,arg1)` |
|Max arguments | 2 |
|Min Arguments | 2 |
|**Arguments**||
|DATA |any expression that DATA(this) will be valid.|
|ERROR |Error value.|
|Result | Class-R descriptor.|
||Use `BUILD_xxx` for immediate structure building.|
||Use `MAKE_xxx` in FUNs for evaluated non-PUBLIC variables.|



### `IF` (Opcode 189)

CC Statement.

Do statement if expression true, else possibly do another.

Example: `IF (_A) _B=2; ELSE _B=3;`.

|||
|-|-|
|TDI syntax| if (condition) {statements} [else {statements}]|
|C Syntax|`TdiIf`|
|Python syntax: False|
|Min Arguments| 2|
|Max arguments| 3|
|Required Usual Forms| `IF (TEST) STMT` <BR> `IF (TEST) STMT ELSE ELSESTMT`.
|Function Form| `IF(TEST,STMT,[ELSESTMT])`. May be syntatically invalid.|
|Arguments Optional| `ELSESTMT`|
|TEST |logical scalar|
|STMT |statement, simple or `{brace enclosed}`.|
|ELSESTMT |statement, simple or `{brace enclosed}`.|
|Result |None|

### `SET_RANGE` (Opcode 311)

Transformation.
Set array bounds and multipliers from a list.

Examples:
* `_A=SET_RANGE(2:3,5,1:10)` is `[1, 3, 5, 7, 9]` and `[2, 4, 6, 8, 10]`
* `SET_RANGE(-2:,:3,_A)` has `LBOUND(_A,0)` of `[-2,-1]` and `UBOUND(_A,1)` of `[-1,3]`.

|||
|-|-|
|TDI syntax | `SET_RANGE(arg0,arg1,argn,...)`|
|C Syntax | TdiSetRange|
|Python Syntax | False|
|Min Arguments | 2|
|Max arguments | 9|
| **Arguments** | Optional: BOUND,....|
|| BOUND,... integer scalar or range, they are taken from ARRAY where omitted.|
| ARRAY | any type scalar, vector, or array.|
| Signals| Same as ARRAY.|
| Units | Same as ARRAY.|
| Form | Same type as ARRAY with shape from the bounds list. Any omitted bounds are picked from the corresponding bounds of ARRAY.|
| Result | Elements in array order from ARRAY. Immediate at compilation even if all but last argument are ranges and provided last argument is an array.|




## Other Special Variables beginning with `$`

### `$MISSING` (Opcode 17)

Missing value (or argument). `$MISSING` is used internally to mark a missing argument and gives zero or blanks. `$MISSING` and `$ROPRAND` execute at compilation.

|||
|-|-|
|TDI syntax| `$MISSING`|
|C Syntax| `Tdi3Missing`|
|Python Syntax| `MDSplus.dMissing`|