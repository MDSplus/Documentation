# TDI Reference

TODO: Confirm whether to leave the scientific notation as it is in when you ping the program, or into standard:
e.g., the program lists $A0 as 52.9177E-12m, but the normal way to write that is 5.29177E-11m

TODO: make a table or something of all the different precision types of numbers you can have (F, G, H, D0 etc) and what they ultimately mean like how many bytes each ones takes up or whatever. the decimal precision is calculated by 1/(2^x) because of binary. plus all the functions to convert between them (like fs/ft_float, etc.)

TODO: make a table or something of shortcuts 
* bit-wise functions/operators (inor,inornot,inot)
* build/make functions
* fun with ascii (char, ichar, achar, iachar, etc)
* 

TODO: remove references to what VAX returns

TODO for Mark:
* remove min arguments/max arguments unless it's "interesting" (not interesting: min-max 1, min1-max2)
* change arg0, arg1 (etc) to more useful things like `_NUM`, or [_NUM] if optional. use backticks
* examples should be rewritten as triple backtick (```) code blocks
* DONE! ~~remove c syntax from all the entries (should not be called by a human)~~
* move opcode, use natural language headings--try options for each. use LT and log10 as examples
* global explanation of mismatched units (if they don't match, it just returns `?`)
* move all the deprecated/broken/unimplemented to their own section



TODO for Stephen
* move opcode to bottom row of syntax table
* python syntax for the `$` constants--need to be all caps after the `d`
* python syntax arguments
* see TODO's in entries
* see also KIND
* replace Fortran operators with their C equivalents
* for the ones that have a symbol, remove the part where you call it by name
* See [legacy syntax]() section at the end for all the fortran, etc. stuff
* move all the examples not in code blocks...into code blocks
* remove the word "examples" above the code blocks

## Contents
Table of all the commands in each category, with symlinks to each heading






|Constants|||
|-|-|-|
| [`$2PI`](#2pi-opcode-372)           | [`$FARADAY`](#faraday-opcode-9) | [`$MU0`](#mu0-opcode-408)        |
| [`$A0`](#a0-opcode--1)              | [`$G`](#g-opcode-10)            | [`$N0`](#n0-opcode-19)           |
| [`$ALPHA`](#alpha-opcode-2)         | [`$GAS`](#gas-opcode-11)        | [`$NA`](#na-opcode-20)           |
| [`$AMU`](#amu-opcode-3)             | [`$GN`](#gas-opcode-11)         | [`$P0`](#p0-opcode-21)           |
| [`$ATM`](#atm-opcode-405)           | [`$H`](#h-opcode-12)            | [`$PI`](#pi-opcode-22)           |
| [`$C`](#c-opcode-4)                 | [`$HBAR`](#hbar-opcode-13)      | [`$QE`](#qe-opcode-23)           |
| [`$CAL`](#cal-opcode-5)             | [`$I`](#i-opcode-14)            | [`$RE`](#re-opcode-24)           |
| [`$DEGREE`](#degree-opcode-6)       | [`$K`](#k-opcode-15)            | [`$RYDBERG`](#rydberg-opcode-26) |
| [`$EPSILON0`](#epsilon0-opcode-406) | [`$ME`](#me-opcode-16)          | [`$T0`](#t0-opcode-27)           |
| [`$EV`](#ev-opcode-7)               | [`$MP`](#mp-opcode-18)          | [`$TORR`](#torr-opcode-28)       |


|Other Special Constants beginning with `$`|||
|-|-|-|
| [`$DEFAULT`](#default-opcode-386)   | [`$NARG`](#narg-opcode-373)         | [`$THIS`](#this-opcode-403)         |
| [`$EXPT`](#expt-opcode-387)         | [`$ROPRAND`](#roprand-opcode-25)    | [`$TRUE`](#true-opcode-29)          |
| [`$FALSE`](#false-opcode-8)         | [`$SHOT`](#shot-opcode-388)         | [`$VALUE`](#value-opcode-30)        |
| [`$MISSING`](#missing-opcode-17)    | [`$SHOTNAME`](#shotname-opcode-444) ||





## Builtins

|A|||||
|-|-|-|-|-|
|ABORT      | ACOSD   | ALLOCATED| ARG_OF | ATAN2D  |
|ABS        | ADD     | AND      | ARRAY  | ATAND   |
|ABS1       | ADJUSTL | AND_NOT  | ASIN   | ATANH   |
|ABSSQ      | ADJUSTR | ANINT    | ASIND  | AXIS_OF |
|ACCUMULATE | AIMAG   | ANY      | AS_IS  |         |
|ACHAR      | AINT    | ARG      | ATAN   |         |
|ACOS       | ALL     | ARGD     | ATAN2  |         |




|B||||
|-|-|-|-|
| BEGIN_OF        |BUILD_CONGLOM   |BUILD_PARAM    |BUILD_WINDOW    |
| BIT_SIZE        |BUILD_DEPENDENCY|BUILD_PATH     |BUILD_WITH_ERROR|
| BREAK           |BUILD_DIM       |BUILD_PROCEDURE|BUILD_WITH_UNITS|
| BSEARCH         |BUILD_DISPATCH  |BUILD_PROGRAM  |BUILTIN_OPCODE  |
| BTEST           |BUILD_EVENT     |BUILD_RANGE    |BYTE            |
| BUILD_ACTION    |BUILD_FUNCTION  |BUILD_ROUTINE  |BYTE_UNSIGNED   |
| BUILD_CALL      |BUILD_METHOD    |BUILD_SIGNAL   |
| BUILD_CONDITION |BUILD_OPAQUE    |BUILD_SLOPE    |



|C||||
|-|-|-|-|
|CASE|COMMA|CONDITION_OF|COUNT|
|CEILING|COMPILE|CONJG|CULL|
|CHAR|COMPLETION_MESSAGE_OF|CONTINUE|CVT|
|CLASS|COMPLETION_OF|COS|
|CLASS_OF|CONCAT|COSD|
|CMPLX|CONDITIONAL|COSH|


|D|||||
|-|-|-|-|-|
|DATA|DECOMPILE|DIM|DO_TASK|D_COMPLEX|
|DATA_WITH_UNITS|DECOMPRESS|DIM_OF|DPROD|D_FLOAT|
|DATE_TIME|DEFAULT|DISPATCH_OF|DSCPTR|
|DBLE|DESCR|DIVIDE|DSCPTR_OF|
|DEALLOCATE|DIAGONAL|DO|DSQL|
|DEBUG|DIGITS|DOT_PRODUCT|DTYPE_RANGE|

|E||||||
|-|-|-|-|-|-|
|ELBOUND|EPSILON|EQV|ESIZE|EXP|EXT_FUNCTION|
|ELEMENT|EQ|ERRORLOGS_OF|EUBOUND|EXPONENT|
|ELSE|EQUALS|ERROR_OF|EVALUATE|EXTEND|
|END_OF|EQUALS_FIRST|ESHAPE|EXECUTE|EXTRACT|


|F||||
|-|-|-|-|
|FCLOSE|FOPEN|FS_FLOAT|F_COMPLEX|
|FINITE|FOR|FTELL|F_FLOAT|
|FIRSTLOC|FRACTION|FT_COMPLEX|
|FIX_ROPRAND|FSEEK|FT_FLOAT|
|FLOOR|FS_COMPLEX|FUN|



|G|||
|-|-|-|
|GE|GOTO|G_FLOAT|
|GETDBI|GT|
|GETNCI|G_COMPLEX|


|H||||
|-|-|-|-|
|HELP_OF|HUGE|H_COMPLEX|H_FLOAT|

|I|||||
|-|-|-|-|-|
|IACHAR|IDENT_OF|IN|INOT|IOR_NOT|
|IAND|IEOR|INAND|INOUT|ISHFT|
|IAND_NOT|IEOR_NOT|INAND_NOT|INT|I_TO_X|
|IBCLR|IF|INDEX|INTERRUPT_OF|
|IBSET|IF_ERROR|INOR|INT_UNSIGNED|
|ICHAR|IMAGE_OF|INOR_NOT|IOR|


|K||
|-|-|
|KIND|KIND_OF|


|L|||||
|-|-|-|-|-|
|LABEL|LE|LGT|LOG10|LONG_UNSIGNED|
|LANGUAGE_OF|LEN|LLE|LOG2|LT|
|LASTLOC|LEN_TRIM|LLT|LOGICAL|
|LBOUND|LGE|LOG|LONG|



|M|||||
|-|-|-|-|-|
|MAKE_ACTION|MAKE_FUNCTION|MAKE_ROUTINE|MAX|MIN|
|MAKE_CALL|MAKE_METHOD|MAKE_SIGNAL|MAXEXPONENT|MINEXPONENT|
|MAKE_CONDITION|MAKE_OPAQUE|MAKE_SLOPE|MAXLOC|MINLOC|
|MAKE_CONGLOM|MAKE_PARAM|MAKE_WINDOW|MAXVAL|MINVAL|
|MAKE_DEPENDENCY|MAKE_PROCEDURE|MAKE_WITH_ERROR|MEAN|MOD|
|MAKE_DIM|MAKE_PROGRAM|MAKE_WITH_UNITS|MERGE|MODEL_OF|
|MAKE_DISPATCH|MAKE_RANGE|MAP|METHOD_OF|MULTIPLY|





|N||||||
|-|-|-|-|-|-|
|NAME_OF|NAND_NOT|NDESC_OF|NEQV|NOR|NOT|
|NAND|NDESC|NE|NINT|NOR_NOT|




|O|||
|-|-|-|
|OBJECT_OF|OPCODE_BUILTIN|OR|
|OCTAWORD|OPCODE_STRING|OR_NOT|
|OCTAWORD_UNSIGNED|OPTIONAL|OUT|


|P|||
|-|-|-|
|PACK|POWER|PRIVATE|
|PERFORMANCE_OF|PRECISION|PROCEDURE_OF|
|PHASE_OF|PRESENT|PRODUCT|
|POST_DEC|PRE_DEC|PROGRAM_OF|
|POST_INC|PRE_INC|PUBLIC|


|Q|||
|-|-|-|
|QUADWORD|QUADWORD_UNSIGNED|QUALIFIERS_OF|

|R|||||
|-|-|-|-|-|
|RADIX|RANK|REM|RESET_PUBLIC|
|RAMP|RAW_OF|REPEAT|RETURN|
|RANDOM|REAL|REPLICATE|ROUTINE_OF|
|RANGE|REF|RESET_PRIVATE|RRSPACING|

|S|||||||
|-|-|-|-|-|-|-|
|SCALE|SET_RANGE|SHOW_PUBLIC|SINH|SORTVAL|SQUARE|SUM
|SCAN|SHAPE|SHOW_VM|SIZE|SPACING|STATEMENT|SWITCH
|SELECTED_INT_KIND|SHIFT_LEFT|SIGNED|SIZEOF|SPAWN|STRING_OPCODE|
|SELECTED_REAL_KIND|SHIFT_RIGHT|SIN|SLOPE_OF|SPREAD|SUBSCRIPT|
|SET_EXPONENT|SHOW_PRIVATE|SIND|SORT|SQRT|SUBTRACT|


|T|||
|-|-|-|
|TAN|TASK_OF|TINY|
|TAND|TEXT|TRANSLATE|
|TANH|TIME_OUT_OF|TRIM|


|U|||
|-|-|-|
|UBOUND|UNION|UNSIGNED
|UNARY_MINUS|UNITS|UPCASE
|UNARY_PLUS|UNITS_OF|USING


|V|||
|-|-|-|
|VAL|VALUE_OF|VERIFY|
|VALIDATION|VAR|
|VALIDATION_OF|VECTOR|


|W|||
|-|-|-|
|WAIT|WINDOW_OF|WRITE|
|WHEN_OF|WORD|
|WHILE|WORD_UNSIGNED|


|X||
|-|-|
|XD|X_TO_I|


|Z|
|-|
|ZERO|

## Constants

### `$2PI` (Two Pi)

|||
|-|-|
|TDI Syntax   | `$2PI`|
|Python Syntax| `MDSplus.d2PI()`|
|Java mdsplus-api Syntax| `CONST.d2Pi()` |
|Opcode       | 372 (0x174)|

Two times π

```tdi
TDI> $2pi
6.283185307179586D0
```

### `$A0` (Bohr Radius)

|||
|-|-|
| TDI Syntax | `$A0` |
| Python Syntax | `MDSplus.dA0()` |
| Java mdsplus-api Syntax | `CONST.dA0()` |
|Opcode       | 1 (0x01)|

The Bohr radius constant (a<sub>0</sub>): 52.9177 x 10<sup>-12</sup> m, with an error of 1168.02 x 10<sup>-21</sup>

```tdi
TDI> $a0
Build_With_Units(Build_With_Error(52.9177E-12, 1168.02E-21), "m")
```

### `$ALPHA` (Fine-Structure Constant)

|||
|-|-|
| TDI syntax| `$ALPHA`|
| Python Syntax| `MDSplus.dALPHA()`|
|Java mdsplus-api Syntax| `CONST.dAlpha()`|
|Opcode       | 2 (0x02)|

The Fine-Structure Constant (α): 0.00729735, with an error of 143.276 x 10<sup>-12</sup>

```tdi
TDI> $alpha
Build_With_Error(.00729735, 143.276E-12)
```

### `$AMU` (Atomic Mass Unit)

|||
|-|-|
|TDI syntax| `$AMU`|
|Python Syntax | `MDSplus.dAMU()`|
|Java mdsplus-api Syntax| `CONST.dAmu()` |
|Opcode       | 3 (0x03)|

One unified atomic mass unit (Da or u): 1660.54 x 10<sup>-30</sup> kg, with an error of 43.0666 x 10<sup>-36</sup>

```tdi
TDI> $amu
Build_With_Units(Build_With_Error(1660.54E-30, 43.0666E-36), "kg")
```

### `$ATM` (Atmospheric Pressure Constant)

|||
|-|-|
|TDI Syntax   | `$ATM`|
|Python Syntax| `MDSplus.dATM()`|
|Java mdsplus-api Syntax| `CONST.dAtm()` |
|Opcode       | 405 (0x195)|

The atmospheric pressure constant: 101325.0 Pa
Alias of `$P0`

```tdi
TDI> $atm
Build_With_Units(101325., "Pa")
```

### `$C` (Speed of Light Constant)

|||
|-|-|
|TDI Syntax   | `$C`|
|Python Syntax| `MDSplus.dC()`|
|Java mdsplus-api Syntax| `CONST.dC()` |
|Opcode|4 (0x04)|

The speed of light (c): 299792458.0 m/s

```tdi
TDI> $c
Build_With_Units(299792458D0, "m/s")
```

### `$CAL` (Calorie)

|||
|-|-|
|TDI Syntax   | `$CAL`|
|Python Syntax| `MDSplus.dCAL()` |
|Java mdsplus-api Syntax| `CONST.dCal()`|
|Opcode|5 (0x05)|

One calorie: 4.1868 J

```tdi
TDI> $cal
Build_With_Units(4.1868, "J")
```

### `$DEGREE` (Degrees to Radians)

|||
|-|-|
|TDI Syntax   | `$DEGREE` |
|Python Syntax| `MDSplus.dDEGREE()` |
|Java mdsplus-api Syntax| `CONST.dDegree()`|
|Opcode|6 (0x06)|

One degree: (pi/180) or 0.0174532925199433 radians.
Used for converting from degrees into radians

```tdi
TDI> $degree
.0174532925199433D0

TDI> 180 * $degree
3.141592653589793D0
```

### `$EPSILON0` (Vacuum Permittivity Constant)

|||
|-|-|
|TDI Syntax   | `$EPSILON0` |
|Python Syntax| `MDSplus.dEPSILON0()` |
|Java mdsplus-api Syntax| `CONST.dEpsilon0()`|
|Opcode|406 (0x196)|

The vacuum permittivity constant (ε<sub>0</sub>): 8854.187817620389 x 10<sup>-15</sup> F/m

```tdi
TDI> $epsilon0
Build_With_Units(8854.187817620389D-15, "F/m")
```

### `$EV` (Electron-Volt)

|||
|-|-|
|TDI Syntax   | `$EV` |
|Python Syntax| `MDSplus.dEV()` |
|Java mdsplus-api Syntax| `CONST.dEv()`|
|Opcode|7 (0x07)|

One Electron-volt (eV): 160.218 x 10<sup>-21</sup> J/eV, with an error of 3654.14 x 10<sup>-30</sup>
> TODO: Change units to just "J"

```tdi
TDI> $ev
Build_With_Units(Build_With_Error(160.218E-21, 3654.14E-30), "J/eV")
```

### `$FARADAY` (Faraday Constant)
|||
|-|-|
|TDI Syntax   | `$FARADAY` |
|Python Syntax| `MDSplus.dFARADAY()` |
|Java mdsplus-api Syntax| `CONST.dFaraday()`|
|Opcode|9 (0x09)|

The Faraday constant (F): 96485.3 C/mol, with an error of .00381419

```tdi
TDI> $faraday
Build_With_Units(Build_With_Error(96485.3, .00381419), "C/mol")
```

### `$G` (Gravitational Constant)
|||
|-|-|
|TDI Syntax   | `$G` |
|Python Syntax| `MDSplus.dG()` |
|Java mdsplus-api Syntax| `CONST.dG()`|
|Opcode|10 (0x0A)|

The gravitational constant (G): 66.743 x 10<sup>-12</sup> m<sup>3</sup>/s<sup>2</sup>/kg, with an error of 1500.02 x 10<sup>-18</sup>

```tdi
TDI> $g
Build_With_Units(Build_With_Error(66.743E-12, 1500.02E-18), "m^3/s^2/kg")
```

### `$GAS` (Ideal Gas Constant)
|||
|-|-|
|TDI Syntax   | `$GAS` |
|Python Syntax| `MDSplus.dGAS()` |
|Java mdsplus-api Syntax| `CONST.dGas()`|
|Opcode|11 (0x0B)|

The ideal gas constant: 8.31446 J/K/mol, with an error of 43.5899 x 10<sup>9</sup>

```tdi
TDI> $gas
Build_With_Units(Build_With_Error(8.31446, 43.5899E-9), "J/K/mol")
```

### `$GN` (Gravity Acceleration Constant)

|||
|-|-|
|TDI Syntax   | `$GN` |
|Python Syntax| `MDSplus.dGN()` |
|Java mdsplus-api Syntax| `CONST.dGn()`|
|Opcode|407 (0x197)|

The acceleration of gravity: 9.80665 m/s<sup>2</sup>

```tdi
TDI> $gn
Build_With_Units(9.80665, "m/s^2")
```

### `$H` (Planck Constant)

|||
|-|-|
|TDI Syntax   | `$H` |
|Python Syntax| `MDSplus.dH()` |
|Java mdsplus-api Syntax| `CONST.dH()`|
|Opcode|12 (0x0C)|

The Planck constant: 662.607 x 10<sup>36</sup> J*s, with an error of 2857.25 x 10<sup>45</sup>

```tdi
TDI> $h
Build_With_Units(Build_With_Error(662.607E-36, 2857.25E-45), "J*s")
```

### `$HBAR` (Reduced Planck Constant)

|||
|-|-|
|TDI Syntax   | `$HBAR` |
|Python Syntax| `MDSplus.dHBAR()` |
|Java mdsplus-api Syntax| `CONST.dHbar()`|
|Opcode|13 (0x0D)|

The reduced Planck constant (H/2pi or <span style="text-decoration: overline">H</span>): 105.457 x 10<sup>36</sup> J*s, with an error of 1967.42 x 10<sup>45</sup>

```tdi
TDI> $hbar
Build_With_Units(Build_With_Error(105.457E-36, 1967.42E-45), "J*s")
```

### `$I` (Imaginary)

|||
|-|-|
|TDI Syntax   | `$I` |
|Python Syntax| `MDSplus.dI()` |
|Java mdsplus-api Syntax| `CONST.dI()`|
|Opcode|14 (0x0E)|

Imaginary (i): `Cmplx(0.0, 1.0)`

```tdi
TDI> $i
Cmplx(0.,1.)
```

### `$K` (Boltzmann Constant)

|||
|-|-|
|TDI Syntax   | `$K` |
|Python Syntax| `MDSplus.dK()` |
|Java mdsplus-api Syntax| `CONST.dK()`|
|Opcode|15 (0x0F)|

The Boltzmann constant: 13.8065 x 10<sup>24</sup> J/K, with an error of 276.341 x 10<sup>33</sup>

```tdi
TDI> $k
Build_With_Units(Build_With_Error(13.8065E-24, 276.341E-33), "J/K")
```

### `$ME` (Electron Mass)

|||
|-|-|
|TDI Syntax   | `$ME` |
|Python Syntax| `MDSplus.dME()` |
|Java mdsplus-api Syntax| `CONST.dMe()`|
|Opcode|16 (0x10)|

The mass of an electron (m<sub>e</sub>): 910.938 x 10<sup>33</sup> kg, with an error of 25.8874 x 10<sup>39</sup>

```tdi
TDI> $me
Build_With_Units(Build_With_Error(910.938E-33, 25.8874E-39), "kg")
```

### `$MP` (Proton Mass)

|||
|-|-|
|TDI Syntax   | `$MP` |
|Python Syntax| `MDSplus.dMP()` |
|Java mdsplus-api Syntax| `CONST.dMp()`|
|Opcode|18 (0x12)|

The mass of a proton (p): 1672.62 x 10<sup>30</sup> kg, with an error of 85.2717 x 10<sup>36</sup>

```tdi
TDI> $mp
Build_With_Units(Build_With_Error(1672.62E-30, 85.2717E-36), "kg")
```

### `$MU0` (Vacuum Permeability)

|||
|-|-|
|TDI Syntax   | `$MU0` |
|Python Syntax| `MDSplus.dMU0()` |
|Java mdsplus-api Syntax| `CONST.dMu0()`|
|Opcode|408 (0x198)|

The permeability of a vacuum (μ<sub>0</sub>): 1256.637061435917 x 10<sup>-9</sup> N/A<sup>2</sup>

```tdi
TDI> $mu0
Build_With_Units(1256.637061435917D-9, "N/A^2")
```

### `$N0` (Loschmidt's Number)

|||
|-|-|
|TDI Syntax   | `$N0` |
|Python Syntax| `MDSplus.dN0()` |
|Java mdsplus-api Syntax| `CONST.dN0()`|
|Opcode|19 (0x13)|

Loschmidt's number (n<sub>0</sub>): 26.8678 x 10<sup>24</sup> /m<sup>3</sup>, with an error of 743.623 x 10<sup>15</sup>
> TODO: Verify units should start with /

```tdi
TDI> $n0
Build_With_Units(Build_With_Error(26.8678E24, 743.623E15), "/m^3")
```

### `$NA` (Avogadro's Number)

|||
|-|-|
|TDI Syntax   | `$NA` |
|Python Syntax| `MDSplus.dNA()` |
|Java mdsplus-api Syntax| `CONST.dNa()`|
|Opcode|20 (0x14)|

Avogadro's number (N<sub>A</sub>): 602.214 x 10<sup>21</sup> /mol, with an error of 11.645 x 10<sup>15</sup>
> TODO: Verify units should start with /

```tdi
TDI> $na
Build_With_Units(Build_With_Error(602.214E21, 11.645E15), "/mol")
```

### `$P0` (Atmospheric Pressure Constant)
|||
|-|-|
|TDI Syntax   | `$P0` |
|Python Syntax| `MDSplus.dP0()` |
|Java mdsplus-api Syntax| `CONST.dP0()`|
|Opcode|21 (0x15)|

Atmospheric pressure: 101325. Pa
Alias of `$ATM`

```tdi
TDI> $p0
Build_With_Units(101325., "Pa")
```

### `$PI` (Pi)

|||
|-|-|
|TDI Syntax   | `$PI` |
|Python Syntax| `MDSplus.dPI()` |
|Java mdsplus-api Syntax| `CONST.dPi()`|
|Opcode|22 (hex(0x16)|

Pi, the circumference divided by the radius (π): 3.141592653589793

```tdi
TDI> $pi
3.141592653589793D0
```

### `$QE` (Elementary Charge)

|||
|-|-|
|TDI Syntax   | `$QE` |
|Python Syntax| `MDSplus.dQE()` |
|Java mdsplus-api Syntax| `CONST.dQe()`|
|Opcode|23|

The negative charge of an electron (e): 160.218 x 10<sup>21</sup> C, with an error of 3654.14 x 10<sup>30</sup>

```tdi
TDI> $qe
Build_With_Units(Build_With_Error(160.218E-21, 3654.14E-30), "C")
```

### `$RE` (Classical Electron Radius)

|||
|-|-|
|TDI Syntax   | `$RE` |
|Python Syntax| `MDSplus.dRE()` |
|Java mdsplus-api Syntax| `CONST.dRe()`|
|Opcode|24|

The classical electron radius: 2817.94 x 10<sup>18</sup> m, with an error of 12.7156 x 10<sup>24</sup>

```tdi
TDI> $re
Build_With_Units(Build_With_Error(2817.94E-18, 12.7156E-24), "m")
```

### `$RYDBERG` (Rydberg Constant)

|||
|-|-|
|TDI Syntax   | `$RYDBERG` |
|Python Syntax| `MDSplus.dRYDBERG()` |
|Java mdsplus-api Syntax| `CONST.dRydberg()`|
|Opcode|26|

The Rydberg constant: 10.9737 x 10<sup>6</sup> /m, with an error of 0.443876
> TODO: Verify units should start with /

```tdi
TDI> $rydberg
Build_With_Units(Build_With_Error(10.9737E6, .443876), "/m")
```

### `$T0` (Standard Temperature Constant)

|||
|-|-|
|TDI Syntax   | `$T0` |
|Python Syntax| `MDSplus.$T0` |
|Java mdsplus-api Syntax| `CONST.dT0()`|
|Opcode|27|

THe standard temperature constant: 273.15 K

```tdi
TDI> $t0
Build_With_Units(273.15, "K")
```

### `$TORR` (Torr)

|||
|-|-|
|TDI Syntax   | `$TORR` |
|Python Syntax| `MDSplus.dTORR()` |
|Java mdsplus-api Syntax| `CONST.dTorr()`|
|Opcode|28|

One Torr (approximately 1mmHg pressure): 133.3223684210526 Pa

```tdi
TDI> $torr
Build_With_Units(133.3223684210526D0, "Pa")
```


## Special Variables

### `$DEFAULT` (Default Node Path)

|||
|-|-|
|TDI Syntax   | `$DEFAULT` |
|Python Syntax| `MDSplus.dDEFAULT()` |
|Java mdsplus-api Syntax| `CONST.dDefault()`|
|Opcode|386|

The path to the current default tree node.

Same as `getdbi('DEFAULT')`.

```tdi
# With a tree open
TDI> $default
"\\MAIN::TOP"

# Without a tree open
TDI> $default
%TDI Error in $DEFAULT()
%TDI Error in EXECUTE("$DEFAULT")
```

See also
* `GETDBI()`

### `$EXPT` (Tree/Experiment Name)

|||
|-|-|
|TDI Syntax   | `$EXPT` |
|Python Syntax| `MDSplus.dEXPT()` |
|Java mdsplus-api Syntax| `CONST.dExpt()`|
|Opcode|387|

The name of the current tree.

Same as `getdbi('NAME')`.

```tdi
# With a tree open
TDI> $expt
"MAIN"

# Without a tree open
TDI> $expt
%TDI Error in $EXPT()
%TDI Error in EXECUTE("$EXPT")
```

See also:
* `GETDBI()`

### `$FALSE` (False Constant)

|||
|-|-|
|TDI Syntax   | `$FALSE` |
|Python Syntax| `MDSplus.dFALSE()` |
|Java mdsplus-api Syntax| `CONST.dFalse()`|
|Opcode|8|

Boolean constant for false: 0BU

Note: Any expression that returns `$false` will display as 0BU

```tdi
TDI> $false
0BU

TDI> 1 == 2
0BU
```

See also:
* `$TRUE`

### `$MISSING` (Missing Value/Argument, Null)

|||
|-|-|
|TDI Syntax   | `$MISSING` |
|Python Syntax| `MDSplus.dMISSING()` |
|Java mdsplus-api Syntax| `CONST.dMissing()`|
|Opcode|17|

Indicates a missing value (or argument), equivalent to `null` in other languages.

> TODO: More examples?
```tdi
TDI>
$Missing
```

See also:
* `$ROPERAND`

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

### `$ROPRAND` (NaN, Infinity, Reserved Operand)

|||
|-|-|
|TDI Syntax   | `$ROPRAND` |
|Python Syntax| `MDSplus.dROPRAND()` |
|Java mdsplus-api Syntax| `CONST.dRoprand()`|
|Opcode       | 25 (0x19)|

Represents NaN or Infinity from floating point math.

```tdi
TDI> 1.0 / 0.0
$ROPRAND
```

### `$SHOT` (Current Shot Number)
|Opcode|388|
|||
|-|-|
|TDI Syntax   | `$SHOT` |
|Python Syntax| `MDSplus.dSHOT()` |
|Java mdsplus-api Syntax| `CONST.dShot()`|

The shot number of the current tree.

Same as `getdbi('shot')` or `getdbi('shotid')`.

```tdi
# With a tree open
TDI> $shot
12345

# With a model tree open
TDI> $shot
-1

# Without a tree open
TDI> $shot
%TDI Error in $SHOT()
%TDI Error in EXECUTE("$shot")
```

See also:
* `$SHOTNAME`
* `GETDBI()`

### `$SHOTNAME` (Current Shot Number String)

|||
|-|-|
|TDI Syntax   | `$SHOTNAME` |
|Python Syntax| `MDSplus.dshotname` |
|Java mdsplus-api Syntax| `CONST.dShotname()`|
|Opcode|444|

The shot number of the current tree as a string, or "MODEL" for shot -1.

```tdi
# With a tree open
TDI> $shotname
"12345"

# With a model tree open
TDI> $shotname
"MODEL"

# Without a tree open
TDI> $shotname
%TDI Error in $SHOTNAME()
%TDI Error in EXECUTE("$shotname")
```

See also:
* `$SHOT`

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
* `$VALUE`
* `RAW_OF()`
* `DIM_OF()`
* `VALUE_OF()`
* `HELP_OF()`

### `$TRUE` (T)

|||
|-|-|
|TDI Syntax   | `$TRUE` |
|Python Syntax| `MDSplus.dTRUE()` |
|Java mdsplus-api Syntax| `CONST.dTrue()`|
|Opcode|29|

Boolean constant for true: 0BU

Note: Any expression that returns `$true` will display as 1BU

```tdi
TDI> $false
1BU

TDI> 1 == 1
1BU
```

See also `$FALSE`.

### `$VALUE` (Current Structure Value)
|Opcode|30|
|||
|-|-|
|TDI Syntax   | `$VALUE` |
|Python Syntax| `MDSplus.dvalue` |
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
* `$THIS`
* `RAW_OF()`
* `VALUE_OF()`


## Built-in Functions

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

### `ABS` (Absolute Value)

|||
|-|-|
|TDI Syntax   | `ABS(_X)` |
|Python Syntax| `MDSplus.ABS(_x)` |
|Opcode       | 32 (0x20)|

Returns the absolute value of `_X`.

`_X` must be numeric, and can be a scalar, array, or `Signal`. If `_X` is an array or `Signal`, the shape will be preserved.

If `_X` contains complex numbers, the result will be the square root of the sum of the squares of the real and imaginary parts. The real and imaginary parts will be scaled to avoid overflow.

Note: `BUILD_WITH_UNITS()` will be preserved.  
Note: `BUILD_WITH_ERROR()` will be discarded.

```tdi
TDI> abs(-2)
2

TDI> abs(cmplx(-3.0, 4.0))
5.

TDI> abs([-1, 2, -3, 4])
[1,2,3,4]

TDI> abs([[-1, 2], [-3, 4]])
[[1,2], [3,4]]

TDI> abs(make_signal([-1, 2, -3], *))
Build_Signal([1,2,3], *)

TDI> abs(make_signal([[-1, 2], [-3, 4]], *))
Build_Signal([[1,2], [3,4]], *)
```

See also:
* `ABS1()` and `ABSSQ()` to avoid the square root for for complex numbers


### `ABS1` 

|Syntax||
|-|-|
|TDI Syntax   | `ABS1(_NUM)` |
|Python Syntax| `MDSplus.ABS1(_NUM)` |
|Opcode|33|

Absolute value with L1 norm. Complex numbers result in the sum of the absolute values of the real and imaginary parts; otherwise, this function has the same behavior as `abs()`.

Example

```
TDI> abs1(cmplx(3.0,-4.0))
7.0
```

See also: `abs()`


### `ABSSQ` 
|Syntax||
|-|-|
|TDI Syntax   | `ABSSQ(_NUM)` |
|Python Syntax| `MDSplus.ABSSQ(_NUM)` |
|Opcode|34|

Absolute value squared.
* Units are same as for `a*a`.
* If arguments are complex, the result is a real number
* Numbers may lose significance.
* Integers and reals are squared
* Complex numbers become the sums of the squares of the real and imaginary parts.

Examples

```TDI
TDI> abssq(cmplx(3.0,4.0))
25.0

TDI> abssq([[-1,2],[-3,4]])
[[1,4], [9,16]]
```



### `ACCUMULATE`
|Syntax||
|-|-|
|TDI Syntax   | `ACCUMULATE(_ARRAY, [_DIM], [_MASK])` |
|Python Syntax| `MDSplus.ACCUMULATE(_ARRAY, [_DIM], [_MASK])` |
|Min arguments| 1 |
|Max arguments| 3 |
|Opcode|439|

> TODO: come back to this definition; needs fine-tuning. replace "mask" with "condition"? 

Running sum of all the elements of `_ARRAY` along dimension `_DIM` corresponding to the true elements of `_MASK`. The result is the running sum of the elements of `_ARRAY`, using only those with true `_MASK` values and value not equal to the reserved operand ($ROPRAND). With `_DIM`, the value of an element of the result is the running sum of the ARRAY elements with dimension `_DIM` fixed as the element number of the result. Without `_DIM`, the result is the sum from the first element ignoring the shape. If no value is found, 0 is given.

* `_ARRAY` numeric array.
* (optional) [`_DIM`] integer scalar from 0 to n-1, where n is rank of ARRAY.
* (optional) [`_MASK`] logical and conformable to ARRAY.
* Can also accept signals, units

Examples

```TDI
# Simple
TDI> accumulate([1,2,3])
[1,3,6]

# Conditional
_C = [1, -2, -3, 4, 5]

TDI> `accumulate(_C,,_C > 0)
[1,-2,-3,5,10]

# This will find the running sum of all positive elements of `C`
TDI> accumulate(_C,,_C GT 0)

# Dimensional
_B = [[1,3,5], [2,4,6]]

TDI> accumulate(_B)
[[1,4,9], [11,15,21]]

TDI> accumulate(_B, 0)
[[1,4,9], [2,6,12]]

TDI> accumulate(_B, 1)
[[1,3,5], [3,7,11]]
```


### `ACHAR` 
|Syntax||
|-|-|
|TDI Syntax   | `ACHAR(_I, [_KIND])` |
|Python Syntax| `MDSplus.ACHAR(i, [kind])` |
|Min arguments| 1 |
|Max arguments| 2 |
|Opcode|35|

Converts the number, array, or signal `_I` into the equivalent ASCII character. 
Optional `_KIND` (see [kind](todo:link)).

Examples:

```tdi
TDI> achar(67)
C

TDI> achar([72, 101, 108, 108, 111])
["H","e","l","l","o"]
```

See also:

* `CHAR` and its inverse `ICHAR` for a processor-dependent.|
* `KIND`


### `ACOS`
|Syntax||
|-|-|
|TDI Syntax   | `ACOS(_NUM)` |
|Python Syntax| `MDSplus.ACOS(_NUM)` |
|Opcode|36|

Arccosine (inverse cosine) in radians; Processor approximation.

Arguments
* Argument must be real and be less than 1 in magnitude. Complex numbers cause error.
* Units are ignored
* Results are in the range 0 to pi, inclusive.
* Out-of-range numbers return `$ROPRAND`.  


Examples

```tdi
TDI> acos(.9)
.451027

TDI> acos($epsilon0)
Build_With_Units(1.570796326786043D0, "?")

TDI> acos([.2, .3, .4, .5])
[1.36944,1.2661,1.15928,1.0472]

TDI> acos(0.54030231)
1

_Signal = Build_Signal([1,.5,.25], *, Build_Dim(*, [-1,0,1]))

TDI> acos(_Signal)
Build_Signal([0.,1.0472,1.31812], *, Build_Dim(*, [-1,0,1]))
```


### `ACOSD`
|Syntax||
|-|-|
|TDI Syntax   | `ACOSD(arg0)` |
|Python Syntax| `MDSplus.ACOSD(arg0)` |
|Opcode|37|

Arccosine (inverse cosine) in degrees; Processor approximation.

Arguments
* Argument must be real and be less than 1 in magnitude. Complex numbers cause an error.
* Units are ignored
* Results in the range 0 to 180.
* Out-of-range numbers get $ROPRAND.

Examples

```tdi
TDI> acosd(0.54030231)
57.2958

_Signal = Build_Signal([1,.5,.25], *, Build_Dim(*, [-1,0,1]))

TDI> acosd(_Signal)
Build_Signal([0.,60.,75.5225], *, Build_Dim(*, [-1,0,1]))
```


### `ADD` 

|Syntax||
|-|-|
|TDI Syntax| `_NUM1 + _NUM2` or `add(_NUM1, _NUM2)`|
|Python Syntax| `MDSplus.add(_NUM1, _NUM2)`|
|Opcode|38|

Adds two numbers.

* Arguments must be numeric.
* Integer overflow is ignored.
* Ensure that arrays are the same length, otherwise, the function will truncate to the shorter one.
* Signals are treated like arrays, and dimensions are ignored.

Examples

```
TDI> add(3,4)
7

TDI> [2,3,4] + 5.0
[7.0,8.0,9.0]

TDI> add(cmplx(3,4),5)
Cmplx(8.,4.)

TDI> add(cmplx(3,4),cmplx(5,6))
Cmplx(8.,10.)

TDI> add([1,2],[3,4])
[4,6]

TDI> add([1,2,3,4],[5,6])
[6,8]

_Signal0 = Build_Signal([1,2,3], *, Build_Dim(*, [-1,0,1]))
_Signal1 = Build_Signal([3,4,5], *, Build_Dim(*, [0,1,2]))

TDI> add(_Signal0, _Signal1)
[4,6,8]
```




### `ADJUSTL` (Adjust to the Left)
|Syntax||
|-|-|
|TDI Syntax   | `ADJUSTL(_STRING)` |
|Python Syntax| `MDSplus.ADJUSTL(_STRING)` |
|Opcode|39|

Adjust to the left, removing leading whitespace and inserting the same number of trailing spaces instead. Any input is treated as a string. Consumed TAB characters only count as a single space.



Examples

```tdi
TDI> adjustl("  word  ")
"word    "

TDI> adjustr("  word  ")
"    word"

# Note: Leading TAB characters will be replaced with spaces at the end
TDI> adjustl("\tword\t")
"word\t "
```

See also:
* `adjustr`
* `TRIM` (non-elemental) to remove trailing blanks and tabs.


### `ADJUSTR` 
|Syntax||
|-|-|
|TDI Syntax   | `ADJUSTR(_STRING)` |
|Python Syntax| `MDSplus.ADJUSTR(_STRING)` |
|Opcode|40|

Adjust to the right, removing trailing whitespace and inserting the same number of leading blanks instead. Any input is treated as a string. Consumed TAB characters only count as a single space.

Examples

```tdi
TDI> adjustl("  word  ")
"word    "

TDI> adjustr("  word  ")
"    word"

# Note: Trailing TAB characters will be replaced with spaces at the beginning
TDI> adjustr("\tword\t")
" \tword"
```

See also:
* `adjustl`
* `TRIM` (non-elemental) to remove trailing blanks and tabs.


### `AIMAG` (Imaginary part of a complex number)
|Syntax||
|-|-|
|TDI Syntax   | `AIMAG(_NUM)` |
|Python Syntax| `MDSplus.AIMAG(_NUM)` |
|Opcode|41|


Returns the imaginary part of a complex number, in the same shape as the input.

Examples
```tdi
TDI> aimag(cmplx(3,4))
4

_IArray = [cmplx(1,2),cmplx(3,4), cmplx(5,6)]

TDI> aimag(_IArray)
[2.,4.,6.]

_IArray2 = [[cmplx(1,2),cmplx(3,4)], [cmplx(5,6), cmplx(7,8)]]

TDI> aimag(_IArray2)
[[2.,4.], [6.,8.]]
```


### `AINT` 
|Syntax||
|-|-|
|TDI Syntax   | `AINT(_NUM, [_KIND])` |
|Python Syntax| `MDSplus.AINT(_NUM, [_KIND])` |
|Opcode|42|


Truncates a real number to a whole number.
* Note: this function only removes numbers after the decimal point; it does not round.

Arguments
* `_NUM` must be real. Complex numbers result in error.
* [_KIND] (optional): Type is `KIND` if it is present, else that of `_NUM`. Scalar integer type number, for example, KIND(1d0).


Examples

```tdi
TDI> aint(-4.5)
-4

TDI> aint($PI)
3D0

TDI> aint(0.999)
0
```

See also:
* `int` for integer result and `byte`, `word`, `long`, `quadword`, `octaword`, and `unsigned_byte`, etc., for specific forms. 
* `anint` and `nint` for rounded integral value.
* `floor` and `ceiling`.


### `ALL` 
|Syntax||
|-|-|
|TDI Syntax   | `ALL(_MASK, [_DIM])` |
|Python Syntax| `MDSplus.ALL(_MASK, [_DIM])` |
|Opcode|43|

Determine if all values are true in `_MASK` along dimension `_DIM`.

Arguments 
* `_MASK`: a logical array.
* [_DIM] optional: integer scalar from 0 to n-1, where n is rank of `_MASK`.

Results
* `ALL(_MASK)` returns `$TRUE` if all elements of `_MASK` are true or if MASK has size zero
* `ALL(_MASK)` returns `$FALSE` if any element of `_MASK` is false.
* For a vector MASK, `ALL(_MASK, _DIM)` is equal to `ALL(_MASK)`. Otherwise, the value of an element of the result is `ALL()` of the elements of `_MASK` varying the `_DIM` subscript.

Examples

```tdi
TDI> ALL([$TRUE,$FALSE,$TRUE])
$FALSE


_B=[[1, 3, 5],[2, 4, 6]]
_C=[[0, 3, 5],[2, 4, 6],[7, 4, 8]]

TDI> ALL(_B NE _C,0)
[$FALSE,$FALSE,$FALSE]

TDI> ALL(_B NE _C,1)
[$FALSE,$FALSE]
```

See also:
* `ANY` for logical. 
* `COUNT` for the number of trues.



### `ALLOCATED`
|Syntax||
|-|-|
|TDI Syntax   | `ALLOCATED(_STRING)` |
|Python Syntax| `MDSplus.ALLOCATED(_STRING)` |
|Opcode|44|

Returns `$TRUE` if a variable has been declared and is populated, else, returns `$FALSE`.
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


### `AND` 
|Syntax||
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



### `AND_NOT`
|Syntax||
|-|-|
|TDI Syntax   | `AND_NOT(_BOOL0, _BOOL1)` |
|Python Syntax| `MDSplus.AND_NOT(_BOOL0, _BOOL1)` |
|Opcode|46|


Logical intersection with negation of second. Returns true if A is true and B is false; otherwise, false.

Examples

```tdi
TDI> and_not([0,0,1,1],[0,1,0,1])
[0BU,0BU,1BU,0BU]

TODO: Stephen

```

### `ANINT`
|Syntax||
|-|-|
|TDI Syntax   | `ANINT(_NUM, [_KIND])` |
|Python Syntax| `MDSplus.ANINT(_NUM, [_KIND])` |
|Opcode|47|

Rounds to the nearest whole number.
* `_NUM` Must be a real number; complex numbers result in error.
* [`_KIND`] Optional: KIND scalar integer type number, for example, KIND(1d0).
* Type is KIND if it is present, else that of A.

Examples
```tdi
TDI> ANINT(2.783)
3.0

TDI> ANINT(-2.783)
-3.0
```

See also: 
* `NINT` for integer
* `INT` and `AINT` for truncated results.


### `ANY` 
|Syntax||
|-|-|
|TDI Syntax   | `ANY(_MASK, [_DIM])` |
|Python Syntax| `MDSplus.ANY(_MASK, [_DIM])` |
|Opcode|48|

Matching function. Returns true if any element matches the condition described in the mask along the dimension. This can compare an array to a single element or two arrays to each other. Not providing a `_DIM` will flatten the array. `_DIM` must be an integer of n-1 of sub-arrays.

Examples
* With:   
`_arr1 = [[1, 2, 3], [4, 5, 6]]`  
`_arr2 = [[3, 2, 1], [6, 4, 5]]`

* `any(_arr1 == _arr2)`  
`1BU` aka `[$TRUE]`

* `any(_arr1 == _arr2,0)`  
`Byte_Unsigned([1,0])` aka `[[$TRUE], [$FALSE]]`

* `any(_arr1 == _arr2,1)`  
`Byte_Unsigned([0,1,0])` aka `[[$FALSE], [$TRUE], [$FALSE]]`

See also
* `ALL` for logical and
* `COUNT` for the number of trues.

TODO: Come back to the old examples
OLD EXAMPLES (these use != instead of ==)
* `ANY([$TRUE,$FALSE,$TRUE])` returns `$TRUE`.
* With `_B=[[1, 3, 5],[2, 4, 6]]` and  
`_C=[[0, 3, 5],[7, 4, 8]]`  
`ANY(_B NE _C)` returns `[$TRUE]`
`ANY(_B NE _C,0)` returns `[$TRUE,$TRUE]`.  
`ANY(_B NE _C,1)` returns `[$TRUE,$FALSE,$TRUE]`.





### `ARG` (Complex number to radians)
|Syntax||
|-|-|
|TDI Syntax   | `ARG(cmplx(_Real, _Imaginary))` |
|Python Syntax| `MDSplus.ARG(arg0)` |
|Opcode|49|

Argument of complex number in radians.
* Argument must be `cmplx()`.
* Calculates via `atan2(aimag(cmplx(_Real, _Imaginary)),real(cmplx(_Real, _Imaginary)))`.

Examples:
```tdi
TDI> arg(cmplx(3.0,4.0))
0.927295

_A = [cmplx(3,4), cmplx(1,1)]

TDI> arg(_A)
[.927295,.785398]
```

See also:
* `abs` for the complex length.


### `ARGD` (Complex number to degrees)
|Syntax||
|-|-|
|TDI Syntax   | `ARGD(cmplx(_Real, _Imaginary))` |
|Python Syntax| `MDSplus.ARGD(cmplx(_Real, _Imaginary))` |
|Opcode|50|

Argument of complex number in degrees.
* Argument must be `cmplx()`.
* Calculates via `atan2d(aimag(cmplx(_Real, _Imaginary)),real(cmplx(_Real, _Imaginary)))`.

Examples:
```
TDI> arg(ARGD(CMPLX(3.0,4.0)))
53.1301

_A = [cmplx(3,4), cmplx(1,1)]

TDI> arg(_A)
[53.1301, 45.0]
```

See also:
* `abs` for the complex length.


### `ARG_OF` 
|Syntax||
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


### `ARRAY` 
|Syntax||
|-|-|
|TDI Syntax   | `ARRAY([_SHAPE], [_KIND])` |
|Python Syntax| `MDSplus.ARRAY([_SHAPE], [_KIND])` |
|Min arguments| 0 |
|Max arguments| 2 |
|Opcode|52|

Generates an unitialized array. The values are not defined and will depend on previous memory usage.
* The `_SHAPE` argument goes from innermost to outermost. Can make up to an 8th dimensional array.
* If `_SHAPE` is absent, the result is a scalar. 
* If `_TYPE` is absent, the result will be floats.


Examples

```TDI
# this makes an array of floats with of shape [3, 4, 6]

TDI> array([3, 4, 6])

/*Here is the output but with line breaks for legibility: 
[[[0.,0.,0.], [0.,0.,0.], [0.,0.,0.], [0.,0.,0.]],
 [[0.,0.,0.], [0.,0.,0.], [0.,0.,0.], [0.,0.,0.]],
 [[0.,0.,0.], [0.,0.,0.], [0.,0.,0.], [0.,0.,0.]],
 [[0.,0.,0.], [0.,0.,0.], [0.,0.,0.], [0.,0.,0.]],
 [[0.,0.,0.], [0.,0.,0.], [0.,0.,0.], [0.,0.,0.]],
 [[0.,0.,0.], [0.,0.,0.], [0.,0.,0.], [0.,0.,0.]]] */


# This makes an array of double precision reals of shape [2,3,4].

TDI> array([2,3,4],1d0)

/*Here is the output but with line breaks for legibility: 
[[[0D0,0D0], [0D0,0D0], [0D0,0D0]],  
[[0D0,0D0], [0D0,0D0], [0D0,0D0]],  
[[0D0,0D0], [0D0,0D0], [0D0,0D0]],  
[[0D0,0D0], [0D0,0D0], [0D0,0D0]]] */ 

# This shows the maximum depth allowed with this function
TDI> array([1,1,1,1,1,1,1,1])
[[[[[[[[0.]]]]]]]]
```

See also: `ramp`, `random`, and `zero`.


### `ASIN` (Arcsine or Inverse Sine, in Radians)
|Syntax||
|-|-|
|TDI Syntax   | `ASIN(_NUM)` |
|Python Syntax| `MDSplus.ASIN(_NUM)` |
|Opcode|53|

Processor approximation to arcsin(X) (inverse sine) in radians.
* `_NUM` argument must be real and be less than or equal to 1 in magnitude.
    * Out-of-range numbers get `$ROPRAND`.
    * Complex numbers cause error.
* Results are in the range from `-pi/2` to `pi/2`.


Examples
```tdi
TDI> ASIN(0.84147098)
1.0
```

See also: `acos`, `acosd`, `asind`


### `ASIND` (Arcsine or Inverse Sine, in Degrees)
|Syntax||
|-|-|
|TDI Syntax   | `ASIND(_NUM)` |
|Python Syntax| `MDSplus.ASIND(_NUM)` |
|Opcode|54|


Processor approximation to arcsin(X) (inverse sine) in degrees.
* `_NUM` argument must be real and be less than or equal to 1 in magnitude.
    * Out-of-range numbers get `$ROPRAND`.
    * Complex numbers cause error.
* Results are in the range `-90` to `90`.

Examples
```tdi
TDI> asind(0.5)
30
```

* See also: `acos`, `acosd`, `asin`



### `AS_IS` 
|Syntax||
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

### `ATAN` (Arctangent, in Radians, for Real Numbers)
|Syntax||
|-|-|
|TDI Syntax   | `atan(_NUM)` |
|Python Syntax| `MDSplus.atan(_NUM)` |
|Opcode|56|

Arctangent, or inverse tangent. Processor approximation to `arctan(X)` (inverse tangent) in radians.
* Arguments must be real. Complex numbers result in error.
* Results are in the range `-pi/2` to `pi/2`, inclusive.
* Units result in error.

Examples
```tdi
TDI> ATAN(1.5574077)
1.0
```

See also:
* `atan` for real numbers, in radians.
* `atand` for real numbers, in degrees.
* `atan2` for complex numbers, in radians.
* `atan2D` for complex numbers, in degrees.
* `arg` for the angle of a complex number.

### `ATAN2` (Arctangent, in Radians, for Complex Numbers)
|Syntax||
|-|-|
|TDI Syntax   | `atan2(_NUM1, _NUM2)` |
|Python Syntax| `MDSplus.atan2(_NUM1, _NUM2)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|57|

Arctangent, or inverse tangent. Processor approximation to `arctan(Y/X)` in radians. 
* The principal value of the argument of the nonzero complex number `CMPLX(X,Y)`.
* Arguments must be real. Complex numbers result in an error.
* Results are in the range -pi to pi. If Y > 0, the result is positive.

Examples:

```TDI
TDI> ATAN2(1.5574077,1.0)
1.0

# the answer is whatever [3*pi/4 , pi/4] evaluates to
TDI> ATAN2([ 1, 1], [-1, 1])
[2.35619,.785398]

TDI> atan2([1,3],1)
[.785398,1.24905]
```

See also:
* `atan` for real numbers, in radians.
* `atand` for real numbers, in degrees.
* `atan2` for complex numbers, in radians.
* `atan2D` for complex numbers, in degrees.
* `arg` for the angle of a complex number.



### `ATAN2D` (Arctangent, in Degrees, for Complex Numbers)
|Syntax||
|-|-|
|TDI Syntax   | `ATAN2D(arg0,arg1)` |
|Python Syntax| `MDSplus.ATAN2D(arg0,arg1)` |
|Min arguments| 2|
|Max arguments| 2|
|Opcode|58|

Arctangent or inverse tangent. Processor approximation to `arctan(Y/X)` in degrees.  
* The principal value of the argument of the nonzero complex number `CMPLX(X,Y)`.
* Arguments must be real. Complex numbers result in an error.
* Results are in the range `-180` to `180`. If `Y>0`, the result is positive.

Examples
```tdi
TDI> ATAN2D(-1.0,-1.0)
-135.0

TDI> ATAN2D([ 1, 1], [-1, 1])
[ 135. , 45.]
```

See also:
* `atan` for real numbers, in radians.
* `atand` for real numbers, in degrees.
* `atan2` for complex numbers, in radians.
* `atan2D` for complex numbers, in degrees.
* `arg` for the angle of a complex number.


### `atand` (Arctangent, in Degrees, for Real Numbers)
|Syntax||
|-|-|
|TDI Syntax   | `atand(arg0)` |
|Python Syntax| `MDSplus.atand(arg0)` |
|Min arguments| 1|
|Max arguments| 1|

Arctangent or inverse tangent. Processor approximation to `arctan(X)` in degrees.
* `_NUM` argument must be real and be less than 1 in magnitude.
* Complex numbers cause error.
* Results lie in the range `-90` to `90`.

Examples

```tdi
TDI> ATAND(1.0)
45.0
```

See also:
* `atan` for real numbers, in radians.
* `atand` for real numbers, in degrees.
* `atan2` for complex numbers, in radians.
* `atan2D` for complex numbers, in degrees.
* `arg` for the angle of a complex number.



### `ATANH` (Hyperbolic Arctangent, for Real Numbers)
|Syntax||
|-|-|
|TDI Syntax   | `ATANH(_NUM)` |
|Python Syntax| `MDSplus.ATANH(_NUM)` |
|Opcode|60|

This is currently broken.

Hyperbolic arctangent (inverse tangent).
* `_NUM` argument must be real. Complex numbers cause error.

Examples

```tdi
TDI> ATANH(0.7615942)
1.0
```

### `AXIS_OF` 
|Syntax||
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
|Syntax||
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

### `BIT_SIZE` 
|Syntax||
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



### `BREAK` 
|Syntax||
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

### `bsearch` 
|Syntax||
|-|-|
|TDI Syntax   | `bsearch(_KEY, _TABLEARRAY, [_MODE], arg3)` |
|Python Syntax| `MDSplus.bsearch(arg0,arg1,arg2,arg3)` |
|Min arguments| 2|
|Max arguments| 4|
|Opcode|67|

TODO: Come back to this, investigate Arg2 and Arg3 further

Binary search in a sorted table.

Arguments
* `_KEY` integer, real, or text, scalar or array. No complex.
* `_TABLEARRAY` ascending-sorted, scalar or array. Should be integer, real, or text.
* `[_MODE]` optional: integer scalar, default is 0.
* `_arg3` TODO: investigate and come back to this. probably kind

Returns:
* The offset in TABLE whose value matches X.  
* Integer offset in table of match.
* For each list element k and matching table element j:
    1. `MODE=0, TABLE[j] == X[k]` with result range 0 to n-1, where n is the number of elements in TABLE or -1 if no exactly matching element number.
    2. `MODE=+1, TABLE[j] <= X[k] < TABLE[j+1]` with result range -1 to n.
    3. `MODE=-1, TABLE[j-1] < X[k] < TABLE[j]` with result range 0 to n+1.

Effectively, `TABLE[-1]` is negative infinity and `TABLE[n]` is positive infinity.

Examples:
```
TDI> BSEARCH(3,1:10)
2

TDI> BSEARCH(1:8,3:5)
[-1,-1,0,1,2,-1,-1,-1]

TDI> MAP(1:10,BSEARCH(3.9,1:10,1))
3

# TODO: apparently sortval ([3,2,1,5,4]) will give you [1,2,3,4,5]. Is this the same as map()?
    _a = [3, 2, 4, 1]
    [3,2,4,1]
    sort (_a)
    [3,1,0,2]
    map(_a,sort(_a))
    [1,2,3,4]
    bsearch(2, map(_a,sort(_a)))
    1
```
    
`See also:
 `SORT` and `SORTI` for data and index sorting.
* `MAP` to pick the selected elements.



### `BTEST` 
|Syntax||
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


## Build Functions

Note:
* Use BUILD_xxx for immediate structure building.
* Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.

TODO: Come back to the BUILD_ and MAKE_ functions? These will all likely require deeper investigation

### `build_action` 
|Syntax||
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

### `BUILD_CALL`
|Syntax||
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


### `BUILD_CONDITION`
|Syntax||
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


### `BUILD_CONGLOM`
|Syntax||
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


### `BUILD_DEPENDENCY`
|Syntax||
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


### `BUILD_DIM` 
|Syntax||
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


### `BUILD_DISPATCH` 
|Syntax||
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


### `BUILD_EVENT`
|Syntax||
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
|Syntax||
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


### `BUILD_METHOD`
|Syntax||
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


### `BUILD_OPAQUE` 
|Syntax||
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


### `BUILD_PARAM`
|Syntax||
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


### `BUILD_PATH`
|Syntax||
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
|Syntax||
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


### `BUILD_PROGRAM` 
|Syntax||
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


### `BUILD_RANGE`
|Syntax||
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


### `BUILD_ROUTINE`
|Syntax||
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


### `BUILD_SIGNAL`
|Syntax||
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


### `BUILD_SLOPE`
|Syntax||
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


### `BUILD_WINDOW`
|Syntax||
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


### `BUILD_WITH_ERROR`
|Syntax||
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


### `BUILD_WITH_UNITS` 

|Syntax||
|-|-|
|TDI syntax | `BUILD_WITH_UNITS(arg0,arg1)` |
|Python Syntax | `MDSplus.BUILD_WITH_UNITS(arg0,arg1)` TODO: Confirm |
|Min Arguments | 2 |
|Max arguments | 2 |
|Opcode 88|

|DATA | any expression that DATA(this) will be valid. |
|UNITS | character string. See the primary section on "Units".|
|Result | Class-R descriptor. <BR> Use `BUILD_xxx` for immediate structure building. <BR> Use `MAKE_xxx` in FUNs for evaluated non-PUBLIC variables.|

|Return Type  |MDS Operation |
Make a describe data with units.
Arguments
DATA any expression that DATA(this) will be valid.
UNITS character string. See the primary section on "Units".
|Result       |Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |_S = BUILD_WITH_UNITS($VALUE*6,'m/s^2') can be used in a
BUILD_SIGNAL(_S,BUILD_WITH_UNITS(5./1024*raw_node,'V')
or similar. Note this could also have been
BUILD_WITH_UNITS(BUILD_SIGNAL($VALUE*6,
BUILD_WITH_UNITS(5./1024*raw_node,'V')),'m/s^2').



Example: `_S = BUILD_WITH_UNITS($VALUE*6,'m/s^2')` can be used in a `BUILD_SIGNAL(_S,BUILD_WITH_UNITS(5./1024*raw_node,'V'`) or similar. Note this could also have been `BUILD_WITH_UNITS(BUILD_SIGNAL($VALUE*6, BUILD_WITH_UNITS(5./1024*raw_node,'V')),'m/s^2')`. |




### `builtin_opcode`
|Syntax||
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

### `byte`
|Syntax||
|-|-|
|TDI Syntax   | `byte(_NUM)` |
|Python Syntax| `MDSplus.byte(_NUM)` |
|Opcode|90|

Converts a number to a one-byte integer.
* Argument must be numeric.
* Returns the truncated whole part of the argument.
* Immediate at compilation. 
* Warning: truncation does not cause an error.

Examples
`BYTE(123)` returns `123B`.
`BYTE(257)` returns `1B`.



### `BYTE_UNSIGNED` 

|Syntax||
|-|-|
|TDI Syntax   | `BYTE_UNSIGNED(_NUM)` |
|Python Syntax| `MDSplus.BYTE_UNSIGNED(_NUM)` |
|Opcode|91|

Convert a number to a one-byte unsigned integer.
* Argument must be numeric.
* Returns the truncated whole part of the argument. Immediate at compilation. 
* Warning: truncation does not cause an error.

Examples
```tdi
TDI> byte_unsigned(123)
123BU

TDI> BYTE_UNSIGNED(257)
1BU
```


### `CASE`
|Syntax||
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

### `CEILING` 
|Syntax||
|-|-|
|TDI Syntax   | `CEILING(_NUM)` |
|Python Syntax| `MDSplus.CEILING(_NUM)` |
|Opcode|93|

Takes a number and rounds up to the nearest whole number.
* Argument must be real. Complex numbers cause an error.

Examples

```
TDI> CEILING(2.783)
3.0

TDI> CEILING(-2.783)
-2.0
```

See also: `floor`

### `CHAR` 
|Syntax||
|-|-|
|TDI Syntax   | `CHAR(_INDEX)` |
|Python Syntax| `MDSplus.CHAR(_INDEX)` |
|Min arguments| 1|
|Max arguments| 2|
|Opcode|94|

The character in a specified position of the ASCII collating sequence. The inverse of `ICHAR`.

* argument must be an integer
* can also receive signals and units as long as 
I must be integer.
For j between 0 and 127, the result is the character in position j of the ASCII collating sequence; otherwise, the result is processor dependent. It is truncated to 8 bits on the VAX.

Examples
```tdi
TDI> char(67) 
"C"

TDI> char([72, 101, 108, 108, 111])
["H","e","l","l","o"]
```

See also: `achar`, `ichar`


### `CLASS` 
|Syntax||
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
|Syntax||
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

### `CMPLX` 
|Syntax||
|-|-|
|TDI Syntax   | `CMPLX(_REALNUM, _IMAGINARYNUM, [_KIND])` |
|Python Syntax| `MDSplus.CMPLX(_REALNUM, _IMAGINARYNUM, [_KIND])` |
|Min arguments| 1 |
|Max arguments| 3 |
|Opcode|97|

Creates a complex number.
* First argument is the real component. 
* Second argument is the imaginary component. If function is called with only one argument, it is assumed that the second number will be zero. 
* (Optional) third component is the Kind. TODO: Come back to this. If KIND is absent, it is ignored; otherwise, CMPLX(X,Y,KIND) has real part REAL(X,KIND) and imaginary part REAL(Y,KIND).
* Immediate at compilation.
* WARNING: truncation does not cause an error.

Examples:
TDI> cmplx(-3)` is `cmplx(-3.0,0.0)`. 
TDI> cmplx(3,4,5d6)` is `cmplx(3d0,4d0)`.



### `COMMA`
|Syntax||
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


### `compile` (Opcode 99)
|Syntax||
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



### `completion_message_of` 
|Syntax||
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
|Syntax||
|-|-|
|TDI Syntax   | `completion_of(arg0)` |
|Python Syntax| `MDSplus.COMPLETION_OF(arg0)` |
|Opcode|100|

|Return Type  |MDS Operation |
Get the completion field.

DISPATCH_OF(A) is searched for this: DSC$K_DTYPE_DISPATCH, the completion field. Otherwise, an error.

TODO: COME BACK TO THIS
See also build functions, dispatch


### `concat`
|Syntax||
|-|-|
|TDI Syntax   | `concat(_STRING0, _STRING1, ..., _STRINGN)` or `_STRING0 // _STRING1`|
|Python Syntax| `MDSplus.concat(_STRING0, _STRING1, ..., _STRINGN)` |
|Min arguments| 2  |
|Max arguments| 254|
|Opcode|10|

Concatenates text strings.
* Limit 253 character expressions.

Examples:
```
TDI> concat("he", "ll", "o")
"hello"`

TDI> ABC // DEF
"ABCDEF"`

TDI> concat("Hello ", ["Mark", "Tim", "Stephen"])
["Hello Mark   ", "Hello Tim    ", "Hello Stephen"]

TDI> concat(["Hello ", "Hi ", "Howdy "], ["Mark", "Tim", "Stephen"])
["Hello Mark   ","Hi    Tim    ","Howdy Stephen"]
```


### `conditional`
|Syntax||
|-|-|
|TDI Syntax   | `conditional(_TSOURCE, _FSOURCE, _MASK)` |
|Python Syntax| `MDSplus.conditional(_TSOURCE, _FSOURCE, _MASK)` |
|Min arguments| 3 |
|Max arguments| 3 |
|Opcode|102|

TODO: investigate further--is this broken?
`conditional (3>4, $true, $false)` seems to always return `$true` no matter what

Select from 2 sources according to a mask.
* Usual Form: MASK ? TSOURCE : FSOURCE. 
* Function Form: CONDITIONAL(TSOURCE,FSOURCE,MASK).
* Warning: range and conditional nesting may be confusing, use parentheses to help. For example, `2?3:4:5` will not compile but `2?3:(4:5)` or `2?(3:4):5` are fine.

Arguments:
* `_TSOURCE` any type and shape.
* `_FSOURCE` any type and shape.
* `_MASK` scalar logical, vector is treated as MERGE.

|Signals      |That of the selected source. 
|Units        |That of the selected source. 
|Form         |That of the selected source.
|Result       |MASK is examined and if a scalar true the source is TSOURCE and if a scalar false the source is FSOURCE. 

See also:
`merge`, for a vector selection.


### `CONDITION_OF` (Opcode 401)
|Syntax||
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



### `CONJG` 
|Syntax||
|-|-|
|TDI Syntax   | `CONJG(ARG0)` |
|Python Syntax| `MDSplus.CONJG(ARG0)` |
|Opcode|103|

Conjugate of a complex number.
* Argument must take the form `cmplx(x,y)` and function will return `cmplx(x,-y)`. 
* Reals are not converted.

Examples
```
TDI> conjg(cmplx(2.0,3.0))
cmplx(2.0,-3.0)
```




### `CONTINUE` 

|Syntax||
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



### `COS`
|Syntax||
|-|-|
|TDI Syntax   | `COS(_NUM)` |
|Python Syntax| `MDSplus.COS(_NUM)` |
|Opcode|106|

Cosine of angle in radians; Processor approximation to cos(X).
* Arguments accepted: real numbers and real part of cmplx(x,y) in radians.
* Units not accepted.

Examples

```tdi
TDI> COS(1)
0.540302

TDI> cos(cmplx(1.0,3))
Cmplx(5.43958,-8.42975)

TDI> cos($2pi)
1D0
```

### `COSD`
|Syntax||
|-|-|
|TDI Syntax   | `COSD(_NUM)`         |
|Python Syntax| `MDSplus.COSD(_NUM)` |
|Opcode|107|

Cosine of angle in degrees; returns processor approximation of cos(x)
* X (degrees) must be real.
* Complex numbers result in an error.
* Units are not accepted

Examples

```tdi
TDI> cosd(60.0)
0.5
```



### `COSH` 
|Syntax||
|-|-|
|TDI Syntax   | `COSH(_NUM)` |
|Python Syntax| `MDSplus.COSH(_NUM)` |
|Opcode|108|

Hyperbolic cosine; returns processor approximation to cosh(X).
* Argument must be real.
* Units not accepted

Examples

```tdi
TDI> COSH(1.0)
1.54308`
```





### `count`
|Syntax||
|-|-|
|TDI Syntax   | `COUNT(_MASK, [_DIM])` |
|Python Syntax| `MDSplus.COUNT(_MASK, [_DIM])` |
|Opcode|109|

Counts the number of true elements in `_MASK` along dimension `_DIM`.

Arguments
* `_MASK` or logical array. 
* `_DIM`(optional)  or integer scalar from 0 to n-1, where n is rank of MASK.
* form: Integer. It is scalar if DIM is absent or MASK is a vector; otherwise, the result is an array of rank n-1 and of shape like MASK's with DIM subscript omitted.

Results
* COUNT(MASK) is equal to the number of true elements of MASK and is 0 if no element of MASK is true or MASK is size zero.
* For a vector MASK, COUNT(MASK,DIM) is equal to COUNT(MASK). For higher dimensional cases, the value of an element of the result is COUNT of elements of MASK varying the DIM subscript.

Examples.

```tdi
TDI> count([$TRUE,$FALSE,$TRUE])
2


    `_B=[[1,3,5,7], [2,4,6,8], [0,0,0,0]]` and  
    `_C=[[0,3,5,6], [7,4,8,8], [1,1,1,1]]`  
    * `count(_B == _C)` returns `4`
    * `count(_B == _C,0)` returns `[2,2,0]`
    * `count(_B == _C,1)` returns `[0,2,1,1]`
```


### `CULL` (Opcode 390)
|Syntax||
|-|-|
|TDI Syntax   | `CULL(arg0,arg1,arg2,arg3) ` |
|Python Syntax| `MDSplus.CULL(arg0,arg1,arg2,arg3)` |
|Min arguments| 1 |
|Max arguments| 4 |

Takes an array and removes values not in bounds.

Arguments: 
* argument0: `A`: MDS signal or dimension or array. 
* argument1: (optional) DIM, or scalar integer from 0 to rank of `A` less one. Must be 0 or absent for a signal. 
* argument2: (optional) `X` or non-complex scalar or array of numbers to check if bounded.
* argument3: __________ TODO Come back to this and investigate further


|Signals      |Same as X. 
|Units        |Same as specified dimension if a signal or dimension. 
|Form         |Shape of X and type from specified dimension.
|Result       |X values that are out of range are eliminated.
* If A is an array, the bounds of the array are used.
* If A is a dimension or the specified dimension of a signal, the extreme data value of the axis are used.

Examples. 
* `cull(1:5,,2:7)` returns `[2,3,4,5]`
* `cull(build_dim(build_window(2,5,1.1),build_range(,,3)),0,5:8)` returns `[8]` because the limits are 7.1 and 16.1.
* `CULL([0,7],,0:3)` returns `[0,1,2,3]`
* `CULL(0:3,,[-1, 3])` returns `[3]`
* `cull([1, 3, 5, 7], ,1:5)` ?=> `[1,2,3,4,5]`  // TODO: come back to this and investigate further?


See also
* `extend` to replace bad values with the limits.

TODO: come back to this and investigate further
cull([1, 3, 5, 7], ,[1,5])
[1,5]

cull([1, 3, 5, 7], ,[2, 4, 6])
[2,4,6]





### `CVT` (Opcode 111)
|Syntax||
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



### `DATA` (Opcode 112)
|Syntax||
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
|Syntax||
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




### `DATE_TIME` (Opcode 114)
|Syntax||
|-|-|
|TDI Syntax   | `DATE_TIME(arg0)` |
|Python Syntax| `MDSplus.DATE_TIME(arg0)` |
|Min arguments| 0 |
|Max arguments| 1 |

* Returns the current/specified data and time as a text string.
* Arguments (Optional): TIME must be a quadword (64-bit), VMS time stamp positive absolute time or negative delta time.
date_time works fine

|Signals      |None. 
|Units        |None. 
|Form         |Character scalar of length 23.
|Result       |The current date and time.

Examples
* `DATE_TIME()` might return `26-JAN-1990 15:15:19.54`.


```
TDI> DATE_TIME(35067168000000000Q + (9999999999999999Q))
" 9-SEP-2001 01:46:39.99"
TDI> date_time(getnci(TSTART, "TIME_INSERTED"))
"28-FEB-2007 12:37:20.83"

```





### `dble` (Opcode 115)
|Syntax||
|-|-|
|TDI Syntax   | `dble(_NUM)` |
|Python Syntax| `MDSplus.dble(_NUM)` |
|Min arguments| 1 |
|Max arguments| 1 |


Double the precision of a number.
* Argument must be numeric and must not be octaword or H floating because they are already maximum precision.
* Returns twice the precision of the argument:
Byte becomes word, word becomes long, long becomes quadword, quadword becomes octaword, F floating becomes D, D or G floating becomes H. 
* Unsigned, signed, real, and complex types remain so.
* Warning: F90 always converts to a double-precision real `D_FLOAT`.

Examples.
* `DBLE(3)` is 3Q.
* `DBLE(3.0)` is 3D0.







### `deallocate` (Opcode 116)
|Syntax||
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



### `debug` (Opcode 117)
|Syntax||
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



### `decompile` (Opcode 119)
|Syntax||
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


### `decompress` (Opcode 120)
|Syntax||
|-|-|
|TDI Syntax   | `DECOMPRESS([_IMAGE],[_ROUTINE],_SHAPE,_DATA)` |
|Python Syntax| `MDSplus.DECOMPRESS([_IMAGE],[_ROUTINE],_SHAPE,_DATA)` |
|Min arguments| 4 |
|Max arguments| 4 |

Expand compressed data into original form. Returns the original data. This is done automatically when compressed, CLASS_CA, data is fetched from the tree.

Arguments
* `[_IMAGE]` (optional) character scalar of `SYS$SHARE:.EXE` file or logical name. Default is `MDSSHR` if no ROUTINE. 
* `[_ROUTINE]` (optional) character scalar of entry point name in shared image.
Default is MDS$DECOMPRESS 
* `_SHAPE` Expanded form data shape. 
* `_DATA` A vector of any type that has the compressed data.

Examples
* `DECOMPRESS(,,BUILD_ARRAY(10), [0x00880246, 0x84620800LU, 0x4befcb4e, 0x080a])` returns `[0,164,228,252,256,250,238,224,207,190]`. (Actually this does not save enough space so the compression would not take place.)

`DECOMPRESS(,,ARRAY(10), [0x00880246, 0x84620800LU, 0x4befcb4e, 0x080a])` returns `[0.,229.813E-45,319.496E-45,353.127E-45,358.732E-45,350.325E-45,333.509E-45,313.891E-45,290.069E-45,266.247E-45]`

TODO: Come back to this and construct a better example


### `DEFAULT` (Opcode 121)
|Syntax||
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


### `descr` (Opcode 123)
|Syntax||
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


### `diagonal` (Opcode 124)
|Syntax||
|-|-|
|TDI Syntax   | `diagonal(_ARRAY,[_FILL])` |
|Python Syntax| `MDSplus.diagonal(_ARRAY,[_FILL])` |
|Min arguments| 1 |
|Max arguments| 2 |

Create a diagonal matrix from its diagonal.

Arguments
* `_ARRAY` numeric or character vector. 
* `[_FILL]` scalar converted to type of ARRAY or a square matrix of the same length as the `_ARRAY`. Default is numeric 0 or character blanks.
* Form: Rank-two of shape [n,n], where n is the size of ARRAY.
* Element [j,j] is ARRAY[j], for j from 0 to n-1. All other elements are _FILL.

Examples
* `diagonal([1,2,3])` returns `[[1,0,0], [0,2,0], [0,0,3]]`
* `diagonal([1,2,3], 5)` returns `[[1,5,5], [5,2,5], [5,5,3]]`
* `diagonal([1,2,3], [[4,5,6], [7,8,9], [10,11,12]])` returns `[[1,5,6], [7,2,9], [10,11,3]]`


### `digits` (Opcode 125)
|Syntax||
|-|-|
|TDI Syntax   | `digits(arg0)`         |
|Python Syntax| `MDSplus.digits(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

The number of significant digits in the model representing the same type as the argument. Returns the number of non-sign bits in an integer or the number of fraction bits in a real or complex number.

Examples
* `DIGITS(1.0)` is 24 on the VAX.





### `dim` (Opcode 126)
|Syntax||
|-|-|
|TDI Syntax   | `DIM(_NUM0, _NUM1)` |
|Python Syntax| `MDSplus.DIM(_NUM0, _NUM1)` |
|Min arguments| 2| 
|Max arguments| 2| 
|Native python|False|


Returns difference of `X-Y` if `X>Y` and zero otherwise.
Both arguments must be integer or real.
Complex numbers result in error.

Examples
* `dim(3.0,2.0)`  returns `1.`
* `dim(3.0,-2.0)` returns `5.`
* `dim(-3.0,2.0)` returns `0.`







### `dim_of` (Opcode 127)
|Syntax||
|-|-|
|TDI Syntax   | `dim_of(_A,[_N])` |
|Python Syntax| `MDSplus.dim_of(_A,[_N])` |
|Min arguments| 1 |
|Max arguments| 2 |


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
|Syntax||
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




### `divide` (Opcode 129)
|Syntax||
|-|-|
|TDI Syntax   | `DIVIDE(_NUM0,_NUM1) ` |
|Python Syntax| `MDSplus.DIVIDE(_NUM0,_NUM1)` |
|Min arguments| 2 |
|Max arguments| 2 |


The quotient of two numbers.
* Usual Form: `X / Y`
* Function Form: `DIVIDE(X,Y)`
* Arguments X and Y must be numeric.

|Signals      |Single signal or smaller data. 
|Units        |X units with inverted Y units separated by a slash. 
|Form         |The compatible form of X and Y.
|Result       |
Returns: 
* The quotient without remainder of X/Y. 
* If the result is real or complex there may be rounding. 
* Integer division truncates. 
* Complex division is `CMPLX((RX*RY-IX*IY)/DEN,(RY*IX-RX*IY)/DEN)` with `DEN=RY^2+RI^2`, where `RX=REAL(X)`, `IX=AIMAG(X)`, etc. The exponents are scaled to prevent overflow or underflow.

* Warning: integer divide by zero is ignored.
Examples. 
* `5/3` returns `1`
* `5/BUILD_WITH_UNITS(3,"s")` returns `BUILD_UNITS(1,"/s")`.
`divide(10, 3)`  returns `3`
`divide(10, 3.0)`  returns `3.33333`



### `do` (Opcode 131)
|Syntax||
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




### `DOT_PRODUCT` (Opcode 132)
|Syntax||
|-|-|
|TDI Syntax   | `DOT_PRODUCT(arg0,arg1)` |
|Python Syntax| `MDSplus.DOT_PRODUCT(arg0,arg1)` |
|Min arguments| 2 |
|Max arguments| 2 |

Performs dot-product multiplication of numeric. 

Arguments
* VECTOR_A and VECTOR_B must be numeric vectors.
* Logicals are treated as integers.
* If arrays not of the same length, the longer will be truncated.

Returns
* For integer or real, result is `SUM(VECTOR_A*VECTOR_B)`
* for complex, `SUM(CONJG(VECTOR_A),VECTOR_B)`. 
* For zero elements the result is zero.

Examples
* `dot_product([1, 2, 3], [4, 5, 6])` returns `32` because  
`(1 * 4) + (2 * 5 ) + (3 * 6)` returns `32`
* `dot_product([$TRUE, $FALSE, $TRUE], [4, 5, 6])` returns `10`

do not keep ?
* `dot_product([1, 2, 3], [4, 5])` returns `14`


### `do_task` (Opcode 448)
|Syntax||
|-|-|
|TDI Syntax   | `DO_TASK(arg0) ` |
|Python Syntax| `MDSplus.DO_TASK(arg0) ` |
|Min arguments| 1 |
|Max arguments| 1 |

TODO: Come Back To This and investigate further

Execute Task
Executes the task item found in the argument.
ARGUMENT TASK refers to an ACTION or a TASK



### `dprod` (Opcode 133)
|Syntax||
|-|-|
|TDI Syntax   | `dprod(_NUM0,_NUM1)` |
|Python Syntax| `MDSplus.dprod(_NUM0,_NUM1)` |
|Min arguments| 2 |
|Max arguments| 2 |

Double precision product; returns the product of `X * Y` with each converted to twice their precision.
* Arguments X and Y must be numeric except octaword or H floating. 
* For F90, they must be default real and result is double.

Examples
* `DPROD(3,4)` returns `12Q`. 
* `DPROD(-3.0,2.0)` returns `-6.0D0`.`

see also: `dble`




### `dscptr` (Opcode 134)
|Syntax||
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
|Syntax||
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


### `DSQL` (Opcode 415)
|Syntax||
|-|-|
|TDI Syntax   | `DSQL(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.DSQL(arg0,arg1,argn,...)` |
|Min arguments| 1   |
|Max arguments| 254 |
|Native python|False|

> TODO: Come back to this when we have a db to test

Description:
Execute a MSsql query
_num=DSQL(sqlcommand,arg0,arg1,...,retarg0,retarg1,...)
Eample. set_database('logbook') _rows=dsql('select count(*) from entries',_num)





### `dtype_range` (Opcode 292)
|Syntax||
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



### `d_complex` (Opcode 139)
|Syntax||
|-|-|
|TDI Syntax   | `d_complex(_REALPART, [_IMAGINARYPART])` |
|Python Syntax| `MDSplus.d_complex(_REALPART, [_IMAGINARYPART])` |
|Min arguments| 1 |
|Max arguments| 2 |


Conversion Elemental.
Convert to D-precision floating Complex. 
* Arguments must be numeric.
* If Y is absent and X is complex, the AIMAG(X) is used for Y. 
* If X and Y are present, the real parts of each are used.
* Immediate at compilation.
* Warning: truncation does not cause an error.

Examples
* ~~`D_COMPLEX(3,4.1)` is `CMPLX(3.0D0,4.1D0)`, approximately.~~
> TODO: come back and investigate why this returns "v0" instead of "D0" per what's prescribed in the original example above
`d_complex(3, 4.1)` returns `Cmplx(3V0,4.099999904632568V0)`

See also `cmplx`, `dble`


### `d_float` (Opcode 140)
|Syntax||
|-|-|
|TDI Syntax   | `D_FLOAT(arg0)` |
|Python Syntax| `MDSplus.D_FLOAT(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |
 
Convert to D-precision floating real.
* Integers, reals and the real part of complex numbers are converted to D-precision reals. 
* Arguments must be numeric.
* Immediate at compilation.
* Warning: truncation does not cause an error.


Examples
~~* D_FLOAT(12), D_FLOAT(12.) D_FLOAT(12H0) are 12D0, approximately.~~
> TODO: Come back to this and investigate why it returns 2v0 instead of 2d0
* `d_float(2)` returns `2V0`

See also `dble`


### `elbound` (Opcode 143)
|Syntax||
|-|-|
|TDI Syntax   | `elbound(_ARRAY, [_DIM])` |
|Python Syntax| `MDSplus.elbound(_ARRAY, [_DIM])` |
|Min arguments| 1 |
|Max arguments| 2 

Same as `LBOUND`. [link]

See also:
* UBOUND for upper bound, SHAPE for number of elements, SIZE for total elements, and E... for signals.
* LBOUND (alternate spelling, same function)


### `element` (Opcode 374)
|Syntax||
|-|-|
|TDI Syntax   | `ELEMENT(_INDEX, _DELIMITOR, _STRING)` |
|Python Syntax| `MDSplus.ELEMENT(_INDEX, _DELIMITER, _STRING)` |
|Min arguments| 3 |
|Max arguments| 3 |

Extracts an element from a string in which the elements are separated by a delimiter character.

Arguments
* _INDEX: an integer. First item is NUMBER=0. 
* _DELIMITER: a character, length one. 
* _STRING: a character.

Return
* The character from the _INDEX-th instance of the delimiter to the next instance or the end of string. `_INDEX=0` returns the part of the string up to the first delimiter. 
* Result is the same length as STRING, so there will be additional white space. Compatible shape. Note: although the DCL function trims the extra whitespace from the result, it is not done here. It may be trimmed, someday for scalars only.
* A blank string is returned if _INDEX not found.
* The whole string is returned if the delimiter is not found and index is 0.

Examples
* `ELEMENT(1,'/','A/B/C')` returns `"B    "`.

* `trim(element(1,'/','A/B/C'))` returns `"B"`

* `element(4,'/','12')` returns `"  "`.

See also: `trim`



### `else` (Opcode 144)
|Syntax||
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


### `end_of` (Opcode 148)
|Syntax||
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





### `epsilon` (Opcode 150)
|Syntax||
|-|-|
|TDI Syntax   | `epsilon(arg0) ` |
|Python Syntax| `MDSplus.epsilon(arg0) ` |
|Min arguments| 1 |
|Max arguments| 1 |

A positive model number that is almost negligible compared to unity in the model representing numbers of the same type as the argument.

Arguments: 
* `X` must be real or complex, scalar or array.
The result is `b^(1-p)`, where `b` is the digit base and `p` is the number of digits in model numbers like `X`.


|Form         |Scalar of same type as real part of X.

Examples
* `EPSILON(1.0)` is `2^-23` on the VAX.
* `EPSILON(1.0)` returns `119.209E-9`

TODO: come back to this? looks like it always returns this constant regardless of argument??




### `eq` 
(Opcode 151)
|Syntax||
|-|-|
|TDI Syntax   | `_A eq _B` `_A == _B` `eq(_A, _B)`|
|Min arguments| 2 |
|Max arguments| 2 |


Tests for equality of two values.
Usual Forms `A == B`, `A EQ B`. 
Function Form `EQ(A,B)`.
* Arguments A and B must both be numeric or character.
* Returns True if X and Y are the equal; otherwise, false. 
* Units are lost if different
* $ROPRAND is not equal to any value.
* Warning: floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that `.1d0+.1==.2` is true. Integer values may be truncated when matched to floating numbers.
 
Examples
* `2==2.0` is $TRUE.
* `eq(build_with_units(2, "V"), build_with_units(2, "W"))` returns `Build_With_Units(1BU, "?")`
* `eq(build_with_units(2, "V"), build_with_units(2, "V"))` returns `1BU`

See also: `ge`, `gt`, `le`, `lt`, `ne`



### `equals` (Opcode 152)
|Syntax||
|-|-|
|TDI Syntax   | `_NAME = _VALUE ` |
|Min arguments| 2
|Max arguments| 2

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
|Syntax||
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



### `eqv` (Opcode 154)
|Syntax||
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


### `errorlogs_of` (Opcode 398)
|Syntax||
|-|-|
|TDI Syntax   | `errorlogs_of(arg0)` |
|Python Syntax| `MDSplus.errorlogs_of(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

Get the errorlogs field.
Argument, A is searched for this: `DSC$K_DTYPE_ACTION`, the errorlogs field. Otherwise, an error.

> TODO: Come back to this one. 



### `error_of` (Opcode 446)
|Syntax||
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



### `eshape` (Opcode 155)
|Syntax||
|-|-|
|TDI Syntax   | `eshape(_SOURCE, [_DIM])` |
|Python Syntax| `MDSplus.eshape(_SOURCE, [_DIM])` |
|Min arguments| 1 |
|Max arguments| 2 |

The shape of an array or a scalar or a signal.

Arguments 
* `_SOURCE` any type scalar, array, or signal. 
* [_DIM] (optional) integer scalar from 0 to n-1, where n is rank of SOURCE.

Form:
* Scalar if DIM present; otherwise, vector of size n.
* Integer for an array, combined type of dimensions for a signal.

Returns:
* The shape of SOURCE for subscript DIM of SOURCE. If no bounds were effective it is one less than the multiplier for subscript DIM of SOURCE. ESHAPE(ARRAY) has value whose j-th component is equal to ESHAPE(ARRAY,j) for each j, 0 to n-1. For a signal, the extent of the dimension if it is of DTYPE_DIMENSION, else as for an array. This does not include both bounds for integers.

Examples
* ESHAPE(_A[2:5,-1:1]) is [4,3]. ESHAPE(3) is [], a zero-length vector.
* with `_A = [[1,2,3],[4,5,6],[7,8,9],[10,11,12]]`  
`eshape(_A)` returns `[3,4]`



### `esize` (Opcode 156)
|Syntax||
|-|-|
|TDI Syntax   | `esize(_ARRAY,[_DIM])` |
|Python Syntax| `MDSplus.esize(_ARRAY,[_DIM])` |
|Min arguments| 1 |
|Max arguments| 2 |

The extent an array or the total number of elements in the array or signal.

Arguments 
* `_ARRAY` any type array or signal.
* `[_DIM]` Optional integer scalar from 0 to n-1, where n is rank of ARRAY.

Returns
* Equal to the extent of dimension `[_DIM]` of `_ARRAY` or, if `[_DIM]` is absent, the total number of elements of ARRAY. 
* For a signal, the extent of the dimension if it is of `DTYPE_DIMENSION`, else as for an array. This does not include both bounds for integers. The volume if no `[_DIM]`.

Examples
* With `_A = [[1,2,3],[4,5,6]]`  
`esize(_A)` returns `6`




### `eubound` (Opcode 157)
|Syntax||
|-|-|
|TDI Syntax   | `eubound(arg0,arg1)` |
|Python Syntax| `MDSplus.eubound(arg0,arg1)` |
|Min arguments| 1 |
|Max arguments| 2 |


All the upper bounds of an array or signal or a specified upper bound.

Arguments 
* ARRAY any type array or signal. 
* DIM integer scalar from 0 to n-1, where n is rank of ARRAY.

Form
* Scalar if DIM present; otherwise, vector of size n.
* Integer for an array, combined type of dimensions for a signal.

> TODO: Come back to these bullet points, which seem verbose

Returns
* EUBOUND(ARRAY,DIM) is equal to the upper bound for subscript DIM of ARRAY. If no bounds were effective it is one less than the multiplier for subscript DIM of ARRAY.
* EUBOUND(ARRAY) has value whose j-th component is equal to EUBOUND(ARRAY,j) for each j, 0 to n-1.
* For a signal, the upper bound on the dimension if it is of DTYPE_DIMENSION, else as for an array.
* empty arrays anywhere return a -1
* Basically it just tells you the highest index number of an array. If the array has sub-arrays, this returns highest index number of each subarray, and then the highest index number of the subarrays. Remember that the first position is 0.

|Signals      |None. 
|Units        |None if array, that of combined dimensions of signal. 

Examples
* with `_A = [1,2,3,4,5]`  
`eubound(_A)` returns `[4]`
* with `_B = [[1,1,1],[2,2,2],[3,3,3],[4,4,4]]`  
`eubound(_B)` returns `[2,3]`
* with `_C = []`  
`eubound(_C)` returns `[-1]`



### `evaluate`
(Opcode 158)
|Syntax||
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
|Syntax||
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


### `exp` (Opcode 160)
|Syntax||
|-|-|
|TDI Syntax   | `exp(arg0) ` |
|Python Syntax| `MDSplus.exp(arg0)` |
|Min arguments| 1
|Max arguments| 1

Exponential
Arguments can be real or complex.
Returns processor approximation to e^X. 
If X is complex, the imaginary part is in radians.

Example:
* `EXP(1.0)` returns `2.71828`, approximately.




### `exponent` (Opcode 161)
|Syntax||
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



### `extend` (Opcode 391)
|Syntax||
|-|-|
|TDI Syntax   | `extend(A,[DIM],[X],arg3) ` |
|Python Syntax| `MDSplus.extend(arg0,arg1,arg2,arg3) ` |
|Min arguments| 1 |
|Max arguments| 4 |

Removes values not in bounds, but replaces them with the upper and lower

Arguments :
* `A`: MDS signal or dimension or VMS array. 
* `[DIM]` (optional) scalar integer from 0 to rank of A less one. Must be 0 or absent for a signal. 
* `[X]` (optional) non-complex scalar or array of numbers to check if bounded.
* arg3???
> TODO: come back to arg3, investigate DIM further which might not be working properly

|Signals      |Same as X. 
|Units        |Same as specified dimension if a signal or dimension. 
|Form         |Shape of X and type from specified dimension.

Returns: 
* X values that are out of range are replaced by the nearer limit.
(i) If A is an array, the bounds of the array are used.
(ii) If A is a dimension or the specified dimension of a signal, the extreme data value of the axis are used.

Examples.
* `EXTEND(1:5,,0:7)` returns `[1,1,2,3,4,5,5,5]`.
* `EXTEND(3:5,,0:7)` returns `[3,3,3,3,4,5,5,5]`.
(ii) `EXTEND(BUILD_DIM(BUILD_WINDOW(2,5,1.1), BUILD_RANGE(,,3)),0,5..8)` is ~~[7.1,7.1,8.]~~ [[7.1,8.] because the limits are 7.1 and 16.1.

> TODO: come back to this build example


See also: `CULL` to eliminate bad values.




### `extract` (Opcode 409)
|Syntax||
|-|-|
|TDI Syntax   | `extract(_START,_LENGTH,_STRING)` |
|Python Syntax| `MDSplus.extract(_START,_LENGTH,_STRING)` |
|Min arguments| 3 |
|Max arguments| 3 |

Extracts an substring from a string starting at an offset.

Arguments 
* _START: integer.
* _LENGTH: integer. 
* _STRING: character.

Returns:
* The string from the START-th character (counting from 0) and of LENGTH count is returned.
* A null string (length is zero) may be returned if _START or _LENGTH are out of range.

Examples. 
* `extract(1,2,'ABCDEFGHIJKLMNOP')` returns `"BC"`. 
* `extract(4,1,'12')` returns `" "`.




### `EXT_FUNCTION` (Opcode 162)
|Syntax||
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






### `fclose` (Opcode 96)
|Syntax||
|-|-|
|TDI Syntax   | `take_from_FCLOSE(arg0)Compiler_syntax` |
|Python Syntax| `MDSplus.FCLOSE(arg0)` |
|Min arguments| 1
|Max arguments| 1

Close the file unit opened by FOPEN.
* Argument: UNIT long integer pointer from FOPEN.
* Returns Error code or 0 if none.

Examples
`_u=fopen('testFile.txt','w'),WRITE(_u,"HELLO WORLD"),fclose(_u)`
`_u=fopen('testFile.txt','r'),_var=READ(_u),fclose(_u)`

See also: `FOPEN`.



### `FINITE` (Opcode 410)
|Syntax||
|-|-|
|TDI Syntax   | `FINITE(arg0)` |
|Python Syntax| `MDSplus.FINITE(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

Checks that a number is not the reserved real value.
* Returns: Each element of X is checked for validity as a floating point number.
* All integers are finite.

Examples:
* `finite(1.)` returns `1BU` or `$TRUE`
* `finite(1./0)` returns `0BU` or `$FALSE`



### `firstloc` (Opcode 164)
|Syntax||
|-|-|
|TDI Syntax   | `firstloc(_MASK,[_DIM]) ` |
|Python Syntax| `MDSplus.firstloc(_MASK,[_DIM]) ` |
|Min arguments| 1
|Max arguments| 2


Locate the leading edges of a set of true elements of a logical mask.

Arguments 
* `_MASK`: logical array. 
* [_DIM] Optional: integer scalar from 0 to n-1, where n is rank of MASK.

|Signals      |Same as MASK. |Units        |None. |Form         |Logical of same shape.

> TODO: come back to this for further investigation

Returns:
* `FIRSTLOC(MASK)` has at most one true element. If there is a true value, it is the first in array element order.
* `FIRSTLOC(MASK,DIM)` is found by applying FIRSTLOC to each of the one-dimensional array sections of MASK that lie parallel to dimension DIM.

Examples.
(i)
First in array order:
FIRSTLOC(_M=[0 0 1 0]) is [0 0 0 0]. [0110] [0100][0101] [0000][0000] [0000]

(ii)
the top edge:
FIRSTLOC(_M,0) is [0 0 1 0]. [0 1 00][0 0 01][0 0 00]




### `fix_roprand` (Opcode 166)
|Syntax||
|-|-|
|TDI Syntax   | `fix_roprand(_X,_REPLACE)` |
|Python Syntax| `MDSplus.fix_roprand(_X,_REPLACE)` |
|Min arguments| 2 |
|Max arguments| 2 |

Fix reserved operand value with substitute.
* Both arguments must be real or complex.
* Returns: Same as X except that elements with $ROPRAND value are replaced by REPLACE. If X is real, the replacement is the real part of REPLACE. If X is complex, the real and imaginary parts are replaced independently.

|Signals      |Single signal or smaller data. |Units        |Same as X. |Form         |Same as X.

|Examples     |
* `FIX_ROPRAND(1./0.,5)` returns `5.0`.




### `float` (Opcode 167)
|Syntax||
|-|-|
|TDI Syntax   | `float(_A,_KIND) ` |
|Python Syntax| `MDSplus.float(_A,_KIND) ` |
|Min arguments| 1 |
|Max arguments| 2 |

Converts to real, if storing in variable, stores as float.

Arguments 
* `_A` numeric; ignores imaginary portion of any complex numbers.
* `[_KIND]` Optional: scalar integer type number, for example, `KIND(1d0)`.

|Signals      |Same as A. |Units        |Same as A. 

|Form         |If KIND present, the type KIND; otherwise, the real type with the same length. To get F, D, G, or H floating result use F_FLOAT, etc.

Returns:
* Immediate at compilation.
* (i) A is integer or real, the result is the truncated approximation.
* (ii) A is complex, the result is the approximation to the real part.  
Note: truncation does not cause an error.

Examples
* `float(-3)` is `-3.0`.
* `float(cmplx(_X,_Y))` is real part of a complex, `_X`.

<!-- Commenting this out because normal people shouldn't need to know this, but for internal purposes: This is done in TDISHR as REAL(Z). In F90, REAL(Z) sets the default floating point size. -->


### `floor` (Opcode 168)
|Syntax||
|-|-|
|TDI Syntax   | `floor(_NUM) ` |
|Python Syntax| `MDSplus.floor(_NUM) ` |
|Min arguments| 1 |
|Max arguments| 1 |

Takes a number and rounds down to the nearest whole number
* Argument must be real. Complex numbers cause an error.

Returns:
* For integer A, no change. 
* For real A>=0, AINT(A). 
* For real A<0, A if AINT(A)==A and AINT(A)-1 otherwise.

Examples. 
* `floor(2.783)` returns `2.0`. 
* `floor(-2.783)` returns `-3.0`.

See also: `ceiling` and `nint`.


### `fopen` (Opcode 265)
|Syntax||
|-|-|
|TDI Syntax   | `fopen(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.fopen(arg0,arg1,argn,...)` |
|Min arguments| 2   |
|Max arguments| 254 |

Open a file name.
Arguments FILENAME character scalar with node, disk, file, and extension. 
* MODE character scalar: r for read, w for write, a for append, and + for update may be added. Note lowercase.
* Returns: Integer scalar, a pointer to a FILE block.

Examples:
* to write.. `_u=fopen('testFile.txt','w'),WRITE(_u,"HELLO WORLD"),fclose(_u)`
* to read `_u=fopen('testFile.txt','r'),_var=READ(_u),fclose(_u)`





### `for` (Opcode 169)
|Syntax||
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


### `fraction` (Opcode 170)
|Syntax||
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



### `fseek` (Opcode 309)
|Syntax||
|-|-|
|TDI Syntax   | `fseek(_UNIT,[_OFFSET],[_ORIGIN]) ` |
|Python Syntax| `MDSplus.fseek(_UNIT,[_OFFSET],[_ORIGIN]) ` |
|Min arguments| 1 |
|Max arguments| 3 |
|Native python|False|

CC IO
Position a file pointer.

Arguments 
* `_UNIT` Integer scalar pointer from FOPEN. 
* `[_OFFSET]` Optional: Long scalar offset (w.r.t. ORIGIN) of file position. 
* `[_ORIGIN]` Optional: Scalar number:
    * 0 for absolute (w.r.t. beginning of file),
    * 1 for relative to current position,
    * 2 for offset from end of file.

Returns: Error code or 0 if none. 
WARNING, does not work properly for "record" files, only stream files.

>TODO: come back to this; it doesn't appear to be working.


### `fs_complex` (Opcode 451)
|Syntax||
|-|-|
|TDI Syntax   | `FS_COMPLEX(_NUM,arg1)` |
|Python Syntax| `MDSplus.FS_COMPLEX(_NUM,arg1)` |
|Min arguments| 1 |
|Max arguments| 2 |

Convert to IEEE single precision floating complex (32-bit x 2).

Result
* Integers, reals and the real part of complex numbers are converted to F-precision reals. Immediate at compilation.
* WARNING, truncation does not cause an error.

Examples
`FS_COMPLEX(12,1)`, `fs_complex(12.,1)`, and `fs_complex(12D0,1)` return `CMPLX(12.0,1)`.


### `fs_float` (Opcode 450)
|Syntax||
|-|-|
|TDI Syntax   | `fs_float(_NUM)` |
|Python Syntax| `MDSplus.fs_float(_NUM)` |
|Min arguments| 1
|Max arguments| 1

Convert to IEEE single precision floating real (32-bit)
* Arguments must be numeric.
* Integers, reals and the real part of complex numbers are converted to F-precision reals. Immediate at compilation.
* Warning: truncation does not cause an error.

Example:
* `fs_float(12)`, `fs_float(12.)`, and `fs_float(12D0)` return `12.0`.


### `ftell` (Opcode 417)
|Syntax||
|-|-|
|TDI Syntax   | `FTELL(arg0) ` |
|Python Syntax| `MDSplus.FTELL(arg0) ` |
|Min arguments| 1 
|Max arguments| 1

> TODO: Come back to this and investigate further

Report position of a file pointer. 
* Argument: UNIT Integer scalar pointer from FOPEN.
* Returns: Error code or 0 if none. 
* WARNING, does not work properly for "record" files, only stream files.

Example

```tdi
/* Lets say you have a file with two lines of text in it */
TDI> _u=fopen('testFile.txt','w'),WRITE(_u,"HELLO WORLD", "\n", "This is line two."),fclose(_u)
0

/* open the file */
TDI> _u=fopen('testFile.txt','r')
Pointer(0x5cea484bdef0)

/* begin at position zero and read the file one line at a time */
TDI> ftell(_u)
0
TDI> _var=READ(_u)
"HELLO WORLD" /* the \n is implied with this*/

TDI> ftell(_u)
12
/* the next read will begin at position 12 of the file. */

TDI> _var=READ(_u)
"This is line two." /* null terminator is implied with this */

TDI> ftell(_u)
30
```



### `ft_complex` (Opcode 453)
|Syntax||
|-|-|
|TDI Syntax   | `FT_COMPLEX(_REALPART,_COMPLEXPART)` |
|Python Syntax| `MDSplus.FT_COMPLEX(_REALPART,_COMPLEXPART)` |
|Min arguments| 1 |
|Max arguments| 2 |

Convert to IEEE double precision floating complex (64-bit x 2).
* Integers, reals and the real part of complex numbers are converted to double precision reals. Immediate at compilation.
* Warning, truncation does not cause an error.

Examples
* `ft_complex(12,1)`, `ft_complex(12.,1)`, and `ft_complex(12d0,1)` return `CMPLX(12.0,1)`.





### `ft_float`  (Opcode 452)
|Syntax||
|-|-|
|TDI Syntax   | `FT_FLOAT(_NUM)` |
|Python Syntax| `MDSplus.ft_float(_NUM)` |
|Min arguments| 1 |
|Max arguments| 1 |

Convert to IEEE double precision floating real (64-bit)
* Arguments must be numeric.
* Integers, reals and the real part of complex numbers are converted to double precision reals. Immediate at compilation.
* Warning, truncation does not cause an error.

Examples
* `FT_FLOAT(12)`, `FT_FLOAT(12.)`, and `FT_FLOAT(12D0)` return `12.0`.




### `fun`  (Opcode 171)
|Syntax||
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


### `f_complex` (Opcode 172)
|Syntax||
|-|-|
|TDI Syntax   | `F_COMPLEX(_REALPART,_COMPLEXPART) ` |
|Python Syntax| `MDSplus.F_COMPLEX(_REALPART,_COMPLEXPART) ` |
|Min arguments| 1 |
|Max arguments| 2 |


Converts to F-precision floating complex.
* Arguments must be numeric. Default is zero.
* If Y is absent and X is complex, the AIMAG(X) is used for Y. * If X and Y are present, the real parts of each are used. Immediate at compilation.
* WARNING, truncation does not cause an error. 

Examples:
* `F_COMPLEX(3,4.1D0)` returns `CMPLX(3.0F0,4.1F0)`.



### `f_float` (Opcode 173)
|Syntax||
|-|-|
|TDI Syntax   | `f_float(_NUM) ` |
|Python Syntax| `MDSplus.f_float(_NUM) ` |
|Min arguments| 1 |
|Max arguments| 1 |


Converts to F-precision (OpenVMS) floating real.
* Arguments must be numeric.
* Integers, reals, and the real part of complex numbers are converted to F-precision reals. Immediate at compilation.
* Warning, truncation does not cause an error.0

Examples
* `F_FLOAT(12)`, `F_FLOAT(12.)`, and `F_FLOAT(12D0)` return `12F`.


### `ge` (Opcode 174)
|Syntax||
|-|-|
|TDI Syntax   | `_X >= _Y` |
|Python Syntax| `MDSplus.GE(x, y)` |
|Min arguments| 2 |
|Max arguments| 2 |


Tests for first greater than or equal to second.
* Arguments must both be numeric or character. Complex numbers are result in error.
* Returns True if X is greater than or equal to Y; otherwise,
false. A reserved operand always returns false. Characters are compared in the processor collating sequence.
* Warning: floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that `.1+.1>=.2` is true. Integer values may be truncated when matched to floating numbers.

Examples
* `2>=2.0` returns `$TRUE`.

See also: `eq`, `gt`, `le`, `lt`, `ne`
See [legacy syntax]()


### `GETDBI` (Opcode 389)
|Syntax||
|-|-|
|TDI Syntax   | `getdbi(arg0,arg1)` |
|Python Syntax| `MDSplus.getdbi(arg0,arg1)` |
|Min arguments| 1 |
|Max arguments| 2 |

> TODO: Come back to this after we do tree stuff and write proper examples

Get database information.
Arguments 
 STRING character scalar. The string may be abbreviated in upper or lower case to any unique form.
Logical OPEN_FOR_EDIT modifiable MODIFIED changes made
Long SHOTID shot number NUMBER_OPENED database pointers active MAX_OPEN database pointers allowed
Character NAME experiment name DEFAULT default/current node
INDEX integer scalar less than MAX_OPEN value. Determines which tree location is reported. The default value of 0 is the current tree.
|Result       |Depends on the experiment, shot number, and history.
|See also     |$DEFAULT, $EXPT, $SHOT, and $SHOTNAME constants.


### `GETNCI` (Opcode 175)
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Min arguments| 2
|Max arguments| 3
******Compiler syntax: GETNCI(arg0,arg1,arg2)
|Native python|False|

> TODO: Come back to this after we do tree stuff and write proper examples

|Return Type  |MDS Operation |
Get node characteristic information about tree elements. Arguments Optional: NODE and USAGE.
NODE a NID or long node identifier or a PATH or character form of the path of a tree element--child or member, or a wildcarded path. May be an array. Default is current position in tree.
* WARNING, path names are case-sensitive. STRING character scalar. The string may be abbreviate in upper or lower case to any unique form. Case-insensitive.
USAGE character scalar or vector. This limits the search of NODE names. It must be a valid usage name like "ALL", "ANY", or "TEXT".
The STRING names by returned type follow. Byte unsigned CLASS storage classification DTYPE storage data type USAGE allowed data type Character FULLPATH path from top of tree MINPATH shortest relative path NODE_NAME last part of pathname ORIGINAL_PART_NAME Original node name in device PATH path from top or tagLogicals COMPRESSIBLE has arrays COMPRESS_ON_PUT use comprssion on put DO_NOT_COMPRESS no compression allowed ESSENTIAL node is essential IS_CHILD parent relationshipIS_MEMBER parent relationshipNID_REFERENCE contains nid references NO_WRITE_MODEL write to model disabled NO_WRITE_SHOT write to shot disabled PARENT_STATE parent on or off PATH_REFERENCE contains path references SETUP_INFORMATION has setup operations STATE on or off USAGE_ACTION allows only action USAGE_ANY allows any data USAGE_AXIS allows only axis USAGE_COMPOUND_DATA allows only compound_data USAGE_DEVICE allows only conglomerate USAGE_DISPATCH allows only dispatch USAGE_NUMERIC allows VMS data USAGE_SIGNAL allows only signal USAGE_STRUCTURE allows no data, was NONE USAGE_SUBTREE allows only subtree USAGE_TASK allows only task USAGE_TEXT allows only text USAGE_WINDOW allows only window WRITE_ONCE change only once Long DEPTH tree parents above LENGTH data size NID_NUMBER tree logical offset NUMBER_OF_CHILDREN number of child nodes NUMBER_OF_MEMBERS number of member nodes PARENT_RELATIONSHIP child or member Long unsigned GET_FLAGS bit flags OWNER ID rights identifier
_
STATUS
status
NID
BROTHER
next child or member
CHILD
first child
MEMBER
first member
PARENT the one above in tree NID arrays CHILDREN_NIDS list of children CONGLOMERATE_NIDS MEMBER_NIDS list of members Quadword unsigned TIME_INSERTED VMS date and time Word unsigned CONGLOMERATE_ELT number of elements Node data RECORD actual data
|Signals      |None, except for RECORD. |Units        |None, except for RECORD. |Form         |VECTOR concatenation of all elements found for the list
of NIDs and PATHs. Scalar for non-array results of single input. All data types are the same for one request except possibly for RECORD. Character names varyin length except for NODE_NAME, which has length 12.
|Result       |A scalar or simple vector list of results. RECORD may not be able to VECTOR the results of a list of NIDs/PATHs. Logicals allow easy testing of bit or value.
>>>>>>>>>WARNING, only GETNCI can handle arrays of NIDs/PATHs.
>>>>>>>>>WARNING, a NID/PATH result used in an expression will have its data taken--just as if the node name had been used. Thus GETNCI(\TOP.XRAY,"MEMBER")//" Z" might be "Xray diagnostic Z" if the first member were the description.
|Examples     |GETNCI(\TOP.XRAY,"PARENT") is \TOP as is GETNCI("\TOP.XRAY","par").



### `GOTO`(Opcode 176)
|Syntax||
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

### `gt` (Opcode 177)
|Syntax||
|-|-|
|TDI Syntax   | `arg0 > arg1` or `arg0 gt arg1` |
|Min arguments| 2 |
|Max arguments| 2 |


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



### `g_complex` (Opcode 178)
|Syntax||
|-|-|
|TDI Syntax   | `G_COMPLEX(_X, _Y)` |
|Python Syntax| `MDSplus.G_COMPLEX(_X, _Y)`|
|Min arguments| 1 |
|Max arguments| 2 |


Convert to G-precision floating complex.
Arguments 
* _X numeric
* _Y numeric. Default is zero.
* If Y is absent and X is complex, the AIMAG(X) is Y. If X and Y are present, the real parts of each are used. Immediate at compilation.
* Warning: truncation does not cause an error.

Examples
* `G_COMPLEX (3,4.125)` returns `cmplx(3G0,4.125G0)`
* `G_COMPLEX(3,4.1)` returns `Cmplx(3G0,4.099999904632568G0)`



### `g_float` (Opcode 179)
|Syntax||
|-|-|
|TDI Syntax   | `G_FLOAT(arg0)` |
|Python Syntax| `MDSplus.G_FLOAT(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |


Convert to G-precision floating real.
* argument must be numeric
* Result: Integers, reals and the real part of complex numbers are converted to G-precision reals. Immediate at compilation.
* Warning, truncation does not cause an error.

Examples
* `G_FLOAT(12)`, `G_FLOAT(12.)`, `G_FLOAT(12D0)` all return `12.0G0`.


### `help_of` (Opcode 180)
|Syntax||
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



### `huge` (Opcode 181)
|Syntax||
|-|-|
|TDI Syntax   | `huge(arg0)` |
|Python Syntax| `MDSplus.huge(arg0)` |
|Min arguments| 1 |
|Max arguments| 1 |

The largest number in the model representing numbers of the same type as the argument.
Arguments X must be numeric scalar or array.

The result is `r^q -1` if X is integer and `(1-(b^-p))b^emax` if X is real, where:
* `r` is the integer base,
* `q` is the number of digits,
* `b` is the real base, 
* `p` is the number of digits, 
* `emax` is the maximum exponent in model numbers like X.

Examples
* HUGE(1.0) is (1-(2^-24))*2^127 and HUGE(0) is 2^31-1 on the VAX.
* huge(1.0) returns `340.282E36`
* huge(1) returns `2147483647`
* huge(1F0) returns `170.141F36`

> TODO: come back to this for further investigation


### `h_complex` (Opcode 182)
|Syntax||
|-|-|
|TDI Syntax   | `H_COMPLEX(arg0,arg1) ` |
|Python Syntax| `MDSplus.H_COMPLEX(arg0,arg1) ` |
|Min arguments| 1 |
|Max arguments| 2 


> TODO: come back to these, possibly delete, these may be deprecated 

Conversion Elemental.
Convert to H-precision floating complex.
Arguments Optional: Y. X numeric. Y numeric. Default is zero.
|Signals      |Single signal or smaller data. |Units        |Single or common units, else bad. |Form         |H-precision complex of compatible shape.
|Result       |If Y is absent and X is complex, the AIMAG(X) is Y. If X and Y are present, the real parts of each are used. Immediate at compilation.
|Examples     |H_COMPLEX(3,4.1) is CMPLX(3.0H0,4.1H0), approximately.


### `H_FLOAT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 183
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: H_FLOAT(arg0) 
|Native python|False|

> TODO: come back to these, possibly delete, these may be deprecated 


Conversion Elemental.
Convert to H-precision floating real.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |H-precision real of same shape.
|Result       |Integers, reals and the real part of complex numbers are converted to H-precision reals. Immediate at compilation.
|Examples     |H_FLOAT(12), H_FLOAT(12.) H_FLOAT(12H0) are 12.0H0, approximately.


### `iachar`(Opcode 184)
|Syntax||
|-|-|
|TDI Syntax   | `iachar(_CHAR)` |
|Python Syntax| `MDSplus.iachar(_CHAR)` |
|Min arguments| 1 |
|Max arguments| 1 |

Returns the position of _CHAR in the ASCII collating sequence, where `0<=IACHAR('C')<=127`; otherwise, a processor value.
* Argument must be a C must be a length-one character.


See also: 
* `lle`, 
* `ichar` and the inverses `achar` and `char`.

> TODO: Figure out if `ichar` and `iachar` are the same (looks like it!) because `char` and `achar` appear to be the same

Examples
* `iachar('X')` returns `88BU`.


### `iand` (Opcode 185)
|Syntax||
|-|-|
|TDI Syntax   | `Arg0 & arg1 ` |
|Python Syntax| `MDSplus.Arg0 & arg1 ` |
|Min arguments| 2
|Max arguments| 2

Bitwise intersection.
* Usual Form `I & J`. 
* Function Form `IAND(I,J)`.
* Arguments I and J must be integers.
* Returns: True for each bit true in I and J; otherwise, false.

|Signals      |Single signal or smaller data. |Units        |Single or common units, else bad. |Form         |Unsigned integer of compatible shape.

Examples
* `IAND(3,5)` returns `1`  
   with 3 being `011`  
   and  5 being `101`,  
   this returns `001` or simply `1`.



### `iand_not` (Opcode 186)
|Syntax||
|-|-|
|TDI Syntax   | `iand_not(arg0,arg1) ` |
|Python Syntax| `MDSplus.iand_not(arg0,arg1) ` |
|Min arguments| 2 |
|Max arguments| 2 |

Bit-wise Elemental.
Bit-by-bit intersection with the J complemented.
* Arguments I and J must be integers.
Returns True for each bit of I true and of J false; otherwise, false.

f compatible shape.

Examples
* `IAND_NOT (3,5)` returns `2`  
   with 3 being `011`  
   and  5 being `101`,  
   this returns `010` or simply `2`.

See also:
`iand`, `ior`


### `ibclr` (Opcode 63)
|Syntax||
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
|Syntax||
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



### `ICHAR` (Opcode 187)
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: ICHAR(arg0)


> TODO: Mark will pick up content from CHAR


The position of a character in the processor collating sequence.
|Arguments, Results|C must be a length-one character.
|Signals      |Same as C. |Units        |Same as C. |Form         |Byte unsigned of same shape.
|Result       |The position of C in the processor collating sequence and is in the range 0<=ICHAR(C)



### `ident_of` (Opcode 188)
|Syntax||
|-|-|
|TDI Syntax   | `ident_of(arg0)` |
|Python Syntax| `MDSplus.ident_of(arg0)` |
|Min arguments| 1
|Max arguments| 1

Get the ident field.
* `DISPATCH_OF(A)` is searched for this: `DSC$K_DTYPE_DISPATCH`, the ident field. Otherwise, an error.



### `ieor` (Opcode 210)

|Syntax||
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
|Syntax||
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


### `IF` (Opcode 189)
|Syntax||
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



### `if_error` (Opcode 190)
|Syntax||
|-|-|
|TDI Syntax   | `IF_ERROR(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.IF_ERROR(arg0,arg1,argn,...)` |
|Min arguments| 1   |
|Max arguments| 254 |

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



### `image_of` (Opcode 191)
|Syntax||
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



### `in` (Opcode 192)

Used in `fun` definition to denote argument is readonly.
Please see `fun` for more information.


### `inand` (Opcode 193)
|Syntax||
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
|Syntax||
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




### `index` (Opcode 195)
|Syntax||
|-|-|
|TDI Syntax   | `index(_STRING,_SUBSTRING,[_BACK]) ` |
|Python Syntax| `MDSplus.index(_STRING,_SUBSTRING,[_BACK]) ` |
|Min arguments| 2 |
|Max arguments| 3 |

The starting position of a substring within a string. Note the result is 1 less than for F90.

Arguments 
* `_STRING` character. 
* `_SUBSTRING` character. 
* `[BACK]` Optional: logical/bool. Tells the function to retrieve either the first or last instance of the `_SUBSTRING`, if true.

Results
* If `_BACK` is absent or is false, the postition of first instance of the `_SUBSTRING` will be returned  or `-1` if there is no such value.  
    * For `len(_STRING) < len(_SUBSTRING)`, the result is `-1` 
    * For `len(_SUBSTRING) = 0`, the result is `0`.
* If `_BACK` present and true, the position of the last instance of the `_SUBSTRING` will be returned or `-1` if there is no such value.
    * For `len(_STRING) < len(_SUBSTRING)`, the result is `-1` 
    * For `len(_SUBSTRING) = 0`, the result is `0`.

Examples. 
* `INDEX('FORTRAN','R')` is `2`.
* `INDEX('FORTRAN','R',$TRUE)` is `4`.



### `inor` (Opcode 196)
|Syntax||
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



### `inor_not` (Opcode 197)
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: INOR_NOT(arg0,arg1) 
|Native python|False|

>TODO: Mark to clean up the formatting, as above

Bit-wise Elemental.
Complement of bit-by-bit union with the second complemented. Equivalant to IAND(NOT(I),J).
Arguments I and J must be integers.
|Signals      |Single signal or smaller data. |Units        |Single or common units, else bad. |Form         |Unsigned integer of compatible shape.
|Result       |False for each bit of I true or of J false; otherwise, true.
|Examples     |`INOR_NOT(3BU,5BU)` in binary is `0B00000100BU`.


### `INOT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 198
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: ~arg0 
|Native python|False|

> TODO: Mark to clean up formatting, as per above bitwise functions

Bit-wise Elemental.
Complement bit-by-bit the argument.
Usual Form ~ J. Function Form INOT(J).
|Arguments, Results|J must be integer.
|Signals      |Same as J. |Units        |Same as J. |Form         |Unsigned integer of same shape. |Result       |Each binary bit is negated. >>>>>>>>>WARNING, F90 calls this NOT, we cannot.
|Examples     |`INOT(5BU)` in binary is `0B11111010`.



### `INOUT` (Opcode 199)

Used in `FUN` definitions to indicate that argument is used for input and output.

Please see `FUN` for more information

Example:
`PUBLIC FUN _MYFUN(INOUT _ARG)`



### `INT` (Opcode number: 201)
|Syntax||
|-|-|
|TDI Syntax   | `INT(arg0,arg1)` |
|Python Syntax| `MDSplus.INT(arg0,arg1)` |
|Min arguments| 1 |
|Max arguments| 2 |

Converts to integer.
* Arguments must numeric.
* Second argument is kind
* Immediate at compilation.

* A is integer or real, the result is the truncated approximation to the low-order part of the integer.
* If A is complex, the result is the approximation to the
real part. 
* WARNING, truncation does not cause an error.

Examples
* `INT(2.783)` returns `2`.
* `INT(2.783, 5d0)` returns `3Q`.



### `INT_UNSIGNED`
|Syntax||
|-|-|
|TDI Syntax   | `INT_UNSIGNED(arg0) ` |
|Python Syntax| `MDSplus.INT_UNSIGNED(arg0) ` |
(Opcode 205
|Min arguments| 1
|Max arguments| 1

> TODO: Mark to ref

Conversion Elemental.
Convert to unsigned integer.
Arguments A must numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |The integer type with the same length. To get specific unsigned integer types use BYTE_UNSIGNED, WORD_UNSIGNED, LONG_UNSIGNED, QUADWORD_UNSIGNED, or OCTAWORD_UNSIGNED.
|Result       |Immediate at compilation.
(i)
A is integer or real, the result is the truncated approximation to the low-order part of the integer.
(ii)
A is complex, the result is the approximation to the
real part. >>>>>>>>>WARNING, truncation does not cause an error.
|Examples     |`INT_UNSIGNED(2.783)` is `2LU`.


### `INTERRUPT_OF` (Opcode 443)
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: INTERRUPT_OF(arg0) 
|Native python|False|

> TODO: Come back to this for further investigation; we don't currently have any good examples with interrupts

|Return Type  |MDS Operation |
Get the interrupt field.
|Arguments, Results|Descriptor as below.
|Result       |DISPATCH_OF(A) is searched for this: DSC$K_DTYPE_DISPATCH, the interrupt field. The dispatch qualifier must be TREE$K_SCHED_ASYNC and the result must evaluate to text DSC$K_DTYPE_T. Otherwise, an error.



### `IOR` (Opcode 207)
|Syntax||
|-|-|
|TDI Syntax   | `_I \| _J` or `ior(_I, _J)` |
|Python Syntax| `MDSplus.ior(_I, _J)` |
|Min arguments| 2 |
|Max arguments| 2 |

> TODO: Mark to clean up formatting, as per above bit-wise functions

Bit-by-bit inclusive OR.
* Arguments `_I` and `_J` must be integers.
* Returns True for either bit true in `_I` and `_J`; otherwise, false. 

Examples     
`IOR(3BU,5BU)` returns `7BU`.



### `ior_not` (Opcode 208)
|Syntax||
|-|-|
|TDI Syntax   | `ior_not(_I, _J)` |
|Python Syntax| `MDSplus.IOR_NOT(_I, _J)` |
|Min arguments| 2 |
|Max arguments| 2 |


Bit-wise/bit-by-bit union with the second complemented.
* Arguments `_I` and `_J` must be integers.
* Returns True for each bit of I true or of J false; otherwise, false.

Examples
* `IOR_NOT(3BU,5BU)` in binary is `0B11111011BU`


### `ishft` (Opcode 312)
|Syntax||
|-|-|
|TDI Syntax   | `ishft(_I,_SHIFT) ` |
|Python Syntax| `MDSplus.ishft(_I,_SHIFT) ` |
|Min arguments| 2 |
|Max arguments| 2 |


Logical bit-wise shift of an element.
* Arguments
    * `_I` must be integer. Octaword is not supported. 
    * `_SHIFT` must be integer. The low byte is used.
* Returns the bits of `_I` shifted `_SHIFT` positions left if positive or right if negative. The vacated bits are cleared.

Examples
* `ISHFT(3,1)` returns `6`.




### `i_to_x` (Opcode 392)
|Syntax||
|-|-|
|TDI Syntax   | `i_to_x(_DIMENSION,[_I])` |
|Python Syntax| `MDSplus.i_to_x(_DIMENSION,[_I])` |
|Min arguments| 1 |
|Max arguments| 2 |


Converts index into axis values.

Arguments:
* `DIMENSION` a dimension with optional window and required axis. If DIMENSION is missing, the unchanged I is returned.
If the window of DIMENSION is missing, the first axis point is assigned an index of 0.
* `[_I]` optional: scalar or array list of axis integer-like values. (For TDI$I_TO_X, the fake address of -1 for I, returns a 2-element vector with the axis bounds.)
* Signals: Same as I.
* Units: Same as axis of DIMENSION.
* Form: Same type as DATA(axis). Same shape as I.

Result
* The window and axis are evaluated for each index point. Although the window start and end indices may be used to determine the value of axis points, they do not limit the range of results.

Examples:
* `I_TO_X(BUILD_DIM(BUILD_WINDOW(2,5,1.1),BUILD_RANGE(,, 3)))` is `Set_Range(2:5,[7.1,10.1,13.1,16.1])`. 
* `I_TO_X(BUILD_DIM(BUILD_WINDOW(2,7,1.1),BUILD_RANGE(,, 3)),1:4)` is `Set_Range(1:4,[4.1,7.1,10.1,13.1])`. The index 1 (axis point 4.1) is outside the valid window of 2 to 7.

See also:
* `CULL` and `EXTEND` to discard or limit axis points.
* `X_TO_I` for the inverse transform. 
* `NINT` to round indices to the nearest integers. 
* `SUBSCRIPT` where this is used for ranges.


### `KIND` (Opcode 137)
|Syntax||
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

See also: `kind_of`

### `KIND_OF` (Opcode 437)
|Syntax||
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

Examples
* KIND_OF(3) is 8 (DTYPE_L).
* KIND_OF(1.2) is 10 (DTYPE_F). 
* KIND_OF(_X) is 191 (DTYPE_IDENT).



### `LABEL`
|Syntax||
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


### `LANGUAGE_OF` (Opcode 214)
|Syntax||
|-|-|
|TDI Syntax   | `LANGUAGE_OF(`_A`) ` |
|Python Syntax| `MDSplus.LANGUAGE_OF(`_A`) ` |
|Min arguments| 1 |
|Max arguments| 1 |


Get the language field.
Argument `_A` is searched for within `DSC$K_DTYPE_PROCEDURE`, the language field. Otherwise, an error.

>TODO: Come back to this? maybe?



### `LASTLOC` (Opcode 215)
|Syntax||
|-|-|
|TDI Syntax   | `LASTLOC(_MASK,[_DIM])` |
|Python Syntax| `MDSplus.LASTLOC(_MASK,[_DIM])` |
|Min arguments| 1 |
|Max arguments| 2 |


Locates the trailing edges of a set of true elements of a logical mask.

Arguments 
* `_MASK` logical array. 
* `[_DIM]` optional: integer scalar from 0 to n-1, where n is rank of MASK.

Results
* `LASTLOC(MASK)` has at most one true element. If there is a true value, it is the first in array element order.
* `LASLOC(MASK,DIM)` is found by applying LASTLOC to each of the one-dimensional array sections of MASK that lie parallel to dimension DIM.

Examples:
With `_M = [[0, 0, 0], [0, 0, 1], [0, 1, 0], [1, 0, 1]]`

```
TDI> LASTLOC(_M)
Byte_Unsigned([[0,0,0], [0,0,0], [0,0,0], [0,0,1]])
TDI> LASTLOC(_M, 0)                                          
Byte_Unsigned([[0,0,0], [0,0,1], [0,1,0], [0,0,1]])
TDI> LASTLOC(_M, 1)                                          
Byte_Unsigned([[0,0,0], [0,0,0], [0,1,0], [1,0,1]])
```



### `LBOUND` (Opcode 130)
|Syntax||
|-|-|
|TDI Syntax   | `LBOUND(_ARRAY, [_DIM])` |
|Python Syntax| `MDSplus.LBOUND(_ARRAY, [_DIM])` |
|Min arguments| 1 |
|Max arguments| 2 |


All the lower bounds of an array or signal or a specified lower bound.

Arguments
* `_ARRAY`: any type array or signal. 
* `[_DIM]`: integer scalar from 0 to n-1, where n is rank of ARRAY.
* Scalar if DIM present, otherwise, vector of size n.  
    Integer for an array;  
    combined type of dimensions for a signal.
* ELBOUND(ARRAY,DIM) is equal to the lower bound for subscript DIM of ARRAY. If no bounds were effective it is 0. ELBOUND(ARRAY) is whose j-th component is equal to ELBOUND(ARRAY,j) for each j, 0 to n-1. For a signal, the lower bound on the dimension if it is of DTYPE_DIMENSION, else as for an array.

Examples:
* `lbound(_A=set_range(2:3,7:10,0))` returns `[2,7]` and   
`lbound(_A,0)` returns `2` and  
`lbound(_A,1)` returns `7`.


See also:
* `UBOUND` for upper bound, SHAPE for number of elements, SIZE for total elements, and E... for signals.
* `ELBOUND` (alternate spelling, same function)


### `le` (Opcode 216)
|Syntax||
|-|-|
|TDI Syntax   | `_X <= _Y`, `_X le _Y`, or `le(_X,_Y)` |
|Python Syntax| `MDSplus.le(_X, _Y)`|
|Min arguments| 2 |
|Max arguments| 2 |

Tests for first argument less than or equal to second argument.
* Arguments X and Y must both be numeric or character.
* Complex numbers are an error.

Returns True if X is less than or equal to Y; otherwise, false. * A reserved operand is always false.
* Characters are compared in the processor collating sequence.
* WARNING, floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that .1+.1<=.2 is true. Integer values may be truncated when matched to floating numbers.

Examples
* `2<=2.0` returns `$TRUE`

See also: `eq`, `ge`, `gt`, `lt`, `ne`



### `len` (Opcode 217)
|Syntax||
|-|-|
|TDI Syntax   | `len(_STRING) ` |
|Python Syntax| `MDSplus.len(_STRING) ` |
|Min arguments| 1
|Max arguments| 1



The length of a character entity or the number of bytes in numeric data (extension).  
* Argument _STRING is a string/character array. <!-- An array may appear to work but currently always returns 4. -->  
* Returns The number of characters in STRING if it is scalar or in an element of STRING if it is an array.  

Examples  
* LEN('abcdefghijk') returns 11.

> TODO: len for arrays appears to be broken  
* `LEN([1,2,3, 4, 5, 6, 7, 8])` returns `4`




### `len_trim` (Opcode 218)
|Syntax||
|-|-|
|TDI Syntax   | `len_trim(_STRING)` |
|Python Syntax| `MDSplus.len_trim(_STRING)` |
|Min arguments| 1 |
|Max arguments| 1 |

Length of the character argument without trailing blank or tab characters.
* Argument _STRING must be character.
* Returns the number of characters after any trailing blanks or tabs are removed.
* If STRING has no nonblanks other than tabs the result is 0.
* Warning: any leading whitespaces are kept and counted as characters.

Examples: 
* `len_trim(' A B    ')`returns `4` 
* `len_trim(' ')` returns `0`.

See also, `adjustl`, `adjustr`, `trim`, `len` 



### `lge` (Opcode 219)
|Syntax||
|-|-|
|TDI Syntax   | `lge(_STRING0, _STRING1)` |
|Python Syntax| `MDSplus.lge(_STRING0, _STRING1)` |
|Min arguments| 2
|Max arguments| 2


Tests whether a string is lexically greater than or equal to another string based on the ASCII collating sequence.
* Arguments STRING0 and STRING1 must be characters.
* Result: If the strings are of unequal length, the comparison is made as if the shorter string were extended on the right with blanks to the length of the longer string. If either string has a character not in the ASCII character set, the result is processor dependent. The result is true if the strings are equal or if STRING0 follows STRING1 in the collating sequence; otherwise, false.

Examples
* `lge('ABC','XYZ')` returns `$FALSE`.
* `lge('ABC','ABC')` returns `$TRUE`
* `lge('XYZ','ABC')` returns `$TRUE`

See also: `iachar`, `lgt`, `lle`, `llt`



### `lgt` (Opcode 220)
|Syntax||
|-|-|
|TDI Syntax   | `LGT(_STRING0, _STRING1)` |
|Python Syntax| `MDSplus.LGT(_STRING0, _STRING1)` |
|Min arguments| 2
|Max arguments| 2


Tests whether a string is lexically greater than another string based on the ASCII collating sequence.
* Arguments _STRING0, _STRING1 must be character.
* Results: If the strings are of unequal length, the comparison is made as if the shorter string were extended on the right with blanks to the length of the longer string. 
* If either string has a character not in the ASCII character set, the result is processor dependent. The result is true if STRING_A follows STRING_B in the collating sequence; otherwise, false.

Examples
* `lgt('ABC','XYZ')` returns `$FALSE`
* `lgt('ABC','ABC')` returns `$FALSE`
* `lgt('XYZ','ABC')` returns `$TRUE`

See also: `iachar`, `lge`, `lle`, `llt`



### `lle` (Opcode 221)
|Syntax||
|-|-|
|TDI Syntax   | `lle(_STRING0, _STRING1)` |
|Python Syntax| `MDSplus.lle(_STRING0, _STRING1)` |
|Min arguments| 2 |
|Max arguments| 2 |


Tests whether a string is lexically less than or equal to another string based on the ASCII collating sequence.
* Arguments _STRING0, _STRING1 must be characters.
* If the strings are of unequal length, the comparison is made as if the shorter string were extended on the right with blanks to the length of the longer string. 
* If either string has a character not in the ASCII character set, the result is processor dependent. The result is true if the strings are equal or if STRING_A follows STRING_B in the collating sequence; otherwise, false.


Examples     

`lle('ABC','XYZ')` is `$TRUE`
`lle('ABC','ABC')` is `$TRUE`
`lle('XYZ','ABC')` is `$FALSE`

See also: `iachar`, `lge`, `lgt`, `llt`



### `llt` (Opcode 222)
|Syntax||
|-|-|
|TDI Syntax   | `LLT(_STRING0, _STRING1)` |
|Python Syntax| `MDSplus.LLT(_STRING0, _STRING1)` |
|Min arguments| 2 |
|Max arguments| 2 |


Tests whether a string is lexically less than another string based on the ASCII collating sequence.
* Arguments _STRING0 and _STRING1 must be character.
* If the strings are of unequal length, the comparison is made as if the shorter string were extended on the right with blanks to the length of the longer string.
* If either string has a character not in the ASCII character set, the result is processor dependent. The result is true if _STRING0 follows _STRING1 in the collating sequence; otherwise, false.


Examples
* `llt('ABC','XYZ')` returns `$TRUE`
* `llt('ABC','ABC')` returns `$FALSE`
* `llt('XYZ','ABC')` returns `$FALSE`

See also: `iachar`, `lge`, `lgt`, `lle`



### `log` (Opcode 223)
|Syntax||
|-|-|
|TDI Syntax   | `log(_NUM) ` |
|Python Syntax| `MDSplus.log(_NUM) `|
|Min arguments| 1 |
|Max arguments| 1 |


Natural logarithm.
* Argument _NUM must be real or complex, HC is converted to GC.
* Units are disregarded
* Returns processor approximation to log X (base e). A complex result is the principal value with imaginary part in the range -pi to pi. The imaginary part of the result is pi only when the real part of X is less than zero and the imaginary part of X is zero.

Examples  
* `LOG(10.0)` returns `2.30259`
* `log(cmplx(2,3))` returns `Cmplx(1.28247,.982794)`

See also: `log10` for base-10 log


### `log10`  (Opcode 224)  
> (version 1--original)
|Syntax||
|-|-|
|TDI Syntax   | `log10(_NUM)` |
|Python Syntax| `MDSplus.log10(_NUM)` |


Common logarithm (base 10).
* Argument `_NUM` must be real.
* Complex numbers result in error.
* Units are disregarded

Examples
* `log10(10.0)` returns `1.0`.




### `LOG10` (Base-10 Logarithm)

> (version 2--opcode moved, natural language title)  

|Syntax||
|-|-|
|TDI Syntax   | `LOG10(_NUM)` |
|Python Syntax| `MDSplus.log10(_NUM)` |
|Opcode |224 (0xE0)|

Common logarithm (base 10).
* Argument `_NUM` must be real.
* Complex numbers result in error.
* Units are disregarded

Examples
```tdi
TDI> log10(10.0)
1.0
```


### `log2` (Opcode 225)
|Syntax||
|-|-|
|TDI Syntax   | `LOG2(_NUM)` |
|Python Syntax| `MDSplus.LOG2(_NUM)` |
|Min arguments| 1 |
|Max arguments| 1 |

Logarithm, base 2.
* Argument `_NUM` must be real. Complex numbers result in error.
* Units are disregarded

Examples
* `log2(8.0)` returns `3.0`.



### `logical`
(Opcode 226)
|Syntax||
|-|-|
|TDI Syntax   | `LOGICAL(_NUM, [_KIND])` |
|Python Syntax| `MDSplus.LOGICAL(_NUM, [_KIND])` |
|Min arguments| 1
|Max arguments| 2


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


### `long` (Opcode 227)
|Syntax||
|-|-|
|TDI Syntax   | `LONG(_NUM)` |
|Python Syntax| `MDSplus.LONG(_NUM)` |
|Min arguments| 1
|Max arguments| 1


Convert a number to long (four-byte) integer.
* Argument _NUM must be numeric.
* Returns The truncated whole part of A.
* Immediate at compilation. 
* WARNING, truncation does not cause an error.
Examples
* `long(123.4)` is `123`.


### `long_unsigned` (Opcode 228)
|Syntax||
|-|-|
|TDI Syntax   | `long_unsigned(_NUM) ` |
|Python Syntax| `MDSplus.long_unsigned(_NUM)` |
|Min arguments| 1
|Max arguments| 1

Converts to long (four-byte) unsigned integer.
* Argument _NUM must be numeric.
* Returns the truncated whole part of A. 
* Immediate at compilation. 
* Warning, truncation does not cause an error.

Examples
* `long_unsigned(123)` returns `123LU`.
* `long_unsigned(-1)` returns `4294967295LU`.


### `lt` (Opcode 229) 

> (option 1--original)

|Syntax||
|-|-|
|TDI Syntax   | `_X < _Y`, `_X LT _Y`, or function form `LT(_X, _Y)` |
|Python Syntax| `MDSplus.LT(X,Y)` |



Tests for first argument less than second.
* Arguments _X and _Y must both be numeric or character.
* Complex numbers result in error.
* Returns True if _X is less than _Y; otherwise, false.
* A reserved operand is always false.
* Characters are compared in the processor collating sequence.
* WARNING, floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that .1+.1<=.2 is true. Integer values may be truncated when matched to floating numbers.

Examples
* `2<2.0` returns `$FALSE`.
* `2 lt 2.1` returns `$TRUE`.
* `lt(2.1, 2)` returns `$FALSE`

See also: `eq`, `ge`, `gt`, `le`, `ne`


### `lt` (Less Than)

> (option 2 gussied up)

|Syntax||
|-|-|
|TDI Syntax   | `_X < _Y`, `_X LT _Y`, or function form `LT(_X, _Y)` |
|Python Syntax| `MDSplus.LT(X,Y)` |
|Opcode       |229 (0xFF) TODO |



Tests for first argument less than second.
* Arguments _X and _Y must both be numeric or character.
* Complex numbers result in error.
* Returns True if _X is less than _Y; otherwise, false.
* A reserved operand is always false.
* Characters are compared in the processor collating sequence.
* WARNING, floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that .1+.1<=.2 is true. Integer values may be truncated when matched to floating numbers.

Examples
```tdi
TDI> 2 < 2.0
0BU

TDI> 
```
* `2<2.0` returns `$FALSE`.
* `2 lt 2.1` returns `$TRUE`.
* `lt(2.1, 2)` returns `$FALSE`

See also: `eq`, `ge`, `gt`, `le`, `ne`



### `MAKE_ACTION`
|Syntax||
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
MAKE_CALL
### `MAKE_CALL`
|Syntax||
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
MAKE_CONDITION
### `MAKE_CONDITION`
|Syntax||
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
MAKE_CONGLOM
### `MAKE_CONGLOM`
|Syntax||
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
MAKE_DEPENDENCY
### `MAKE_DEPENDENCY`
|Syntax||
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
MAKE_DIM
### `MAKE_DIM`
|Syntax||
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
MAKE_DISPATCH
### `MAKE_DISPATCH`
|Syntax||
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
MAKE_FUNCTION
### `MAKE_FUNCTION`
|Syntax||
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
MAKE_METHOD
### `MAKE_METHOD`
|Syntax||
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
MAKE_OPAQUE
### `MAKE_OPAQUE`
|Syntax||
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
MAKE_PARAM
### `MAKE_PARAM`
|Syntax||
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
MAKE_PROCEDURE
### `MAKE_PROCEDURE`
|Syntax||
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
MAKE_PROGRAM
### `MAKE_PROGRAM`
|Syntax||
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
MAKE_RANGE
### `MAKE_RANGE`
|Syntax||
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
MAKE_ROUTINE
### `MAKE_ROUTINE`
|Syntax||
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
MAKE_SIGNAL
### `MAKE_SIGNAL`
|Syntax||
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
MAKE_SLOPE
### `MAKE_SLOPE`
|Syntax||
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
MAKE_WINDOW
### `MAKE_WINDOW`
|Syntax||
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
MAKE_WITH_ERROR
### `MAKE_WITH_ERROR`
|Syntax||
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
MAKE_WITH_UNITS
### `MAKE_WITH_UNITS`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 433
|Min arguments| 2
|Max arguments| 2
Compiler syntax: MAKE_WITH_UNITS(arg0,arg1)

|Native python|False|

Description:
|Return Type  |MDS Operation |
Make a describe data with units.
Arguments
DATA any expression that DATA(this) will be valid.
UNITS character string. See the primary section on "Units".
|Result       |Class-R descriptor. Use BUILD_xxx for immediate structure building. Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
|Examples     |_S = MAKE_WITH_UNITS($VALUE*6,'m/s^2') can be used in a MAKE_SIGNAL(_S,MAKE_WITH_UNITS(5./1024*raw_node,'V') or similar. Note this could also have been MAKE_WITH_UNITS(MAKE_SIGNAL($VALUE*6, MAKE_WITH_UNITS(5./1024*raw_node,'V')),'m/s^2').



### `MAP`
|Syntax||
|-|-|
|TDI Syntax   | `MAP(_ARRAY,_OFFSET)` |
|Python Syntax| `MDSplus.MAP(_ARRAY,_OFFSET)` |
|Min arguments| 2 |
|Max arguments| 2 |
|Opcode|394|

Element selection from an array. Basically, it lets you grab sub-samples from an array or sort it out. See examples

Arguments
* `_ARRAY` (A) an array of any type considered to be a vector.
* `_OFFSET` (B) a list of offsets into the `_ARRAY`.  
Values are from 0 to the number of elements in A less 1. Out-of-bounds values are considered to be at the limits.

|Signals      |Same as B. 
|Units        |Same as A. 
|Form         |Same type as A and same shape as B.
|Result       |Each value in B is used to look up a value in A. The value is copied into the result. This is the same as A(B) in IDL when B is a vector.
* WARNING, multidimensional arrays referenced by bad offsets will likely be junk.

Examples

```tdi
 TDI> MAP(1:10,[20,-1,5])
 [10,1,6]
 
 _A=5:1:-1
 
 TDI> MAP(_A,SORTI(_A))
 [1,2,3,4,5]
 # note that this is the same as SORT(5:1:-1).
```

See also:

* CULL to remove bad B values. 
* SUBSCRIPT for dimensional indexing into signal and multiple index access to arrays.



### `MAX`
|Syntax||
|-|-|
|TDI Syntax   | `MAX(_NUM0, _NUM1, _NUM2,...)` |
|Python Syntax| `MDSplus.MAX(_NUM0, _NUM1, _NUM2,...)` |
|Min arguments| 2  |
|Max arguments| 254|
|Opcode|233|

Returns the maximum (highest?) value.
* Arguments must be integer or real. Complex numbers cause error.
* Signals: The single signal or the smallest.
* Units: The single or matching units, else bad. 
* Form: The compatible form of all the arguments. Conversion is done pairwise.
* Result: The largest 
* Arguments, Results: A reserved operand will dominate.

Examples

```tdi
TDI> MAX(-9.0,7.0,2.0) 
7.0
```

### `MAXEXPONENT`
|Syntax||
|-|-|
|TDI Syntax   | `MAXEXPONENT(_NUM)` |
|Python Syntax| `MDSplus.MAXEXPONENT(_NUM)` |
|Opcode|234|


The maximum exponent in the model representing numbers of the same type as the argument.
|Arguments, Results|X is real, scalar or array.
|Signals      |None. 
|Units        |None. 
|Form         |Integer scalar.
|Result       |The number emax for the model of the same type as X. 

Examples
```tdi
MAXEXPONENT(1.0) is 127 on the VAX.
```



### `MAXLOC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
|Min arguments| 1|
|Max arguments| 3|
******Compiler syntax: MAXLOC(_ARRAY, [_MASK], [_arg3])

|Opcode|235|


Determine the location of an element of ARRAY with the maximum value of the elements identified by MASK.

Arguments 
* `_ARRAY` numeric array. 
* `[_MASK]` Optional: logical and conformable with ARRAY.
* `[_arg3]`: TODO: investigate further 

|Signals      |None. |Units        |None. |Form         |Long vector of size equal to rank of ARRAY.
|Result       |The result is the vector of subscripts of an element whose value equals the maximum of all elements of ARRAY or all elements for which MASK is true. Reserved operands ($ROPRAND) are ignored. Each subscript will be in the extent of its dimension. For zero size, no true elements in MASK, or all $ROPRAND the result is undefined. If more than one element has the maximum value the result is the first in array order. The result is an offset vector even if there is a lower bound.
Examples
```
TDI> MAXLOC([2,4,6])
[2]

_A=[0 -5 8 -3]
TDI> MAXLOC(_A,_A LT 6)
[2,1]. [3 4-1 2][1 5 6-4]
# TODO: investigate further
```


|See also     |MAXVAL for the value.




### `MAXVAL`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 236
|Min arguments| 1
|Max arguments| 3
******Compiler syntax: MAXVAL(arg0,arg1,arg2)
|Native python|False|


|Return Type  |F90 Transformation |
Maximum value of the elements of ARRAY along
dimension DIM corresponding to true elements of MASK.
Arguments Optional: DIM, MASK. ARRAY numeric array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY. MASK logical and conformable to ARRAY.
|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. |Units        |Same as ARRAY. |Form         |Same type as ARRAY. It is a scalar if DIM is absent or
ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.
|Result       |The result without DIM is the maximum value of the elements of ARRAY, testing only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the maximum of ARRAY elements with DIM dimension fixed as the element number of the result. If no value is found, -HUGE(ARRAY) is returned.
Examples. MAXVAL([1,2,3]) is 3. MAXVAL(_C,,_C LT 0) finds the maximum negative element of C. If _B=[[1, 3, 5],[2, 4, 6]] MAXVAL(_B,0) is [5,6] and MAXVAL(_B,1) is [2,4,6].
|See also     |MAXLOC for the location.
MEAN
### `MEAN`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 237
|Min arguments| 1
|Max arguments| 3
******Compiler syntax: MEAN(arg0,arg1,arg2) 
|Native python|False|


|Return Type  |Transformation |
Average value of the elements of ARRAY along dimension DIM corresponding to the true elements of MASK.
Arguments Optional: DIM, MASK. ARRAY numeric array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY. MASK logical and conformable to ARRAY.
|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. |Units        |Same as ARRAY. |Form         |Same type as ARRAY. It is a scalar if DIM is absent or
ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.
|Result       |The result without DIM is the mean value of the elements of ARRAY, testing only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the mean of ARRAY elements with dimension DIM fixed as the element number of the result. If no value is found, zero is given.
Examples. MEAN([1,2,3]) is 2. MEAN(_C,,_C GT 0) finds the mean of positive element of C. If : _B=[[1, 3, 5],[2, 4, 6]] MEAN(_B,0) is [3,4] and MEAN(_B,1) is [1,3,5].
MERGE
### `MERGE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 239
|Min arguments| 3
|Max arguments| 3
******Compiler syntax: MERGE(arg0,arg1,arg2) 
|Native python|False|


F90 Logical Elemental.
Choose alternative value according to a mask.
Arguments TSOURCE any type compatible with FSOURCE. FSOURCE any type compatible with TSOURCE. MASK logical, conformable with TSOURCE and FSOURCE.
|Signals      |Single signal or smaller data. |Units        |Single or common units (excluding MASK), else bad. |Form         |The type is the compatible type of FSOURCE and TSOURCE.
The shape conformable to FSOURCE, TSOURCE, and MASK.
|Result       |If the MASK value is true, the TSOURCE value is use; otherwise, the FSOURCE value is use.
Examples. MERGE([1,2,3],[4,5,6],[$TRUE,$FALSE,$TRUE]) is [1,5,3]. If TSOURCE is the array [1 6 5], FSOURCE is the array[24 6]
[032] andMASK is[1 01], [748] [001]then MERGE(TSOURCE,FSOURCE,MASK) is[1 3 5].
[7 4 6]
|See also     |CONDITIONAL with form: MASK ? TSOURCE : FSOURCE, for scalar mask test.
METHOD_OF
### `METHOD_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 240
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: METHOD_OF(arg0)Native python: True

|Return Type  |MDS Operation |
Get the method field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this:
DSC$K_DTYPE_METHOD, the method field.
Otherwise, an error.
MIN
### `MIN`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 241
|Min arguments| 2
|Max arguments| 254
Compiler syntax: MIN(arg0,arg1,argn,...)

|Native python|False|

Description:
|Type         |F90 Numeric Elemental|
Minimum value.
Arguments Integer or real. Complex numbers are an error.
|Signals      |The single signal or the smallest.
|Units        |The single or matching units, else bad.
|Form         |The compatible form of all the arguments. Conversion is
done pairwise.
|Result       |The smallest |Arguments, Results|A reserved operand will dominate.
|Examples     |MIN(-9.0,7.0,2.0) is -9.0.
MINEXPONENT
### `MINEXPONENT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 242
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: MINEXPONENT(arg0) 
|Native python|False|


F90 Inquiry.
The minimum exponent in the model representing numbers of the same type as the argument.
|Arguments, Results|X must be real or complex, scalar or array.
|Signals      |None. |Units        |None. |Form         |Integer scalar.
|Result       |The number emin for the model of the same type as X.
|Examples     |MINEXPONENT(1.0) is -127 on the VAX.
MINLOC
### `MINLOC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 243
|Min arguments| 1
|Max arguments| 3
******Compiler syntax: MINLOC(arg0,arg1,arg2)
|Native python|False|


|Return Type  |F90 Transformation |
Determine the location of an element of ARRAY having the minimum value of the elements identified by MASK.
Arguments Optional: MASK. ARRAY numeric array. MASK logical and conformable with ARRAY.
|Signals      |None. |Units        |None. |Form         |Long vector of size equal to rank of ARRAY.
|Result       |The result is the vector of subscripts of an element whose value equals the minimum of all elements of ARRAY or all elements for which MASK is true. Reserved operands ($ROPRAND) are ignored. Each subscript will be in the extent of its dimension. For zero size, no true elements in MASK, or all $ROPRAND the result is undefined. If more than one element has the maximum value the result is the first in array order. The result is an offset vector even if there is a lower bound.
Examples. MINLOC([2,4,6]) is [0].
For _A=[0 -5 8 -3], MINLOC(_A,_A GT -4) is [0,3]. [3 4-1 2][1 5 6-4]
|See also     |MINVAL for the value.
MINVAL
### `MINVAL`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 244
|Min arguments| 1
|Max arguments| 3
******Compiler syntax: MINVAL(arg0,arg1,arg2)

|Native python|False|

 |Return Type  |F90 Transformation |
Minimum value of the elements of ARRAY alongdimension DIM corresponding to true elements of MASK.
Arguments Optional: DIM, MASK. ARRAY numeric array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY. MASK logical and conformable to ARRAY.
|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. |Units        |Same as ARRAY. |Form         |Same type as ARRAY. It is a scalar if DIM is absent or
ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.
|Result       |The result without DIM is the minimum value of the elements of ARRAY, testing only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the minimum of ARRAY elements with DIM dimension fixed as the element number of the result. If no value is found, +HUGE(ARRAY) is returned.
Examples. MINVAL([1,2,3]) is 3. MINVAL(_C,,_C GT 0) finds the minimum positive element of C. If _B=[[1, 3, 5],[2, 4, 6]] MINVAL(_B,0) is [1,2] and MINVAL(_B,1) is [1,3,5].
|See also     |MINLOC for the location.
MOD
### `MOD`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 245
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: arg0 MOD arg1 
|Native python|False|


|Type         |F90 Numeric Elemental|
Remainder.
Usual Form A MOD P.
Arguments A and P must be integer or real. Complex numbers are an error.
|Signals      |Single signal or smaller data. |Units        |Single or common units, else bad. |Form         |Compatible form of A and P.
|Result       |If P NE 0, the result is A-INT(A/P)*P. If P==0, the result is the $ROPRAND for reals and undefined for integers.
Examples. MOD(3.0,2.0) is 1.0. MOD(8,5) is 3. MOD(-8,5) is -3. MOD(8,-5) is -3. MOD(-8,-5) is -3.
MODEL_OF
### `MODEL_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 246
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: MODEL_OF(arg0)
|Native python|False|


|Return Type  |MDS Operation | Get the model field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_CONGLOM, the model field. Otherwise, an error.
MULTIPLY
### `MULTIPLY`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 247
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: arg0 * arg1 
|Native python|False|


|Return Type  |Numeric Elemental |
Multiplication.
Usual Form X * Y. Function Form MULTIPLY(X,Y).
Arguments X and Y must be numeric.
|Signals      |Single signal or smaller data. |Units        |Those of X joined with those of Y by an asterisk. |Form         |Compatible form of X and Y.
|Result       |Product of corresponding elements of X and Y. >>>>>>>>>WARNING, integer overflow is ignored.
Examples. 3.0 * 2 is 6.0. BUILD_WITH_UNITS(3.0,"V")* BUILD_SIGNAL(BUILD_WITH_UNITS($VALUE*2,"s"),4)) is BUILD_SIGNAL(BUILD_WITH_UNITS(24.0,"V*s"),4).
NAME_OF
### `NAME_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 248
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: NAME_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the name field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_CONGLOM, the name field. Otherwise, an error.
NAND
### `NAND`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 249
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: NAND(arg0,arg1)
|Native python|False|


Logical Elemental.
Negation of logical intersection of elements.
Usual Forms L NAND M.
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match.
|Form         |Logical of compatible shape.
|Result       |False if both are true; otherwise, true.
|Examples     |[0,0,1,1] && [0,1,0,1] is [$TRUE,$TRUE,$TRUE,$FALSE].
NAND_NOT
### `NAND_NOT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 250
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: NAND_NOT(arg0,arg1) 
|Native python|False|


Logical Elemental.
Negation of logical intersection of first with negation of second. Logically equivalent to NOT(L) OR M.
Accepted Form. L NAND_NOT M.
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape.
|Result       |True if L is false or M is true; otherwise, false. |Examples     |[0,0,1,1] NAND_NOT [0,1,0,1] is [$TRUE,$TRUE,$FALSE,$TRUE].
NDESC
### `NDESC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 251
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: NDESC(arg0) 
|Native python|False|


MDS Information.
The number of descriptors in an MDS record.
|Arguments, Results|A must be an MDS class-R descriptor.
|Signals      |None. |Units        |None. |Form         |Byte unsigned scalar. |Result       |The number of descriptors in the class-R descriptor.
Descriptor data types (DSC$K_DTYPE_DSC) are removed. Use NDESC for count without NID, PATH, or variable. Use NDESC_OF for count including them.
Examples. NDESC($VALUE) is 0. NDESC(A+B) may be error.
NDESC_OF
### `NDESC_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 438
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: NDESC_OF(arg0)
|Native python|False|


MDS Information.
The number of descriptors in an MDS record.
|Arguments, Results|A must be an MDS class-R descriptor.
|Signals      |None. |Units        |None. |Form         |Byte unsigned scalar.
|Result       |The number of descriptors in the class-R descriptor. Descriptor data types (DSC$K_DTYPE_DSC) are removed. Use NDESC for count without NID, PATH, or variable. Use NDESC_OF for count including them.
Examples. NDESC_OF($VALUE) is 0. NDESC_OF(A+B) is 2.


### `NE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 252
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: arg0 != arg1, arg0 <> arg1, arg0 NE arg1 
|Native python|False|


Logical Elemental.
Tests for inequality of two values.
Usual Forms X != Y, X <> Y, X NE Y. F90 form /= is not allowed. Function Form NE(X,Y).
Arguments X and Y must both be numeric or character.
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape.
|Result       |True if X and Y are the unequal; otherwise, false. $ROPRAND is not unequal to any value, thus gives false.
>>>>>>>>>WARNING, floating point operations may not match an exact calculation for nonterminating binary fractions. You cannot predict that .1+.1!=.2 will be false.
|Examples     |2<>2. is $FALSE.

See also: `eq`, `ge`, `gt`, `le`, `lt`




### `NEQV`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 254
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: NEQV(arg0,arg1)
|Native python|False|


Logical Elemental.
Test that logical values are unequal.
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape. |Result       |True if exactly one of X and Y are true;
otherwise, false.
|Examples     |2>3 NEQV 3>4 is $FALSE.
NINT
### `NINT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 255
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: NINT(arg0,arg1)
|Native python|False|

Description: |Type         |F90 Numeric Elemental|
Nearest integer.
|Arguments, Results|Optional: KIND. A real. Complex numbers are an error. Integers are passed. KIND scalar integer type number, for example, KIND(1). (Today. Ignored, always returns LONG.)
|Signals      |Same as A. |Units        |Same as A. |Form         |Integer.
|Result       |If A>0, NINT(A) is INT(A+0.5); else it is INT(A-0.5).
Examples. NINT(2.783) is 3. NINT(-2.783) is -3.
NOR
### `NOR`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 256
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: NOR(arg0,arg1)
|Native python|False|


Logical Elemental.
Negation of logical union of elements.
Usual Forms L NOR M.
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape.
|Result       |False if either is true; otherwise, true.
|Examples     |[0,0,1,1] && [0,1,0,1] is [$TRUE,$FALSE,$FALSE,$FALSE].
NOR_NOT
### `NOR_NOT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 257
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: NOR_NOT(arg0,arg1) 
|Native python|False|


Logical Elemental.
Negation of logical union of first with negation of second. Logically equivalent to NOT(L) AND M.
Accepted Form. L NOR_NOT M.
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape.
|Result       |True if L is false and M is true; otherwise, false.
|Examples     |[0,0,1,1] NOR_NOT [0,1,0,1] is [$FALSE,$TRUE,$FALSE,$FALSE].
NOT
### `NOT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 258
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: NOT(arg0) 
|Native python|False|


Logical Elemental.
Negate a logical. True is 1BU, False is 0BU.
Usual Form ! L or NOT L. Function Form NOT(L).
|Arguments, Results|L must be logical.
|Signals      |Same as L. |Units        |Same as L. |Form         |Logical.
|Result       |True if lowest bit of converted integer is off. >>>>>>>>>WARNING, do not confuse this with the bit-wise INOT(J). What F90 calls NOT, we call INOT.
|Examples     |NOT([1,2,3]) is [$FALSE,$TRUE,$FALSE]).
OBJECT_OF
### `OBJECT_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 259
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: OBJECT_OF(arg0)
|Native python|False|


|Return Type  |MDS Operation |
Get the object field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this:
DSC$K_DTYPE_METHOD, the object field. Otherwise, an error.
OCTAWORD
### `OCTAWORD`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 260
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: OCTAWORD(arg0)
|Native python|False|


Conversion Elemental.
Convert to octaword (16-byte) integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Octaword-length integer.
|Result       |The truncated whole part of A. Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error.
Examples. OCTAWORD(123) is 123O. OCTAWORD(65537) is 65537O.
OCTAWORD_UNSIGNED
### `OCTAWORD_UNSIGNED`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 261
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: OCTAWORD_UNSIGNED(arg0)
|Native python|False|


Conversion Elemental.
Convert to octaword (16-byte) unsigned integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Octaword-length unsigned integer.
|Result       |The truncated whole part of A.
Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error. |Examples     |OCTAWORD_UNSIGNED(123) is 123oU.
OPCODE_BUILTIN
### `OPCODE_BUILTIN`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 263
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: OPCODE_BUILTIN(arg0) 
|Native python|False|


MDS Information.
The string name of a builtin's opcode.
|Arguments, Results|I must be an unsigned word scalar. It must be from 0 to the number of defined opcodes less one.
|Signals      |Same as I. |Units        |Same as I. |Form         |Character scalar of same shape. |Result       |The uppercase name for the opcode.
|Examples     |OPCODE_BUILTIN(0) is "$".
OPCODE_STRING
### `OPCODE_STRING`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
(Opcode 264
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: OPCODE_STRING(arg0) 
|Native python|False|


MDS Information.
The string name of an opcode.
|Arguments, Results|I must be an unsigned word scalar. It must be from 0 to the number of defined opcodes less one.
|Signals      |Same as I. |Units        |Same as I. |Form         |Character scalar of same shape.
|Result       |The uppercase name for the opcode.
|Examples     |OPCODE_STRING(0) is "OPC$$".
OPTIONAL
### `OPTIONAL`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 266
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: OPTIONAL _arg
|Native python|False|


Used in FUN definitions to indicate argument is optional
OR
### `OR`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 267
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: arg0 || arg1, arg0 OR arg1 
|Native python|False|


Logical Elemental.
Logical union of elements.
Usual Forms L || M, L OR M. Function Form OR(L,M).
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape.
|Result       |True if either is true; otherwise, false. >>>>>>>>>WARNING, do not confuse with | which is bit-wise IOR.
|Examples     |[0,0,1,1] || [0,1,0,1] is [$FALSE,$TRUE,$TRUE,$TRUE].
OR_NOT
### `OR_NOT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 268
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: OR_NOT(arg0,arg1) 
|Native python|False|


Logical Elemental.
Logical union of first with negation of second.
Accepted Form. L OR_NOT M.
Arguments L and M must be logical (lowest bit is 1 for true).
|Signals      |Single signal or smaller data. |Units        |None unless both have units and they don't match. |Form         |Logical of compatible shape.
|Result       |True if L is true or M is false; otherwise, false.
|Examples     |[0,0,1,1] OR_NOT [0,1,0,1] is [$TRUE,$FALSE,$TRUE,$TRUE].
OUT
### `OUT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 269
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: OUT _arg
|Native python|False|


Used in FUN definitions to indicate argument is an output argument
PACK
### `PACK`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 270
|Min arguments| 2
|Max arguments| 3
******Compiler syntax: PACK(arg0,arg1,arg2) 
|Native python|False|


|Return Type  |F90 Transformation |
Pack an array into a vector under control of a mask.
Arguments Optional: VECTOR. ARRAY any type. MASK logical conformable to ARRAY. VECTOR ARRAY's type, length at least equal to last true element
of MASK.
|Signals      |The single signal or the smallest. |Units        |The single or matching units, else bad. |Form         |The type is from ARRAY, ARRAY. The shape is rank one
equal to the number of trues if no VECTOR or the shape of VECTOR if present. If no VECTOR and MASK is a scalar true, the result is ARRAY shaped.
|Result       |The elements as selected by MASK from ARRAY. The remaining elements are filled from VECTOR.
Examples. Gather the nonzero elements of M = [0,0,0]. [9,0,0][0,0,7]
PACK(M,M NE 0) is [9,7] and PACK(M,M NE 0,[2,4,6,8,10,12]) is [9,7,6,8,10,12].
PERFORMANCE_OF
### `PERFORMANCE_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 399
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PERFORMANCE_OF(arg0) 
|Native python|False|


|Return Type  |MDS Operation |
Get the performance field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_ACTION, the performance statistics field. Otherwise, an error.
PHASE_OF
### `PHASE_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 271
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PHASE_OF(arg0)
|Native python|False|


|Return Type  |MDS Operation |
Get the phase field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_DISPATCH, the phase field.
Otherwise, an error.
POST_DEC
### `POST_DEC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 272
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: _var-
|Native python|False|


Variable Elemental.
Decrement variable but give old value.
Usual Form NAME--. Function Form POST_DEC(NAME).
|Arguments, Results|NAME must be a variable with numeric value or operator on variable.
|Signals      |Same as NAME. |Units        |Same as NAME. |Form         |Same as NAME.
|Result       |Old value of NAME.
Side Effect. NAME is now one less than before.
|Examples     |For _A=6, A--is 6 and _A is now 5.
POST_INC
### `POST_INC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 273
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: _var++ 
|Native python|False|


Variable Elemental.
Increment variable but give old value.
Usual Form NAME++. Function Form POST_INC(NAME).
|Arguments, Results|NAME must be a variable with numeric value or operator on variable.
|Signals      |Same as NAME. |Units        |Same as NAME. |Form         |Same as NAME.
|Result       |Old value of NAME.
Side Effect. NAME is now one more than before.
|Examples     |For _A=6, A++ is 6 and _A is now 7.
POWER
### `POWER`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 274
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: arg0 ^ arg1, arg0 ** arg1 
|Native python|False|


|Return Type  |Numeric Elemental |
Raise number to a power.
Usual Forms X^Y, X**Y. Function Form POWER(X,Y).
Arguments X and Y must be numeric.
|Signals      |Single signal or smaller data. |Units        |None, bad if X or Y have units. |Form         |The compatible form of X and Y if both are byte, word,
or long or both are real or complex; otherwise, the type
of X. >>>>>>>>>WARNING, long unsigned and longer integer types are truncated. >>>>>>>>>WARNING, quad-precision complex--HC^HC is truncated to GC^GC.
|Result       |Converts integer exponents to long and takes integral power. For real, or complex powers gives EXP(LOG(X)*Y). This will be $ROPRAND if X is not positive.
>>>>>>>>>WARNING, 0.0^0 is not detected as an error and results in 1.0.
>>>>>>>>>WARNING, do not use -X^2., which is (-X)^2.0, when you mean -(X^2), because it will bomb. Note that negation binds tighter than power.
>>>>>>>>>WARNING, use integer exponents when you mean that. For example, X^2.0 is an order of magnitude slower than X^2.
Examples. 2^3 is 8. 2**0.5 is 1.41428, approximately, and is better written as SQRT(2).
PRECISION
### `PRECISION`
|Syntax||
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
### `PRESENT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 275
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PRESENT(arg0) 
|Native python|False|


F90 Variable Inquiry.
Determine if an optional argument present.
|Arguments, Results|A must be an optional argument of the FUN in which the PRESENT function reference appears.
|Signals      |None. |Units        |None. |Form         |Logical scalar.
|Result       |$TRUE if A present or $FALSE otherwise. |Examples     |FUN _test(_A) {return PRESENT(_A);} when called _test() is $FALSE and _test(3) is $TRUE.
PRE_DEC
### `PRE_DEC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 276
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: --_var 
|Native python|False|


Variable Elemental.
Decrement variable and give new value.
Usual Form --NAME. Function Form PRE_DEC(NAME).
|Arguments, Results|NAME must be a variable with numeric value or operator on variable.
|Signals      |Same as NAME. |Units        |Same as NAME. |Form         |Same as NAME.
|Result       |New value of NAME.
Side Effect. NAME is now one less than before.
|Examples     |For _A=6, --A is 5 and _A is now 5.
PRE_INC
### `PRE_INC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 277
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: ++_var 
|Native python|False|


Variable Elemental.
Increment variable and give new value.
Usual Form ++NAME. Function Form PRE_INC(NAME).
|Arguments, Results|NAME must be a variable with numeric value or operator on variable.
|Signals      |Same as NAME. |Units        |Same as NAME. |Form         |Same as NAME.
|Result       |New value of NAME.
Side Effect. NAME is now one more than before.
|Examples     |For _A=6, ++A is 7 and _A is now 7.
PRIVATE
### `PRIVATE`
|Syntax||
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
PROCEDURE_OF
### `PROCEDURE_OF`
|Syntax||
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
PRODUCT
### `PRODUCT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 280
|Min arguments| 1
|Max arguments| 3
******Compiler syntax: PRODUCT(arg0,arg1,arg2)
|Native python|False|


|Return Type  |F90 Transformation |
Product of all the elements of ARRAY alongdimension DIM corresponding to true elements of MASK.
Arguments Optional: DIM, MASK. ARRAY numeric array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY. MASK logical and conformable to ARRAY.
|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. |Units        |Those of ARRAY repeated valid number of times. (Today, none.)
|Form         |Same type as ARRAY. It is a scalar if DIM is absent or ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.
Result.
(i)
Without DIM, the product of the elements of ARRAY, using only those with true MASK values and value not equal to the reserved operand.
(ii)
With DIM, the value of an element of the result is the product of ARRAY elements with dimension DIM fixed as the element number of the result. If no value is found, the number one is given.
Examples.
(i)
PRODUCT([1,2,3]) is 6. PRODUCT(_C,,_C GT 0) finds the product of all positive element of C.
(ii)
If _B=[[1, 3, 5],[2, 4, 6]]
PRODUCT(_B,0) is [15,48] and PRODUCT(_B,1) is [2,12,30].
PROGRAM_OF
### `PROGRAM_OF`
|Syntax||
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
PUBLIC
### `PUBLIC`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 284
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: PUBLIC(arg0) 
|Native python|False|


Variable Operation.
Specifies the use of a public variable.
Usual Form PUBLIC NAME.
|Arguments, Results|NAME mus be a variable name.
|Signals      |Same as NAME. |Units        |Same as NAME. |Form         |A copy of the contents of the variable.
|Result       |That of the contents of the variable.
|Examples     |PUBLIC _A = 42 sets the public variable _A to 42.
QUADWORD
### `QUADWORD`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 285
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: QUADWORD(arg0)
|Native python|False|


Conversion Elemental.
Convert to quadword (8-byte) integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Quadword-length integer.
|Result       |The truncated whole part of A.
Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error. Examples. QUADWORD(123) is 123O. QUADWORD(65537) is 65537O.
QUADWORD_UNSIGNED
### `QUADWORD_UNSIGNED`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 286
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: QUADWORD_UNSIGNED(arg0)
|Native python|False|


Conversion Elemental.
Convert to quadword (8-byte) unsigned integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Quadword-length unsigned integer. |Result       |The truncated whole part of A.
Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error.
|Examples     |QUADWORD_UNSIGNED(123) is 123oU.
QUALIFIERS_OF
### `QUALIFIERS_OF`
|Syntax||
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
RADIX
### `RADIX`
|Syntax||
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
RAMP
### `RAMP`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
(Opcode 289
|Min arguments| 0
|Max arguments| 2
******Compiler syntax: RAMP(arg0,arg1)
|Native python|False|


|Return Type  |Transformation |
Generate an ascending array.
Arguments Optional: SHAPE, MOLD. SHAPE integer vector. MOLD numeric.
|Signals      |None. |Units        |None. |Form         |Type of MOLD and shape (dimensions) is SHAPE. If SHAPE
is absent, the result is a scalar. If MOLD is absent, the result will be longs.
|Result       |Successive integral values starting at zero.
|Examples     |_X = RAMP([2,3,4],1d0) makes an array of double precision floating point numbers of shape [2,3,4]. The values are _X[0,0,0]=0d0, _X[1,0,0]=1d0, ... _X[1,2,3]=23d0.
|See also     |ARRAY, RANDOM, and ZERO.
RANDOM
### `RANDOM`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 290
|Min arguments| 0
|Max arguments| 2
******Compiler syntax: RANDOM(arg0,arg1) 
|Native python|False|


F90 Modified |Return Type  |Transformation |
Generate an array of pseudorandom numbers.
Arguments Optional: SHAPE, MOLD. SHAPE integer vector. MOLD numeric.
|Signals      |None. |Units        |None. |Form         |Type of MOLD and shape (dimensions) is SHAPE. If SHAPE
is absent, the result is a scalar. If MOLD is absent, the result will be floats.
|Result       |The result will be different with each call unless RANDOMSEED is used. Integers are on the full range, floating numbers are from 0 to 1.
|Examples     |_X = RANDOM(2,1d0) makes a vector of double precision numbers with value [.7043401852374758D0,.6857676661043094D0].
|See also     |ARRAY, RAMP, and ZERO.
RANGE
### `RANGE`
|Syntax||
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
RANK
### `RANK`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 293
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: RANK(arg0) 
|Native python|False|


Inquiry.
Number of dimensions, zero for scalar.
|Arguments, Results|X is any VMS data type.
|Signals      |None. |Units        |None. |Form         |Integer scalar.
|Result       |The number of dimensions of an array, zero fo a scalar.
Examples. RANK(3) is 0. RANK(RAMP([3,4])) is 2.
RAW_OF
### `RAW_OF`
|Syntax||
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
REAL
### `REAL`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 296
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: REAL(arg0,arg1)
|Native python|False|

NOTE: using the second arg (kind) causes core dump.

Conversion Elemental.
Convert to real.
Arguments Optional: KIND. A numeric. KIND scalar integer type number, for example, KIND(1d0).
|Signals      |Same as A. |Units        |Same as A. |Form         |If KIND present, the type KIND; otherwise, the real
type with the same length. To get F, D, G, or H floating result use F_FLOAT, etc.
|Result       |Immediate at compilation.
(i)
A is integer or real, the result is the truncated approximation.
(ii)
A is complex, the result is the approximation to the real part.
Examples. REAL(-3) is -3.0. REAL(Z,Z) is real part of the complex. This is done in TDISHR as REAL(Z). In F90, REAL(Z) sets the default floating point size.
REF
### `REF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 298
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: REF(arg0) 
|Native python|False|


CALL mode. Pass the data of the argument by reference. |Arguments, Results|X is any type, scalar or array that DATA can evaluate. Use..... Starting address of VMS data, like Fortran %REF('123'). The address of the DATA of the |Arguments, Results|For X alone, non-data forms may be passed. May programs cannot handle these forms. The REF form is expected by most Fortran routines but the DESCR form is used for characters.
REM
### `REM`
|Syntax||
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



### `REPEAT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 299
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: REPEAT(arg0,arg1) 
|Native python|False|


|Return Type  |F90 Character Elemental |
Concatenate several copies of a string.
Arguments STRING character. NCOPIES integer scalar, not negative.
|Signals      |Same as STRING. |Units        |Same as STRING. |Form         |Character of length NCOPIES times that of STRING.
|Result       |The concatenation of NCOPIES copies of STRING. Examples. REPEAT('H',2) is "HH". REPEAT('XYZ',0) is "".



### `REPLICATE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 300
|Min arguments| 3
|Max arguments| 3
******Compiler syntax: REPLICATE(arg0,arg1,arg2) 
|Native python|False|


|Return Type  |Transformation |
Replicates an array by increasing a dimension.
Arguments ARRAY any type. DIM integer scalar from 0 to n-1, where n is rank of ARRAY. NCOPIES integer scalar.
|Signals      |Same as ARRAY except DIM-th dimension is removed. |Units        |Same as ARRAY. |Form         |Same type and rank as array with shape [E[0:DIM-1],
MIN(NCOPIES,0)*E[DIM],E[DIM+1:n]] where E is the shape of ARRAY.
|Result       |NCOPIES replications of the values of ARRAY.
|Examples     |REPLICATE([2 4],1,3) is [2 4 2 4 2 4].
[35] [353535] Written as an expression the array is Set_Range(2,2,[2,3,3,4]) and gives Set_Range(2,6,[2,3,4,5, 2,3,4,5, 2,3,4,5]). For DIM=0 it gives Set_Range(6,2,[2,3, 2,3, 2,3, 4,5, 4,5, 4,5]).
|See also     |REPEAT to concatenate copies of a string. SPREAD to increase the number of dimensions.
RESET_PRIVATE
### `RESET_PRIVATE`
|Syntax||
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
RESET_PUBLIC
### `RESET_PUBLIC`
|Syntax||
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
RETURN
### `RETURN`
|Syntax||
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
ROUTINE_OF
### `ROUTINE_OF`
|Syntax||
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
RRSPACING
### `RRSPACING`
|Syntax||
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
SCALE
### `SCALE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 307
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: SCALE(arg0,arg1) 
|Native python|False|


|Type         |F90 Numeric Elemental|
Changes X exponent by I, multiplying X by b^I.
Arguments X real or complex. I integer.
|Signals      |Same as X. |Units        |Same as X. |Form         |Same as X.
|Result       |X*b^I, where b is the base of real model numbers, provided the result is within range.
|Examples     |SCALE(3.0,2) is 12.0 on the VAX.
SCAN
### `SCAN`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 308
|Min arguments| 2
|Max arguments| 3
******Compiler syntax: SCAN(arg0,arg1,arg2) 
|Native python|False|


|Return Type  |F90 Character Elemental |
Scan a string for a character in a set.
Arguments Optional: BACK. STRING character. SET character. BACK logical.
|Signals      |Single signal or smallest data. |Units        |Same as STRING. |Form         |Integer type, compatible shape of all.
|Result       |The result is -1 if STRING does not contain any of the characters that are in SET of if the length of STRING or SET is zero.
(i)
BACK is absent or false. The offset of the leftmost character of STRING that is in SET.
(ii)
BACK present and true. The offset of the rightmost character of STRING that is in SET.
Examples. SCAN('FORTRAN','TR') is 2. SCAN('FORTRAN','TR',$TRUE) is 4. SCAN('FORTRAN','BCD') is -1.
|See also     |VERIFY to check that all character are in a set.
SELECTED_INT_KIND
### `SELECTED_INT_KIND`
|Syntax||
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
SELECTED_REAL_KIND
### `SELECTED_REAL_KIND`
|Syntax||
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
SET_EXPONENT
### `SET_EXPONENT`
|Syntax||
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


### `SET_RANGE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 311
|Min arguments| 2
|Max arguments| 9
******Compiler syntax: SET_RANGE(arg0,arg1,argn,...)
|Native python|False|


|Return Type  |Transformation |
Set array bounds and multipliers from a list.
Arguments Optional: BOUND,.... BOUND,... integer scalar or range, they are taken from ARRAY where omitted. ARRAY any type scalar, vector, or array.
|Signals      |Same as ARRAY. |Units        |Same as ARRAY. |Form         |Same type as ARRAY with shape from the bounds list. Any
omitted bounds are picked from the corresponding bounds of ARRAY.
|Result       |Elements in array order from ARRAY. Immediate at compilation even if all but last argument are ranges and provided last argument is an array.
Examples. 
_A=SET_RANGE(2:3,5,1:10) is [1, 3, 5, 7, 9]. [2, 4, 6, 8, 10]  
SET_RANGE(-2:,:3,_A) has LBOUND(_A,0) of [-2,-1] and UBOUND(_A,1) of [-1,3].

```
TDI> set_range(2:3, 5, 1:10)
Set_Range(2:3,0:4,[[1,2], [3,4], [5,6], [7,8], [9,10]])

TDI> set_range(2:3, 3:5, 1:10)
Set_Range(2:3,3:5,[[1,2], [3,4], [5,6]])

TDI> set_range(2, 10, 1:20)
[[1,2], [3,4], [5,6], [7,8], [9,10], [11,12], [13,14], [15,16], [17,18], [19,20]]

TDI> set_range(2, 10, 0:40:2)
[[0,2], [4,6], [8,10], [12,14], [16,18], [20,22], [24,26], [28,30], [32,34], [36,38]]
```





### `SHAPE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 135
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: SHAPE(arg0,arg1) 
|Native python|False|


F90 Inquiry.
The shape of an array or a scalar.
Arguments OPTIONAL: DIM (To follow F90 use SIZE with a DIM). SOURCE any type scalar, array, or signal. DIM integer scalar from 0 to n-1, where n is rank of SOURCE.
|Signals      |None.
|Units        |None. |Form         |Integer vector of size equal to rank of SOURCE.
|Result       |The declared shape of SOURCE
for subscript DIM of SOURCE. If no bounds were declared
it is one less than the multiplier for subscript DIM of
SOURCE. SHAPE(ARRAY) has value whose j-th component is
equal to SHAPE(ARRAY,j) for each j, 0 to n-1.
Examples. SHAPE(_A[2:5,-1:1]) is [4,3]. SHAPE(3) is [], a zero-length vector.
See also LBOUND for lower bound, UBOUND for upper bound, SIZE for total elements, and E... for signals.
SHIFT_LEFT
### `SHIFT_LEFT`
|Syntax||
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
SHIFT_RIGHT
### `SHIFT_RIGHT`
|Syntax||
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
SHOW_PRIVATE
### `SHOW_PRIVATE`
|Syntax||
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
SHOW_PUBLIC
### `SHOW_PUBLIC`
|Syntax||
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
SHOW_VM
### `SHOW_VM`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 380
|Min arguments| 0
|Max arguments| 2
******Compiler syntax: SHOW_VM(arg0,arg1) 
|Native python|False|


Show virtual memory consumption of this process
SIGNED
### `SIGNED`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 317
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SIGNED(arg0) 
|Native python|False|


Conversion Elemental.
Convert to signed integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Signed integer of same length as real part of A.
|Result       |The truncated integer. Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error.
|Examples     |SIGNED(3LU) is 3.
SIN
### `SIN`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 318
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SIN(arg0) 
|Native python|False|


F90 Mathematical Elemental.
Sine of angle in radians.
|Arguments, Results|X must be real or complex. HC is converted to GC.
|Signals      |Same as X. |Units        |None, bad if X has units. |Form         |Same as X.
|Result       |Processor approximation to sin(X). Real X and real part of complex X is in radians.
|Examples     |SIN(1.0) is 0.84147098, approximately.
SIND
### `SIND`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 319
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SIND(arg0) 
|Native python|False|


Mathematical Elemental.
Sine of angle in radians.
|Arguments, Results|X must be real. Complex numbers are an error.
|Signals      |Same as X. |Units        |None, bad if X has units. |Form         |Same as X.
|Result       |Processor approximation to sin(X) with X in degrees.
|Examples     |SIN(30.0) is 0.5, approximately.
SINH
### `SINH`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 320
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SINH(arg0) 
|Native python|False|


F90 Mathematical Elemental.
Hyperbolic sine.
|Arguments, Results|X must be real. Complex numbers are an error.
|Signals      |Same as X. |Units        |None, bad if X has units. |Form         |Same as X.
|Result       |Processor approximation to sinh(X).
|Examples     |SINH(1.0) is 1.1752012, approximately.
SIZE
### `SIZE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 136
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: SIZE(arg0,arg1)
|Native python|False|


F90 Inquiry.
The extent an array or the total declared number of elements in the array.
Arguments Optional: DIM. ARRAY any type array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY.
|Signals      |None. |Units        |None. |Form         |Integer scalar.
|Result       |Equal to the declared extent of dimension DIM of ARRAY or, if DIM is absent, the total declared number of elements of ARRAY.
Examples. SIZE(_A[2:5,-1:1]),1) is 3. SIZE(_A[2:5,-1:1]) is 12.
See also LBOUND for lower bound, SHAPE for number of elements, UBOUND for upper bound, and E... for signals.
SIZEOF
### `SIZEOF`
|Syntax||
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



### `SLOPE_OF`
|Syntax||
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




### `SORT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 402
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: SORT(arg0,arg1)
|Native python|False|


|Type         |Miscellaneous|
Make index list of ascending array.
|Arguments, Results|ARRAY integer, real, or character.
|Signals      |Same as ARRAY. |Units        |None. |Form         |Array of offsets.
|Result       |The ascending order list of offsets, such that MAP(A,SORT(A))[j] <= MAP(A,SORT(A))[j+1]. >>>>>>>>>WARNING, equal values may not be in their original order. This is may be true for all n*log2(n) sorts.
Examples. SORT([3,5,4,6]) is [0,2,1,3]. SORT(['abc','ab','b']) is [1,0,2]. _a=[3,5,4,6],MAP(_a,SORT(_a)) is [3,4,5,6].
|See also     |SORTVAL to get sorted array without the index.
SORTVAL
### `SORTVAL`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 325
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: SORTVAL(arg0,arg1) 
|Native python|False|


|Type         |Miscellaneous|
Rearrange element to make an ascending array.
|Arguments, Results|ARRAY integer, real, or character.
|Signals      |Same as ARRAY. |Units        |Same as ARRAY. |Form         |Same as ARRAY.
|Result       |The ascending ordered list of values, such that SORTVAL(ARRAY)[j] <= SORTVAL(ARRAY)[j+1] for all j. This is the same as MAP(ARRAY,SORT(ARRAY)).
Examples. SORTVAL([3,5,4,6]) is [3,4,5,6]. SORTVAL(['abc','ab','b']) is ['ab ','abc','b '].
|See also     |SORT to sort index. That index may be use for several arrays. BSEARCH for a binary search.
SPACING
### `SPACING`
|Syntax||
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
SPAWN
### `SPAWN`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 327
|Min arguments| 0
|Max arguments| 3
******Compiler syntax: SPAWN(arg0,arg1,arg2) 
|Native python|False|


VMS IO.
Do commands or command file.
Arguments. Optional: COMMAND, INPUT, OUTPUT COMMAND character scalar of command to execute. INPUT character scalar name of file for SYS$INPUT. OUTPUT character scalar name of file as SYS$OUTPUT.
|Signals      |None. |Units        |None. |Form         |Status returned.
|Result       |None.
>>>>>>>>>WARNING, side effects.
SPREAD
### `SPREAD`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 328
|Min arguments| 3
|Max arguments| 3
******Compiler syntax: SPREAD(arg0,arg1,arg2)

|Native python|False|

 |Return Type  |F90 Transformation |
Replicates an array by adding a dimension. Broadcasts several copies of source along a specified dimension.
Arguments SOURCE any type, rank (n) must be less than 254. DIM integer scalar from 0 to n. NCOPIES integer scalar.
|Signals      |Same as ARRAY except that dimensions DIM and above are
moved up one and dimension DIM is empty. |Units        |Same as ARRAY. |Form         |Same type as SOURCE with shape [E[0:DIM-1],
MIN(NCOPIES,0),E[DIM:n]] where E is the shape of SOURCE.
|Result       |The value of an element with subscripts [r0,r1,...rn] is the value of the element of source with subscripts [s0,...sn-1], where [s0,...sn-1] is [r0,...rn] with subscript DIM omitted.
|Examples     |SPREAD([2,3,4],0,3) is the array [2 3 4]. [2 3 4][2 3 4]
SQRT
### `SQRT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 329
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SQRT(arg0) 
|Native python|False|


F90 Mathematical Elemental.
Square root.
|Arguments, Results|X must be real or complex. HC is convert to GC.
|Signals      |Same as X. |Units        |Half the count of each unit.(Today, bad if X has units.)|Form         |Same as X.
Result. The processor approximation to the square root of X. A complex result is the principal value with the real part greater that or equal to zero. When the real part is 0, the imaginary part is >= 0.
|Examples     |SQRT(4.0) is 2.0, approximately.
SQUARE
### `SQUARE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 330
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: SQUARE(arg0) 
|Native python|False|


|Return Type  |Numeric Elemental | Product of number with itself.
|Arguments, Results|X must be numeric.
|Signals      |Same as X. |Units        |Same as X * X. |Form         |Same as X.
|Result       |X * X.
|Examples     |SQUARE(3) is 9.
STATEMENT
### `STATEMENT`
|Syntax||
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
STRING_OPCODE
### `STRING_OPCODE`
|Syntax||
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
SUBSCRIPT
### `SUBSCRIPT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 335
|Min arguments| 1
|Max arguments| 9
******Compiler syntax: SUBSCRIPT(arg0,arg1,argn,...)
|Native python|False|


CC-F90 Modified Operation.
Pick certain element of an expression.
Usual Form X[ SUB,... ]. (The Brackets are required.)Function Form SUBSCRIPT(X,[SUB],...).
Arguments Optional: SUB,.... X array or signal. SUB,... ranges, vector lists, scalars.
>>>>>>>>>WARNING, the number of subscripts must not exceed the rank of X. >>>>>>>>>WARNING, if X is a signal and the subscripted dimension
exists and SUB is a explicit range without a delta, then all valid subscripts between the begin and end values of the range are used. This behavior may be forced for more complex expressions of SUB by using $VALUE as the delta of a range.
|Signals      |Same as X. The trailing scalar axes are removed. For non-trailing-scalar axes the axis is valid values selected to match the SUB values.
|Units        |Same as X. |Form         |Type of X and shape dependent on number of valid elements in each subscript.
|Result       |The selected values from X. For signals, the SUB values are truncated by CULL and converted by X_TO_I to indices. The nearest integral value is used. For non-signals, the values are culled and used to select values from X.
Examples. [1,2,3][2] is 3. [1,2,3][3] is [] a null vector. Build_signal(1:100,*,build_dim(*,.01:1:.01))[.2:.25] is build_signal([20,21,22,23,24,25],*, [.2,.21,.22,.23,.24,.25]).
|See also     |EXTEND to continue endpoint values to prevent culling. MAP to use offsets into the array X. NINT to round indices to the nearest integers.
SUBTRACT
### `SUBTRACT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 336
|Min arguments| 2
|Max arguments| 2
******Compiler syntax: SUBTRACT(arg0,arg1) 
|Native python|False|


|Return Type  |Numeric Elemental |
Subtract numbers.
Usual Form A -B. Function Form SUBTRACT(A,B).
Arguments A and B must be numeric.
|Signals      |Single signal or smaller data. |Units        |Single or common units, else bad. |Form         |Compatible form of A and B.
|Result       |The element-by-element difference of objects A and B. >>>>>>>>>WARNING, integer overflow is ignored.
|Examples     |[2,3,4] -5.0 is [-3.0,-2.0,-1.0].
SUM
### `SUM`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 337
|Min arguments| 1
|Max arguments| 3
******Compiler syntax: SUM(arg0,arg1,arg2) 
|Native python|False|


|Return Type  |F90 Transformation |
Sum of all the elements of ARRAY along dimension DIM corresponding to the true elements of MASK.
Arguments Optional: DIM, MASK. ARRAY numeric array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY. MASK logical and conformable to ARRAY.
|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. |Units        |Same as ARRAY. |Form         |Same type as ARRAY. It is a scalar if DIM is absent or
ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.
|Result       |The result without DIM is the sum of the elements of ARRAY, using only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the sum of the ARRAY elements with dimension DIM fixed as the element number of the result. If no value is found, 1 is given.
Examples. SUM([1,2,3]) is 6. SUM(_C,,_C GT 0) finds the sum of all positive element of C.
If _B=[[1, 3, 5],[2, 4, 6]] SUM(_B,0) is [9,12] and SUM(_B,1) is [3,7,11].
SWITCH
### `SWITCH`
|Syntax||
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
TAN
### `TAN`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 340
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: TAN(arg0) 
|Native python|False|


F90 Mathematical Elemental.
Tangent.
|Arguments, Results|X must be real. Complex numbers are an error.
|Signals      |Same as X. |Units        |None, bad if X has units. |Form         |Same as X.
|Result       |Processor approximation to tan(X), with X in radians.
|Examples     |TAN(1.0) is 1.5574077, approximately.
TAND
### `TAND`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 341
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: TAND(arg0) 
|Native python|False|


F90 Mathematical Elemental.
Tangent in degrees.
|Arguments, Results|X must be real. Complex numbers are an error.
|Signals      |Same as X. |Units        |None, bad if X has units. |Form         |Same as X.
|Result       |Processor approximation to tan(X), with X in degrees. |Examples     |TAN(45.0) is 1.0, approximately.
TANH
### `TANH`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 342
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: TANH(arg0) 
|Native python|False|


F90 Mathematical Elemental.
Hyperbolic tangent.
|Arguments, Results|X must be real. Complex numbers are an error.
|Signals      |Same as X. |Units        |None, bad if X has units. |Form         |Same as X.
|Result       |Processor approximation to tanh(X). |Examples     |TANH(1.0) is 0.76159416, approximately.
TASK_OF
### `TASK_OF`
|Syntax||
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
### `TEXT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |

(Opcode 344
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: TEXT(arg0,arg1)
|Native python|False|


Conversion Elemental.
Convert to text of given length.
Arguments Optional: LENGTH. X numeric or character. LENGTH integer scalar.
|Signals      |Same as X. |Units        |Same as X. |Form         |Character of given length or length associated with the
type of X. These are used B/BU 4, W/WU 8, L/LU 12, Q/QU 20, O/OU 36, F 16, D/G 24, H 40, FC 32, DC/GC 48, and HC 80.
|Result       |A character string that represent the number. (As of now, quadword and octaword are converted to hex.)>>>>>>>>>WARNING, truncation does not cause an error.
|Examples     |TEXT(1.2) is " 0.1200000E+02".
TIME_OUT_OF
### `TIME_OUT_OF`
|Syntax||
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
TINY
### `TINY`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
(Opcode 346
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: TINY(arg0) 
|Native python|False|


F90 Inquiry.
The smallest positive number in the model representing numbers of the type of the argument.
|Arguments, Results|X must be real or complex.
|Signals      |Same as X. |Units        |Same as X. |Form         |Scalar of same type as real part of X.
|Result       |The result is 1 if X is integer and b^(emin-1) if X is real, where b is the real base and emin is the minimum exponent in model numbers like X.
|Examples     |TINY(1.0) is 2^-128 on the VAX.
TRANSLATE
### `TRANSLATE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 381
|Min arguments| 3
|Max arguments| 3
******Compiler syntax: TRANSLATE(arg0,arg1,arg2) 
|Native python|False|


Character Elemental.
Replace matching characters with others.
Arguments STRING character. TRANSLATION character. MATCH character.
|Signals      |That of dominant shape. |Units        |Same as STRING. |Form         |Character of compatible shape.
|Result       |For each character of STRING found in MATCH the corresponding character in TRANSLATION replaces it.
|Examples     |TRANSLATE('ABCDEF','135','ACE') is "1B3D5F".
TRIM
### `TRIM`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 349
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: TRIM(arg0) 
|Native python|False|


|Return Type  |F90 Transformation |
The argument with trailing blank characters removed, including tabs.
|Arguments, Results|STRING is character scalar.
|Signals      |Same as STRING. |Units        |Same as STRING. |Form         |Character with a length that is the length less the
number of trailing blanks (and tabs) in STRING.
|Result       |Same as STRING except any trailing blanks are removed. If STRING contains no nonblank characters, the result has zero length.
|Examples     |TRIM(' A B ') is " A B".
|See also     |ADJUSTL and ADJUSTR to justify strings.
UBOUND
### `UBOUND`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 138
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: UBOUND(arg0,arg1) 
|Native python|False|


F90 Inquiry.
All the lower bounds of an array or a specified lower bound.
Arguments Optional: DIM.
ARRAY any type array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY.
|Signals      |None. |Units        |None. |Form         |Integer scalar if DIM present,
otherwise, vector of size n.
|Result       |UBOUND(ARRAY,DIM) is equal to the declared lower bound for subscript DIM of ARRAY. If no bounds were declared it is one less than the multiplier for subscript DIM of ARRAY. UBOUND(ARRAY) has value whose j-th component is equal to UBOUND(ARRAY,j) for each j, 0 to n-1.
|Examples     |UBOUND(_A=SET_RANGE(2:3,7:10,0)) is [3,10] and UBOUND(_A,1) is 10.
See also LBOUND for lower bound, SHAPE for number of elements, SIZE for total elements, and E... for signals.
UNARY_MINUS
### `UNARY_MINUS`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 350
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: UNARY_MINUS(arg0) 
|Native python|False|


|Return Type  |Numeric Elemental |
Negate a number.
Usual Form -X.
|Arguments, Results|X must be numeric.
|Signals      |Same as X. |Units        |Same as X. |Form         |Same as X except unsigned become signed.
|Result       |Negate each element. (Two's complement for integers on VAX.)Immediate at compilation.
|Examples     |-2LU is -2.
UNARY_PLUS
### `UNARY_PLUS`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 351
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: UNARY_PLUS(arg0) 
|Native python|False|


|Return Type  |Numeric Elemental |
Make a signed number. (Generally unneeded.)
Usual Form + X.
|Arguments, Results|X must be numeric.
|Signals      |Same as X. |Units        |Same as X. |Form         |Same as X except unsigned become signed.
|Result       |Make number of each element. Immediate at compilation.
|Examples     |+2LU is 2.
UNION
### `UNION`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 352
|Min arguments| 0
|Max arguments| 254
******Compiler syntax: UNION(arg0,arg1,argn,...)
|Native python|False|


|Return Type  |Transformation |
The union of sets, keeping only unique values.
Arguments Any sortable data types--character, integer, or real.
|Signals      |None. |Units        |The combined type of all arguments. |Form         |The compatible type of all arguments.
|Result       |The A's are combined by VECTOR and sorted. Duplicates are removed.
|Examples     |UNION([4,5],[2,3,5]) is [2,3,4,5].
UNITS
### `UNITS`
|Syntax||
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
UNITS_OF
### `UNITS_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 354
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: UNITS_OF(arg0)
|Native python|False|


|Return Type  |MDS Operation |
Get the units field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for this: DSC$K_DTYPE_WITH_UNITS, the units field. Otherwise, a single blank is returned.
Examples. UNITS_OF(BUILD_WITH_UNITS(42.,"V")) is "V".
UNITS_OF(42) is " ".
UNSIGNED
### `UNSIGNED`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 356
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: UNSIGNED(arg0)
|Native python|False|


Conversion Elemental.
Convert to unsigned integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Unsigned integer of same length as real part of A. |Result       |The truncated integer.
Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error.
|Examples     |UNSIGNED(2.783) is 2LU.
UPCASE
### `UPCASE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 383
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: UPCASE(arg0) 
|Native python|False|


Character Elemental.
Change all alphabetics to uppercase.
|Arguments, Results|STRING must be character.
|Signals      |Same as STRING. |Units        |Same as STRING. |Form         |Same as STRING.
|Result       |The same as STRING with all lower case alphabetics replaced by the corresponding uppercase character.
|Examples     |UPCASE('Name') is "NAME".
USING
### `USING`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
(Opcode 384
|Min arguments| 2
|Max arguments| 4
******Compiler syntax: USING(arg0,arg1,arg2,arg3) 
|Native python|False|


|Return Type  |MDS Operation |
Evaluate expression from a different tree location.
Arguments Optional: DEFAULT, SHOTID, EXPT. A an expression.
>>>>>>>>>WARNING, pathnames in the expression A will be relative to the temporary tree location and may not be related to the old tree.
DEFAULT character, NID, long, or PATH scalar. The new tree path.
>>>>>>>>>WARNING, relative paths are like the full name in the old tree. SHOTID integer scalar. The shot number. EXPT character scalar. The experiment name.
|Result       |Depends on the expression at the node in the new tree. The old node, shot, and experiment are used to evaluate the expressions for DEFAULT, SHOTID, and EXPT. If SHOTID or EXPT present, a new tree is opened for reading. The temporary path is set from DEFAULT. If omitted, the values used are those of the current tree and path. There will be an error if the old tree is not open or the old path is bad.
|Examples     |Say shot 1234 is a "vacuum" subtraction shot for the current shot and we are positioned at \TOP.XRAY:CHAN_01, which has data, then the subtracted data might be
:DATA -USING(:DATA,,1234)
VAL
### `VAL`
|Syntax||
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


### `VALIDATION`
|Syntax||
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
|Syntax||
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
VALUE_OF
### `VALUE_OF`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 359
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: VALUE_OF(arg0)
|Native python|False|


|Return Type  |MDS Operation |
Get the value field.
|Arguments, Results|Descriptor as below.
|Result       |A is searched for these: DSC$K_DTYPE_DIMENSION, VALUE_OF(window field). DSC$K_DTYPE_PARAM, the value field. DSC$K_DTYPE_SIGNAL, the data field. DSC$K_DTYPE_WINDOW, the value_at_idx0 field. DSC$K_DTYPE_WITH_UNITS, the data field. Otherwise, DATA(A).
>>>>>>>>>WARNING, because the data field of a signal is likely to use $VALUE, DATA(VALUE_OF(signal)) may not work. Use DATA(signal) instead.
|Examples     |VALUE_OF(BUILD_PARAM(42,"the answer",$VALUE>6)) is 42.
VAR
### `VAR`
|Syntax||
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
VECTOR
### `VECTOR`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 361
|Min arguments| 0
|Max arguments| 254
******Compiler syntax: VECTOR(arg0,arg1,argn,...)
|Native python|False|


F90 Modified |Return Type  |Transformation |
Form a vector or array from scalar,
vector, array, range, and promote inputs.
Usual Form [X,...]. For F90 compatiblity, (/ is [ and /) is ].
Arguments Must be compatible types.
|Signals      |Single signal or smallest data. |Units        |Single or common units, else bad. |Form         |Type of highest data type found. The size is the sum of
the sizes of all the arguments. If the shapes of all arguments are the same, the result has one more dimension, the last, of size equal to the number of arguments. F90 defines only a vector result.
|Result       |A vector with all the values in the arguments. Immediate at compilation.
Examples. [2,3:5,4@6] is [2,3,4,5,6,6,6,6]. [[1,2],[3,4],5:6] is [1 3 5], long array shaped [2,3]. [2 46]
1:3 is a vector, [1:3] is an array of shape [1,3], so don't use extraneous brackets.
VERIFY
### `VERIFY`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 362
|Min arguments| 2
|Max arguments| 3
******Compiler syntax: VERIFY(arg0,arg1,arg2)
|Native python|False|


|Return Type  |F90 Character Elemental |
Verify that a set of characters has all the character in a string.
Arguments Optional: BACK. STRING character. SET character. BACK logical.
|Signals      |Single signal or smaller data. |Units        |Same as STRING. |Form         |Integer type, compatible shape of all.
|Result       |The result is -1 if STRING contains only the characters that are in SET of if the length of STRING or SET is 0.
(i)
BACK is absent or false. The offset of the leftmost character of STRING that is not in SET.
(ii)
BACK present and true. The offset of the rightmost character of STRING that is not in SET.
Examples. VERIFY('ABBA','AB') is -1.
(i)
VERIFY('ABBA','A') is 1.
(ii)
VERIFY('ABBA','A',$TRUE) is 2.
|See also     |SCAN to find a character in a set.
WAIT
### `WAIT`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 363
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: WAIT(arg0) 
|Native python|False|


IO.
Suspend processing for at least the time given.
|Arguments, Results|SECONDS must be real scalar.
|Result       |None.
|Examples     |WAIT(3.5) delays 3 and 1/2 seconds. this might retain a plot or comment for a short time.
WHEN_OF
### `WHEN_OF`
|Syntax||
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
WHILE
### `WHILE`
|Syntax||
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
WINDOW_OF
### `WINDOW_OF`
|Syntax||
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
### `WORD`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 368
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: WORD(arg0) 
|Native python|False|


Conversion Elemental.
Convert to word (two-byte) integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Word-length integer. |Result       |The truncated whole part of A.
Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error.
Examples. WORD(123) is 123W. WORD(65537) is 1W.
WORD_UNSIGNED
### `WORD_UNSIGNED`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 369
|Min arguments| 1
|Max arguments| 1
******Compiler syntax: WORD_UNSIGNED(arg0) 
|Native python|False|


Conversion Elemental.
Convert to word (two-byte) unsigned integer.
|Arguments, Results|A must be numeric.
|Signals      |Same as A. |Units        |Same as A. |Form         |Word-length unsigned integer.
|Result       |The truncated whole part of A. Immediate at compilation. >>>>>>>>>WARNING, truncation does not cause an error.
Examples. WORD_UNSIGNED(123) is 123WU. WORD_UNSIGNED(65537) is 1WU.


### `WRITE`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 370
|Min arguments| 1
|Max arguments| 254
******Compiler syntax: WRITE(arg0,arg1,argn,...)
|Native python|False|

WRITE ([UNIT],[ARG]...)IO.
Writes text values to terminal or file.
Arguments Optional
UNIT Character scalar or * for stdout. ARG... Any type.
|Result       |Numeric or text scalars and arrays are converted to text and output to the selected UNIT. Arrays are on separate lines; scalars are packed without space up to the terminal line width. If the data type or class if nonstandard, DECOMPILE is used to make a text string that is output.
>>>>>>>>>WARNING, No explicit formatting is provided. You can use
CVT(-1.2,"12345678") to get a string "-1.2E+00" or DECOMPILE(-1.2) to get "-1.2".
Example.. WRITE(*,'x=',1.2,3,[4,5],6) appears as
x= 1.20000E+00 3 45 6




### `XD`
|Syntax||
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
X_TO_I
### `X_TO_I`
|Syntax||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
*******
(Opcode 393
|Min arguments| 1
|Max arguments| 2
******Compiler syntax: X_TO_I(arg0,arg1) 
|Native python|False|
 Description:
MDS Transform Elemental.
Convert index into axis values.
Arguments Optional X.
DIMENSION a dimension with optional window and axis. If DIMENSION is missing, the unchanged X is returned. If the window of DIMENSION is missing, the first axis point is assigned an index of 0.
X scalar or array list of axis values. (For TDI$X_TO_I, the fake address of -1 for X, returns a 2-element vector with the index bounds.)
|Signals      |Same as X. |Units        |Same as axis of DIMENSION. |Form         |Same type as DATA(axis). Same shape as X.
|Result       |The window and axis are evaluated for each axis point X. The result is the index value of that point. Although the window start and end indices may be used to determine the value of axis points, they do not limit the range of results.
Examples. X_TO_I(BUILD_DIM(BUILD_WINDOW(2,5,1.1), BUILD_RANGE(,,3))) is [2,3,4,5] corresponding to axis [7.1,10.1,13.1,16.1]. X_TO_I(BUILD_DIM(BUILD_WINDOW(2,7,1.1), BUILD_RANGE(,,3)),[4.1,7.1,10.1,13.1]) is [1.,2.,3.,4.]. The index 1 (axis point 4.1) is outside the valid window of 2 to 7.
|See also     |CULL and EXTEND to discard or limit axis points. I_TO_X for the inverse transform. NINT to round indices to the nearest integers.
ZERO
### `ZERO`
|Syntax||
|-|-|
|TDI Syntax|Tdi3Zero
*******
(Opcode 371
|Min arguments| 0
|Max arguments| 2
******Compiler syntax: ZERO(arg0,arg1)
|Native python|False|
 Description:
|Return Type  |Transformation |
Generate an array of zeroes.
Arguments Optional: SHAPE, MOLD. SHAPE integer vector. MOLD any numeric.
|Signals      |None. |Units        |None. |Form         |Type of MOLD and shape (dimensions) is SHAPE.
If SHAPE is absent, the result is a scalar. If MOLD is absent, the result will be longs. |Result       |The value of each element is 0.
|Examples     |_X = ZERO([2,3,4],1d0) makes an array of double precision floating point numbers of shape [2,3,4]. They are all 0d0.
|See also     |ARRAY, RAMP, and RANDOM.
Total of 404 builtins of which 103 are implemented in Python









## Builtins--Here is the Full list, just in case

ABORT
ABS
ABS1
ABSSQ
ACCUMULATE
ACHAR
ACOS
ACOSD
ADD
ADJUSTL
ADJUSTR
AIMAG
AINT
ALL
ALLOCATED
AND
AND_NOT
ANINT
ANY
ARG
ARGD
ARG_OF
ARRAY
ASIN
ASIND
AS_IS
ATAN
ATAN2
ATAN2D
ATAND
ATANH
AXIS_OF

BEGIN_OF
BIT_SIZE
BREAK
BSEARCH
BTEST
BUILD_ACTION
BUILD_CALL
BUILD_CONDITION
BUILD_CONGLOM
BUILD_DEPENDENCY
BUILD_DIM
BUILD_DISPATCH
BUILD_EVENT
BUILD_FUNCTION
BUILD_METHOD
BUILD_OPAQUE
BUILD_PARAM
BUILD_PATH
BUILD_PROCEDURE
BUILD_PROGRAM
BUILD_RANGE
BUILD_ROUTINE
BUILD_SIGNAL
BUILD_SLOPE
BUILD_WINDOW
BUILD_WITH_ERROR
BUILD_WITH_UNITS
BUILTIN_OPCODE
BYTE
BYTE_UNSIGNED

CASE
CEILING
CHAR
CLASS
CLASS_OF
CMPLX
COMMA
COMPILE
COMPLETION_MESSAGE_OF
COMPLETION_OF
CONCAT
CONDITIONAL
CONDITION_OF
CONJG
CONTINUE
COS
COSD
COSH
COUNT
CULL
CVT

DATA
DATA_WITH_UNITS
DATE_TIME
DBLE
DEALLOCATE
DEBUG
DECOMPILE
DECOMPRESS
DEFAULT
DESCR
DIAGONAL
DIGITS
DIM
DIM_OF
DISPATCH_OF
DIVIDE
DO
DOT_PRODUCT
DO_TASK
DPROD
DSCPTR
DSCPTR_OF
DSQL
DTYPE_RANGE
D_COMPLEX
D_FLOAT

ELBOUND
ELEMENT
ELSE
END_OF
EPSILON
EQ
EQUALS
EQUALS_FIRST
EQV
ERRORLOGS_OF
ERROR_OF
ESHAPE
ESIZE
EUBOUND
EVALUATE
EXECUTE
EXP
EXPONENT
EXTEND
EXTRACT
EXT_FUNCTION

FCLOSE
FINITE
FIRSTLOC
FIX_ROPRAND
FLOOR
FOPEN
FOR
FRACTION
FSEEK
FS_COMPLEX
FS_FLOAT
FTELL
FT_COMPLEX
FT_FLOAT
FUN
F_COMPLEX
F_FLOAT

GE
GETDBI
GETNCI
GOTO
GT
G_COMPLEX
G_FLOAT

HELP_OF
HUGE
H_COMPLEX
H_FLOAT

IACHAR
IAND
IAND_NOT
IBCLR
IBSET
ICHAR
IDENT_OF
IEOR
IEOR_NOT
IF
IF_ERROR
IMAGE_OF
IN
INAND
INAND_NOT
INDEX
INOR
INOR_NOT
INOT
INOUT
INT
INTERRUPT_OF
INT_UNSIGNED
IOR
IOR_NOT
ISHFT
I_TO_X

KIND
KIND_OF
LABEL
LANGUAGE_OF
LASTLOC
LBOUND
LE
LEN
LEN_TRIM
LGE
LGT
LLE
LLT
LOG
LOG10
LOG2
LOGICAL
LONG
LONG_UNSIGNED
LT

MAKE_ACTION
MAKE_CALL
MAKE_CONDITION
MAKE_CONGLOM
MAKE_DEPENDENCY
MAKE_DIM
MAKE_DISPATCH
MAKE_FUNCTION
MAKE_METHOD
MAKE_OPAQUE
MAKE_PARAM
MAKE_PROCEDURE
MAKE_PROGRAM
MAKE_RANGE
MAKE_ROUTINE
MAKE_SIGNAL
MAKE_SLOPE
MAKE_WINDOW
MAKE_WITH_ERROR
MAKE_WITH_UNITS
MAP
MAX
MAXEXPONENT
MAXLOC
MAXVAL
MEAN
MERGE
METHOD_OF
MIN
MINEXPONENT
MINLOC2.302581, approximately.
MINVAL
MOD
MODEL_OF
MULTIPLY

NAME_OF
NAND
NAND_NOT
NDESC
NDESC_OF
NE
NEQV
NINT
NOR
NOR_NOT
NOT

OBJECT_OF
OCTAWORD
OCTAWORD_UNSIGNED
OPCODE_BUILTIN
OPCODE_STRING
OPTIONAL
OR
OR_NOT
OUT

PACK
PERFORMANCE_OF
PHASE_OF
POST_DEC
POST_INC
POWER
PRECISION
PRESENT
PRE_DEC
PRE_INC
PRIVATE
PROCEDURE_OF
PRODUCT
PROGRAM_OF
PUBLIC

QUADWORD
QUADWORD_UNSIGNED
QUALIFIERS_OF

RADIX
RAMP
RANDOM
RANGE
RANK
RAW_OF
REAL
REF
REM
REPEAT
REPLICATE
RESET_PRIVATE
RESET_PUBLIC
RETURN
ROUTINE_OF
RRSPACING

SCALE
SCAN
SELECTED_INT_KIND
SELECTED_REAL_KIND
SET_EXPONENT
SET_RANGE
SHAPE
SHIFT_LEFT
SHIFT_RIGHT
SHOW_PRIVATE
SHOW_PUBLIC
SHOW_VM
SIGNED
SIN
SIND
SINH
SIZE
SIZEOF
SLOPE_OF
SORT
SORTVAL
SPACING
SPAWN
SPREAD
SQRT
SQUARE
STATEMENT
STRING_OPCODE
SUBSCRIPT
SUBTRACT
SUM
SWITCH

TAN
TAND
TANH
TASK_OF
TEXT
TIME_OUT_OF
TINY
TRANSLATE
TRIM

UBOUND
UNARY_MINUS
UNARY_PLUS
UNION
UNITS
UNITS_OF
UNSIGNED
UPCASE
USING

VAL
VALIDATION
VALIDATION_OF
VALUE_OF
VAR
VECTOR
VERIFY

WAIT
WHEN_OF
WHILE
WINDOW_OF
WORD
WORD_UNSIGNED
WRITE

XD
X_TO_I

ZERO



---
---
> this is buffer text. for internal use only because vscode does weird things when multiple people are typing in the same doc

---so

