
# Logical

### `LOGICAL` (Convert to Logical)

|||
|-|-|
|TDI Syntax   | `LOGICAL(_NUM, [_KIND])` |
|Python Syntax| `MDSplus.LOGICAL(_NUM, [_KIND])` |
|Opcode|226|


Converts to a logical. True is 1BU, False is 0BU.

Arguments:
* `_NUM`: an integer.
* `[_KIND]` optional: scalar integer type number, for example, KIND($TRUE). Today, there is only one logical type.)
* Returns True if lowest bit of converted integer is "on" (1).
* Warning: truncation does not cause an error.

Examples
`logical(_L OR NOT _L)` is `$TRUE`.
`logical($FALSE or not $FALSE)` is `$TRUE`.
`logical(5)` is `1BU`

## `$TRUE` (True Constant)

|||
|-|-|
|TDI Syntax   | `$TRUE` |
|Python Syntax| `MDSplus.dTRUE()` |
|Java mdsplus-api Syntax| `CONST.dTrue()`|
|Opcode|29|

Boolean constant for true: 1

Note: Any expression that returns `$TRUE` will display as `1BU`.

```tdi
TDI> $true
1BU

TDI> 1 == 1
1BU
```

See also:
* [`$FALSE`](#false-false-constant)

## `$FALSE` (False Constant)

|||
|-|-|
|TDI Syntax   | `$FALSE` |
|Python Syntax| `MDSplus.dFALSE()` |
|Java mdsplus-api Syntax| `CONST.dFalse()`|
|Opcode|8|

Boolean constant for false: 0

Note: Any expression that returns `$FALSE` will display as `0BU`.

```tdi
TDI> $false
0BU

TDI> 1 == 2
0BU
```

See also:
* [`$TRUE`](#true-true-constant)

# Comparison Operators

### `EQ` (Equal To)

|||
|-|-|
|TDI Syntax   | `_X == _Y`, `_X EQ _Y` or `EQ(_X, _Y)`|
|Python Syntax| `MDSplus.EQ(x, y)`|
|Opcode|151|

Returns [`$TRUE`](#true-true-constant) if `_X` is equal to `_Y`, or [`$FALSE`](#false-false-constant) otherwise.

To assign a value to a variable, use [`EQUALS()`](#equals-variable-assignment).

`_X` and `_Y` must be [Numeric](#numeric) or [Character](#character). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` or `_Y` are [Numeric](#numeric), the value(s) must be [Real](#real). If they are [Characters](#character), they will be compared by their ASCII values.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

Any `$ROPRAND` values of `_X` or `_Y` will result in `$FALSE`.

Note: This can be used to create a `_MASK` argument for functions that take one.

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded, however mismatched units will cause the units to be replaced with '?' instead.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 1 == 2
0BU

TDI> 2 == 2
1BU

TDI> 'a' == 'b'
0BU

TDI> 'a' == 'A'
0BU

TDI> 'this' == 'that'
0BU

TDI> [1, 2, 3, 4, 5] == 3
Byte_Unsigned([0,0,1,0,0])

TDI> [1, 2, 3] == [3, 2, 1]
Byte_Unsigned([0,1,0])

TDI> [1, 2, 3, 4] == [1, 0]
Byte_Unsigned([1,0])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) == 2
Build_Signal(Byte_Unsigned([0,1,0,0]), *, [.1,.2,.3,.4])

# The ? indicating a unit mismatch
TDI> build_with_units(42, 'm') == build_with_units(42, 'ft')
Build_With_Units(1BU, "?")
```

See also:
* [`NE()`](#ne-not-equal-to)
* [`LT()`](#lt-less-than)
* [`LE()`](#le-less-than-or-equal-to)
* [`GT()`](#gt-greater-than)
* [`GE()`](#ge-greater-than-or-equal-to)


### `NE` (Not Equal To)

|||
|-|-|
|TDI Syntax   | `_X != _Y`, `_X <> _Y`, `_X NE _Y` or `NE(_X, _Y)` |
|Python Syntax| `MDSplus.NE(x, y)`|
|Opcode|252|

Returns [`$TRUE`](#true-true-constant) if `_X` is not equal to `_Y`, or [`$FALSE`](#false-false-constant) otherwise.

`_X` and `_Y` must be [Numeric](#numeric) or [Character](#character). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` or `_Y` are [Numeric](#numeric), the value(s) must be [Real](#real). If they are [Characters](#character), they will be compared by their ASCII values.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

Any `$ROPRAND` values of `_X` or `_Y` will result in `$TRUE`.

Note: This can be used to create a `_MASK` argument for functions that take one.

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded, however mismatched units will cause the units to be replaced with '?' instead.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 1 != 2
1BU

TDI> 2 != 2
0BU

TDI> 'a' != 'b'
1BU

TDI> 'a' != 'A'
1BU

TDI> 'this' != 'that'
1BU

TDI> [1, 2, 3, 4, 5] != 3
Byte_Unsigned([1,1,0,1,1])

TDI> [1, 2, 3] != [3, 2, 1]
Byte_Unsigned([1,0,1])

TDI> [1, 2, 3, 4] != [1, 0]
Byte_Unsigned([0,1])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) != 2
Build_Signal(Byte_Unsigned([1,0,1,1]), *, [.1,.2,.3,.4])

# The ? indicating a unit mismatch
TDI> build_with_units(42, 'm') != build_with_units(42, 'ft')
Build_With_Units(0BU, "?")
```

See also:
* [`EQ()`](#eq-equal-to)
* [`LT()`](#lt-less-than)
* [`LE()`](#le-less-than-or-equal-to)
* [`GT()`](#gt-greater-than)
* [`GE()`](#ge-greater-than-or-equal-to)


Logical Elemental.
Tests for inequality of two values.
Usual Forms X != Y, X <> Y, X NE Y. F90 form /= is not allowed. Function Form NE(X,Y).
Arguments X and Y must both be numeric or character.
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape.
|Result       |True if X and Y are the unequal; otherwise, false. $ROPRAND is not unequal to any value, thus gives false.
* WARNING, floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that .1+.1!=.2 will be false.
|Examples     |2<>2. is $FALSE.

See also: `eq`, `ge`, `gt`, `le`, `lt`

### `LT` (Less Than)

|||
|-|-|
|TDI Syntax   | `_X < _Y`, `_X LT _Y`, or `LT(_X, _Y)` |
|Python Syntax| `MDSplus.LT(x, y)` |
|Opcode|229|

Returns [`$TRUE`](#true-true-constant) if `_X` is less than `_Y`, or [`$FALSE`](#false-false-constant) otherwise.

`_X` and `_Y` must be [Numeric](#numeric) or [Character](#character). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` or `_Y` are [Numeric](#numeric), the value(s) must be [Real](#real). If they are [Characters](#character), they will be compared by their ASCII values.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

Any `$ROPRAND` values of `_X` or `_Y` will result in `$FALSE`.

Note: This can be used to create a `_MASK` argument for functions that take one.

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded, however mismatched units will cause the units to be replaced with '?' instead.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 1 < 2
1BU

TDI> 2 < 1
0BU

TDI> 'a' < 'b'
1BU

TDI> 'a' < 'B'
0BU

TDI> 'this' < 'that'
0BU

TDI> [1, 2, 3, 4, 5] < 3
Byte_Unsigned([1,1,0,0,0])

TDI> [1, 2, 3] < [1, 3, 2]
Byte_Unsigned([0,1,0])

TDI> [1, 2, 3, 4] < [1, 3]
Byte_Unsigned([0,1])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) < 2
Build_Signal(Byte_Unsigned([1,0,0,0]), *, [.1,.2,.3,.4])

# The ? indicating a unit mismatch
TDI> build_with_units(42, 'm') < build_with_units(42, 'ft')
Build_With_Units(0BU, "?")
```

See also:
* [`EQ()`](#eq-equal-to)
* [`NE()`](#ne-not-equal-to)
* [`LE()`](#le-less-than-or-equal-to)
* [`GT()`](#gt-greater-than)
* [`GE()`](#ge-greater-than-or-equal-to)

### `LE` (Less Than or Equal To)

|||
|-|-|
|TDI Syntax   | `_X <= _Y`, `_X le _Y`, or `le(_X,_Y)` |
|Python Syntax| `MDSplus.le(_X, _Y)`|
|Opcode|216|

Returns [`$TRUE`](#true-true-constant) if `_X` is less than or equal to `_Y`, or [`$FALSE`](#false-false-constant) otherwise.

`_X` and `_Y` must be [Numeric](#numeric) or [Character](#character). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` or `_Y` are [Numeric](#numeric), the value(s) must be [Real](#real). If they are [Characters](#character), they will be compared by their ASCII values.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

Any `$ROPRAND` values of `_X` or `_Y` will result in `$FALSE`.

Note: This can be used to create a `_MASK` argument for functions that take one.

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded, however mismatched units will cause the units to be replaced with '?' instead.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 1 <= 2
1BU

TDI> 2 <= 1
0BU

TDI> 'a' <= 'b'
1BU

TDI> 'a' <= 'B'
0BU

TDI> 'this' <= 'that'
0BU

TDI> [1, 2, 3, 4, 5] <= 3
Byte_Unsigned([1,1,1,0,0])

TDI> [1, 2, 3] <= [1, 3, 2]
Byte_Unsigned([1,1,0])

TDI> [1, 2, 3, 4] <= [0, 2]
Byte_Unsigned([0,1])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) <= 2
Build_Signal(Byte_Unsigned([1,1,0,0]), *, [.1,.2,.3,.4])

# The ? indicating a unit mismatch
TDI> build_with_units(42, 'm') <= build_with_units(42, 'ft')
Build_With_Units(1BU, "?")
```

See also:
* [`EQ()`](#eq-equal-to)
* [`NE()`](#ne-not-equal-to)
* [`LT()`](#lt-less-than)
* [`GT()`](#gt-greater-than)
* [`GE()`](#ge-greater-than-or-equal-to)

### `GT` (Greater Than)

|||
|-|-|
|TDI Syntax   | `_X > _Y`, `_X GT _Y`, or `GT(_X, _Y)` |
|Python Syntax| `MDSplus.GT(x, y)`|
|Opcode|177|

Returns [`$TRUE`](#true-true-constant) if `_X` is greater than `_Y`, or [`$FALSE`](#false-false-constant) otherwise.

`_X` and `_Y` must be [Numeric](#numeric) or [Character](#character). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` or `_Y` are [Numeric](#numeric), the value(s) must be [Real](#real). If they are [Characters](#character), they will be compared by their ASCII values.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

Any `$ROPRAND` values of `_X` or `_Y` will result in `$FALSE`.

Note: This can be used to create a `_MASK` argument for functions that take one.

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded, however mismatched units will cause the units to be replaced with '?' instead.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 1 > 2
0BU

TDI> 2 > 1
1BU

TDI> 'a' > 'b'
0BU

TDI> 'a' > 'B'
1BU

TDI> 'this' > 'that'
1BU

TDI> [1, 2, 3, 4, 5] > 3
Byte_Unsigned([0,0,0,1,1])

TDI> [1, 2, 3] > [1, 3, 2]
Byte_Unsigned([0,0,1])

TDI> [1, 2, 3, 4] > [1, 0]
Byte_Unsigned([0,1])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) > 2
Build_Signal(Byte_Unsigned([0,0,1,1]), *, [.1,.2,.3,.4])

# The ? indicating a unit mismatch
TDI> build_with_units(42, 'm') > build_with_units(42, 'ft')
Build_With_Units(0BU, "?")
```

See also:
* [`EQ()`](#eq-equal-to)
* [`NE()`](#ne-not-equal-to)
* [`LT()`](#lt-less-than)
* [`LE()`](#le-less-than-or-equal-to)
* [`GE()`](#ge-greater-than)


Tests for first greater than second.
* Usual Forms `X>Y` or `X GT Y`.  
  Function Form GT(X,Y).
* Warning, floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that .1+.1>=.2 is true. Integer values may be truncated when matched to floating numbers.
* Returns true if X is greater than Y; otherwise, false.
    * A reserved operand is always false.
    * Characters are compared in the processor collating sequence.
    * Arguments X and Y must both be numeric or character. Complex numbers are an error.


Examples
* `2>2.0` returns `$FALSE`.
* Example with units:
    ```
    TDI> _A = Build_With_Units(2, "cm")
    Build_With_Units(2, "cm")
    TDI> _B = Build_With_Units(3, "mm")
    Build_With_Units(3, "mm")
    TDI> _A > _B
    Build_With_Units(0BU, "?")
    TDI> _B > _A
    Build_With_Units(1BU, "?")
    ```

See also: `eq`, `ge`, `le`, `lt`, `ne`

### `GE` (Greater Than or Equal To)

|||
|-|-|
|TDI Syntax   | `_X >= _Y`, `_X GE _Y` or `GE(_X, _Y)` |
|Python Syntax| `MDSplus.GE(x, y)` |
|Opcode|174|

Returns [`$TRUE`](#true-true-constant) if `_X` is greater than or equal to `_Y`, or [`$FALSE`](#false-false-constant) otherwise.

`_X` and `_Y` must be [Numeric](#numeric) or [Character](#character). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` or `_Y` are [Numeric](#numeric), the value(s) must be [Real](#real). If they are [Characters](#character), they will be compared by their ASCII values.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

Any `$ROPRAND` values of `_X` or `_Y` will result in `$FALSE`.

Note: This can be used to create a `_MASK` argument for functions that take one.

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded, however mismatched units will cause the units to be replaced with '?' instead.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 1 >= 2
0BU

TDI> 2 >= 1
1BU

TDI> 'a' >= 'b'
0BU

TDI> 'a' >= 'B'
1BU

TDI> 'this' >= 'that'
1BU

TDI> [1, 2, 3, 4, 5] >= 3
Byte_Unsigned([0,0,1,1,1])

TDI> [1, 2, 3] >= [1, 3, 2]
Byte_Unsigned([1,0,1])

TDI> [1, 2, 3, 4] >= [3, 2]
Byte_Unsigned([0,1])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) >= 2
Build_Signal(Byte_Unsigned([0,1,1,1]), *, [.1,.2,.3,.4])

# The ? indicating a unit mismatch
TDI> build_with_units(42, 'm') >= build_with_units(42, 'ft')
Build_With_Units(1BU, "?")
```

See also:
* [`EQ()`](#eq-equal-to)
* [`NE()`](#ne-not-equal-to)
* [`LT()`](#lt-less-than)
* [`LE()`](#le-less-than-or-equal-to)
* [`GT()`](#gt-greater-than)

## Logic Operators

### `eqv` (Opcode 154)

|||
|-|-|
|TDI Syntax   | `eqv(_BOOL0,_BOOL1)` |
|Python Syntax| `MDSplus.eqv(_BOOL0,_BOOL1)` |
|Min arguments| 2 |
|Max arguments| 2 |

Test that logical values are equal.
* Arguments must be logical (lowest bit is 1 for true).
* True if both are true or both are false; otherwise, false.

Examples
* `2>3 EQV 3>4` returns `$TRUE`.

### `NEQV`
|||
|-|-|
|TDI Syntax   | `NEQV(_A, _B)` |
|Python Syntax| `MDSplus.NEQV(_A, _B)` |
|Opcode|254|

True if exactly one of `_A` and `_B` are true; otherwise, false.
* equivalent to exclusive-OR, i.e., `XOR`
* For bit-wise equivalent, see `ieor`
* `_A` and `_B` must be boolean.

Examples 

2>3 NEQV 3>4 is $FALSE.
```
TDI> $true && $false neqv $false || $false
0BU
TDI> $true && $false neqv $false || $true
1BU
TDI> $true && $true neqv $false || $true
0BU

TDI> [0, 0, 1, 1] && [0,1,0,1] neqv [0,0,1,1] || [0,1,0,1]
Byte_Unsigned([0,1,1,0])
```

Logical Elemental.
Test that logical values are unequal.
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape. |Result       |True if exactly one of X and Y are true;
otherwise, false.
|Examples     |2>3 NEQV 3>4 is $FALSE.
NINT

### `NOT`
|||
|-|-|
|TDI Syntax   | `!_A` or `NOT _A` or `NOT(_A)` |
|Python Syntax| `MDSplus.NOT(_A)` |
|Opcode|258|

Negates a logical. True is 1BU, False is 0BU.
* For bit-wise operator see [INOT](#inot). 
* Argument should be [logical](#logical)
* Returns the opposite

TODO: Stephen and Tim 

Examples
```tdi
TDI> !$false
1BU
TDI> not $true
0BU
TDI> not [0,0,1,1]
Byte_Unsigned([1,1,0,0])

TDI> not [1,2,3]
Byte_Unsigned([0,1,0])

if (!$false) { write(*, "help"); }
TODO: Stephen & Tim

```

### `AND` (Boolean/Logical AND)

|||
|-|-|
|TDI Syntax   | `_A && _B` or `AND(_A, _B)`|
|Python Syntax| `MDSplus.AND(a, b)` |
|Opcode|45|

Logical intersection of elements. Returns true if both are true; otherwise, false.
* Note: do not confuse with `&` which is bit-wise `IAND`.
* Arguments are expected to be booleans (0 or 1)

Examples

```tdi
TDI> [0,0,1,1] && [0,1,0,1]
[0BU,0BU,0BU,1BU]
```

See also
* `eqv`, `nand`, `neqv`, `nor`, `or`, and others like `and_not` for other logical functions.



### `AND_NOT` (AND of the NOT)

|||
|-|-|
|TDI Syntax   | `AND_NOT(_X, _Y)` |
|Python Syntax| `MDSplus.AND_NOT(x, y)` |
|Opcode|46|

Returns the logical intersection of `_X` and the negation of `_Y`, equivalent to `_X && !_Y`.

To get the bitwise AND of the NOT use [`IAND_NOT`](#iand_not-bitwise-and-of-the-not).

> TODO: Make a logical section in the glossary
`_X` and `_Y` must be [Logical](#logical). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

```tdi
TDI> and_not($TRUE, $FALSE)
1BU

TDI> and_not([0,0,1,1], [0,1,0,1])
Byte_Unsigned([0,0,1,0])

TDI> and_not([0,1], [1,0]) == ([0,1] && ![1,0])
Byte_Unsigned([1,1])
```


### `OR` (Boolean/Logical OR)
|||
|-|-|
|TDI Syntax   | ``_A \|\| _B` or `_A OR _B` or `OR(_A, _B)`` |
|Python Syntax| `MDSplus.or` |
|Opcode|267|


Returns true if either is true; otherwise, false. 
* _A and _B must be [logical](#logical)
* Note: do not confuse with | which is bit-wise `IOR`.

Examples
```tdi
[0,0,1,1] || [0,1,0,1] is [$FALSE,$TRUE,$TRUE,$TRUE].
```


### `OR_NOT` (Boolean/Logical OR of the NOT)
|||
|-|-|
|TDI Syntax   | `OR_NOT(_A, _B) ` |
|Python Syntax| `MDSplus.OR_NOT(_A, _B) ` |
|Opcode|268|

Returns True if A is true or B is false; otherwise, false.
* _A and _B must be [logical](#logical)
* Logical union of first with negation of second.

Examples
```tdi
[0,0,1,1] OR_NOT [0,1,0,1] is [$TRUE,$FALSE,$TRUE,$TRUE].
```


### `NAND` (NOT AND)
|||
|-|-|
|TDI Syntax   | `NAND(_A, _B)`, or  `_A NAND _B` |
|Python Syntax| `MDSplus.NAND(_A, _B)` |
|Opcode|249|

Returns False if both are true; otherwise, true.
* Equivalent to `NOT AND`, or `NOT (A AND B)`
* Negation of [logical](#logical) intersection of elements. 
* `_A` and `_B` must be boolean.


_A and _B must be boolean.

Examples
```tdi
TDI> [0,0,1,1] nand [0,1,0,1]
Byte_Unsigned([1,1,1,0])
```


### `NAND_NOT` (NOT AND NOT)
|||
|-|-|
|TDI Syntax   | `NAND_NOT(_A, _B)` or `_A NAND_NOT _B`|
|Python Syntax| `MDSplus.NAND_NOT(_A, _B)` |
|Opcode|250|

If A is true and B is false, returns false, otherwise true.
* Equivalent to `NOT(_A and NOT(_B))`
* Negation of [logical](#logical) intersection of first with negation of second.
* `_A` and `_B` must be boolean.

Examples

```tdi
TDI> [0,0,1,1] NAND_NOT [0,1,0,1]
Byte_Unsigned([1,1,0,1])
```

### `NOR`
|||
|-|-|
|TDI Syntax   | `NOR(_A, _B)` |
|Python Syntax| `MDSplus.NOR(_A, _B)` |
|Opcode|256|

Returns True if both are false, otherwise, false, i.e., false unless both are false
* `_A` and `_B` must be boolean.

```tdi
TDI> $false nor $false
1BU

TDI> [0,0,1,1] nor [0,1,0,1]
Byte_Unsigned([1,0,0,0])
```


### `NOR_NOT`
|||
|-|-|
|TDI Syntax   | `NOR_NOT(_A, _B)` |
|Python Syntax| `MDSplus.NOR_NOT(_A, _B)` |
|Opcode|257|

True if `_A` is false and `_B` is true; otherwise, false.
* Logically equivalent to NOT(L) AND M.
* Negation of logical union of first with negation of second.
* `_A` and `_B` must be boolean.

```tdi
TDI> $false nor_not $true
1BU

TDI> [0,0,1,1] nor_not [0,1,0,1]
Byte_Unsigned([0,1,0,0])
```



### `ANY` (Any True)

|||
|-|-|
|TDI Syntax   | `ANY(_ARRAY, [_DIM])` |
|Python Syntax| `MDSplus.ANY(mask, [dim])` |
|Opcode|48|

> TODO: Link to dimension explanation
Returns [`$TRUE`](#true-true-constant) if any value in `_ARRAY` is [`$TRUE`](#true-true-constant). If `_DIM` is present, each element of that dimension (link) will be checked independently.

To check if all values are [`$TRUE`](#true-true-constant), use [`ALL`](#all-all-true). To count the number of [`$TRUE`](#true-true-constant) values, use [`COUNT`](#count-number-of-true-values).

`_ARRAY` must be a [Logical](#logical), and should be an [Array](#array) or a [Signal](#signal).

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> any([$true, $false, $true])
1BU
TDI> any([1, 0, 1])
1BU

TDI> any([$false, $false, $false])
0BU
TDI> any([0, 0, 0])
0BU

TDI> _array = [1, 2, 3] == [3, 2, 1]
Byte_Unsigned([0,1,0])
TDI> any(_array)
1BU

# Equivalent to any([0, 0, 1, 1, 0, 1, 0, 1])
TDI> any([[0,0,1,1], [0,1,0,1]])
1BU

# Equivalent to [any([0,0,1,1]), any([0,1,0,1])]
TDI> any([[0,0,1,1], [0,1,0,1]], 0)
Byte_Unsigned([1,1])

# Equivalent to [any([1,1]), any([0,0])]
TDI> any([[1,1], [0,0]], 0)
Byte_Unsigned([1,0])

# Equivalent to [any([0,0]), any([0,1]), any([1,0]), any([1,1])]
TDI> any([[0,0,1,1], [0,1,0,1]], 1)
Byte_Unsigned([0,1,1,1])
```

See also:
* [`ALL`](#all-all-true)
* [`COUNT`](#count-number-of-true-values)

### `ALL` (All True)

|||
|-|-|
|TDI Syntax   | `ALL(_ARRAY, [_DIM])` |
|Python Syntax| `MDSplus.ALL(mask, [dim])` |
|Opcode|43|

> TODO: Link to dimension explanation
Returns [`$TRUE`](#true-true-constant) if all values in `_ARRAY` are [`$TRUE`](#true-true-constant). If `_DIM` is present, each element of that dimension (link) will be checked independently.

To check if any value is [`$TRUE`](#true-true-constant), use [`ANY`](#any-any-true). To count the number of [`$TRUE`](#true-true-constant) values, use [`COUNT`](#count-number-of-true-values).

`_ARRAY` must be a [Logical](#logical), and should be an [Array](#array) or a [Signal](#signal).

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> all([$true, $true, $true])
1BU
TDI> all([1, 1, 1])
1BU

TDI> all([$true, $false, $true])
0BU
TDI> all([1, 0, 1])
0BU

TDI> _array = [1, 2, 3] != [4, 5, 6]
Byte_Unsigned([1,1,1])
TDI> all(_array)
1BU

TDI> _array = [1, 2, 3] == [3, 2, 1]
Byte_Unsigned([0,1,0])
TDI> all(_array)
0BU

# Equivalent to all([0, 0, 1, 1, 0, 1, 0, 1])
TDI> all([[0,0,1,1], [0,1,0,1]])
0BU

# Equivalent to [all([0,0,1,1]), all([0,1,0,1])]
TDI> all([[0,0,1,1], [0,1,0,1]], 0)
Byte_Unsigned([0,0])

# Equivalent to [all([1,1]), all([0,0])]
TDI> all([[1,1], [0,0]], 0)
Byte_Unsigned([1,0])

# Equivalent to [all([0,0]), all([0,1]), all([1,0]), all([1,1])]
TDI> all([[0,0,1,1], [0,1,0,1]], 1)
Byte_Unsigned([0,0,0,1])
```

See also:
* [`ANY`](#any-any-true)
* [`COUNT`](#count-number-of-true-values)



### `COUNT` (Number of True Values)

|||
|-|-|
|TDI Syntax   | `COUNT(_MASK, [_DIM])` |
|Python Syntax| `MDSplus.COUNT(mask, [dim])` |
|Opcode|109|

Returns the number of [`$TRUE`](#true-true-constant) values in `_MASK`. If `_DIM` is present, each element of that dimension (link) will be checked independently.

To check if all values are [`$TRUE`](#true-true-constant), use [`ALL`](#all-all-true). To check if any value is [`$TRUE`](#true-true-constant), use [`ANY`](#any-any-true). 

`_ARRAY` must be a [Logical](#logical), and should be an [Array](#array) or a [Signal](#signal).

[`BUILD_WITH_UNITS()`](#build_with_units) will be discarded.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> count([$true, $false, $true])
2
TDI> count([1, 0, 1])
2

TDI> _array = [1, 2, 3] == [3, 2, 1]
Byte_Unsigned([0,1,0])
TDI> count(_array)
1

# Equivalent to count([0, 0, 1, 1, 0, 1, 0, 1])
TDI> count([[0,0,1,1], [0,1,0,1]])
4

# Equivalent to [count([0,0,0,1]), count([0,1,1,1])]
TDI> count([[0,0,0,1], [0,1,1,1]], 0)
[1,3]

# Equivalent to [count([0,0]), count([0,1]), count([1,0]), count([1,1])]
TDI> count([[0,0,1,1], [0,1,0,1]], 1)
[0,1,1,2]
```

See also:
* [`ALL`](#all-all-true)
* [`ANY`](#any-any-true)

# Bitwise

### `SHIFT_LEFT`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 314
|Min arguments| 2
|Max arguments| 2
Compiler syntax: SHIFT_LEFT(arg0,arg1)

|Native python|False|

Description:
|Return Type  |Numeric Elemental |
Logical or arithmetic left shift of an element.
Usual Form I << SHIFT. Function Form SHIFT_LEFT(I,SHIFT).
Arguments
I must be integer. Octaword is not supported.
SHIFT must be integer, must be positive. The low byte is used.
|Signals      |Single signal or smaller data. |Units        |Same as I. |Form         |Type of I, compatible shape of all.
|Result       |The bits of I shifted SHIFT positions left.
(i)
For unsigned numbers, the vacated bits are cleared.
(ii)
For signed numbers, an arithmetic shift if SHIFT is from 0 to the size in bits; otherwise, undefined.
Examples. (i) 0X12UB << 4 is 0X20UB.
(ii) 0X12SB << 4 is 0X20UB on the VAX.

### `SHIFT_RIGHT`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 315
|Min arguments| 2
|Max arguments| 2
Compiler syntax: SHIFT_RIGHT(arg0,arg1)

|Native python|False|

Description:
|Return Type  |Numeric Elemental |
Logical or arithmetic right shift of an element.
Usual Form I >> SHIFT. Function Form SHIFT_RIGHT(I,SHIFT).
Arguments
I must be integer. Octaword is not supported.
SHIFT must be integer. The low byte is used.
|Signals      |Single signal or smaller data. |Units        |Same as I. |Form         |Type of I, compatible shape of all.
|Result       |The bits of I shifted SHIFT positions right.
(i)
For unsigned numbers, the vacated bits are cleared.
(ii)
For signed numbers, the vacated bits are filled from the sign bit (two's complement arithmetic shift).
Examples. (i) 0X12UB >> 4 is 0X20UB. (ii) 0X89SB >> 4 is 0XF8SB.

### `ishft` 

|||
|-|-|
|TDI Syntax   | `ishft(_I,_SHIFT) ` |
|Python Syntax| `MDSplus.ishft(_I,_SHIFT) ` |
|Min arguments| 2 |
|Max arguments| 2 |
|Opcode|312|


Logical bit-wise shift of an element.
* Arguments
    * `_I` must be integer. Octaword is not supported. 
    * `_SHIFT` must be integer. The low byte is used.
* Returns the bits of `_I` shifted `_SHIFT` positions left if positive or right if negative. The vacated bits are cleared.

Examples
* `ISHFT(3,1)` returns `6`.


### `BTEST` 
|||
|-|-|
|TDI Syntax   | `BTEST(_BIT_FIELD, _POWEROF2)` |
|Python Syntax| `MDSplus.BTEST(_BIT_FIELD, _POWEROF2)` |
|Opcode|69|

This function preforms a bit-wise calculation to see if a specific bit in a bitfield is set by providing a bitfield and a postion (power of 2) to compare. 
* True is returned if the bit at the provided position is 1; and false otherwise.
* If first argument is a scalar, second argument can be an array of any length
* The first argument should be a a bit field
* If both arguments are arrays, they must match in length
* The second argument (_POWEROF2) reads from the rightmost bit to the left.

Examples

```TDI
TDI> btest(5, [0, 1, 2, 3])
Byte_Unsigned([1,0,1,0])
# (hint: 5 in binary is 0101)

TDI> btest(8,3)
1BU

# TODO: bug here to be investigated further. this is the old example...
* if _A = Set_range(2,2,[1,3,2,4]):  
    * `btest(_A,2)` returns Set_Range(2,2,[$FALSE,$FALSE,$FALSE,$TRUE]).
    * `btest(2,_A)` returns Set_Range(2,2,[$TRUE,$FALSE,$FALSE,$FALSE]).

# ...but this is what it actually returns; investigate further
_A = Set_range(2,2,[1,3,2,4])
`btest(_A,2)`
`Byte_Unsigned([[0,0], [0,0]])`
`btest(2,_A)`
`Byte_Unsigned([[1,0], [0,0]])`
```

See also:
* `ibclr` to clear
* `bits` to extract
* `ibset` to set



### `ibclr` (Opcode 63)

|||
|-|-|
|TDI Syntax   | `ibclr(_I,_POS)` |
|Python Syntax| `MDSplus.ibclr(_I,_POS)` |
|Min arguments| 2 |
|Max arguments| 2 |

Clear one bit to zero.

Arguments
* _I any. F90 requires integer. 
* _POS integer offset within the element of I, must be nonnegative and less than BIT_SIZE(I).
* Returns `I` but with the bit at offset `POS` cleared.

Examples
* `IBCLR(14, 1)` is `12`.
* `IBCLR(31,[1,2,3,4])` is `[29,27,23,15]`.

See also:
`ibset` to set, `ibits` to extract, and `btest` to test.


### `ibset` (Opcode 68)

|||
|-|-|
|TDI Syntax   | `IBSET(_I,_BIT)` |
|Python Syntax| `MDSplus.ibset(_I,_BIT)` |
|Min arguments| 2 |
|Max arguments| 2 |

Set a bit to one.
Arguments
* `_I` any. F90 requires integer.
* `_BIT` integer offset within the element of I. Must be nonnegative and less than `BIT_SIZE(_I)`.

|Signals      |Same as I. |Units        |Same as I. |Form         |Same type as I, compatible shape.
|Result       |Same as I with bit at offset BIT set.

Examples
* `IBSET(12,1)` returns `14`.
* `IBSET(0,[1,2,3,4])` returns `[2,4,8,16]`.

See also:
`ibclr` to clear, `ibits` to extract, and `btest` to test.

## Comparison Operators

### `IAND` (Bitwise AND)

|||
|-|-|
|TDI Syntax   | `_X & _Y` or `IAND(_X, _Y)` |
|Python Syntax| `MDSplus.IAND(x, y)` |
|Opcode|185|

Returns the bitwise AND of `_X` and `_Y`.

To get the logical AND use [`AND`](#and-booleanlogical-and).

`_X` and `_Y` must be [Numeric](#numeric) and should be [Integers](#integer). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

The return type will be the unsigned variant of the input type; `Long` would become `Long_Unsigned`.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 0b1110 & 0b0101
4LU

TDI> 14 & 5
4LU

# Byte -> Byte_Unsigned
TDI> 5B & 1B
1BU

TDI> [3, 4, 5] & 1
Long_Unsigned([1LU,0LU,1LU])

TDI> [3, 4, 5, 6] & [1, 2]
Long_Unsigned([1LU,0LU])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) & 1
Build_Signal(Long_Unsigned([1LU,0LU,1LU,0LU]), *, [.1,.2,.3,.4])

TDI> build_with_units(14, 'm') & 5
Build_With_Units(4LU, "m")
```

See also:
* [`AND`](#and-booleanlogical-and)
* [`IAND_NOT()`](#iand_not-bitwise-and-of-the-not)

### `IAND_NOT` (Bitwise AND of the NOT)

|||
|-|-|
|TDI Syntax   | `IAND_NOT(_X, _Y) ` |
|Python Syntax| `MDSplus.IAND_NOT(x, y) ` |
|Opcode|186|

Returns the bitwise AND of `_X` and the NOT of `_Y`, equivalent to `_X & ~_Y`.

To get the logical AND of the NOT use [`AND_NOT`](#and_not-and-of-the-not).

`_X` and `_Y` must be [Numeric](#numeric) and should be [Integers](#integer). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

The return type will be the unsigned variant of the input type; `Long` would become `Long_Unsigned`.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

> TODO: Improve examples
```tdi
TDI> iand_not(0b1110, 0b0101)
10LU

TDI> iand_not(14, 5)
10LU

# Byte -> Byte_Unsigned
TDI> iand_not(5B, 1B)
4BU

TDI> iand_not([3, 4, 5], 1)
Long_Unsigned([2LU,4LU,4LU])

TDI> iand_not([3, 4, 5, 6], [1, 2])
Long_Unsigned([2LU,4LU])

TDI> iand_not(make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]), 1)
Build_Signal(Long_Unsigned([0LU,2LU,2LU,4LU]), *, [.1,.2,.3,.4])

TDI> iand_not(build_with_units(14, 'm'), 5)
Build_With_Units(10LU, "m")
```

See also:
* [`IAND`](#iand-bitwise-and)
* [`AND_NOT()`](#and_not-and-of-the-not)


### `ieor` (Opcode 210)

|||
|-|-|
|TDI Syntax   | `ieor(_I,_J)` |
|Python Syntax| `MDSplus.ieor(_I,_J)` |
|Min arguments| 2
|Max arguments| 2


Bitwise exclusive-OR.
* True for exactly one bit of I and J true; otherwise, false.
* Arguments I and J must be integers.

Examples
* `IEOR (3,5)` returns `6`  
   with 3 being `011`  
   and  5 being `101`,  
   this returns `110` or simply `2`.


### `IEOR_NOT` (Opcode 211)

|||
|-|-|
|TDI Syntax   | `IEOR_NOT(_I,_J)` |
|Python Syntax| `MDSplus.IEOR_NOT(_I,_J)` |
|Min arguments| 2 |
|Max arguments| 2 |

Bit-wise exclusive-OR with the second complemented. Equivalent to `INOT(IEOR(_I,_J))`.
* Arguments I and J must be integers.

Examples
* `IEOR_NOT(1bu,3bu)` in binary is `0B11111101BU`
* `btest(ieor_not(1bu,3bu), 0:7:1)` returns `Byte_Unsigned([1,0,1,1,1,1,1,1])`
* `btest(ieor_not(3bu,5bu), 0:7:1)` returns `Byte_Unsigned([1,0,0,1,1,1,1,1])`


### `inand` (Opcode 193)

|||
|-|-|
|TDI Syntax   | `inand(_I, _J) ` |
|Python Syntax| `MDSplus.inand(_I, _J) ` |
|Min arguments| 2
|Max arguments| 2

Complement of bit-wise/bit-by-bit intersection.
* Arguments `_I` and `_J` must be integers.
* Returns False for each bit true in I and J; otherwise, true.

Examples:
* `INAND(3BU,5BU)` in binary is `0B11111110BU`.



### `inand_not` (Opcode 194)

|||
|-|-|
|TDI Syntax   | `inand_not(_I, _J)` |
|Python Syntax| `MDSplus.inand_not(_I, _J)` |
|Min arguments| 2
|Max arguments| 2

Complement of bit-wise/bit-by-bit intersection with the second complemented. 
* Equivalant to `IOR(INOT(I),J)`.
* Arguments `_I` and `_J` must be integers.
* Returns False for each bit of I true and of J false; otherwise, true.

Examples
* `INAND_NOT(3WU,5WU)` in binary is `0B11111101BU`.


### `inor` (Opcode 196)

|||
|-|-|
|TDI Syntax   | `INOR(_I,_J)` |
|Python Syntax| `MDSplus.INOR(_I,_J)` |
|Min arguments| 2 |
|Max arguments| 2 |


Complement of Bit-wise/bit-by-bit union.
* Arguments I and J must be integers.
* Returns False for either bit true in I and J; otherwise, true.

Examples
* `INOR(3BU,5BU)` in binary is `0B11111000BU`.

### `INOR_NOT` 

|||
|-|-|
|TDI Syntax   | `INOR_NOT(_I,_J) ` |
|Python Syntax| `MDSplus.INOR_NOT(_I,_J)` |
|Min arguments| 2
|Max arguments| 2
|Opcode|197|

Complement of bit-wise/bit-by-bit union with the second complemented. Equivalant to `IAND(NOT(I),J)`.
Arguments I and J must be integers.

Result: False for each bit of I true or of J false; otherwise, true.

Examples
* `INOR_NOT(3BU,5BU)` in binary is `0B00000100BU`.


### `INOT`
|||
|-|-|
|TDI Syntax   | `INOT(_J)` |
|Python Syntax| `MDSplus.INOT(_J)` |
|Opcode|198|

Complement bit-wise/bit-by-bit the argument.
Usual Form ~ J. Function Form INOT(J).
Each binary bit is negated. 
WARNING, F90 calls this NOT, we cannot.
Examples
* `INOT(5BU)` in binary is `0B11111010`.

### `IOR` (Bitwise OR)

|||
|-|-|
|TDI Syntax   | `_X \| _Y` or `IOR(_X, _Y)` |
|Python Syntax| `MDSplus.IOR(x, y)` |
|Opcode|207|

Returns the bitwise inclusive OR of `_X` and `_Y`.

To get the logical OR use [`OR`](#or-booleanlogical-or).

`_X` and `_Y` must be [Numeric](#numeric) and should be [Integers](#integer). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

The return type will be the unsigned variant of the input type; `Long` would become `Long_Unsigned`.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 0b1110 | 0b0101
15LU

TDI> 14 | 5
15LU

# Byte -> Byte_Unsigned
TDI> 5B | 1B
5BU

TDI> [3, 4, 5] | 1
Long_Unsigned([3LU,5LU,5LU])

TDI> [3, 4, 5, 6] | [1, 2]
Long_Unsigned([3LU,6LU])

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) | 1
Build_Signal(Long_Unsigned([1LU,3LU,3LU,5LU]), *, [.1,.2,.3,.4])

TDI> build_with_units(14, 'm') | 5
Build_With_Units(15LU, "m")
```

See also:
* [`OR`](#or-booleanlogical-or)
* [`IOR_NOT()`](#ior_not-bitwise-or-of-the-not)

### `IOR_NOT` (Bitwise OR of the NOT)

|||
|-|-|
|TDI Syntax   | `IOR_NOT(_X, _Y)` |
|Python Syntax| `MDSplus.IOR_NOT(x, y)` |
|Opcode|208|

Returns the bitwise OR of `_X` and the NOT of `_Y`, equivalent to `_X | ~_Y`.

To get the logical OR of the NOT use [`OR_NOT`](#or_not-booleanlogical-or-of-the-not).

`_X` and `_Y` must be [Numeric](#numeric) and should be [Integers](#integer). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

The return type will be the unsigned variant of the input type; `Long` would become `Long_Unsigned`.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

> TODO: Improve examples
```tdi
TDI> ior_not(0b1110, 0b0101)
4294967294LU

TDI> ior_not(14, 5)
4294967294LU

# Byte -> Byte_Unsigned
TDI> ior_not(5B, 1B)
255BU
TDI> ior_not([3B, 4B, 5B], 1B)
Byte_Unsigned([255,254,255])

TDI> ior_not([3B, 4B, 5B, 6B], [1B, 2B])
Byte_Unsigned([255,253])

TDI> ior_not(make_signal(Byte([1, 2, 3, 4]), *, [0.1, 0.2, 0.3, 0.4]), 1B)
Build_Signal(Byte_Unsigned([255,254,255,254]), *, [.1,.2,.3,.4])

TDI> ior_not(build_with_units(14B, 'm'), 5B)
Build_With_Units(254BU, "m")
```

See also:
* [`IOR`](#ior-bitwise-or)
* [`OR_NOT`](#or_not-booleanlogical-or-of-the-not)
