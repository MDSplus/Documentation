
# Glossary

### Kind

This is another way to refer to [DTypes](TODO link to Dtypes), or a unique ID for each data type.

Use [`KIND_OF()`](#kind_of-opcode-437) to query the `kind` of a variable or constant.

If a function has a `_KIND` argument, you may pass a value from the [DType table](TODO:link) or from the `Kind` column in any of the tables below. This will cause the result of the function to be cast to that data type, if possible.

### Numeric

Refers to a numeric quantity.

This can be a [Scalar](#scalar), [Array](#array), or [Signal](#signal), unless otherwise specified.

### Logical

Refers to a logical (boolean) quantity, which can be either 0 for [`$FALSE`](#false-false-constant) or 1 for [`$TRUE`](#true-true-constant).

> TODO: Check and Improve. Should "type" say "kind" instead?
The type should be `Unsigned_Byte()`, but any [`Integer`](#integer) type should work.

This can be a [Scalar](#scalar), [Array](#array), or [Signal](#signal), unless otherwise specified.

### Scalar

Refers to a single value, which can be [Integer](#integer), [Floating Point](#floating-point), or [Complex Number](#complex-number), unless otherwise specified.

### Real Number

> Note: This usually refers to floating point numbers, should we differentiate?

This refers to any number that is not imaginary or complex.

See [`Integer`](#integer) and [`Floating point`](#floating-point) for more information.
