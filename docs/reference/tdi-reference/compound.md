
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

## Signal

## Window

## Value With Error

## Value With Units

Used to store units alongside data.

[`MAKE_WITH_UNITS(_VALUE, _UNITS)`](#) (Delayed)  
[`BUILD_WITH_UNITS(_VALUE, _UNITS)`](#build_with_units) (Immediate)

`_VALUE` can be anything, but is usually [Numeric](#).  
Retrieve with [`VALUE_OF(_this)`](#value_of) (or [`DSCPTR_OF(_this, 0)`](#)).

`_UNITS` should be a [Character](#).  
Retrieve with [`UNITS_OF(_this)`](#units_of) (or [`DSCPTR_OF(_this, 1)`](#)).

[`DATA`](#) can be used to get and evaluate the value.

[`DATA_WITH_UNITS`](#) can be used to get and evaluate the value while retaining the units.

> TODO: Improve

Note: Many functions will discard units, others may modify the units based on the operation. For example, [`MULTIPLY`](#) will combine both units with a '*', and [`ADD`](#) will replace mismatched units with '?'.

> TODO: Improve

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

# Accessors

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

### `UNITS_OF`

|||
|-|-|
|TDI Syntax   | `UNITS_OF(_OBJECT)` |
|Python Syntax| `MDSplus.UNITS_OF(object)` |
|Opcode|354|

If `_OBJECT` is a [Value With Units](#value-with-units), returns the `_UNITS` field. Otherwise, returns a ' '.

# Deprecations

## Procedure

Use Function instead

## Program

Use Function instead

## Routine

Use Function instead

## Slope

Use Range