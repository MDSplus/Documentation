
# Language

### `compile` (Opcode 99)

|||
|-|-|
|TDI Syntax   | `compile(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.compile(arg0,arg1,argn,...)` |
|Min arguments| 1|
|Max arguments| 254|

Convert a text string into a functional form of the expression with the possibility of including other descriptors.
* Comments (`/* ... */`) are removed and may be nested.
* Comments cannot be recovered by `decompile`. 

Optional Arguments: 
* `_STRING` character scalar. 
* Other expressions that may be accessed as $a where a runs from 1 to the number of additional arguments.

Examples
```
TDI> compile("add(1, 2)")
1 + 2

TDI> compile ("$+$+$", _a, _b, _c)
_a + _b + _c
```

See also: `decompile`, `rem` to retain a comment, `execute`

### `decompile` (Opcode 119)

|||
|-|-|
|TDI Syntax   | `decompile(arg0,_MAX) ` |
|Python Syntax| `MDSplus.decompile(arg0,_MAX) ` |
|Min arguments| 1 |
|Max arguments| 2 |

Converts the argument expression to text that will compile to the same expression. Any comments are removed before being returned.

Arguments 
* `arg0` any MDS or VMS data description. 
* `_MAX` (optional) Integer scalar for the maximum number of vector elements to display. Default is all.

|Signals      |None. 
|Units        |None. 
|Form         |Character scalar. Length limit is 65535.
|Result       |

Examples
* Simple example

    ```tdi
    TDI> _dc = decompile(_a + _b)
    "_a + _b"
    TDI> _a = 1 
    1
    TDI> _b = 2
    2
    TDI> compile(_dc)
    _a + _b
    TDI> data(compile(_dc))
    3
    ```
* `DECOMPILE('_A+\TOP.XRAY.CHAN01:DATA/*my expression*/')` returns `_A + \TOP.XRAY.CHAN01:DATA.` 
* Some forms are converted to the most common one: `CONCAT(_B,"X")` will be _B // "X". Control characters, double quotes, and backslashes (\) are converted to their backslash form.

see also: `compile`, `data`


### `evaluate`
(Opcode 158)

