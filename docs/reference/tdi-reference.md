# TDI Reference

## Constants

### `$2PI`
```
Builtin Name: $2PI
TdiShr Function: Tdi2Pi
Opcode number: 372
Min Arguments: 0
Max arguments: 0
Compiler syntax: $2PI
Native python: True
Description:
CONSTANT: 2PI - equivalent to circumference of a circle divided by its radius (approx 6.2831853072)
```

### `$A0`
```
Builtin Name: $A0
TdiShr Function: TdiA0
Opcode number: 1
Min Arguments: 0
Max arguments: 0
Compiler syntax: $A0
Native python: True
Description:
CONSTANT: "$A0" BOHR Radius == 52.9177E-12m, with a margin of error of 1168.02E-21
```



## Other Special Variables beginning with `$`


## `$`
```
TdiShr Function: Tdi
Opcode number: 0
Min Arguments: 0
Max arguments: 0
Compiler syntax: `$`
Native python: False
```
Description:
Argument placeholder. Object not actually created in compilations. Placeholders are replaced by arguments passed to the compile operation. A placeholder can be simply `$` or they can be trailed by a number, i.e. `$2` specifying the second argument (arguments are indexed beginning with `1` for the first argument using positional placeholders). if a `$n` is used as a placeholder, subsequent `$` placeholders without a position number will use the next placeholder after `$n`. For example: `compile("_x=$//$3//$1//$",'how ','are ','you ')` would produce the string: `how you how are`.

