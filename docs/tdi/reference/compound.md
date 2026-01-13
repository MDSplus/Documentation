

### `$THIS` (Current Structure)

|||
|-|-|
|TDI Syntax   | `$THIS` |
|Python Syntax| `MDSplus.dTHIS()` |
|Java mdsplus-api Syntax| `CONST.dThis()`|
|Opcode|403|

For use with `Signal` or `Param`, can be used to access another field of the current structure.

Note: Can trigger infinite recursion

> TODO: Investigate use with Param and signal subscripting (see TdiGetData.c:605)

```tdi
# Reference the `raw` field of the Signal when defining the `value` field
# Note: The more correct way to do this is with $VALUE
TDI> _sig = build_signal(raw_of($this) * 10, [1, 2, 3])
Build_Signal(RAW_OF($THIS) * 10, [1,2,3])

# The `value` field is now an expression of the `raw` field
TDI> data(_sig)
[10,20,30]


# Reference a `dimension` field of the Signal when defining the `value` field
TDI> _sig = build_signal(dim_of($this) * 100, *, [0.1, 0.2, 0.3])
# The `value` field is now an expression of the first `dimension` field

TDI> data(_sig)
[10.,20.,30.]
```

See also:
* `BUILD_SIGNAL`
* `BUILD_PARAM`
* [`$VALUE`](#value-current-structure-value)
* `RAW_OF()`
* `DIM_OF()`
* `VALUE_OF()`
* `HELP_OF()`

### `$VALUE` (Current Structure Value)

|Opcode|30|
|||
|-|-|
|TDI Syntax   | `$VALUE` |
|Python Syntax| `MDSplus.dVALUE()` |
|Java mdsplus-api Syntax| `CONST.dValue()`|

For use with `Signal` or `Param`, can be used to access another field of the current structure.

When used in the `value` field of a `Signal`, it will reference the `raw_of()` the signal.
> TODO: Param

Note: Can trigger infinite recursion

> TODO: Investigate use with Param (see TdiGetData.c:622)

---

```tdi
# Reference the `raw` field of the Signal when defining the `value` field
TDI> _sig = build_signal($value * 10, [1, 2, 3])
Build_Signal($VALUE * 10, [1,2,3])

# The `value` field is now an expression of the `raw` field
TDI> data(_sig)
[10,20,30]
```

See also:
* `BUILD_SIGNAL`
* `BUILD_PARAM`
* [`$THIS`](#this-current-structure)
* `RAW_OF()`
* `VALUE_OF()`


# Types

## Action

## Call

## Condition

## Conglom

## Dependency

## Dimension

## Dispatch

## Event

## Function

## Method

## Opaque

## Parameter

## Path

## Range

> Warn about `RANGE()`

## Signal

`build_signal`/`make_signal`
`data` vs `value_of`/`raw_of`
use as an Array proxy
note that an operation involving two signals usually results in data, not a signal

## Window

## Value With Error

## Value With Units

Used to store units alongside data.

Units are case-sensitive, and you are responsible for managing the abbreviations. TDI will not understand that 'm' is the same as 'meters', for example.

Many functions will discard units, and others may modify the units based on the operation. Often, mismatched units will be replaced with '?'. See [`MULTIPLY`](#) and [`ADD`](#) for examples.

[`MAKE_WITH_UNITS(_VALUE, _UNITS)`](#) (Delayed)  
[`BUILD_WITH_UNITS(_VALUE, _UNITS)`](#build_with_units) (Immediate)

* `_VALUE` can be anything, but is usually [Numeric](#).  
Retrieve with [`VALUE_OF(_this)`](#value_of) (or [`DSCPTR_OF(_this, 0)`](#)).

* `_UNITS` should be a [Character](#).   
Retrieve with [`UNITS_OF(_this)`](#units_of) (or [`DSCPTR_OF(_this, 1)`](#)).

[`DATA()`](#) can be used to get and evaluate the value.

[`DATA_WITH_UNITS()`](#) can be used to get and evaluate the value while retaining the units.

```tdi
TDI> build_with_units(42, 'm')
Build_With_Units(42, "m")


TDI> value_of(build_with_units(42, 'm'))
42

TDI> units_of(build_with_units(42, 'm'))
"m"


TDI> build_with_units(1 : 10, 'm')
Build_With_Units(1 : 10, "m")

TDI> value_of(build_with_units(1 : 10, 'm'))
1 : 10

TDI> data(build_with_units(1 : 10, 'm'))
[1,2,3,4,5,6,7,8,9,10]
```

# Constructors

build - immediate
make - delayed

Difference between our `build_` and `make_` functions in TDI is that `build_` leaves variable references as variable references:
* `build_signal(_A,*,0:100)` creates a record that refers to the current (at evaluation time) value of the variable `_A`.
* `make_signal(_A,*,0:100)` creates a record that contains the current value of the variable `_A`.

### `build_action` 
|||
|-|-|
|TDI Syntax   | `build_action(arg0,arg1,arg2,arg3,arg4)` |
|Python Syntax| `MDSplus.build_action(arg0,arg1,arg2,arg3,arg4)` |
|Min arguments| 2|
|Max arguments| 5|
|Opcode|70|

Make an action descriptor.
Arguments
* DISPATCH dispatch descriptor.
* TASK procedure, program, routine, or method descriptor.
* ERRORLOGS a character scalar for error reports.
* COMPLETION notification list.
* PERFORMANCE unsigned long vector of statistics from execution.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |BUILD_ACTION(BUILD_DISPATCH("ident","phase","when",
"completion"),BUILD_ROUTINE(timeout,image,routine))
has only dispatch and task.

See also: Build Functions,  make_action

### `MAKE_ACTION`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 418
|Min arguments| 2
|Max arguments| 5
******Compiler syntax: MAKE_ACTION(arg0,arg1,arg2,arg3,arg4)
|Native python|False|


|Return Type  |MDS Operation |
Make an action descriptor.
Arguments DISPATCH dispatch descriptor. TASK procedure, program, routine, or method descriptor. ERRORLOGS a character scalar for error reports. COMPLETION notification list. PERFORMANCE unsigned long vector of statistics from execution.
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |MAKE_ACTION(MAKE_DISPATCH("ident","phase","when", "completion"),MAKE_ROUTINE(timeout,image,routine)) has only dispatch and task.

### `BUILD_CALL`
|||
|-|-|
|TDI Syntax   | `BUILD_CALL(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.BUILD_CALL(arg0,arg1,argn,...)` |
|Min arguments| 3|
|Max arguments| 254|
|Opcode 397|

|Return Type  |MDS Operation |
Make a call of a routine in a sharable image.
Usual Forms IMAGE->ROUTINE:KIND([ARG],...) or IMAGE->ROUTINE([ARG])
Arguments Optional: KIND, ARG... .
KIND byte unsigned scalar of KIND returned in R0.
Use DSC$K_DTYPE_DSC=24 for a pointer to an XD.
Use DSC$K_DTYPE_MISSING=0 for no information.
Default type is long integer.
Other accepted types are BU WU LU QU OU B W L Q O F D
NID and null-terminated strings T PATH EVENT.
IMAGE character scalar. It must be a simple filename in
SYS$SHARE or a logical name of the file.
ROUTINE character scalar.
ARG... arguments with certain options.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Use this form if IMAGE or ROUTINE must be expressions.
|Examples     |BUILD_CALL(24,'TDISHR','TDI$SIND',DESCR(30.)) is
the slow and hard way to do SIND(30.).
|See also     |CALL for info on argument form and type of output.

### `MAKE_CALL`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 434
|Min arguments| 3
|Max arguments| 254
******Compiler syntax: MAKE_CALL(arg0,arg1,argn,...)
|Native python|False|


|Return Type  |MDS Operation |
Make a call of a routine in a sharable image.
Usual Forms IMAGE->ROUTINE:KIND([ARG],...) or IMAGE->ROUTINE([ARG])
Arguments Optional: KIND, ARG... .
KIND byte unsigned scalar of KIND returned in R0. Use DSC$K_DTYPE_DSC=24 for a pointer to an XD. Use DSC$K_DTYPE_MISSING=0 for no information. Default type is long integer. Other accepted types areBU WU LUQU OUBW L QOF D NID and null-terminated strings T PATH EVENT.
IMAGE character scalar. It must be a simple filename in
SYS$SHARE or a logical name of the file. ROUTINE character scalar. ARG... arguments with certain options.
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables. Use this form if IMAGE or ROUTINE must be expressions.
|Examples     |MAKE_CALL(24,'TDISHR','TDI$SIND',DESCR(30.)) is the slow and hard way to do SIND(30.).
|See also     |CALL for info on argument form and type of output.

### `BUILD_CONDITION`
|||
|-|-|
|TDI Syntax   | `BUILD_CONDITION(arg0,arg1)` |
|Python Syntax| `MDSplus.BUILD_CONDITION(arg0,arg1)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|71|

|Return Type  |MDS Operation |
Make a condition descriptor.OBSOLETE. NO LONGER SUPPORTED.
Arguments
MODIFIER word unsigned, evaluated:
TREE$K_NEGATE_CONDITION 7
TREE$K_IGNORE_UNDEFINED 8
TREE$K_IGNORE_STATUS 9
CONDITION MDS event or path.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by COMPILE_DEPENDENCY.
|See also     |BUILD_DEPENDENCY BUILD_EVENT and COMPILE_DEPENDENCY.


### `MAKE_CONDITION`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 419
|Min arguments| 2
|Max arguments| 2
Compiler syntax: MAKE_CONDITION(arg0,arg1)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a condition descriptor.
Arguments
MODIFIER word unsigned, evaluated:
TREE$K_NEGATE_CONDITION 7
TREE$K_IGNORE_UNDEFINED 8
TREE$K_IGNORE_STATUS 9
CONDITION MDS event or path.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by COMPILE_DEPENDENCY.
|See also     |MAKE_DEPENDENCY MAKE_EVENT and COMPILE_DEPENDENCY.

### `BUILD_CONGLOM`
|||
|-|-|
|TDI Syntax   | `BUILD_CONGLOM(arg0,arg1,arg2,arg3)` |
|Python Syntax| `MDSplus.BUILD_CONGLOM(arg0,arg1,arg2,arg3)` |
|Min arguments| 4|
|Max arguments| 4|
|Opcode|72|

|Return Type  |MDS Operation |
Make a conglomerate descriptor.
Arguments
IMAGE character scalar.
MODEL character scalar.
NAME character scalar.
QUALIFIERS long vector, module dependent.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routines.

### `MAKE_CONGLOM`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 420
|Min arguments| 4
|Max arguments| 4
Compiler syntax: MAKE_CONGLOM(arg0,arg1,arg2,arg3)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a conglomerate descriptor.
Arguments
IMAGE character scalar.
MODEL character scalar.
NAME character scalar.
QUALIFIERS long vector, module dependent.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routines.

### `BUILD_DEPENDENCY`
|||
|-|-|
|TDI Syntax   | `BUILD_DEPENDENCY(arg0,arg1,arg2)` |
|Python Syntax| `MDSplus.BUILD_DEPENDENCY(arg0,arg1,arg2)` |
|Min arguments| 3|
|Max arguments| 3|
|Opcode|73|

|Return Type  |MDS Operation |
Make a dependency descriptor.
Arguments
OP_CODE word unsigned scalar, evaluated.
TREE$K_DEPENDENCY_AND 10
TREE$K_DEPENDENCY_OR 11
ARG_1 MDS condition, event, or path.
ARG_2 MDS condition, event, or path.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by COMPILE_DEPENDENCY.
|See also     |BUILD_CONDITION BUILD_EVENT and COMPILE_DEPENDENCY.

### `MAKE_DEPENDENCY`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 421
|Min arguments| 3
|Max arguments| 3
Compiler syntax: MAKE_DEPENDENCY(arg0,arg1,arg2)

|Native python|False|

Description:
|Return Type  |MDS Operation | Make a dependency descriptor.
Arguments
OP_CODE word unsigned scalar, evaluated.
TREE$K_DEPENDENCY_AND 10
TREE$K_DEPENDENCY_OR 11
ARG_1 MDS condition, event, or path.
ARG_2 MDS condition, event, or path.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by COMPILE_DEPENDENCY.
|See also     |MAKE_CONDITION MAKE_EVENT and COMPILE_DEPENDENCY.

### `BUILD_DIM` 
|||
|-|-|
|TDI Syntax   | `BUILD_DIM(arg0,arg1)` |
|Python Syntax| `MDSplus.BUILD_DIM(arg0,arg1)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|74|

|Return Type  |MDS Operation |
Make a dimension descriptor.
Arguments Optional: WINDOW.
WINDOW window descriptor.
If missing, all point of AXIS are included and
the initial point of the axis has an index of 0.
AXIS slope or, if defined, other descriptor type.
|Signals      |None.
|Units        |From AXIS. Should be same as WINDOW's value_at_idx0.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
The array will have bounds only if the
window has a defined value at index 0.
|Examples     |BUILD_DIM(BUILD_WINDOW(-1,3,10.),BUILD_SLOPE(3.))
makes dimension with value
SET_RANGE(-1:3, [7.,10.,13.,16.,19.]).

### `MAKE_DIM`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 422
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: MAKE_DIM(arg0,arg1) 
|Native python|False|


|Return Type  |MDS Operation |
Make a dimension descriptor.
Arguments Optional: WINDOW.
WINDOW window descriptor. If missing, all point of AXIS are included and the initial point of the axis has an index of 0.
AXIS slope or, if defined, other descriptor type.
|Signals      |None. |Units        |From AXIS. Should be same as WINDOW's value_at_idx0. |Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables. The array will have bounds only if the window has a defined value at index 0.
|Examples     |MAKE_DIM(MAKE_WINDOW(-1,3,10.),MAKE_SLOPE(3.)) makes dimension with value SET_RANGE(-1:3, [7.,10.,13.,16.,19.]).

### `BUILD_DISPATCH` 
|||
|-|-|
|TDI Syntax   | `BUILD_DISPATCH(arg0,arg1,arg2,arg3,arg4)` |
|Python Syntax| `MDSplus.BUILD_DISPATCH(arg0,arg1,arg2,arg3,arg4)` |
|Min arguments| 5|
|Max arguments| 5|
|Opcode|75|

|Return Type  |MDS Operation |
Make a dispatch descriptor.
Arguments
TYPE byte unsigned scalar, evaluated:
TREE$K_SCHED_ASYNC 1
TREE$K_SCHED_SEQ 2
TREE$K_SCHED_COND 3
IDENT character scalar.
PHASE character scalar.
WHEN character scalar?
COMPLETION character scalar?
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routine.

### `MAKE_DISPATCH`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 423
|Min arguments| 5
|Max arguments| 5
******Compiler syntax: MAKE_DISPATCH(arg0,arg1,arg2,arg3,arg4) 
|Native python|False|


|Return Type  |MDS Operation |
Make a dispatch descriptor.
Arguments
TYPE byte unsigned scalar, evaluated: TREE$K_SCHED_ASYNC 1 TREE$K_SCHED_SEQ 2 TREE$K_SCHED_COND 3
IDENT character scalar. PHASE character scalar. WHEN character scalar? COMPLETION character scalar?
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routine.

### `BUILD_EVENT`
|||
|-|-|
|TDI Syntax   | `BUILD_EVENT(arg0)` |
|Python Syntax| `MDSplus.BUILD_EVENT(arg0)` |
|Opcode|76|

|Return Type  |MDS Operation |
Make an event descriptor.
|Arguments, Results|STRING must be a character scalar expression.
|Result       |Class-S, data type-EVENT descriptor.
Immediate at compilation.
|Examples     |BUILD_EVENT('SHOT_DONE') makes an event for use in other
descriptors.
|See also     |BUILD_CONDITION BUILD_DEPENDENCY and COMPILE_DEPENDENCY.

### `BUILD_FUNCTION` 
|||
|-|-|
|TDI Syntax   | `BUILD_FUNCTION(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.BUILD_FUNCTION(arg0,arg1,argn,...)` |
|Min arguments| 1|
|Max arguments| 254|
|Opcode|77|

|Return Type  |MDS Operation |
Make a function descriptor.
Arguments Optional: ARG,... .
OPCODE unsigned word from 0 to the number defined less one.
ARG,... as needed by the function described by OPCODE.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |BUILD_FUNCTION(BUILTIN_OPCODE('SIN'),30) makes an
expression SIN(30).

### `MAKE_FUNCTION`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 424
|Min arguments| 1
|Max arguments| 254
******Compiler syntax: MAKE_FUNCTION(arg0,arg1,argn,...)
|Native python|False|


|Return Type  |MDS Operation |
Make a function descriptor.
Arguments Optional: ARG,... .
OPCODE unsigned word from 0 to the number defined less one.
ARG,... as needed by the function described by OPCODE.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |MAKE_FUNCTION(BUILTIN_OPCODE('SIN'),30) makes an expression SIN(30).


### `BUILD_METHOD`
|||
|-|-|
|TDI Syntax   | `BUILD_METHOD(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.BUILD_METHOD(arg0,arg1,argn,...)` |
|Min arguments| 3|
|Max arguments| 254|
|Opcode|78|

|Return Type  |MDS Operation |
Make a method descriptor.
Arguments Optional: ARG,... .
TIME_OUT real scalar.
METHOD character scalar.
OBJECT character scalar.
ARG,... as needed by METHOD applied to OBJECT.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routine.

### `MAKE_METHOD`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 425
|Min arguments| 3
|Max arguments| 254
Compiler syntax: MAKE_METHOD(arg0,arg1,argn,...)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a method descriptor.
Arguments Optional: ARG,... .
TIME_OUT real scalar.
METHOD character scalar.
OBJECT character scalar.
ARG,... as needed by METHOD applied to OBJECT.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routine.

### `BUILD_OPAQUE` 
|||
|-|-|
|TDI Syntax   | `BUILD_OPAQUE(arg0,arg1)` |
|Python Syntax| `MDSplus.BUILD_OPAQUE(arg0,arg1)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|454|

|Return Type  |MDS Operation |
Construct an Opaque object consisting of a byte array and a description string.
Usual Forms BUILD_OPAQUE(ARRAY,STRING)
Arguments:
ARRAY byte unsigned array
STRING text to indicate the format of the array (i.e. mpeg,gif,jpeg)
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |BUILD_OPAQUE([32bu,40bu,41bu,...],'jpeg')
Store a jpeg image in an MDSplus node. The MDSplus python
module provides an image method for Opaque objects which
uses the Image python module to examine the bytes
and determine the Image type contained in the bytes.
A series of Opaque objects can be stored as individual
segments in a tree node.

### `MAKE_OPAQUE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 455
|Min arguments| 2
|Max arguments| 2
Compiler syntax: MAKE_OPAQUE(arg0,arg1)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Construct an Opaque object consisting of a byte array and a description string. Usual Forms BUILD_OPAQUE(ARRAY,STRING)
Arguments:
ARRAY byte unsigned array
STRING text to indicate the format of the array (i.e. mpeg,gif,jpeg)
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |BUILD_OPAQUE([32bu,40bu,41bu,...],'jpeg')
Store a jpeg image in an MDSplus node. The MDSplus python
module provides an image method for Opaque objects which
uses the Image python module to examine the bytes
and determine the Image type contained in the bytes.
A series of Opaque objects can be stored as individual segments in a tree node.

### `BUILD_PARAM`
|||
|-|-|
|TDI Syntax   | `build_param(_VALUE, _HELP, _VALIDATION)` |
|Python Syntax| `MDSplus.build_param(_VALUE, _HELP, _VALIDATION)` |
|Min arguments| 3|
|Max arguments| 3|
|Opcode|79|

* Makes a parameter descriptor.
* Arguments
* `_VALUE` any.
* `_HELP` character. Textual information about VALUE.
* `_VALIDATION` logical scalar.
    * `$VALUE` may be used by VALIDATION to test VALUE without explicit reference to a tree path.
    * `$THIS` will give the parameter descriptor itself.
    * `$VALUE` and `$THIS` may only be used within `GET_DATA` evaluations of the arguments.
* WARNING Use of $THIS and $VALUE may be infinitely recursive.

|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Examples
<!-- as long as the value is greater than 6 and the `help_of` text is not an empty string, validation will return true  --> 
* with `_PARAM = build_param(42.0,'The answer.', $VALUE > 6 && help_of($THIS) <> "")`  
then `data({_PARAM})` is `42.0` and `validation({_PARAM})` returns `1BU`.

### `MAKE_PARAM`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 426
|Min arguments| 3
|Max arguments| 3
Compiler syntax: MAKE_PARAM(arg0,arg1,arg2)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a parameter descriptor.
Arguments
VALUE any.
HELP character. Textual information about VALUE.
VALIDATION logical scalar. $VALUE may be used by VALIDATION to
test VALUE without explicit reference to a tree path.
$THIS will give the parameter descriptor itself.
$VALUE and $THIS may only be used within GET_DATA
evaluations of the arguments.
>>>>>>>>>WARNING Use of $THIS and $VALUE may be infinitely recursive.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |MAKE_PARAM(42.0,'The answer.',
$VALUE > 6 && HELP_OF($THIS) <> "").
DATA(above) is 42.0 and VALIDATION(above) is 1BU.

### `BUILD_PATH`
|||
|-|-|
|TDI Syntax   | `BUILD_PATH(arg0)` |
|Python Syntax| `MDSplus.BUILD_PATH(arg0)` |
|Min arguments| 1|
|Max arguments| 1|
|Opcode|80|

|Return Type  |MDS Operation |
Make a path (tree location) descriptor.
|Arguments, Results|STRING must be a character scalar expression.
|Result       |Class-S, data type-PATH descriptor.
Immediate at compilation.
|Examples     |BUILD_PATH('\TOP.XRAY:LEADER') makes a path that can be
evaluated.


### `BUILD_PROCEDURE` 
|||
|-|-|
|TDI Syntax   | `BUILD_PROCEDURE(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.BUILD_PROCEDURE(arg0,arg1,argn,...)` |
|Min arguments| 3|
|Max arguments| 254|
|Opcode|81|

|Return Type  |MDS Operation |
Make a procedure call
Arguments Optional: ARG,... .
TIME_OUT real scalar.
LANGUAGE character scalar. The language in which the procedure
is written.
PROCEDURE character scalar.
ARG,... as needed by the procedure.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routine.

### `MAKE_PROCEDURE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 427
|Min arguments| 3
|Max arguments| 254
Compiler syntax: MAKE_PROCEDURE(arg0,arg1,argn,...)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a procedure call
Arguments Optional: ARG,... .
TIME_OUT real scalar.
LANGUAGE character scalar. The language in which the procedure
is written.
PROCEDURE character scalar.
ARG,... as needed by the procedure.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routine.

### `BUILD_PROGRAM` 
|||
|-|-|
|TDI Syntax   | `BUILD_PROGRAM(arg0,arg1)` |
|Python Syntax| `MDSplus.BUILD_PROGRAM(arg0,arg1)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|82|

|Return Type  |MDS Operation |
Make a procedure call
Arguments Optional: ARG,... .
TIME_OUT real scalar.
LANGUAGE character scalar. The language in which the procedure
is written.
PROCEDURE character scalar.
ARG,... as needed by the procedure.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |None, normally done by module add routine.

### `MAKE_PROGRAM`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 428
|Min arguments| 2
|Max arguments| 2
Compiler syntax: MAKE_PROGRAM(arg0,arg1)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a program call
Arguments
TIME_OUT real scalar.
PROGRAM character scalar. The name of a program to be run.
The program must be responsible for entering its data in
the tree.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |MAKE_PROGRAM(1.2,'MYDISK:MYPROGRAM').

### `BUILD_RANGE`
|||
|-|-|
|TDI Syntax   | `BUILD_RANGE(arg0,arg1,arg2)` |
|Python Syntax| `MDSplus.BUILD_RANGE(arg0,arg1,arg2)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|83|

|Return Type  |MDS Operation |
Make a range descriptor.
Usual Form START .. END [.. DELTA] or START : END [: DELTA].
Arguments Optional: DELTA; START and END when used as subscript
limits. See the specific routine; otherwise, required.
START scalar. The starting value.
END scalar. The last value.
DELTA scalar. The increment. Default is one.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
This uses a data type RANGE, whereas
DTYPE_RANGE(START,END,DELTA) is a function.
On evaluation, the compatible data type.
A vector of length max((END - BEGIN)/DELTA,0) elements.
The first value will be BEGIN and successive values will
differ by DELTA. The last value will not be futher from
BEGIN than END.
WARNING, the number of element cannot always be predicted for fractional delta, 1:2:.1 may have 10 or 11 elements.
WARNINGS, the colon (:) form may be confused with a tree member and the dot-dot (..) form is hard to read/understand, use spaces.
Examples. 2:5 becomes [2,3,4,5] and 2:5:1.8 becomes [2.,3.8].

### `MAKE_RANGE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 429
|Min arguments| 2
|Max arguments| 3
******Compiler syntax: MAKE_RANGE(arg0,arg1,arg2) 
|Native python|False|


|Return Type  |MDS Operation |
Make a range descriptor.
Usual Form START .. END [.. DELTA] or START : END [: DELTA].
Arguments Optional: DELTA; START and END when used as subscript
limits. See the specific routine; otherwise, required. START scalar. The starting value. END scalar. The last value. DELTA scalar. The increment. Default is one.
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables. This uses a data type RANGE, whereas DTYPE_RANGE(START,END,DELTA) is a function. On evaluation, the compatible data type. A vector of length max((END -BEGIN)/DELTA,0) elements.
The first value will be BEGIN and successive values will differ by DELTA. The last value will not be futher from BEGIN than END.
>>>>>>>>>WARNING, the number of element cannot always be predicted for fractional delta, 1:2:.1 may have 10 or 11 elements.
>>>>>>>>>WARNINGS, the colon (:) form may be confused with a tree member and the dot-dot (..) form is hard to read/understand, use spaces.
Examples. 2:5 becomes [2,3,4,5] and 2:5:1.8 becomes [2.,3.8].

### `BUILD_ROUTINE`
|||
|-|-|
|TDI Syntax   | `BUILD_ROUTINE(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.BUILD_ROUTINE(arg0,arg1,argn,...)` |
|Min arguments| 3|
|Max arguments| 254|
|Opcode|84|

|Return Type  |MDS Operation |
Make a routine descriptor.
Arguments Optional: ARG,... .
TIME_OUT real scalar.
IMAGE character scalar.
ROUTINE character scalar.
ARG,... as needed by the routine.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |BUILD_ROUTINE(1.2,MYIMAGE,MYROUTINE,5).


### `MAKE_ROUTINE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 430
|Min arguments| 3
|Max arguments| 254
******Compiler syntax: MAKE_ROUTINE(arg0,arg1,argn,...)
|Native python|False|


|Return Type  |MDS Operation |
Make a routine descriptor.
Arguments Optional: ARG,... . TIME_OUT real scalar. IMAGE character scalar. ROUTINE character scalar. ARG,... as needed by the routine.
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |MAKE_ROUTINE(1.2,MYIMAGE,MYROUTINE,5).

### `BUILD_SIGNAL`
|||
|-|-|
|TDI Syntax   | `BUILD_SIGNAL(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.BUILD_SIGNAL(arg0,arg1,argn,...)` |
|Min arguments| 2|
|Max arguments| 10|
|Opcode|85|

|Return Type  |MDS Operation |
Make data with dimensions.
Arguments Optional: DIMENSION,... .
DATA any expression. It may include $VALUE for RAW without a
tree reference or $THIS to refer to the whole signal.
$VALUE and $THIS may only be used within GET_DATA
evaluations of the signal.
WARNING Use of $THIS and $VALUE may be infinitely recursive.
RAW any expression. Usually the actual stored integer data.
DIMENSION,... dimension descriptor. The number of dimension
descriptors must match rank of DATA.
WARNING, if the dimension is not of data type dimension, then
subscripting is by index value and not axis value.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |BUILD_SIGNAL(BUILD_WITH_UNITS($VALUE*6,'m/s^2'),
BUILD_WITH_UNITS(5./1024*[1,2,3],'V'),
BUILD_DIMENSION(BUILD_WINDOW(0,2,10.),
BUILD_SLOPE(BUILD_WITH_UNITS(3.,'s'))))
NOTE: Use BUILD_xxx for immediate structure building. (From Build_Call.)
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Use this form if IMAGE or ROUTINE must be expressions.

### `MAKE_SIGNAL`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 431
|Min arguments| 2
|Max arguments| 10
******Compiler syntax: MAKE_SIGNAL(arg0,arg1,argn,...)
|Native python|False|


|Return Type  |MDS Operation |
Make data with dimensions.
Arguments Optional: DIMENSION,... .
DATA any expression. It may include $VALUE for RAW without a tree reference or $THIS to refer to the whole signal. $VALUE and $THIS may only be used within GET_DATA evaluations of the signal.
>>>>>>>>>WARNING Use of $THIS and $VALUE may be infinitely recursive. RAW any expression. Usually the actual stored integer data. DIMENSION,... dimension descriptor. The number of dimension
descriptors must match rank of DATA. >>>>>>>>>WARNING, if the dimension is not of data type dimension, then subscripting is by index value and not axis value.
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Example.
MAKE_SIGNAL( MAKE_WITH_UNITS( $VALUE*6, 'm/s^2' ), MAKE_WITH_UNITS( 5./1024*[1,2,3], 'V' ), MAKE_DIMENSION( MAKE_WINDOW( 0,2,10. ),
MAKE_SLOPE( MAKE_WITH_UNITS(3.,'s') )
))Here the RAW part of the Signal is referred to in the expression for the DATA part as $
VALUE. NOTE: Use BUILD_xxx for immediate structure building. (From Build_Call.)Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.

### `BUILD_SLOPE`
|||
|-|-|
|TDI Syntax   | `BUILD_SLOPE(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.BUILD_SLOPE(arg0,arg1,argn,...)` |
|Min arguments| 1|
|Max arguments| 254|
|Opcode|86|

|Return Type  |MDS Operation |
Make a piece-wise linear slope-axis for dimension.
>>>>>>>>>WARNING, this is a deprecated feature and there is no assurance
of future support.
Arguments Optional: BEGIN, END, and more segments.
SLOPE real scalar. Ratio of change of axis to change of index.
BEGIN real scalar. Axis starting point.
END real scalar. Axis ending point, the last value.
Note. The axis may be divided into multiple segments.
Without a window ISTART, there must be a first BEGIN.
If the slope is used in a dimension with a window, then
the greater of the window's ISTART or the first BEGIN is
used and the lesser of the window's IEND or the last END
is used, assuming positive slope.
|Signals      |None.
|Units        |Combined from SLOPE and BEGIN. END units are combined
from the first segment if no BEGIN is applied.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Examples. BUILD_SLOPE(3.0) is a constant ratio of 3 axis values
per index step. Axes can be infinite in extent.
A finite axis of BUILD_SLOPE(3,12,21) has data points
[12,15,18,21].
BUILD_SLOPE(3.0,,10.,4.0,20.0) has points at
...,4.0,7.0,20.0,24.0,28.0,... . Note that the dead zone
from 10 to 20 is absent and that thus 10.0 becomes 20.0.
Often BEGIN[j+1] is the same as END[j] + SLOPE[j] as in
a clock that does not stop but does change rate.

### `MAKE_SLOPE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 440
|Min arguments| 1
|Max arguments| 254
******Compiler syntax: MAKE_SLOPE(arg0,arg1,argn,...)
|Native python|False|


|Return Type  |MDS Operation |
Make a piece-wise linear slope-axis for dimension. >>>>>>>>>WARNING, this is a deprecated feature and there is no assurance of future support.
Arguments Optional: BEGIN, END, and more segments. SLOPE real scalar. Ratio of change of axis to change of index. BEGIN real scalar. Axis starting point. END real scalar. Axis ending point, the last value.
Note. The axis may be divided into multiple segments. Without a window ISTART, there must be a first BEGIN. If the slope is used in a dimension with a window, then the greater of the window's ISTART or the first BEGIN is used and the lesser of the window's IEND or the last END is used, assuming positive slope.
|Signals      |None. |Units        |Combined from SLOPE and BEGIN. END units are combined from the first segment if no BEGIN is applied.
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Examples. MAKE_SLOPE(3.0) is a constant ratio of 3 axis values per index step. Axes can be infinite in extent. A finite axis of MAKE_SLOPE(3,12,21) has data points [12,15,18,21]. MAKE_SLOPE(3.0,,10.,4.0,20.0) has points at ...,4.0,7.0,20.0,24.0,28.0,... . Note that the dead zone
from 10 to 20 is absent and that thus 10.0 becomes 20.0. Often BEGIN[j+1] is the same as END[j] + SLOPE[j] as in a clock that does not stop but does change rate.

### `BUILD_WINDOW`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Min arguments| 3|
|Max arguments| 3|
|Opcode|87|

|Return Type  |MDS Operation |
Make a window descriptor for a dimension.
Arguments Optional: ISTART, IEND, X_AT_0.
ISTART integer scalar. First element stored.
IEND integer scalar. Last element stored.
X_AT_0 real scalar. Value at index zero.
The effective defaults are -HUGE(1), +HUGE(1), and zero.
If missing completely, the beginning of the axis is
used for X_AT_0 when evaluating a dimension.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |BUILD_WINDOW(-1024,7168,BUILD_WITH_UNIT(-0.1,'s'))

### `MAKE_WINDOW`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 432
|Min arguments| 3
|Max arguments| 3
Compiler syntax: MAKE_WINDOW(arg0,arg1,arg2)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a window descriptor for a dimension.
Arguments Optional: ISTART, IEND, X_AT_0.
ISTART integer scalar. First element stored.
IEND integer scalar. Last element stored.
X_AT_0 real scalar. Value at index zero.
The effective defaults are -HUGE(1), +HUGE(1), and zero.
If missing completely, the beginning of the axis is
used for X_AT_0 when evaluating a dimension.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |MAKE_WINDOW(-1024,7168,MAKE_WITH_UNIT(-0.1,'s'))

### `BUILD_WITH_ERROR`
|||
|-|-|
|TDI Syntax   | `BUILD_WITH_ERROR(arg0,arg1)` |
|Python Syntax| `MDSplus.BUILD_WITH_ERROR(arg0,arg1)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|445|

|Return Type  |MDS Operation |
Make a data with error structure.
Arguments
DATA any expression that DATA(this) will be valid.
ERROR Error value.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Example:
_A0 = Build_With_Error(52.9177E-12, 2400E-21)

### `MAKE_WITH_ERROR`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 447
|Min arguments| 2
|Max arguments| 2
Compiler syntax: MAKE_WITH_ERROR(arg0,arg1)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a data with error structure.
Arguments
DATA any expression that DATA(this) will be valid.
ERROR Error value.
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Example:
_A0 = Build_With_Error(52.9177E-12, 2400E-21)

### `BUILD_WITH_UNITS` 

|||
|-|-|
|TDI syntax | `BUILD_WITH_UNITS(_VALUE, _UNITS)` |
|Python Syntax | `MDSplus.WithUnits(value, units)` or `MDSplus.BUILD_WITH_UNITS(value, units)` |
|Opcode 88|

See [Value With Units](#value-with-units).

### `MAKE_WITH_UNITS`

|||
|-|-|
|TDI Syntax   | `MAKE_WITH_UNITS(_VALUE, _UNITS)` |
|Opcode|433|

See [Value With Units](#value-with-units).

### `dtype_range` (Opcode 292)

|||
|-|-|
|TDI Syntax   | `DTYPE_RANGE(_START,_END,[_INCREMENT])` |
|Python Syntax| `MDSplus.DTYPE_RANGE(_START,_END,[_INCREMENT])`|
|Min arguments| 2 |
|Max arguments| 3 |


Compile time evaluation of a BUILD_RANGE
* Form: DTYPE_RANGE(_START,_END,[_INCREMENT])
* This is intended to be used with integers and while fractional elements may work there also may be some odities with when they end due to rounding
* WARNING, the number of elements cannot always be predicted for fractional delta, (e.g., `1:2:.1` may return 10 or 11 elements).

Arguments 
* `_START` anything that evaluates to a numeric value to denote start of range 
* `_END` anything that evaluates to a numeric value to denote end of range 
* `[_INCRMENT]` (optional) anything that evaluates to a numeric value to denote increment from one to the next

Example: 
* `DTYPE_RANGE(1,100,10)` is `[1,11,21,31,41,51,61,71,81,91]`
* Equivalent to `DATA(1 : 100 : 10)`


The range is 99 = End - Begin = 100 - 1
n_fractional_elements = range divided by delta = 99 / 17.5 = 5.687...
The code then rounds n_fractional_elements to the nearest whole number = n_rounded_elments = 6
max range = n_rounded_elements * delta + begin = 6 * 17.5 + 1 = 106

> TODO: This is weird, but makes sense given Mark W.'s explanation below. Come back to this and investigate to confirm
`DTYPE_RANGE(1.0,100,17.5)` returns
`[1.,18.5,36.,53.5,71.,88.5,106.]`

Here is how this function likely works:
* First, the The range is calculated (_END - _START)
* n_fractional_elements = range divided by delta = 99 / 17.5 = 5.687...
* The code then rounds n_fractional_elements to the nearest whole number = * n_rounded_elements = 6
* max range = n_rounded_elements * delta + begin = 6 * 17.5 + 1 = 106


# Accessors

### `AXIS_OF` 
|||
|-|-|
|TDI Syntax   | `axis_of(arg0)` |
|Python Syntax| `MDSplus.axis_of(arg0)` |
|Opcode 61|

This is deprecated.

Get the axis field.
Argument is searched for these:
* `DSC$K_DTYPE_DIMENSION`, the axis field.
* `DSC$K_DTYPE_RANGE`, the range.
* `DSC$K_DTYPE_SLOPE`, the slope, !deprecated!.
* Otherwise, an error.

Examples

```tdi
TDI> AXIS_OF(BUILD_DIM(BUILD_WINDOW(B,E,X0),1:10))
1:10
```

### `BEGIN_OF`

|||
|-|-|
|TDI Syntax   | `BEGIN_OF(_A, [_N])` |
|Python Syntax| `MDSplus.BEGIN_OF(_A, [_N])` |
|Min arguments| 1|
|Max arguments| 2|
|Opcode|64|

Gets the `begin` field of things that have a `begin` field (ranges, slopes, windows, etc.).
TODO: reword this as needed

Arguments 
* `_A` is searched for these:
    * `DSC$K_DTYPE_RANGE`, the begin field (may be an array).
    * `DSC$K_DTYPE_SLOPE`, N-th segment's begin field !deprecated!.
    * `DSC$K_DTYPE_WINDOW`, the startidx field.
    * Otherwise, an error.

* `_N` optional: integer scalar, for slopes from 1 to the number of segments less one. The first segment has no beginning if the axis is infinite.


Examples

```tdi
TDI> BEGIN_OF(1:10)
1
```

See also: 
* `end_of`

### `completion_message_of` 
|||
|-|-|
|TDI Syntax   | `completion_message_of(arg0)` |
|Python Syntax| `MDSplus.completion_message_of(arg0)` |
|Opcode|442|

MDS Operation
Get the completion field.
Argument is searched for this: DSC$K_DTYPE_ACTION, the completion_message field.
Otherwise, an error.

See also build functions

TODO: COME BACK TO THIS


### `completion_of` 
|||
|-|-|
|TDI Syntax   | `completion_of(arg0)` |
|Python Syntax| `MDSplus.COMPLETION_OF(arg0)` |
|Opcode|100|

|Return Type  |MDS Operation |
Get the completion field.

DISPATCH_OF(A) is searched for this: DSC$K_DTYPE_DISPATCH, the completion field. Otherwise, an error.

TODO: COME BACK TO THIS
See also build functions, dispatch

### `CONDITION_OF` (Opcode 401)

|||
|-|-|
|TDI Syntax   | `CONDITION_OF(arg0)` |
|Python Syntax| `MDSplus.CONDITION_OF(arg0)` |
|Min arguments| 1
|Max arguments| 1

TODO: Come back to this

|Return Type  |MDS Operation |
Get the condition field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_CONDITION, the condition field. Otherwise, an error.

### `dim_of` (Opcode 127)

|||
|-|-|
|TDI Syntax   | `dim_of(_A,[_N])` |
|Python Syntax| `MDSplus.dim_of(_A,[_N])` |
|Min arguments| 1 |
|Max arguments| 2 |

Not to be confused with `dim`.

Gets the dimension.
Arguments
* `A`: VMS or MDS descriptor as below.
    * DSC$K_CLASS_A, range of N-th lower and upper bounds. 
    * DSC$K_CLASS_APD, range of N-th lower and upper bounds. 
    * DSC$K_CLASS_CA, range of N-th lower and upper bounds. 
    * DSC$K_DTYPE_DIMENSION, unchanged. 
    * DSC$K_DTYPE_SIGNAL, the N-th dimension field. 
    * Otherwise, an error.
* `N`: (optional): integer scalar from 0 to the number of dimension of a signal.

Examples
* `DIM_OF([1,2,3])` returns `0 : 2`, or, the range from 0 to 2.
* `DIM_OF([1,3,5,7])` returns `0 : 3`
* With `_b  = [[1, 2, 3], [4, 5, 6]]`
    * `dim_of(_b)`    returns `0 : 2`
    * `dim_of(_b, 0)` returns `0 : 2`
    * `dim_of(_b, 1)` returns `0 : 1`

### `DISPATCH_OF` (Opcode 128)

|||
|-|-|
|TDI Syntax   | `DISPATCH_OF(arg0)` |
|Python Syntax| `MDSplus.DISPATCH_OF(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

|Return Type  |MDS Operation |
Get the dispatch field.
Argument must be one of:
* DSC$K_DTYPE_ACTION, the dispatch field. 
* DSC$K_DTYPE_DISPATCH, unchanged. 
* Otherwise, an error.

TODO: Come back to this


### `dscptr` (Opcode 134)

|||
|-|-|
|TDI Syntax   | `dscptr(arg0,arg1) ` |
|Python Syntax| `MDSplus.dscptr(arg0,arg1) ` |
|Min arguments| 1 |
|Max arguments| 2 |

> TODO: investigate further--doesn't seem to be working. Deprecated/never implemented?

Get a field of any class-R descriptor.

Arguments
* `A` any class-R or class-APD descriptor. 
* `N` (optional) integer scalar from 0 to the number of pointers less 1.

Result
* The N-th descriptor of A for class R or the N-th list element for class APD. * Descriptor data types (DSC$K_DTYPE_DSC) are removed. 
* Immediate at compilation for non-class-R. 
* Use `DSCPTR` for A without NID, PATH, or variable. 
* Use `DSCPTR_OF` for A including them.
* Warning: the N-th element may not describe the N-th data value.

Examples
`DSCPTR(A+B,1)` is `B`.

See also: 
* `ARG_OF` for argument fields of some class-R descriptors 
* specific `xxx_OF` routines for other fields.

### `dscptr_of` (Opcode 436)

|||
|-|-|
|TDI Syntax   | `dscptr_of(arg0,arg1)` |
|Python Syntax| `MDSplus.dscptr_of(arg0,arg1)` |
|Min arguments| 1 |
|Max arguments| 2 |

Get a field of any class-R descriptor.

Arguments
* `A` any class-R or class-APD descriptor.
* `N` (optional) integer scalar from 0 to the number of pointers less 1.

Returns: 
* The N-th descriptor of A for class R or the N-th list element for class APD.
* Descriptor data types (DSC$K_DTYPE_DSC) are removed.
* Immediate at compilation for non-class-R.
* Use `DSCPTR` for A without NID, PATH, or variable.
* Use `DSCPTR_OF` for A including them.
* Warning, the N-th element may not describe the N-th data value.

Examples
* `DSCPTR_OF(A+B,1)` is `B`.
See also
* `ARG_OF` for argument

### `end_of` (Opcode 148)

|||
|-|-|
|TDI Syntax   | `end_of(_RANGE,[_N]) ` |
|Python Syntax| `MDSplus.end_of(_RANGE,[_N]) ` |
|Min arguments| 1 |
|Max arguments| 2 |

Get the end of a field.

Arguments
* `_RANGE` must be one of the below. 
    * `DSC$K_DTYPE_RANGE,` the end field. (`_start: _end: _increment`)
    * `DSC$K_DTYPE_SLOPE`, N-th segment's end field. 
    * !deprecated! `DSC$K_DTYPE_WINDOW`, the endidx field. Otherwise, an error.
* `[_N]` (optional) Actually this doesn't work. lol  
~~integer scalar, for slopes from 0 to the number of segments less two. The last segment has no end if the axis is infinite.~~
> TODO: come back to this and investigate

Examples
`END_OF(1:10)` returns `10`.

See also: `set_range`

### `errorlogs_of` (Opcode 398)

|||
|-|-|
|TDI Syntax   | `errorlogs_of(arg0)` |
|Python Syntax| `MDSplus.errorlogs_of(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

Get the errorlogs field.
Argument, A is searched for this: `DSC$K_DTYPE_ACTION`, the errorlogs field. Otherwise, an error.

> TODO: Come back to this one. 



### `error_of` (Opcode 446)

|||
|-|-|
|TDI Syntax   | `error_of(arg0)` |
|Python Syntax| `MDSplus.error_of(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

Gets the error field of a build_with_error object.
* Arguments: Object with error field
* Returns the value of the error field or an evaluation error

Example
* `error_of(build_with_error(1, .002))` returns `.002`


### `help_of` (Opcode 180)

|||
|-|-|
|TDI Syntax   | `help_of(arg0)` |
|Python Syntax| `MDSplus.help_of(arg0)` |G_FLOAT(12)
|Min arguments| 1 |
|Max arguments| 1 |

Get the help field.
* Argument is searched for in `DSC$K_DTYPE_PARAM`, and returns text in the help field (2nd argument of `build_param`). Otherwise, an error.

Examples
`HELP_OF(BUILD_PARAM(42,"the answer",$VALUE>6))` is `"the answer"`. 

See also
* `build_param`, `make_param`
* `$VALUE` and `$THIS` for use of this within a parameter.


### `ident_of` (Opcode 188)

|||
|-|-|
|TDI Syntax   | `ident_of(arg0)` |
|Python Syntax| `MDSplus.ident_of(arg0)` |
|Min arguments| 1
|Max arguments| 1

Get the ident field.
* `DISPATCH_OF(A)` is searched for this: `DSC$K_DTYPE_DISPATCH`, the ident field. Otherwise, an error.


### `image_of` (Opcode 191)

|||
|-|-|
|TDI Syntax   | `IMAGE_OF(arg0)` |
|Python Syntax| `MDSplus.IMAGE_OF(arg0)` | 
|Min arguments| 1 |
|Max arguments| 1 |

Get the image field. 
Argument is searched for within these:
* DSC$K_DTYPE_CALL, the image field. 
* DSC$K_DTYPE_CONGLOM, the image field. 
* DSC$K_DTYPE_ROUTINE, the image field. Otherwise, an error.

> TODO: Come back to this for further investigation

### `INTERRUPT_OF` 

|||
|-|-|
|TDI Syntax   | `INTERRUPT_OF(arg0) ` |
|Python Syntax| `MDSplus.INTERRUPT_OF(arg0) ` |
|Opcode|443|

> TODO: Come back to this for further investigation; we don't currently have any good examples with interrupts

|Return Type  |MDS Operation |
Get the interrupt field.
|Arguments, Results|Descriptor as below.
|Result       |DISPATCH_OF(A) is searched for this: DSC$K_DTYPE_DISPATCH, the interrupt field. The dispatch qualifier must be TREE$K_SCHED_ASYNC and the result must evaluate to text DSC$K_DTYPE_T. Otherwise, an error.

### `LANGUAGE_OF` (Opcode 214)

|||
|-|-|
|TDI Syntax   | `LANGUAGE_OF(`_A`) ` |
|Python Syntax| `MDSplus.LANGUAGE_OF(`_A`) ` |
|Min arguments| 1 |
|Max arguments| 1 |


Get the language field.
Argument `_A` is searched for within `DSC$K_DTYPE_PROCEDURE`, the language field. Otherwise, an error.

>TODO: Come back to this? maybe?


### `NDESC` (Number of Descriptors, TODO)

|||
|-|-|
|TDI Syntax   | `NDESC(arg0) ` |
|Python Syntax| `MDSplus.NDESC(arg0) ` |
|Opcode|251|

Returns the number of descriptors in the class-R descriptor of an MDS record.
* Argument must be an MDS class-R descriptor.
* Descriptor data types (`DSC$K_DTYPE_DSC`) are removed.
* Use `NDESC` for count without NID, PATH, or variable. 
* Use `NDESC_OF` for count including them.

Examples (TODO...)
```tdi
NDESC($VALUE) is 0. 

# Correct syntax
TDI> _sum = make_function(builtin_opcode("add"),3, 4)
3 + 4
TDI> ndesc(_sum)
2BU

# This syntax will cause an error; use the above example or NDESC_OF.
TDI> ndesc(4+5)
%TDI Error in NDESC(4 + 5)
%TDI Error in EXECUTE("ndesc(4+5)")
```


### `NDESC_OF` (Number of Descriptors of, TODO)
|||
|-|-|
|TDI Syntax   | `NDESC_OF(arg0)` |
|Python Syntax| `MDSplus.NDESC_OF(arg0)` |
|Opcode|438|

Returns the number of descriptors in the class-R descriptor of an MDS record.
* Argument must be an MDS class-R descriptor.
* Descriptor data types (`DSC$K_DTYPE_DSC`) are removed.
* Use `NDESC` for count without NID, PATH, or variable. 
* Use `NDESC_OF` for count including them.

Examples

```tdi
TDI> NDESC_OF($VALUE)
0BU

TDI> NDESC_OF(4+5)
2BU

TDI> _sum = make_function(builtin_opcode("add"),3, 4)
3 + 4
TDI> NDESC_OF(_sum)
%TDI Error in NDESC_OF(_sum)
%TDI Error in EXECUTE("NDESC_OF(_sum)")
```

### `OBJECT_OF`
|||
|-|-|
|TDI Syntax   | `OBJECT_OF(_METHOD)` |
|Python Syntax| `MDSplus.OBJECT_OF(_METHOD)` |
|Opcode|259|

Gets the object field from `DSC$K_DTYPE_METHOD`

### `PERFORMANCE_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Opcode|399|


Get the performance statistics field from DSC$K_DTYPE_ACTION


### `PHASE_OF`
|||
|-|-|
|TDI Syntax   | `PHASE_OF(arg0)` |
|Python Syntax| `MDSplus.PHASE_OF(arg0)` |
|Opcode|271|

Get the phase field from DSC$K_DTYPE_DISPATCH.


### `PROCEDURE_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 279
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PROCEDURE_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the procedure field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_PROCEDURE, the procedure field. Otherwise, an error.

### `PROGRAM_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 281
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PROGRAM_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the program field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_PROGRAM, the program field. Otherwise, an error.

### `QUALIFIERS_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 287
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: QUALIFIERS_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the qualifiers field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for these: DSC$K_DTYPE_CALL, the type byte unsigned. DSC$K_DTYPE_CONDITION, the modifier unsigned word. DSC$K_DTYPE_CONGLOM, the qualifiers field. DSC$K_DTYPE_DEPENDENCY, the opcode unsigned word. DSC$K_DTYPE_DISPATCH, the type byte unsigned. DSC$K_DTYPE_FUNCTION, the opcode unsigned word. Otherwise, an error.
|Examples     |QUALIFIER_OF(A+B) is 38 (at this writing).

### `RAW_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 294
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: RAW_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the raw field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_SIGNAL, the raw field. All others DATA(A).
|Examples     |RAW_OF(BUILD_SIGNAL(6*$VALUE,42)) is 42.
|See also     |$VALUE and $THIS for use of this within a signal.

### `ROUTINE_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 305
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: ROUTINE_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the routine field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for these: DSC$K_DTYPE_CALL, the routine field. DSC$K_DTYPE_ROUTINE, the routine field. Otherwise, an error.

### `SLOPE_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 322
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: SLOPE_OF(arg0,arg1) 
|Native python|False|


|Return Type  |MDS Operation |
Get the slope/delta field.
Arguments Optional: N.
`A` descriptor as below.  
    * A is searched for these: DSC$K_DTYPE_RANGE, the delta field or 1. DSC$K_DTYPE_SLOPE, the N-th slope field. Otherwise, an error.
`N` integer scalar, from 0 to number of slope segments less one.
|Result       |
Examples. SLOPE_OF(2:5) is 1. SLOPE_OF(1:10:0.5) is 0.5.

### `TASK_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 343
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: TASK_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the task field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for these: DSC$K_DTYPE_ACTION, the task field. DSC$K_DTYPE_PROCEDURE, unchanged.. DSC$K_DTYPE_PROGRAM, unchanged.. DSC$K_DTYPE_ROUTINE, unchanged.. DSC$K_DTYPE_METHOD, unchanged.. Otherwise, an error.
TEXT

### `TIME_OUT_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 345
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: TIME_OUT_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the time_out field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for these: DSC$K_DTYPE_METHOD, time_out field. DSC$K_DTYPE_PROCEDURE, time_out field. DSC$K_DTYPE_PROGRAM, time_out field. DSC$K_DTYPE_ROUTINE, time_out field. Otherwise, an error.

### `UNITS`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 353
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: UNITS(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the data of the units field or a blank.
|Arguments, Results|Expression that is evaluated.
|Result       |DSC$K_DTYPE_DIMENSION, UNITS(axis field). DSC$K_DTYPE_RANGE, combined UNITS of the fields. DSC$K_DTYPE_SLOPE, combined UNITS of the fields. DSC$K_DTYPE_WINDOW, UNITS(value_at_idx0 field). DSC$K_DTYPE_WITH_UNITS, DATA(units field). else removing SIGNAL, PARAM, and such. Otherwise, a single blank is returned, an empty string cannot be used by IDL. This recursive definition will find the first WITH_UNITS field available.
>>>>>>>>>WARNING, types for which DATA is undefined give an error.
|Examples     |Let _A=BUILD_WITH_UNITS(42,'m'//'/s'), then UNITS(_A) is "m/s".

### `UNITS_OF`

|||
|-|-|
|TDI Syntax   | `UNITS_OF(_OBJECT)` |
|Python Syntax| `MDSplus.UNITS_OF(object)` |
|Opcode|354|

If `_OBJECT` is a [Value With Units](#value-with-units), returns the `_UNITS` field. Otherwise, returns a ' '.

### `VALUE_OF`

|||
|-|-|
|TDI Syntax   | `VALUE_OF(_OBJECT)` |
|Python Syntax| `MDSplus.VALUE_OF(object)` |
|Opcode|359|

Based on the type of `_OBJECT`:
* [Dimension](#dimension) returns the `_WINDOW` field.
* [Parameter](#parameter) returns the `_VALUE` field.
* [Signal](#signal) returns the `_VALUE` field.
* [Window](#window) returns the `_VALUE_AT_IDX0` field.
* [Value With Error](#value-with-error) returns the `_VALUE` field.
* [Value With Units](#value-with-units) returns the `_VALUE` field.
* Otherwise, returns [`DATA(_object)`](#data).

### `VALIDATION`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 385
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: VALIDATION(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Evaluate the validation field of a parameter.
|Arguments, Results|PARAM must be or make a param.
|Result       |Sets $THIS to the parameter and sets $VALUE to the value field of the param and does DATA(validation field).
|Examples     |Let _A=BUILD_PARAM(42,"text of this param",$VALUE<6), then VALIDATION(_A) is $FALSE.

### `VALIDATION_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 358
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: VALIDATION_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the validation field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_PARAM, the validation field.
Otherwise, an error.
>>>>>>>>>WARNING, because the validation field is likely to use $VALUE or $THIS, DATA(VALIDATION_OF(parmeter)) will not work. Use VALIDATION(parameter) for the correct result.
|Examples     |VALIDATION_OF(BUILD_PARAM(42,"the answer",$VALUE>6)) is $VALUE>6, which cannot be evaluated.

### `WHEN_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 364
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: WHEN_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the when field.
|Arguments, Results|Descriptor as below.
|Result       |DISPATCH_OF(A) is searched for this: DSC$K_DTYPE_DISPATCH, the when field. Otherwise, an error.

### `WINDOW_OF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 367
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: WINDOW_OF(arg0)
|Native python|False|


|Return Type  |MDS Operation |
Get the window field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for these: DSC$K_DTYPE_DIMENSION, the window field. DSC$K_DTYPE_WINDOW, unchanged. Otherwise, an error.
WORD

# Deprecations

## Procedure

Use Function instead

## Program

Use Function instead

## Routine

Use Function instead

## Slope

Use Range