|||
|-|-|
|TDI Syntax   | `evaluate(arg0)` |
|Python Syntax| `MDSplus.EVALUATE(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

Removes descriptors and node (NID and PATH) pointers and evaluates functions.
Common Usual Form
* Include a backtick (``` ` ```) in an expression or statement to have it be evaluated at  compile-time. Everything else will be a runtime evaluation.  
Note: because of its low precedence, parentheses must be outside the backtick (``` ` ```)  to constrain it unlike the other operators. 

Arguments:
* Any MDS or VMS data description. VMS and most MDS data types are passed. A NID or PATH is found in the current tree and re-evaluated.
* FUNCTION data types are executed and their result returned but not re-evaluated.

Examples:
* `evaluate(2+3)` returns 5
* ```(`2+3)+4``` compiles to `5+4`, which will evaluate to `9` at runtime.




### `execute` (Opcode 159)

|||
|-|-|
|TDI Syntax   | `EXECUTE(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.EXECUTE(arg0,arg1,argn,...)` |
|Min arguments| 1   |
|Max arguments| 254 |
Native python: True

Convert a text string into a functional form of the expression with the possibility of including other descriptors. Comments (/* ... */) are removed and may be nested. Then EVALUATE the expression.

Arguments 
* STRING character scalar. 
> TODO: come back to this and explain it better
* [ARG] (Optional) other expressions that may be accessed as `$k` where `k` runs from 1 to the number of additional arguments. Successive arguments may be accessed by `$` starting from the first. Once `$k` appears, subsequent `$` designates the arguments following it. The $k allows inputs to be used several times but k must be less than the number of arguments actual passed, maximum 253. `$0` is STRING.

Returns:
* The compiled and evaluated value of the string with the current values of the arguments.

Examples
* EXECUTE("2+\TOP.XRAY.CHAN01:DATA") is two more than the data of a channel.
* example use case:
    ```
    TDI> _expr = "2"
    "2"
    TDI> _expr = _expr // "+" //"3"
    "2+3"
    TDI> execute(_expr)
    5
    ```
* example with `$`:
    ```
    TDI> _a = 2
    2
    TDI> _b = 3
    3
    TDI> _c = 4
    4
    TDI> execute("$+$+$", _a, _b, _c)
    9`
    ```

See also: `compile`, `decompile`


### `DATA` (Opcode 112)

|||
|-|-|
|TDI Syntax   | `DATA(arg0) ` |
|Python Syntax| `MDSplus.DATA(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |


Removes signal and parameter descriptors and evaluates ranges and tries to give a VMS data type.
* Argument may be any data type with a data/value field.
* For a dimension, the axis values are returned. 
* For a signal or with_units, the evaluated data field is returned. 
* For a param, the evaluated value field is returned. 
* For a range, the values are returned. 
* For VMS data, no change is made. 
* Immediate at compilation.

|Signals      |None. 
|Units        |None unless X is AS_IS. 
|Form         |VMS scalar or array.
|Result       |

Examples
* `DATA(BUILD_SIGNAL(42.*$VALUE,6))` returns `252.`.
* `DATA(compile("add(1, 2)"))` returns`3`
* Since `compile("add(1, 2)")` returns `1 + 2`, then  
`DATA(compile("add(1, 2)"))` returns `3`

See also: `compile`

### `DATA_WITH_UNITS` (Opcode 404)

|||
|-|-|
|TDI Syntax   | `DATA_WITH_UNITS(arg0)` |
|Python Syntax| `MDSplus.DATA_WITH_UNITS(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

Removes signal and parameter descriptors and evaluates ranges and tries to give a VMS data type bound in a `with_units` descriptor.
* Argument may be any data type with a data/value field.
* Form: `With_units` descriptor with a VMS scalar or array data field. The units pointer may be null or point to a standard units data (today, text).
* For a dimension, the axis values are returned. For a signal or `with_units`, the evaluated data field is returned. For a param, the evaluated value field is returned. For a range, the values are returned. For VMS data, no change is made. The result has a data field and if there are units the units descriptor with the first units found.
* Immediate at compilation.

Examples
* `data_with_units(build_with_units(2 + 3, "hz"))` returns `Build_With_Units(5, "hz")`
* `DATA_WITH_UNITS(BUILD_SIGNAL(42.*$VALUE, BUILD_WITH_UNITS(6,'counts')))` returns `Build_With_Units(252,'counts')`.

See also: `data`, `compile`

## Writing Functions

> TODO: Move to Guide

`.fun` or `.py` file located in the `$MDS_PATH` with a function matching the name of the file.

e.g.
`tdi/helloworld.fun`
```tdi
public fun helloworld() {
    write(*, "Hello, World!");
}
```

### `fun`  (Opcode 171)

|||
|-|-|
|TDI Syntax   | `fun name(arglist){statements}` |
|Python Syntax| `MDSplus.fun name(arglist){statements}` |
|Min arguments| 2   |
|Max arguments| 254 |

Define a function, its argument form, and the action taken or invoke a function.

Usual Definition. 
* `FUN functionname([ARG],...) STMT `
* `FUN private functionname([ARG],...) STMT `
* `FUN public functionname([ARG],...) STMT.`

Usual Invocation.
* `functionname([X],...)`
* `PRIVATE functionname([X],...)`
* `PUBLIC functionname([X],...).`


Arguments
* FUNCTIONNAME an alphanumeric name beginning with an underscore or a dollar sign. The name defined and invoke must match exactly. 
    * NAME may be preceded by PRIVATE or PUBLIC to specify the scope of its definition. Default is PRIVATE. A PRIVATE FUN is seen only by the routine defining it. A PUBLIC FUN is seen by all routines. 
* [ARG] optional: an alphanumeric name beginning with an underscore or a dollar sign that will define the variable referenced in STMT. Each argument may have modifiers IN, INOUT, or OUT to specify the transfer of data between the calling and the called routines. OPTIONAL may precede a modifier or the variable name in an ARG. ARG marked as IN should not be modified in STMT and never changes the actual input. The default mode is IN. STMT a statement form.
* WARNING, use care in tree pathnames used in PUBLIC FUN, they will be relative to invocation, not to the definition. PRIVATE FUN invocations are, of necessity, at that node. 
* [X] optional: the actual instance of the arguments in the calling routine. If the corresponding ARG is marked as INOUT or OUT this must be a variable. If the corresponding ARG is not marked OPTIONAL, then that X must be present and not null.
* Side Effect: NAME is allocated, any prior value is freed.

Result
* The argument expression of a RETURN statement or none.

Additional information available:
* `in VARIABLENAME` *This is  the default*
    * Defines argument that is evaluated but not rewritten. (Pass by value)
* `inout VARIABLENAME`
    * Defines argument that is evaluated and rewritten when the FUN finishes. (Pass by reference)
* `optional VARIABLENAME`
    * Defines argument that may be omitted in actual call.
    * Arguments: must be a variable name, or IN, INOUT, or OUT before a variable name.
* `out VARIABLENAME`
    * Defines argument that is not evaluated, begins as undefined in the FUN and is written when the FUN finishes.


Examples
1. To create a function:
    `FUN _SINCOSD(IN _ANGLE, OUT _SIN, OPTIONAL OUT _COS) { _SIN = SIND(_ANGLE); IF (PRESENT(_COS)) _COS = COSD(_ANGLE); }`

    Then `_ SINCOSD(30,_Y,_X)`  
    sets:
    `_Y` to `0.5` and  
    `_X` to `0.8660254` *if present*. 
    
    This has no functional result. You can specify a `return()` if desired.


2. Example with return

    ```
    TDI> _a = 33
    TDI> fun and_one(_num) {return (++_num);}
    Fun and_one (_num) {
        Return (++_num);
    }
    TDI> and_one(_a)
    34

    TDI> _a
    33
    ```

3. inout
    ```
    TDI> _a = 33
    TDI> fun and_one(inout _num) {++_num;}
    Fun and_one (INOUT _num) {
        ++_num;
    }

    TDI> _a
    34
    ```


4. Example that's a bit more light-hearted
    ```
    TDI> fun _in_and_out(in _order, out _delivery, optional out _sides) { _delivery = _order; if(present(_sides)) _sides = "animal fries";}
    Fun _in_and_out (IN _order, OUT _delivery, OPTIONAL OUT _sides) {
        _delivery = _order;
        If (PRESENT(_sides)) {
            _sides = "animal fries";
        }
    }
    TDI> _in_and_out("Burger", _myOrder, _mySides) 
    "animal fries"
    TDI> _myOrder
    "Burger"
    TDI> _mySides
    "animal fries"
    ```

### `RETURN`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 302
|Min arguments| 0
|Max arguments| 1
******Compiler syntax: RETURN(arg0) 
|Native python|False|


CC Modified Statement.
Return from a FUN with value.
Required Usual Form. RETURN (X);. Function Form RETURN(X). May be syntatically invalid.
|Arguments, Results|Optional: X. X any. Unlike CC, the parentheses are required. >>>>>>Note that a null is RETURN(*) or RETURN().
|Result       |X.
|Examples     |FUN(_A,_B) {RETURN(A*B);}

### `in` (Opcode 192)

Used in `fun` definition to denote argument is readonly.
Please see `fun` for more information.


### `OUT`
|||
|-|-|
|TDI Syntax   | `OUT _arg` |
|Opcode|269|

Used in FUN definitions to indicate argument is an output argument

### `INOUT` (Opcode 199)

Used in `FUN` definitions to indicate that argument is used for input and output.

Please see `FUN` for more information

Example:
`PUBLIC FUN _MYFUN(INOUT _ARG)`


### `OPTIONAL`
|||
|-|-|
|TDI Syntax   | `OPTIONAL _arg` |
|Opcode|266|

Used in FUN definitions to indicate argument is optional


### `PRESENT` (Optional Argument Present)

|||
|-|-|
|TDI Syntax   | `PRESENT(_ARGUMENT)` |
|Opcode|275|

```tdi
public fun say_hello(optional in _name, optional in _excited)
{
    if (present(_name)) {
        _name = "world";
    }

    _message = "Hello, " // _name;

    if (present(arg2)) {
        write(*, _message);
    }
    else {
        write(*, _message, "!");
    }
}
```


F90 Variable Inquiry.
Determine if an optional argument present.
|Arguments, Results|A must be an optional argument of the FUN in which the PRESENT function reference appears.
|Signals      |None. |Units        |None. |Form         |Logical scalar.
|Result       |$TRUE if A present or $FALSE otherwise. |Examples     |FUN _test(_A) {return PRESENT(_A);} when called _test() is $FALSE and _test(3) is $TRUE.

### `PUBLIC`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 284
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PUBLIC(arg0) 
|Native python|False|

global


Variable Operation.
Specifies the use of a public variable.
Usual Form PUBLIC NAME.
|Arguments, Results|NAME mus be a variable name.
|Signals      |Same as NAME. |Units        |Same as NAME. |Form         |A copy of the contents of the variable.
|Result       |That of the contents of the variable.
|Examples     |PUBLIC _A = 42 sets the public variable _A to 42.


### `PRIVATE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 278
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PRIVATE(arg0) 
|Native python|False|


Variable Operation.
Specifies the use of a private variable.
Usual Form PRIVATE NAME.
|Arguments, Results|NAME must be a variable name.
|Signals      |None. |Units        |None. |Form         |A copy of the contents of the variable.
|Result       |That of the contents of the variable.
|Examples     |PRIVATE _A = 42 sets the private variable _A to 42.


### `RESET_PRIVATE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 376
|Min arguments| 0
|Max arguments| 0
******Compiler syntax: RESET_PRIVATE() 
|Native python|False|


Variables.
Frees all private variables of all levels and their memory.
Arguments None.
|Result       |None.
Side Effect. All private variables are freed and forgotton.
|Examples     |RESET_PRIVATE().

### `RESET_PUBLIC`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 377
|Min arguments| 0
|Max arguments| 0
******Compiler syntax: RESET_PUBLIC() 
|Native python|False|


Variables.
Frees all public variables and their memory.
Arguments None.
|Result       |None.
Side Effect. All public variables are freed and forgotton.
|Examples     |RESET_PUBLIC().

### `VAL`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 357
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: VAL(arg0) 
|Native python|False|


CALL mode.
Pass the data of the argument by value.
|Arguments, Results|X is any type, scalar or array that DATA can evaluate.
Use..... Integer scalar like a CC call or Fortran %VAL(123). The value of the DATA of the argument used like an address.

### `REF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 298
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: REF(arg0) 
|Native python|False|


CALL mode. Pass the data of the argument by reference. |Arguments, Results|X is any type, scalar or array that DATA can evaluate. Use..... Starting address of VMS data, like Fortran %REF('123'). The address of the DATA of the |Arguments, Results|For X alone, non-data forms may be passed. May programs cannot handle these forms. The REF form is expected by most Fortran routines but the DESCR form is used for characters.

### `XD`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 400
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: XD(arg0)
|Native python|False|


CALL mode.
Pass the data of the argument by extended descriptor. This is the only form that can pass signals and other class-R described data.
|Arguments, Results|X is any VMS or MDS type that can be EVALUATED.
Use..... Only routines written with MDS calls can use these descriptors.

### `VAR`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 360
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: VAR(arg0,arg1)
|Native python|False|


Variables.
Specifies a private or public variable by textual name.
|Arguments, Results|Optional: REPLACE. STRING the character scalar name of a variable.
>>>>>>>>>WARNING, all names that do not begin with an underscore (_) or dollar sign ($) cannot be accessed other than by VAR. $-names are reserved for system names.
REPLACE the new value of STRING.
|Result       |That of the old contents of the variable.
|Examples     |_A=42,VAR("_A") is 42.

### `REM`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 441
|Min arguments| 1
|Max arguments| 254
******Compiler syntax: REM(arg0,arg1,argn,...)
|Native python|False|
Store a comment in an expression. No action is taken on the arguments. REM(" ...") is a null operation that can retain a comment; it must be where a null expression is valid.
Arguments Optional: COMMENT. COMMENT,... any type.
|Result       |None.
|Examples     |REM("addition example"),2+3 is 5.

`rem("this is a note for future reference"), 1+2` returns `3`


### `EXT_FUNCTION` (Opcode 162)

|||
|-|-|
|TDI Syntax   | `image->routine(args) or tdi-fun-name(args)` |
|Python Syntax| `MDSplus.image->routine(args) or tdi-fun-name(args)` |
|Min arguments| 2 |
|Max arguments| 254 |

> TODO: Come back to this...more investigation required

Do a FUN, do a routine in an image, or do a command file.
Usual Form xxx->yyy(arg...) or _zzz(arg...)

Methods.
(1) no IMAGE and ROUTINE is a defined function.
(2) IMAGE and ROUTINE define an .EXE image with symbol table and an entry point routine.
(3) IMAGE with .FUN extension default and IMAGE filename define a file of TDISHR commands.

(1) Arguments (Optional: ARG,... )
* `IMAGE` *, a missing |Arguments, Results
* `ROUTINE` Character scalar FUN name previously defined. 
* `[ARG]` Optional:As needed by the routine.
Result: As defined by the function.

(2) Arguments (Optional: IMAGE, ARG,... )
* `[IMAGE]` Optional: Character scalar filename or *, default MDS$FUNCTIONS. 
* `ROUTINE` Character scalar entry point name. 
* `[ARG]` Optional: As needed by the routine. The forms DESCR, REF, and VAL force passing by descriptor, reference, or long value. These force the DATA of the argument to be evaluated. The default is to pass by whatever descriptor is generated.
Result: Function is called like a TDISHR one, i.e., augmented bythe output descriptor function.

(3) Arguments   (Optional: IMAGE, ARG,... )
* `[IMAGE]` Optional: Character scalar directory name or *, default MDS$PATH.  
Warning:, usually MDS$PATH should point the local directory first. ROUTINE Character scalar filename.
* `[ARG]` Optional: Allowed only for a defining FUN. As needed by the routine.  
Warning, You must pick a non-conflicting name. The easiest way is to begin both FUN and filename with an underscore (_).

|Result       |The entire file is read (limit 16k bytes) and it is executed. If the compilation was a FUN and IMAGE is missing, the FUN is invoked with arguments. NOTE, The second time around this will use method (1). The result is the last expression evaluated or the returned value of the function.

Examples
If MDS$PATH is [] and file _FTEST.FUN has:
```
    FUN PUBLIC _FTEST(OPTIONAL IN _X) {
        IF (PRESENT(_X)) WRITE(*,'_x =',_X);
        ELSE WRITE(*,'no argument');
    }
```
_FTEST(123) returns 17 and prints on the terminal: _x= 123
If file _OUTER.FUN has: FUN PUBLIC _OUTER(IN _A, IN _B) { RETURN (SPREAD(_A, 0, SIZE(_B)) * SPREAD(_B, 1, SIZE(_A))); }
_OUTER([1,2,3],[4,5]) is the outer product: [[4,5], [8,10], [12,15]].



### `debug` (Opcode 117)

|||
|-|-|
|TDI Syntax   | `debug(_OPTION)` |
|Python Syntax| `MDSplus.DEBUG(_OPTION)` |
|Min arguments| 0 |
|Max arguments| 1 |


Controls debugging output. Returns previous value of debugging messages. An empty string is returned if no error was detected.
* Arguments: OPTION is an integer scalar and is the bitwise combination of these codes:
    * OPTION = 1 (`0001`), "prepends" the first error message text.
    * OPTION = 2 (`0010`), prints the error message.
    * OPTION = 4 (`0100`), clears the error message and status.

Examples
* `debug(7)` appends the first detected error's text, prints the message, and frees the message string. 
* `debug(5)` can fetch and clear the error string.

TODO: come back to this and verify it's working



### `$MISSING` (Missing Value/Argument, Null)

|||
|-|-|
|TDI Syntax   | `$MISSING` |
|Python Syntax| `MDSplus.dMISSING()` |
|Java mdsplus-api Syntax| `CONST.dMissing()`|
|Opcode|17|

Indicates a missing value (or argument), equivalent to null in other languages.

> TODO: More examples?
```tdi
TDI>
$Missing
```

See also:
* [`$ROPRAND`](#roprand-nan-infinity-reserved-operand)


### `$NARG` (Number of Arguments)

|||
|-|-|
|TDI Syntax   | `$NARG` |
|Python Syntax| `MDSplus.dNARG()` |
|Java mdsplus-api Syntax| `CONST.dNarg()`|
|Opcode|373|

The number of arguments used to invoke the current function.

```tdi
TDI> fun count_args(optional in _a, optional in _b, optional in _c) { return($NARG); }
Fun count_args (OPTIONAL IN _a, OPTIONAL IN _b, OPTIONAL IN _c) {
        Return ($NARG);
}

TDI> count_args(1)
1
TDI> count_args(1, 2)
2
TDI> count_args(1, 2, 3)
3
```

See also:
* `FUN`

### `ABORT` (Abort Execution)

|||
|-|-|
|TDI Syntax   | `ABORT()` |
|Python Syntax| `MDSplus.ABORT()` |
|Opcode       | 31 (0x1f)|

Aborts an expression by causing an error (`TdiABORT`).

```tdi
# If _a is undefined or evaluating it causes an error
TDI> if_error(_a, abort())
%TDI Error in EVALUATE(_a)
%TDI Error in ABORT()
%TDI Error in EVALUATE(ABORT())
%TDI Error in IF_ERROR(_a, ABORT())
%TDI Error in EXECUTE("if_error(_a, abort())")
```

See also:
* `IF_ERROR()`

### `if_error` (Handle Error, Try/Catch)

|||
|-|-|
|TDI Syntax   | `IF_ERROR(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.IF_ERROR(arg0,arg1,argn,...)` |
|Opcode|190|

Evaluate arguments until no error.
* Arguments can be any expression.
* Returns That of the first expression without an error. If all have errors, the result is the final error.

Examples
* `IF_ERROR(_A EQ _B, _A, _B)` gives the expression if `_A` and `_B` are defined or the one defined; else an error.

* with `_a = 100`
    * `if_error(_a > _b, _a, _b)` returns `100`
    * `if_error(_a > _b, _b, _a)` returns `100`

* with `_D = 3`
    * `if_error(_A, _B, _C, _D)` returns `3`


### `ARG_OF` 
|||
|-|-|
|TDI Syntax   | `ARG_OF(_DESCRIPTOR, [_INDEX])` |
|Python Syntax| `MDSplus.ARG_OF(_DESCRIPTOR, [_INDEX])` |
|Opcode|51|

Returns the n-th argument of an expression.
* If no `_INDEX` value is given, defaults to the first (position 0)

TODO: REWRITE WITH STEPHEN
MDS Operation
Get the N-th argument of a record descriptor.
The count does not include dscptrs like image or routine.

A descriptor of class DSC$K_CLASS_R with arguments.
N integer scalar from 0 to the number of descriptors -1.

Examples

```tdi
_sum = make_function(builtin_opcode("add"),3, 4)

TDI> arg_of(_sum)
3

TDI> arg_of(_sum, 1)
4
```

See also
* `DSCPTRS_OF` for any descriptor.

### `AS_IS` 
|||
|-|-|
|TDI Syntax   | `AS_IS(_ARG0)` |
|Python Syntax| `MDSplus.as_is(_ARG0)` |
|Opcode|55|

Protects the argument from one level of evaluation.
* `_ARG0` argument may be any expression and may be a NID, PATH, or FUNCTION.
* returns the argument without evaluation.


Examples

```TDI
# This makes the variable _A into an expression. So whereever `_A` is used, the current value of _B will be multiplied by three and that will be used.

TDI> _A = AS_IS(_B * 3.0)

# Note: The above expression would have returned the then-current value and will not automatically change as _B does.

TDI> _a = as_is(_b * 10)
TDI> _b = 2

TDI> _a
_b * 10

TDI> data(_a)
20

TDI> _b = 3

TDI> data(_a)
30
```

See also: `arg_of`, `data`, 


### `ALLOCATED`
|||
|-|-|
|TDI Syntax   | `ALLOCATED(_STRING)` |
|Python Syntax| `MDSplus.ALLOCATED(_STRING)` |
|Opcode|44|

Returns [`$TRUE`](#true-true-constant) if a variable has been declared and is populated, else, returns [`$FALSE`](#false-false-constant).
* Argument expected is variable name or  text string.
* ALLOCATED(_Not_in use) is $FALSE unless it has appeared on the left side of an assignment expression.

Example:
```
_a = 1

TDI> allocated(_a)
1BU

TDI> allocated("_a")
1BU

TDI> allocated(_b)
0BU

TDI> allocated("_b")
0BU
```

See also
* `deallocate` to remove names
* `reset_private` or `reset_public` for more drastic actions.


### `deallocate` (Opcode 116)

|||
|-|-|
|TDI Syntax   | `deallocate(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.deallocate(arg0,arg1,argn,...)` |
|Min arguments| 0   |
|Max arguments| 254 |

Release variables by wildcarded name or release all private variables.

Arguments 
* (Optional:) STRING.... STRING,... character scalars. 
* If STRING is absent, all private variables are released.
* Wildcards `%` and `*` are allowed.  

Examples     
* simple example:
    ```tdi
    TDI> _a = 1234
    1234
    TDI> _b = 4321
    4321
    TDI> deallocate(_a, _b)
    2

    TDI> _b
    %TDI Error in EXECUTE("_b")

    TDI> _a
    %TDI Error in EXECUTE("_a")

    ```
* `DEALLOCATE("_A*")` removes all starting with `_A`.


### `EQUALS` (Variable Assignment)

|||
|-|-|
|TDI Syntax   | `_NAME = _VALUE ` |
|Opcode|152|


To check if two things are equal, use [`EQ()`](#eq-equal-to).


Stores a value in a name variable.
Usual Form: `_NAME = X` 
Function Form `_EQUALS(_NAME,X)`

Arguments NAME variable name optionally preceded by PRIVATE or PUBLIC.
* Begin name with underscore (`_`) for user variables.
* Dollar sign (`$`) is used for system variables.
* A text string but not an expression is acceptable.
* Value may be  an expression of any type.

Examples
`_A=[1,2,3]`


### `equals_first` (Opcode 153)

|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: _x (operator)= value 
|Native python|False|

> TODO: COME BACK TO THIS

Variable Elemental.
Store in a name variable using variable in binary operation. This saves writing the variable name twice.
Usual Forms NAME^=Y, NAME*=Y, NAME/ =Y, NAME MOD=Y, NAME+=Y, NAME-=Y, NAME<<=Y, NAME>>=Y, NAME//=Y, NAME IS_IN=Y, NAME>==Y, NAME GE=Y, NAME> =Y, NAME GT=Y, NAME<==Y, NAME LE=Y, NAME< =Y, NAME LT=Y, NAME===Y, NAME EQ=Y, NAME!==Y, NAME/==Y, NAME<>=Y, NAME NE=Y, NAME&=Y, NAME|=Y, NAME EQV=Y, NAME NEQV=Y, NAME&&=Y, NAME AND=Y, NAME AND_NOT=Y, NAME NAND=Y, NAME NAND_NOT=Y, NAME||=Y, NAME OR=Y, NAME OR_NOT=Y, NAME NOR=Y, NAME NOR NOT=Y
NAME@=Y.
_
,
Arguments
X i ithabi y(t t)op t .Th
an express on w nar wo-argumen era or e first argument must be a variable name, like in NAME+6. Only those listed above are acceptable to the compiler.
>>>>>>>>>WARNING, special punctuation is required for /, >, and < because they may be confused with single operators /=, >=, and <=.
|Result       |Same as X.
Side Effect. NAME now has value X or X operated on by Y.
|Examples     |For _A=[1,2,3], _A+=4 is [5,6,7].


### `for` (Opcode 169)

|||
|-|-|
|TDI Syntax   | `for([_INIT],[_TEST],[_UPDATE]){_STATEMENT...}` |
|Python Syntax| `MDSplus.for([_INIT],[_TEST],[_UPDATE]) {_STATEMENT...}` |
|Min arguments| 4   |
|Max arguments| 254 |

Initialize, test, and update a loop.

Argument 
* `[_INIT]` Optional: any expression. 
* `[_TEST]` Optional: logical scalar. 
* `[_UPDATE]` Optional: any expression. 
* `_STATEMENT` can be simple or compound (like {S1 S2}).  
Note: multiple statements `(like S1 S2)` in call form are considered to be in braces.

Examples
* `FOR (_J=DSIZE(_X); --_J>=0; ) IF(_X[_J]) BREAK;`

```
for(_I=0; _I < 3; ++_I) {write(*,_i);};
        0
        1
        2
```


### `do` (Opcode 131)

|||
|-|-|
|TDI Syntax   | `do(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.do(arg0,arg1,argn,...)` |
|Min arguments| 2   |
|Max arguments| 254 |

Do-While loop; repeats until expression is false.
* Usual Form: `DO {STMT} WHILE (X);`
* Function Form: `DO(TEST,STMT...)` May be syntatically invalid.

Arguments
* STMT statement list. The curly braces are required!
* TEST logical scalar.
* Note that TEST is first argument of call form.
* Warning: multiple statements in call form are considered to be in braces.

Examples

```
do { write(*, _a++); } while(_a < 5)
          0
          1
          2
          3
          4
12 /* the return from write */
```

TODO: Decide whether to keep the example below (it's based on the original example, which isn't great, and features a weird hack in the `while` portion)
```
TDI> _x = [3, 4, 1, 2]
[3,4,1,2]
TDI> _j = 0
0
TDI> do { _j = _x[_j]; write(*, _j); } while (_j >= 0 && _j < 4)
          3
          2
          1
          4
12 /* the return from write */
```


### `WHILE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 366
|Min arguments| 2
|Max arguments| 254
******Compiler syntax: WHILE(arg0,arg1,argn,...)
|Native python|False|


CC Statement.
Repeat while expression is true.
Require Usual Form. WHILE (TEST) STMT. Function Form WHILE(TEST,STMT,...). May be syntatically invalid.
Arguments TEST logical scalar. STMT statement, simple or {compound}.
>>>>>>WARNING, multiple statements in call form are considered to be in braces. |Result       |None.
|Examples     |WHILE (RANDOM()<0.99) ++_J;

### `BREAK` 
|||
|-|-|
|TDI Syntax   | `BREAK` |
|Python Syntax| `MDSplus.BREAK()` |
|Opcode 66|

Breaks from a `for` or `while` loop or `switch` statement.
* To be included in a `fun` script.


Examples
```tdi
TDI> for(_j=0; _j < 5; _j+=1) IF (_j == 3) break; IF (_j>=5) abort();
TDI> _j
3
```

### `CONTINUE` 

|||
|-|-|
|TDI Syntax   | `continue` or  `continue()`|
|Python Syntax| `MDSplus.continue` |
|Opcode|104|

Take next iteration of FOR or WHILE loop.
* Usual Form CONTINUE;. 
* Function Form CONTINUE(). May be syntatically invalid.

Arguments None.  
Results. None.

Examples     
```
FOR (_J=SIZE(_X); --_J>=0; ) {     IF (_X[_J]) CONTINUE; ... } 
#where lots of code is skipped for those true.
```

```
for( _i = 0; _i <= 5; ++_i)
{
    if (_i % 2 == 0)
    {
        continue;
    }
    write(*, _i);
}

/* output would look like this */
          1
          3
          5
/* Function will output _i again due to the incrementing action in the for loop. The variable no longer meets the condition to run the action in the for loop so the last action that is run is "++_i" */
6
```

### `SWITCH`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 338
|Min arguments| 2
|Max arguments| 254
******Compiler syntax: SWITCH(arg0,arg1,argn,...)
|Native python|False|


CC Statement.
Select from cases presented in the statement.
Required Usual Form. SWITCH (X) STMT. Function Form SWITCH(X,STMT,...). May be syntatically invalid.
Arguments X any scalar that can be compared. STMT statement, simple or {compound}.
>>>>>>WARNING, multiple statements in call form are considered to be in braces.
|Result       |None.
|Examples     |SWITCH (_k) { CASE (1) _j=_THING1; BREAK; CASE (4.5:5.5) _j=_OTHER_THING; BREAK; CASE DEFAULT ABORT(); }.

### `CASE`
|||
|-|-|
|TDI Syntax   | `CASE(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.CASE(arg0,arg1,argn,...)` |
|Min arguments| 2|
|Max arguments| 254|
|Opcode|92|

TODO: come back to this and test with a file.

CC-F90 Modified Statement.
Do statement if SWITCH test matches value. Required Usual Form CASE (X) STMT. 
Note F90 uses SELECT CASE (X) ... END CASE. Function Form CASE(X,STMT,...). May be syntatically invalid.

Arguments
X any comparison scalar or scalar range. The range must not be stepped but may be open ended. For example, 4, 4:, :6, and 4:6 are acceptable.
STMT statement simple or {compound} or multiple.
|Result       |None.
|Examples     |
SWITCH (_k) { 
    CASE (1) _j=_THING1; BREAK; 
    CASE (4.5:5.5) _j=_OTHER_THING; BREAK; 
    CASE DEFAULT ABORT(); 
    }

```
SWITCH (_k) { 
    CASE (1) _j=_THING1; BREAK;
    CASE (4.5:5.5) _j=_OTHER_THING; BREAK;
    CASE DEFAULT _j=-1; BREAK; 
}
```

See also `default`, `switch`

### `DEFAULT` (Opcode 121)

|||
|-|-|
|TDI Syntax   | `DEFAULT` |
|Python Syntax| `MDSplus.DEFAULT` |
|Min arguments| 1   |
|Max arguments| 254 |

CC Statement.
* Required Usual Form: `CASE DEFAULT STMT.` 
* Function Form `DEFAULT(STMT,...)`. May be syntatically invalid. 

Arguments, Results
* STMT must be a statement, simple or compound
(like {S1 S2}) or multiple (like S1 S2). 
WARNING, only one CASE DEFAULT should appear in a SWITCH.

Examples
```
_k = 13
_thing1 = 5
_other_thing = 9

switch (_k) { 
    case (1) _j=_thing1; BREAK;
    case (4.5:5.5) _j=_other_thing; BREAK;
    case default _j=-1; BREAK; 
}

/* RESULTS IN: _j = -1 */
```

See also `case`, `switch`

### `LABEL`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 212
|Min arguments| 2
|Max arguments| 254
******Compiler syntax: LABEL _gub : 
|Native python|False|


Modified CC Statement.
Label holder for statements.
Required Usual Form. LABEL NAME : STMT. Functiom Form LABEL(NAME,STMT,...). May be syntatically invalid.
Arguments NAME character scalar. Should begin with underscore (_). STMT statement, simple or compound (like {S1 S2} or
multiple (like S1 S2).
|Result       |STMT ignored except in a GOTO that does not match the LABEL.
|Examples     |IF (_A > 0) GOTO _XX ... LABEL _XX : ...

> TODO: This may be broken, See `GOTO`


### `GOTO`(Opcode 176)

|||
|-|-|
|TDI Syntax   | `GOTO(arg0)` |
|Python Syntax| `MDSplus.GOTO(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

> TODO: come back to this and investigate further; possibly broken?

CC Statement.
Branch to label.
Usual Form: GOTO NAME;
Function Form GOTO(NAME).

Decompiles to usual form.

Arguments: NAME must be character with name of a label in the local code.

Examples     
`IF (_X[2]) GOTO _MYLABEL; ... LABEL _MYLABEL : ... .`

```
TDI> fun example_goto(_skip_number) { if(_skip_number = 2) goto(_here); write(*, "this did not skip"); return(0); label _here: write(*, "this did skip"); return(1);}
Fun example_goto (_skip_number) {
	If (_skip_number = 2) {
		GoTo _here;
	}
	WRITE(*, "this did not skip");
	Return (0);
	Label _here : WRITE(*, "this did skip");
	Return (1);
}
```

### `IF` (Opcode 189)

|||
|-|-|
|TDI Syntax   | `if (condition) {statements} [else {statements}] ` |
|Python Syntax| `MDSplus.if` |
|Min arguments| 2 |
|Max arguments| 3 |

Do statement if expression true, else possibly do another.

* Required Usual Forms: `IF (TEST) STMT, IF (TEST) STMT ELSE ELSESTMT`
* Function Form `IF(TEST,STMT,[ELSESTMT])`. May be syntatically invalid.
Arguments Optional: ELSESTMT. TEST logical scalar. STMT statement, simple or {brace enclosed}. ELSESTMT statement, simple or {brace enclosed}.

Examples
* `IF (_A) _B=2; ELSE _B=3;`


### `else` (Opcode 144)

|||
|-|-|
|TDI Syntax   | `else` |
|Python Syntax| `MDSplus.else` |
|Min arguments| 0 |
|Max arguments| 0 |


Runs only when an `if` statment's conditions are not met.

Example:
```
> _a = $false
> if(_a) write(*, "foo"); else write(*, "bar");
bar
```

### `descr` (Opcode 123)

|||
|-|-|
|TDI Syntax   | `DESCR(arg0)` |
|Python Syntax| `MDSplus.DESCR(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

TODO: COME BACK TO THIS

CALL mode.

Pass the data of the argument by descriptor.

Argument: `x` Any type, scalar or array that `DATA` can evaluate.

Use: Descriptor of VMS data, like Fortran %DESCR(1.23). The descriptor of the DATA of the argument.
For X alone, non-data forms may be passed. Many programs cannot handle these forms.

### `STATEMENT`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 331
|Min arguments| 0
|Max arguments| 254
******Compiler syntax: STATEMENT(arg0,arg1,argn,...)
|Native python|False|


CC Statement.
Hold multiple statements as if one.
Required Usual Form. {STMT ...}. Function Form STATEMENT(STMT,...) May be syntatically invalid.
Arguments STMT,... must be statements. Simple statements end with a semicolon (;), compound statements are in braces ({}).
|Result       |None.
|Examples     |IF (_X[2]) { _B= 2; _C= 3;
}.


### `COMMA`
|||
|-|-|
|TDI Syntax   | `comma(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.comma(arg0,arg1,argn,...)` |
|Min arguments| 2|
|Max arguments| 254|
|Opcode|98|

Evaluates each argument, returns results only from the last argument.
* Arguments may be expressions.
* Note that used as an argument of a function, it must be parenthesized.

```tdi
TDI> comma(_a=3, _b=4, _a + _b)`
7 
# the variables `_a` and `_b` will also be set
```

## Querying (TODO: Rename)

### `BIT_SIZE` (Bit Size, Number of Bits)

|||
|-|-|
|TDI Syntax   | `BIT_SIZE(_ARG)` |
|Python Syntax| `MDSplus.BIT_SIZE(_ARG)` |
|Opcode|411|

Returns the length of integer or other type in bits.
* input can be any type, scalar or array.
* for arrays, returns the size of an individual element, not the whole array

Examples

```tdi
TDI> bit_size(1)
32
```

### `digits` (Opcode 125)

|||
|-|-|
|TDI Syntax   | `digits(arg0)`         |
|Python Syntax| `MDSplus.digits(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

The number of significant digits in the model representing the same type as the argument. Returns the number of non-sign bits in an integer or the number of fraction bits in a real or complex number.

Examples
* `DIGITS(1.0)` is 24 on the VAX.


### `CLASS` 

|||
|-|-|
|TDI Syntax   | `class(arg0)` |
|Python Syntax| `MDSplus.class(arg0)` |
|Opcode|95|


Class of data storage descriptor.
* Argument may be any descriptor.
* Returns byte unsigned of the descriptor class.
* Descriptor data types `(DSC$K_DTYPE_DSC)` are removed.
* Use `CLASS` for data class without NID, PATH, or variable. 
* Use `CLASS_OF` for data class including them.
TODO: STEPHEN TO INVESTIGATE

Examples
```tdi
# TODO: Confirm these outputs
# CLASS_S
TDI> CLASS(3)
1BU

# CLASS_A
TDI> CLASS([])
4BU

#The following will return the class of the value in variable `_A`
TDI> CLASS(_A)

```

### `CLASS_OF` 
|||
|-|-|
|TDI Syntax   | `CLASS_OF(arg0)` |
|Python Syntax| `MDSplus.CLASS_OF(arg0)` |
|Opcode|435|

Class of data storage descriptor.
* Argument may be any descriptor.
* Returns Byte unsigned of the descriptor class. 
* Descriptor data types `(DSC$K_DTYPE_DSC)` are removed.
* Use `CLASS` for data class without NID, PATH, or variable. 
* Use `CLASS_OF` for data class including them.

Examples
```tdi
# TODO: Confirm these outputs

TDI> CLASS_OF(3)
1BU (DSC$K_CLASS_S)

TDI> CLASS_OF([])
4BU (DSC$K_CLASS_A)

TDI> CLASS(_A)
1BU (DSC$K_CLASS_S)
```

### `KIND` (Opcode 137)

|||
|-|-|
|TDI Syntax   | `kind(_A)` |
|Python Syntax| `MDSplus.kind(_A)` |
|Min arguments| 1 |
|Max arguments| 1 |
|Native python|False|

MDS/VMS Inquiry.
Data type of data storage descriptor.
Argument `_A` may be any descriptor.

Result:
* Byte unsigned of the descriptor data type.
* Descriptor data types (DTYPE) are removed.
* Use KIND for data type without NID, PATH, or variable.
* Use KIND_OF for data type including them.

Examples
* `KIND(3)` is `8BU` (`DTYPE_L`).
* `KIND(1.2)` is `52BU` (`DTYPE_F`).
* `KIND(_X)` is the kind of the value in variable `_X`, `kind(_X = 3)` = `8BU`.

Note: 
* `KIND` runs at runtime.
* `KIND_OF` runs at compile time.

See also: `kind_of`

### `KIND_OF` (Opcode 437)

|||
|-|-|
|TDI Syntax   | `KIND_OF(_A)` |
|Python Syntax| `MDSplus.KIND_OF(_A)` |
|Min arguments| 1 |
|Max arguments| 1 |
|Native python|False|

MDS/VMS Inquiry.
Data type of data storage descriptor.

Argument `_A` may be any descriptor.

Result:
* Byte unsigned of the descriptor data type.
* Descriptor data types (`DTYPE_DSC`) are removed. 
* Use KIND for data type without `NID`, `PATH`, or `variable`. 
* Use KIND_OF for data type including them.

Note: 
* `KIND` runs at runtime.
* `KIND_OF` runs at compile time.

Examples
* KIND_OF(3) is 8 (DTYPE_L).
* KIND_OF(1.2) is 10 (DTYPE_F). 
* KIND_OF(_X) is 191 (DTYPE_IDENT).

### `CVT` (Opcode 111)

|||
|-|-|
|TDI Syntax   | `CVT(arg0,arg1)` |
|Python Syntax| `MDSplus.CVT(arg0,arg1)` |
|Min arguments| 2 |
|Max arguments| 2 |

Converts data type by example.
* The converted value of the corresponding element of A.
* Types permitted are byte, word, long, quadword, and octaword unsigned and signed; F, D, G, and H floating real and complex; text. (No text to numbers, today.)
* Warning: truncation does not cause an error.
* Immediate at compilation.
* Arguments
    * Arg0: any type that can be converted to MOLD type. 
    * Arg1: MOLD any type that A can be converted from.

Examples
* `CVT(123,"1234")` returns `" 123"`, four character of long. Note, the default string would have been 12 characters.
* `cvt(1234, "123")` returns `"234"`, note the string is truncated by dropping the first characters.
* `cvt($pi, 1)` returns `3`
* `cvt($pi, 1.0)` returns `3.14159`
* `cvt($pi, 1d0)` returns `3.141592653589793D0`


### `builtin_opcode`
|||
|-|-|
|TDI Syntax   | `BUILTIN_OPCODE(_BUILTINNAME)` |
|Python Syntax| `MDSplus.BUILTIN_OPCODE(_BUILTINNAME)` |
|Min arguments| 1|
|Max arguments| 1|
|Opcode|89|


Takes a string that is the name of any builtin with an opcode and returns that opcode. 

Examples

```tdi
TDI> BUILTIN_OPCODE('$')
0W

TDI> builtin_opcode('$PI')
22W

TDI> builtin_opcode('add')
38W

TDI> builtin_opcode('subtract')
336W

TDI> builtin_opcode('multiply')
247W

TDI> builtin_opcode('builtin_opcode')
89W
```

### `STRING_OPCODE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 334
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: STRING_OPCODE(arg0) 
|Native python|False|


MDS Character Elemental.
Convert string to an opcode value.
|Arguments, Results|STRING must be character.
|Signals      |Same as STRING. |Units        |None, bad if STRING has units. |Form         |Unsigned word.
|Result       |The number associated with the opcode name. Opcode names are like "OPC$STRING_OPCODE".
|Examples     |STRING_OPCODE('$') is 0.

### `OPCODE_BUILTIN`
|||
|-|-|
|TDI Syntax   | `OPCODE_BUILTIN(_NUM) ` |
|Python Syntax| `MDSplus.OPCODE_BUILTIN(_NUM) ` |
|Opcode|263|

Returns the string name (in uppercase) of a builtin's opcode.
* Argument must be an unsigned word [scalar](#scalar) of an existing opcode.
* For the reverse, see [`builtin_opcode`](#builtin_opcode)

TODO: how is this different from `opcode_string`?


```tdi
TDI> opcode_builtin(0)
"$"
TDI> opcode_builtin(263)
"OPCODE_BUILTIN"

TDI> opcode_builtin(1000)
%TDI Error in OPCODE_BUILTIN(1000)
%TDI Error in EXECUTE("opcode_builtin(1000)")
```


### `OPCODE_STRING`
|||
|-|-|
|TDI Syntax   | `OPCODE_STRING(_NUM)` |
|Python Syntax| `MDSplus.OPCODE_STRING(_NUM)`|
|Opcode|264|

Returns the string name (in uppercase) of an opcode.
Argument must be an unsigned word [scalar](#scalar) of an existing opcode.

TODO: how is this different from `opcode_builtin`?

```tdi
TDI> opcode_string(0)
"OPC$$"
TDI> opcode_string(264)
"OPC$OPCODE_STRING"
```


### `exponent` (Opcode 161)

|||
|-|-|
|TDI Syntax   | `exponent(arg0)` |
|Python Syntax| `MDSplus.exponent(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |


The exponent part of the argument when represented as a model number.
* Arguments must be real. Complex numbers result in error.
* Returns The exponent or the model representation with bias removed, provided X is nonzero. For zero, result is zero.

> TODO : Come back to this. results different on modern computer vs. vax output listed in examples below

Examples.
* `Exponent(1.0)` is `1` and `EXPONENT(4.1)` is `3` on the VAX.

### `MAXEXPONENT`
|||
|-|-|
|TDI Syntax   | `MAXEXPONENT(_NUM)` |
|Python Syntax| `MDSplus.MAXEXPONENT(_NUM)` |
|Opcode|234|

The maximum exponent in the model representing numbers of the same type as the argument.

TODO: Come back to this. Basically it just returns the numerical limit of the exponent part of a float. This and MAXEXPONENT() made more sense back when there were all different types of floats and they all had a different exp bias, but now that there are two standard floats, it will only ever return 127 for float or 1023 for double

Inputs must be floating points, otherwise they will be converted to float. 
If larger than float, it upcasts to a double

Examples
```tdi
MAXEXPONENT(1.0) is 127 on the VAX.
```

See also: `minexponent`

### `MINEXPONENT`
|||
|-|-|
|TDI Syntax   | `MINEXPONENT(arg0)` |
|Python Syntax| `MDSplus.MINEXPONENT(arg0)` |
|Opcode|242|

TODO: Come back to this. Basically it just returns the numerical limit of the exponent part of a float. This and MAXEXPONENT() made more sense back when there were all different types of floats and they all had a different exp bias, but now that there are two standard floats, this is it!

The minimum exponent in the model representing numbers of the same type as the argument.
X must be real or complex, scalar or array.

Inputs must be floating points, otherwise they will be converted to float. 
If larger than float, it upcasts to a double


Examples     
```tdi
TDI> minexponent(1)
-127

TDI> minexponent(1q)
-1023

TDI> minexponent(1.0)
-127
```


### `fraction` (Opcode 170)

|||
|-|-|
|TDI Syntax   | `fraction(arg0)` |
|Python Syntax| `MDSplus.fraction(arg0)` |
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: fraction(arg0)
|Native python|False|

> TODO : Come back to this and investigate further. Lots of unexpected results

Fractional part of the model representation of the argument value.
|Arguments, Results|X must be real or complex.
|Signals      |Same as X. |Units        |Same as X. |Form         |Same as X.
|Result       |The value of X with the exponent set to its bias value.
|Examples     |FRACTION(3.0) is 0.75 on the VAX.


### `PRECISION`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 142
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PRECISION(arg0)
|Native python|False|


Inquiry.
The decimal precision in the model representing numbers of the argument type.
|Arguments, Results|X must be real or complex, scalar or array.
|Signals      |None. |Units        |None. |Form         |Integer scalar.
|Result       |INT((p-1)*LOG10(b))+k, where p is the number of fraction digits, b is the digit size, and k is 1 if b is an integral power of ten and 0 otherwise.
|Examples     |PRECISION(1.0) is INT((24-1)*LOG10(2))=INT(6.92)=6 on the VAX.
PRESENT

### `SPACING`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
(Opcode 326
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SPACING(arg0) 
|Native python|False|


|Type         |F90 Numeric Elemental|
Absolute spacing of model numbers near argument.
|Arguments, Results|X must be real. Complex numbers are an error.
|Signals      |Same as X. |Units        |Same as X. |Form         |Same as X.
|Result       |b^(e-p), where b is the base, e is the exponent part of X and p is the digits of precision.
|Examples     |SPACING(3.0) is 2^-22 on the VAX.

### `RRSPACING`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
(Opcode 306
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: RRSPACING(arg0)

|Native python|False|

 |Type         |F90 Numeric Elemental|
The reciprocal of the relative spacing of model numbers near the argument value.
|Arguments, Results|X must be real. Complex numbers are an error.
|Signals      |Same as X. |Units        |Same as X. |Form         |Same as X.
|Result       |Value ABS(X*b^-e)*b^p, where b is the real base, e is exponent part of X, and p is the number of digits in X.
|Examples     |RRSPACING(-3.0) is 0.75*2^24 on the VAX.

### `RADIX`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 288
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: RADIX(arg0) 
|Native python|False|


F90 Inquiry.
The base of the model representing numbers of the same type as the argument.
|Arguments, Results|X is numeric scalar or array.
|Signals      |None. |Units        |None. |Form         |Integer scalar.
|Result       |The base of the real or integer model.
Examples. RADIX(1.0) is 2 and RADIX(123) is 2 on the VAX.

### `RANGE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 141
|Min arguments| 1
|Max arguments| 1
Compiler syntax: RANGE(arg0) 
|Native python|False|
Description:
F90 Inquiry.
The decimal exponent range in the model representing the type of the argument.
|Arguments, Results|X must be real or complex, scalar or array.
|Signals      |None. |Units        |None. |Form         |Integer scalar. |Result       |INT(MIN(LOG10(HUGE(X)),-LOG10(TINY(X)))).
|Examples     |RANGE(1.0) is 38 on VAX.


### `SELECTED_INT_KIND`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 413
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SELECTED_INT_KIND(arg0)
|Native python|False|


F90 Inquiry.
The kind value of an integer that will represent the number of decimal digits.
|Arguments, Results|R must be a scalar integer.
Signality. None. |Units        |None. |Form         |Scalar integer.
|Result       |A value equal to the kind type parameter of an integer data type that represents all values with between -10^R and 10^R, or if no such kind is available, the result is -1. If more than one kind meets the criteria, the result is the one with the smallest range.
|Examples     |SELECTED_INT_KIND(6) is 8 (DSC$K_DTYPE_L) on the VAX.

### `SELECTED_REAL_KIND`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 414
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: SELECTED_REAL_KIND(arg0,arg1)
|Native python|False|


F90 Inquiry.
The kind value of an real that will represent the number of decimal digits and the decimal exponent range.
|Arguments, Results|Optional: P and R must be a scalar integers.
Signality. None. |Units        |None. |Form         |Scalar integer.
|Result       |A value equal to the kind type parameter of a real data type with decimal precision, as returned by PRECISION, of at least P digits and exponent range, as returned by RANGE of at least R. If no such kind is available the result is -1 if the precision is not available, -2 if the exponent is not available, or -3 if neither. If more than one kind meets the criteria, the result is the one with the smallest decimal precision.
|Examples     |SELECTED_REAL_KIND(6,30) is 10 (DSC$K_DTYPE_F) on the VAX.

### `SET_EXPONENT`

|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 310
|Min arguments| 2
|Max arguments| 2
Compiler syntax: SET_EXPONENT(arg0,arg1)
|Native python|False|


|Type         |F90 Numeric Elemental|
Model number whose fractional part is the fractional part is that of X and whose exponent part is I.
Arguments X real or complex. I integer.
|Signals      |Same as X. |Units        |Same as X. |Form         |Same as X.
|Result       |X*b^(I-e), where b is the real number base and e is exponent offset.
|Examples     |SET_EXPONENT(3.0,1) is 1.5 on the VAX.



### `SHOW_PRIVATE`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 378
|Min arguments| 0
|Max arguments| 254
******Compiler syntax: SHOW_PRIVATE(arg0,arg1,argn,...)
|Native python|False|


Variable IO.
Display on normal output the contents of a wildcard list of variable names or all the variables.
Arguments Optional: STRING. STRING,... character scalar with wildcards % and *. If omitted all private variables are displayed.
|Result       |None.
Side Effect. Writes to stdout, SYS$OUTPUT on the VAX.
|Examples     |_A = 42, SHOW_PRIVATE("_A") produces Private _A = 42

### `SHOW_PUBLIC`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 379
|Min arguments| 0
|Max arguments| 254
******Compiler syntax: SHOW_PUBLIC(arg0,arg1,argn,...)
|Native python|False|


Variable IO.
Display on normal output the contents of a wildcard list of variable names or all the variables.
Arguments Optional: STRING. STRING,... character scalar with wildcards % and *. If omitted all public variables are written.
|Result       |None.
Side Effect. Writes to stdout, SYS$OUTPUT on the VAX.
|Examples     |_A = 42, SHOW_PUBLIC("_A") produces Public _A = 42

### `SHOW_VM`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 380
|Min arguments| 0
|Max arguments| 2
******Compiler syntax: SHOW_VM(arg0,arg1) 
|Native python|False|


Show virtual memory consumption of this process



### `SIZEOF`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 321
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SIZEOF(arg0) 
|Native python|False|


Inquiry.
Size of whole excluding descriptor.
|Arguments, Results|Any VMS type. |Signals      |None. |Units        |None. |Form         |Integer scalar.
|Result       |The number of bytes in the evaluated expression.
|Examples     |SIZEOF(123) is 4.



