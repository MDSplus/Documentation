# TDI Reference

TODO: Confirm whether to leave the scientific notation as it is in when you ping the program, or into standard:
e.g., the program lists $A0 as 52.9177E-12m, but the normal way to write that is 5.29177E-11m

TODO: a lot of decimals also include D0 at the end. Keep?

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





















Builtins--Here is the Full list, just in case

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
MINLOC
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





Source:  `Tdi_builtins.pdf`

template for each entry:
```
### `TitleGoesHere` (Opcode )
|||
|-|-|
|TDI Syntax | `take from Compiler syntax` |
|C Syntax | `take from `TdiShr Function` except instead of `Tdi` it should say `Tdi3` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith**d**___ANDMAKEITLOWERCASE` |
|Java mdsplus-api Syntax| `CONST.ifitexistsitgoeshere()`|

Description goes here
```

to check the java syntax open this folder in a new vscode window
C:\Users\myuen\Documents\GitHub\mdsplus\java\mdsplus-api\src\main\java\mds\data\descriptor_r\function\CONST.java


## Constants

### `$2PI` (Opcode 372)

|||
|-|-|
|TDI Syntax | `$2PI`|
|C Syntax   | `Tdi32Pi` |
|Python Syntax| `MDSplus.d2pi`|
|Java mdsplus-api Syntax| `CONST.d2Pi()` |

Two times pi, or equivalent to circumference of a circle divided by its radius (approx 6.2831853072)


### `$A0` (Opcode  1)

|||
|-|-|
| TDI Syntax | `$A0` |
| C Syntax | `Tdi3A0()` |
| Python Syntax | `MDSplus.dA0` |
| Java mdsplus-api Syntax | `CONST.dA0()` |

The BOHR Radius Constant of 52.9177E-12m, with a margin of error of 1168.02E-21


### `$ALPHA` (Opcode 2)

|||
|-|-|
| TDI syntax| `$ALPHA`|
| C Syntax | `Tdi3Alpha`|
| Python Syntax| `MDSplus.dalpha`|
|Java mdsplus-api Syntax| `CONST.dAlpha()`|

Fine-structure Constant: 7.29735308e-3 or 
0.00729735, error of 143.276E-12


### `$AMU` (Opcode 3)

|||
|-|-|
|TDI syntax: `$AMU`|
|C Syntax | `Tdi3Amu`|
|Python Syntax | `MDSplus.damu`|
|Java mdsplus-api Syntax| `CONST.dAmu()` |

Unified atomic mass unit: 1.6605402e-27, or 1660.54E-30 kg, error of 43.0666E-36


### `$ATM` (Opcode 405)

|||
|-|-|
|TDI Syntax | `$ATM`|
|C Syntax | `Tdi3Atm`|
|Python Syntax| `MDSplus.datm`|
|Java mdsplus-api Syntax| `CONST.dAtm()` |

Atmospheric pressure: 101325. Pa


### `$C` (Opcode 4)

|||
|-|-|
|TDI Syntax | `$C`|
|C Syntax | `Tdi3C`|
|Python Syntax| `MDSplus.dc`|
|Java mdsplus-api Syntax| `CONST.dC()` |

Speed of light: 299792458. m/s


### `$CAL` (Opcode 5)

|||
|-|-|
|TDI Syntax | `$CAL`|
|C Syntax | `Tdi3Cal` |
|Python Syntax| `MDSplus.dcal` |
|Java mdsplus-api Syntax| `CONST.dCal()`|

Calorie: 4.1868 J


### `$DEGREE` (Opcode 6)

|||
|-|-|
|TDI Syntax | `$DEGREE` |
|C Syntax | `Tdi3Degree` |
|Python Syntax| `MDSplus.ddegree` |
|Java mdsplus-api Syntax| `CONST.dDegree()`|

Degree (pi/180): 0.0174532925199433


### `$EPSILON0` (Opcode 406)
|||
|-|-|
|TDI Syntax | `$EPSILON0` |
|C Syntax | `Tdi3Epsilon0` |
|Python Syntax| `MDSplus.depsilon0` |
|Java mdsplus-api Syntax| `CONST.dEpsilon0()`|

Epsilon0, Permitivity of vacuum: 8854.187817620389 e-15 F/m


### `$EV` (Opcode 7)
|||
|-|-|
|TDI Syntax | `$EV` |
|C Syntax | `Tdi3Ev` |
|Python Syntax| `MDSplus.dev` |
|Java mdsplus-api Syntax| `CONST.dEv()`|

Electron volt: 160.218E-21 J/eV, with error 3654.14E-30


### `$FARADAY` (Opcode 9)
|||
|-|-|
|TDI Syntax | `$FARADAY` |
|C Syntax | `Tdi3Faraday` |
|Python Syntax| `MDSplus.dfaraday` |
|Java mdsplus-api Syntax| `CONST.dFaraday()`|

Faraday constant: 96485.3 C/mol, with error .00381419


### `$G` (Opcode 10)
|||
|-|-|
|TDI Syntax | `$G` |
|C Syntax | `Tdi3G` |
|Python Syntax| `MDSplus.dg` |
|Java mdsplus-api Syntax| `CONST.dG()`|

Gravitational constant: 66.743E-12 m^3/s^2/kg, with error 1500.02E-18


### `$GAS` (Opcode 11)
|||
|-|-|
|TDI Syntax | `$GAS` |
|C Syntax | `Tdi3Gas` |
|Python Syntax| `MDSplus.dgas` |
|Java mdsplus-api Syntax| `CONST.dGas()`|

Gas constant: 8.31446 J/K/mol, with error 43.5899E-9


### `$GN` (Opcode 407)
|||
|-|-|
|TDI Syntax | `$GN` |
|C Syntax | `Tdi3Gn` |
|Python Syntax| `MDSplus.dgn` |
|Java mdsplus-api Syntax| `CONST.dGn()`|

Acceleration of gravity: 9.80665 m/s^2


### `$H` (Opcode 12)
|||
|-|-|
|TDI Syntax | `$H` |
|C Syntax | `take from `Tdi3H` |
|Python Syntax| `MDSplus.dh` |
|Java mdsplus-api Syntax| `CONST.dH()`|

Planck constant: 662.607E-36 J*s, with error 2857.25E-45


### `$HBAR` (Opcode 13)
|||
|-|-|
|TDI Syntax | `$HBAR` |
|C Syntax | `Tdi3Hbar` |
|Python Syntax| `MDSplus.dhbar` |
|Java mdsplus-api Syntax| `CONST.dHbar()`|

Planck constant/2PI: 105.457E-36 J*s, with error 1967.42E-45


### `$I` (Opcode 14)
|||
|-|-|
|TDI Syntax | `$I` |
|C Syntax | `Tdi3I` |
|Python Syntax| `MDSplus.di` |
|Java mdsplus-api Syntax| `CONST.dI()`|

Imaginary: Cmplx(0.,1.)


### `$K` (Opcode 15)
|||
|-|-|
|TDI Syntax | `$K` |
|C Syntax | `Tdi3K` |
|Python Syntax| `MDSplus.dk` |
|Java mdsplus-api Syntax| `CONST.dK()`|

Boltzmann constant: 13.8065E-24 J/K, with error 276.341E-33


### `$ME` (Opcode 16)
|||
|-|-|
|TDI Syntax | `$ME` |
|C Syntax | `Tdi3Me` |
|Python Syntax| `MDSplus.dme` |
|Java mdsplus-api Syntax| `CONST.dMe()`|

Mass of electron: 910.938E-33 kg, with error 25.8874E-39


### `$MP` (Opcode 18)
|||
|-|-|
|TDI Syntax | `$MP` |
|C Syntax | `Tdi3Mp` |
|Python Syntax| `MDSplus.dmp` |
|Java mdsplus-api Syntax| `CONST.dMp()`|

Mass of proton: 1672.62E-30 kg, with error 85.2717E-36


### `$MU0` (Opcode 408)
|||
|-|-|
|TDI Syntax | `$MU0` |
|C Syntax | `Tdi3Mu0` |
|Python Syntax| `MDSplus.dmu0` |
|Java mdsplus-api Syntax| `CONST.dMu0()`|

Permeability of vacuum: 1256.637061435917D-9 N/A^2


### `$N0` (Opcode 19)
|||
|-|-|
|TDI Syntax | `$N0` |
|C Syntax | `Tdi3N0` |
|Python Syntax| `MDSplus.dn0` |
|Java mdsplus-api Syntax| `CONST.dN0()`|

Loschmidt's number: 26.8678E24 /m^3, with error 743.623E15


### `$NA` (Opcode 20)
|||
|-|-|
|TDI Syntax | `$NA` |
|C Syntax | `Tdi3Na` |
|Python Syntax| `MDSplus.dna` |
|Java mdsplus-api Syntax| `CONST.dNa()`|

Avogadro's number: 602.214E21 /mol, with error 11.645E15


### `$P0` (Opcode 21)
|||
|-|-|
|TDI Syntax | `$P0` |
|C Syntax | `Tdi3P0` |
|Python Syntax| `MDSplus.dp0` |
|Java mdsplus-api Syntax| `CONST.dP0()`|

Atmospheric pressure: 101325. Pa


### `$PI` (Opcode 22)
|||
|-|-|
|TDI Syntax | `$PI` |
|C Syntax | `Tdi3Pi` |
|Python Syntax| `MDSplus.dpi` |
|Java mdsplus-api Syntax| `CONST.dPi()`|

Pi, Circumference/radius: 3.141592653589793D0


### `$QE` (Opcode 23)
|||
|-|-|
|TDI Syntax | `$QE` |
|C Syntax | `Tdi3Qe` |
|Python Syntax| `MDSplus.dqe` |
|Java mdsplus-api Syntax| `CONST.dQe()`|

Charge on electron: 160.218E-21 C, with error 3654.14E-30


### `$RE` (Opcode 24)
|||
|-|-|
|TDI Syntax | `$RE` |
|C Syntax | `Tdi3Re` |
|Python Syntax| `MDSplus.dre` |
|Java mdsplus-api Syntax| `CONST.dRe()`|

Classical electron rad: 2817.94E-18 m, with error 12.7156E-24


### `$RYDBERG` (Opcode 26)
|||
|-|-|
|TDI Syntax | `$RYDBERG` |
|C Syntax | `Tdi3Rydberg` |
|Python Syntax| `MDSplus.drydberg` |
|Java mdsplus-api Syntax| `CONST.dRydberg()`|

Rydberg constant: 10.9737E6 /m, with error 0.443876


### `$T0` (Opcode 27)
|||
|-|-|
|TDI Syntax | `$T0` |
|C Syntax | `Tdi3T0` |
|Python Syntax| `MDSplus.$T0` |
|Java mdsplus-api Syntax| `CONST.dT0()`|

Standard temperature: 273.15 K


### `$TORR` (Opcode 28)
|||
|-|-|
|TDI Syntax | `$TORR` |
|C Syntax | `Tdi3Torr` |
|Python Syntax| `MDSplus.dtorr` |
|Java mdsplus-api Syntax| `CONST.dTorr()`|

Torr or 1mm Hg pressure: 133.3223684210526D0 Pa






## Other Special Variables beginning with `$`

### `$DEFAULT` (Opcode 386)

|||
|-|-|
|TDI Syntax | `$DEFAULT` |
|C Syntax | `Tdi3MdsDefault` |
|Python Syntax| `MDSplus.ddefault` |
|Java mdsplus-api Syntax| `CONST.dDefault()`|

Current default tree node (TreeNode) location


### `$EXPT` (Opcode 387)
|||
|-|-|
|TDI Syntax | `$EXPT` |
|C Syntax | `Tdi3Exp` |
|Python Syntax| `MDSplus.dexpt` |
|Java mdsplus-api Syntax| `CONST.dExpt()`|

Current tree name


### `$FALSE` (Opcode 8)
|||
|-|-|
|TDI Syntax | `$FALSE` |
|C Syntax | `Tdi3False` |
|Python Syntax| `MDSplus.dfalse` |
|Java mdsplus-api Syntax| `CONST.dFalse()`|

False: 0 bu (zero bytes unsigned)


### `$MISSING` (Opcode 17)
|||
|-|-|
|TDI Syntax | `$MISSING` |
|C Syntax | `take from `Tdi3Missing` |
|Python Syntax| `MDSplus.$missing` |
|Java mdsplus-api Syntax| `CONST.dMissing()`|

Missing value (or argument). `$MISSING` is used internally to mark a missing argument and gives zero or blanks. `$MISSING` and `$ROPRAND` execute at compilation.


### `$NARG` (Opcode 373)
|||
|-|-|
|TDI Syntax | `$NARG` |
|C Syntax | `Tdi3Narg` |
|Python Syntax| `MDSplus.dnarg` |
|Java mdsplus-api Syntax| `CONST.dNarg()`|

Special: Actual arguments used to invoke the FUN

TODO: ask Stephen what this means and also if "specials" get any other treatment and Also it says native python false is there anything we need to do about that?


### `$ROPRAND` (Opcode 25)
|||
|-|-|
|TDI Syntax | `$ROPRAND` |
|C Syntax | `Tdi3Roprand` |
|Python Syntax| `MDSplus.droprand` |
|Java mdsplus-api Syntax| `CONST.dRoprand()`|

SPECIAL: Reserved operand "float nan"
TODO: Interestingly, native python = true for this one. Ask Stephen what that means


### `$SHOT` (Opcode 388)
|||
|-|-|
|TDI Syntax | `$SHOT` |
|C Syntax | `Tdi3Shot` |
|Python Syntax| `MDSplus.dshot` |
|Java mdsplus-api Syntax| `CONST.dShot()`|

The current tree's shot number


### `$SHOTNAME` (Opcode 444)
|||
|-|-|
|TDI Syntax | `$SHOTNAME` |
|C Syntax | `Tdi3Shotname` |
|Python Syntax| `MDSplus.dshotname` |
|Java mdsplus-api Syntax| `CONST.dShotname()`|

The current tree's shot number as text, can return MODEL

### `$THIS` (Opcode 403)
|||
|-|-|
|TDI Syntax | `$THIS` |
|C Syntax | `Tdi3This` |
|Python Syntax| `MDSplus.dthis` |
|Java mdsplus-api Syntax| `CONST.dThis()`|

SPECIAL: Signal or param associated with one of its parts

### `$TRUE` (Opcode 29)
|||
|-|-|
|TDI Syntax | `$TRUE` |
|C Syntax | `Tdi3True` |
|Python Syntax| `MDSplus.dtrue` |
|Java mdsplus-api Syntax| `CONST.dTrue()`|

True: 1 bu (byte unsigned)


### `$VALUE` (Opcode 30)
|||
|-|-|
|TDI Syntax | `$VALUE` |
|C Syntax | `Tdi3Value` |
|Python Syntax| `MDSplus.dvalue` |
|Java mdsplus-api Syntax| `CONST.dValue()`|

SPECIAL: "$VALUE" Raw field in a signal or value field in a param or subscript dimensional element

---

## Functions

## A

### `abort` (Opcode 31)
|||
|-|-|
|TDI Syntax | `ABORT(arg0,arg1,argn,...)` |
|C Syntax | `Tdi3Abort` |
|Python Syntax| `MDSplus.ABORT(arg0,arg1,argn,...)` |

Miscellaneous.

Abort an expression by causing an error.
Arguments Any, ignored.

Result.. None, error status.

Example. IF_ERROR(A,B,ABORT()) aborts if both members are bad.


### `abs` (Opcode 32)
|||
|-|-|
|TDI Syntax | `abs(arg0)` |
|C Syntax | `Tdi3Abs` |
|Python Syntax| `MDSplus.abs(arg0)` |

F90 Numeric Elemental.

Absolute value.

Argument. A must be numeric.

Signals. Same as A.

Units... Same as A.

Form.... Same as A except if A is complex, the result is real.

Result.. Unsigned integers are unchanged, negative integers and reals are negated, complex numbers get square roots of the sum of the squares of real and imaginary parts. The complex number parts are scaled to avoid overflow.

Example. ABS(CMPLX(3.0,4.0)) is 5.0.

See also. ABS1 and ABSSQ for complex number to avoid a square root.
ARG for the complex angle.

### `abs1` (Opcode 33)
|||
|-|-|
|TDI Syntax | `ABS1(arg0)` |
|C Syntax | `Tdi3Abs1` |
|Python Syntax| `MDSplus.ABS1(arg0)` |

Numeric Elemental.

Absolute value with L1 norm.

Argument. A must be numeric.

Signals. Same as A.

Units... Same as A.

Form.... Same as A except if A is complex, the result is real.
Result.. Unsigned integers are unchanged, negative integers
and reals are negated, complex numbers become the sums
of the absolute values of the real and imaginary parts.
Example. ABS1(CMPLX(3.0,-4.0)) is 7.0.


### `abssq` (Opcode 34)
|||
|-|-|
|TDI Syntax | `ABSSQ(arg0)` |
|C Syntax | `Tdi3AbsSq` |
|Python Syntax| `MDSplus.ABSSQ(arg0)` |

Numeric Elemental.

Absolute value squared.

Argument. A must be numeric.

Signals. Same as A.
Units... Same as for A * A.
Form.... Same as A except if A is complex, the result is real.

Result.. Integers may lose significance. Integers and reals are squared, complex numbers become the sums of the squares of the real and imaginary parts.

Example. ABSSQ(CMPLX(3.0,4.0)) is 25.0.





### `ACCUMULATE` (Opcode 439)
|||
|-|-|
|TDI Syntax | `accumulate(arg0,arg1,arg2)` |
|C Syntax | `Tdi3Accumulate` |
|Python Syntax| `MDSplus.accumulate()` |

Transformation.
Running sum of all the elements of ARRAY along dimension DIM corresponding to the true elements of MASK.

Arguments Optional: DIM, MASK.
* ARRAY numeric array.
* DIM integer scalar from 0 to n-1, where n is rank of ARRAY.
* MASK logical and conformable to ARRAY.

Signals: Same as ARRAY.
Units: Same as ARRAY.


Form: Same type and shape as ARRAY.

Result: The result is the running sum of the elements of ARRAY, using only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the running sum of the ARRAY elements with dimension DIM fixed as the element
number of the result. Without DIM, the result is the sum from the first element ignoring the shape.
If no value is found, 0 is given.

Examples:

```
ACCUMULATE([1,2,3]) is [1,3,6].

ACCUMULATE(_C,,_C GT 0) finds the running sum of all positive element of C.

If _B=[[1, 3, 5],[2, 4, 6]]

ACCUMULATE(_B) is [[1, 4, 9],[11, 15, 21]]

ACCUMULATE(_B,0) is [[1, 4, 9],[2, 6, 12]]

ACCUMULATE(_B,1) is [[1, 3, 3],[7, 3, 9]]
```

### `ACHAR` (Opcode 35)
|||
|-|-|
|TDI Syntax | `ACHAR(arg0,arg1)` |
|C Syntax | `Tdi3Achar` |
|Python Syntax| `MDSplus.ACHAR(arg0,arg1)` |

F90 Character Elemental.

The character in a specified position of the ASCII collating sequence. The inverse of IACHAR.

Argument. I must be integer.

Signals. Same as I.
Units... Same as I.
Form.... Length-one character of same shape.

Result.. For j between 0 and 127, the result is the character in position j of the ASCII collating sequence; otherwise,
the result is processor dependent. It is truncated to 8 bits on the VAX.

Example. ACHAR(88) has the value 'X'.

See also. CHAR and its inverse ICHAR for a processor-dependent.


### `ACOS` (Opcode 36)
|||
|-|-|
|TDI Syntax | `ACOS(arg0)` |
|C Syntax | `Tdi3Acos` |
|Python Syntax| `MDSplus.ACOS(arg0)` |

F90 Mathematical Elemental.

Arccosine (inverse cosine).

Argument. X must be real and be less than 1 in magnitude. Complex numbers cause an error.

Signals. Same as X.
Units... None, bad if X has units.
Form.... Real of same shape.

Result.. Processor approximation to arccos(X) in radians.
It lies in the range 0 to pi, inclusive.
Out-of-range numbers get $ROPRAND.
Example. ACOS(0.54030231) is 1.0, approximately.


### `ACOSD` (Opcode 37)
|||
|-|-|
|TDI Syntax | `ACOSD(arg0)` |
|C Syntax | `take from `TdiShr Function` except instead of `Tdi` it should say `Tdi3` |
|Python Syntax| `MDSplus.ACOSD(arg0)` |

Mathematical Elemental.

Arccosine (inverse cosine) in degrees.

Argument. X must be real and be less than 1 in magnitude. Complex numbers cause an error.

Signals. Same as X.
Units... None, bad if X has units.
Form.... Real of same shape.

Result.. Processor approximation to arccos(X) in degrees. It lies in the range 0 to 180. Out-of-range numbers get $ROPRAND.

Example. ACOSD(0.5) is 60.0, approximately.


### `ADD` (Opcode 38)

|||
|-|-|
|TDI Syntax| `A + B` or `ADD(A, B)`|
|C Syntax| `Tdi3ADD(A, B)`|
|Python Syntax| `MDSplus.ADD(A, B)`|

Numeric Elemental. Add numbers.

Arguments A and B must be numeric.

**WARNING**: integer overflow is ignored.

Example: `[2,3,4] + 5.0` is `[7.0,8.0,9.0]`. 

>TODO: figure out whether it makes sense to have this in a more centralized place. This tells you what happens when you add two signals together, or add two numbers with different units (should be different with add/subtract vs multiply/divide, for example)


### `ADJUSTL` (Opcode 39)
|||
|-|-|
|TDI Syntax | `ADJUSTL(arg0)` |
|C Syntax | `Tdi3Adjustl` |
|Python Syntax| `MDSplus.ADJUSTL(arg0)` |

F90 Character Elemental.

Adjust to the left, removing leading blanks (and tabs) and inserting trailing blanks.

Argument. STRING must be character.

Signals. Same as STRING.
Units... Same as STRING.
Form.... Same as STRING.
Result.. Same as STRING except that any leading blanks and tabs have been deleted and the same number of trailing blanks have been inserted.

Example. ADJUSTL(' WORD') is "WORD ".


### `ADJUSTR` (Opcode 40)
|||
|-|-|
|TDI Syntax | `ADJUSTR(arg0)` |
|C Syntax | `Tdi3Adjustr` |
|Python Syntax| `MDSplus.ADJUSTR(arg0)` |

F90 Character Elemental.

Adjust to the right, removing trailing blanks (and tabs) and inserting leading blanks.

Argument. STRING must be character.
Signals. Same as STRING.
Units... Same as STRING.
Form.... Same as STRING.
Result.. Same as STRING except that any trailing blanks and tabs have been deleted and the same number of leading blanks
have been inserted.

Example. ADJUSTR('WORD ') is " WORD".

See also. TRIM (non-elemental) to remove trailing blanks and tabs.



### `AIMAG` (Opcode 41)
|||
|-|-|
|TDI Syntax | `AIMAG(arg0)` |
|C Syntax | `Tdi3Aimag` |
|Python Syntax| `MDSplus.AIMAG(arg0)` |

F90 Numeric Elemental.

Imaginary part of a complex number.

Argument. Z must be complex.

Signals. Same as Z.
Units... Same as Z.
Form.... Real of same shape.

Result.. Real with the same type parameter as Z. If Z has the value CMPLX(x,y) the result is y.

Example. AIMAG(CMPLX(2.0,3.0)) is 3.0.


### `AINT` (Opcode 42)
|||
|-|-|
|TDI Syntax | `AINT(arg0,arg1)` |
|C Syntax | `Tdi3Aint` |
|Python Syntax| `MDSplus.AINT(arg0,arg1)` |

F90 Numeric Elemental.

Trunctation to a whole number.

Argument. Optional: KIND.
* A: real. Complex numbers are an error.
* KIND: scalar integer type number, for example, KIND(1d0).

Signals. Same as A.
Units... Same as A.
Form.... Same as A.
Result.. Type is KIND if it is present, else that of A. If |A|<1, AINT(A) is 0; else AINT is largest integer
that does not exceed the magnitude of A and whose sign is that of A. Overflow is not detected.

Examples. AINT(2.783) is 2.0. AINT(-2.783) is -2.0.

See also:
* INT for integer result and BYTE, WORD, LONG, QUADWORD, OCTAWORD, and UNSIGNED_BYTE, etc., for specific forms. * ANINT and NINT for rounded integral value.
* FLOOR and CEILING.


### `ALL` (Opcode 43)
|||
|-|-|
|TDI Syntax | `ALL(arg0,arg1)` |
|C Syntax | `Tdi3All` |
|Python Syntax| `MDSplus.ALL(arg0,arg1)` |

F90 Transformation.

Determine if all values are true in MASK along dimension DIM.

Arguments Optional: DIM.
MASK logical array.
DIM integer scalar from 0 to n-1, where n is rank of MASK.

Signals. None.
Units... None.
Form.... Logical. It is scalar if DIM is absent or MASK is a vector; otherwise, the result is an array of rank n-1 and of shape like MASK's with DIM subscript omitted.

Result.
(i) ALL(MASK) is $TRUE if all elements of MASK are true or if MASK has size zero and is $FALSE if any element of MASK is false.
(ii) For a vector MASK, ALL(MASK,DIM) is equal to ALL(MASK). Otherwise, the value of an element of the result is ALL of the elements of MASK varying the DIM subscript.

Examples.

(i) ALL([$TRUE,$FALSE,$TRUE]) is $FALSE.

(ii) If _B=[[1, 3, 5],[2, 4, 6]] and
_C=[[0, 3, 5],[2, 4, 6],[7, 4, 8]]
ALL(_B NE _C,0) is [$FALSE,$FALSE,$FALSE].
ALL(_B NE _C,1) is [$FALSE,$FALSE].

See also. ANY for logical or, COUNT for the number of trues.


### `ALLOCATED` (Opcode 44)
|||
|-|-|
|TDI Syntax | `ALLOCATED(arg0)` |
|C Syntax | `Tdi3Allocated` |
|Python Syntax| `MDSplus.ALLOCATED(arg0)` |

F90 Variable Inquiry.

Indicate if a variable is currently allocated.

Argument. NAME must be a variable name or a text string.

Signals. None.

Units... None.

Form.... Logical scalar.

Result.. $TRUE if NAME is currently allocated, otherwise $FALSE.

Example. ALLOCATED(_Not_in use) is $FALSE unless it has appeared on the left side of an assignment expression.

See also. DEALLOCATE to remove names and RESET_PRIVATE or RESET_PUBLIC for more drastic actions.


### `AND` (Opcode 45)
|||
|-|-|
|TDI Syntax | `arg0 && arg1` |
|C Syntax | `Tdi3And` |
|Python Syntax| `MDSplus.arg0 && arg1` |

TODO: Confirm python syntax for this one

Logical Elemental.

Logical intersection of elements.

Usual Forms: L && M, L AND M.
Function Form: AND(L,M).

Arguments L and M must be logical (lowest bit is 1 for true).

Signals. Single signal or smaller data.

Units... None unless both have units and they don't match.

Form.... Logical of compatible shape.

Result.. True if both are true; otherwise, false.

>>>>>>>>>WARNING, do not confuse with & which is bit-wise IAND.

Example. [0,0,1,1] && [0,1,0,1] is [$FALSE,$FALSE,$FALSE,$TRUE]. See also. EQV, NAND, NEQV, NOR, OR, and others like AND_NOT for other logical functions.



### `AND_NOT` (Opcode 46)
|||
|-|-|
|TDI Syntax | `AND_NOT(arg0,arg1)` |
|C Syntax | `Tdi3AndNot` |
|Python Syntax| `MDSplus.AND_NOT(arg0,arg1)` |

Logical Elemental.
Logical intersection with negation of second.
Accepted Form. L AND_NOT M.
Arguments L and M must be logical (lowest bit is 1 for true).
Signals. Single signal or smaller data.
Units... None unless both have units and they don't match.
Form.... Logical of compatible shape.
Result.. True if L is true and M is false; otherwise, false.
Example. [0,0,1,1] AND_NOT [0,1,0,1] is
[$FALSE,$FALSE,$TRUE,$FALSE].


### `ANINT` (Opcode 47)
|||
|-|-|
|TDI Syntax | `ANINT(arg0,arg1)` |
|C Syntax | `Tdi3Anint` |
|Python Syntax| `MDSplus.ANINT(arg0,arg1)` |

F90 Numeric Elemental.
Nearest whole number.
Argument. Optional: KIND.
A real. Complex numbers are an error.
KIND scalar integer type number, for example, KIND(1d0).
Signals. Same as A.
Units... Same as A.
Form.... Same as A.
Result.. Type is KIND if it is present, else that of A.
If A>0, ANINT(A) is AINT(A+0.5); else, ANINT(A) is
AINT(A-0.5).
Examples. ANINT(2.783) is 3.0. ANINT(-2.783) is -3.0.
See also. NINT for integer and INT and AINT for truncated results.


### `ANY` (Opcode 48)
|||
|-|-|
|TDI Syntax | `ANY(arg0,arg1)` |
|C Syntax | `Tdi3Any` |
|Python Syntax| `MDSplus.ANY(arg0,arg1)` |

F90 Transformation.
Determine whether any value is true in MASK along
dimension DIM.
Arguments Optional: DIM.
MASK logical array.
DIM integer scalar from 1 to n-1, where n is rank of MASK.
Signals. None.
Units... None.
Form.... Logical. It is scalar if DIM is absent or MASK is a
vector; otherwise, the result is an array of rank n-1
and shaped like MASK with DIM subscript omitted.
Result.
(i) ANY(MASK) is $TRUE if any elements of MASK are true and
has $FALSE if no element is true or MASK is size zero.
(ii) For a vector MASK, ANY(MASK,DIM) is equal to ANY(MASK).
Otherwise, the value of an element of the result is
ANY of the elements of MASK varying the DIM subscript.
Examples.
(i) ANY([$TRUE,$FALSE,$TRUE]) is $TRUE.
(ii) For
_B=[[1, 3, 5],[2, 4, 6]] and
_C=[[0, 3, 5],[7, 4, 8]]
ANY(_B NE _C,0) is [$TRUE,$TRUE].
ANY(_B NE _C,1) is [$TRUE,$FALSE,$TRUE].
See also. ALL for logical and, COUNT for the number of trues.


### `ARG` (Opcode 49)
|||
|-|-|
|TDI Syntax | `ARG(arg0)` |
|C Syntax | `Tdi3Arg` |
|Python Syntax| `MDSplus.ARG(arg0)` |

Mathematical Elemental.
Argument of complex number in radians.
Argument. Z must be complex.
Signals. Same as Z.
Units... None.
Form.... Real of same shape.
Result.. ATAN2(AIMAG(Z),REAL(Z)).
Example. ARG(CMPLX(3.0,4.0)) is 0.9272952, approximately.
See also. ABS for the complex length.


### `ARGD` (Opcode 50)
|||
|-|-|
|TDI Syntax | `ARGD(arg0)` |
|C Syntax | `Tdi3Argd` |
|Python Syntax| `MDSplus.ARGD(arg0)` |

Mathematical Elemental.
Argument of complex number in degrees.
Argument. Z must be complex.
Signals. Same as Z.
Units... None.
Form.... Real of same shape.
Result.. ATAN2D(AIMAG(Z),REAL(Z)).
Example. ARGD(CMPLX(3.0,4.0)) is 53.1301, approximately.


### `ARG_OF` (Opcode 51)
|||
|-|-|
|TDI Syntax | `ARG_OF(arg0,arg1)` |
|C Syntax | `Tdi3ArgOf` |
|Python Syntax| `MDSplus.ARG_OF(arg0,arg1)` |

MDS Operation.
Get the N-th argument of a record descriptor.
The count does not include dscptrs like image or routine.
Arguments Optional: N.
A descriptor of class DSC$K_CLASS_R with arguments.
N integer scalar from 0 to the number of descriptors - 1.
Result.. The N-th argument pointed to by A searched for:
    DSC$K_DTYPE_CALL
    DSC$K_DTYPE_CONDITION, the condition field.
    DSC$K_DTYPE_DEPENDENCY
    DSC$K_DTYPE_FUNCTION
    DSC$K_DTYPE_METHOD
    DSC$K_DTYPE_PROCEDURE
    DSC$K_DTYPE_ROUTINE
    Otherwise, an error.
Example. ARG_OF(A+B,1) is B because A+B is a FUNCTION.
See also. DSCPTRS_OF for any descriptor.


### `ARRAY` (Opcode 52)
|||
|-|-|
|TDI Syntax | `ARRAY(arg0,arg1)` |
|C Syntax | `Tdi3Array` |
|Python Syntax| `MDSplus.ARRAY(arg0,arg1)` |

Transformation.
Generate an uninitialized array.
Arguments Optional: SHAPE, MOLD.
SHAPE integer vector.
MOLD any by example.
Signals. None.
Units... None.
Form.... Type of MOLD and shape (dimensions) is SHAPE. If SHAPE is absent, the result is a scalar. If MOLD is absent, the result will be floats.
Example. ARRAY([2,3,4],1d0) makes an array of double precision reals of shape [2,3,4]. The value are not defined and will depend on previous memory usage.
See also. RAMP, RANDOM, and ZERO.


### `ASIN` (Opcode 53)
|||
|-|-|
|TDI Syntax | `ASIN(arg0)` |
|C Syntax | `Tdi3Asin` |
|Python Syntax| `MDSplus.ASIN(arg0)` |

F90 Mathematical Elemental.
Arcsine (inverse sine).
Argument. X must be real and be less than or equal to 1 in
magnitude. Complex numbers cause an error.
Signals. Same as X.
Units... None, bad if X has units.
Form.... Real of same shape.
Result.. Processor approximation to arcsin(X) in radians.
It lies in the range -pi/2 to pi/2.
Out-of-range numbers get $ROPRAND.
Example. ASIN(0.84147098) is 1.0, approximately.


### `ASIND` (Opcode 54)
|||
|-|-|
|TDI Syntax | `ASIND(arg0)` |
|C Syntax | `Tdi3Asind` |
|Python Syntax| `MDSplus.ASIND(arg0)` |

Mathematical Elemental.
Arcsine (inverse sine) in degrees.
Argument. X must be real and be less than 1 in magnitude.
Complex numbers cause an error.
Signals. Same as X.
Units... None, bad if X has units.
Form.... Real of same shape.
Result.. Processor approximation to arcsin(X) in degrees.
It lies in the range -90 to 90.
Out-of-range numbers get $ROPRAND.
Example. ASIND(0.5) is 30.0, approximately.


### `AS_IS` (Opcode 55)
|||
|-|-|
|TDI Syntax | `AS_IS(arg0)` |
|C Syntax | `Tdi3AsIs` |
|Python Syntax| `MDSplus.AS_IS(arg0)` |

Compile operation.
Protects the argument from one level of evaluation.
Argument. X may be any expression and may be a NID, PATH, or
FUNCTION.
Result.. The argument without evaluation.
Example. _A = AS_IS(_B * 3.0) makes the variable _A into an
expression. So whereever _A is used the current value of
_B will be multiplied by three and that will be used.
Note that _A = _B * 3.0 would have returned the then
current value and will not change as _B does.


### `ATAN` (Opcode 56)
|||
|-|-|
|TDI Syntax | `ATAN(arg0)` |
|C Syntax | `Tdi3Atan` |
|Python Syntax| `MDSplus.ATAN(arg0)` |

F90 Mathematical Elemental.
Arctangent (inverse tangent).
Argument. X must be real. Complex numbers are an error.
Signals. Same as X.
Units... None, bad if X has units.
Form.... Real of same shape.
Result.. Processor approximation to arctan(X) in radians.
It lies in the range -pi/2 to pi/2, inclusive.
Example. ATAN(1.5574077) is 1.0, approximately.


### `ATAN2` (Opcode 57)
|||
|-|-|
|TDI Syntax | `ATAN2(arg0,arg1)` |
|C Syntax | `Tdi3Atan2` |
|Python Syntax| `MDSplus.ATAN2(arg0,arg1)` |

F90 Mathematical Elemental.
Arctangent (inverse tangent). The principal
value of the argument of the nonzero complex number
CMPLX(X,Y).
Arguments X any Y must be real. Complex numbers are an error.
Signals. Single signal or smaller data.
Units... None unless both have units and they don't match.
Form.... The compatible form of X and Y.
Result.. Processor approximation to arctan(Y/X) in radians.
It lies in the range -pi to pi.
If Y > 0, the result is positive.
Examples. ATAN2(1.5574077,1.0) is 1.0, approximately.
ATAN2([ 1, 1], [-1, 1]) is [ 3*pi/4 , pi/4].
See also. ARG for the angle of a complex number.


### `ATAN2D` (Opcode 58)
|||
|-|-|
|TDI Syntax | `ATAN2D(arg0,arg1)` |
|C Syntax | `Tdi3Atan2d` |
|Python Syntax| `MDSplus.ATAN2D(arg0,arg1)` |

Mathematical Elemental.
Arctangent (inverse tangent) in degrees. The
principal value of the argument of the nonzero complex
number CMPLX(X,Y).
Arguments X and Y must be real. Complex numbers are an error.
Signals. Single signal or smaller data.
Units... None unless both have units and they don't match.
Form.... The compatible form of X and Y.
Result.. Processor approximation to arctan(Y/X) in degrees.
It lies in the range -180 to 180.
If Y>0, the result is positive.
Example. ATAN2D(-1.0,-1.0) is -135.0, approximately.
ATAN2D([ 1, 1], [-1, 1]) is [ 135. , 45.].
See also. ARGD for the angle of a complex number in degrees.

### `ATAND` (Opcode 59)
|||
|-|-|
|TDI Syntax | `ATAND(arg0)` |
|C Syntax | `Tdi3Atand` |
|Python Syntax| `MDSplus.ATAND(arg0)` |

Mathematical Elemental.
Arctangent (inverse tangent) in degrees.
Argument. X must be real and be less than 1 in magnitude.
Complex numbers cause an error.
Signals. Same as X.
Units... None, bad if X has units.
Form.... Real of same shape.
Result.. Processor approximation to arctan(X) in degrees.
It lies in the range -90 to 90.
Example. ATAND(1.0) is 45.0, approximately.


### `ATANH` (Opcode 60)
|||
|-|-|
|TDI Syntax | `ATANH(arg0)` |
|C Syntax | `Tdi3Atanh` |
|Python Syntax| `MDSplus.ATANH(arg0)` |

Mathematical Elemental.
Hyperbolic arctangent (inverse tangent).
Argument. X must be real. Complex numbers cause an error.
Signals. Same as X.
Units... None, bad if X has units.
Form.... Real of same shape.
Result.. Processor approximation to arctanh(X) in radians.
Example. ATANH(0.7615942) is 1.0, approximately.


### `AXIS_OF` (Opcode 61)
|||
|-|-|
|TDI Syntax | `AXIS_OF(arg0)` |
|C Syntax | `Tdi3AxisOf` |
|Python Syntax| `MDSplus.AXIS_OF(arg0)` |

MDS Operation.
Get the axis field.
Argument. Descriptor as below.
Result.. A is searched for these:
DSC$K_DTYPE_DIMENSION, the axis field.
DSC$K_DTYPE_RANGE, the range.
DSC$K_DTYPE_SLOPE, the slope, !deprecated!.
Otherwise, an error.
Example. AXIS_OF(BUILD_DIM(BUILD_WINDOW(B,E,X0),1..10)) is 1..10.


### `BEGIN_OF` (Opcode 64)
|||
|-|-|
|TDI Syntax | `BEGIN_OF(arg0,arg1)` |
|C Syntax | `Tdi3BeginOf` |
|Python Syntax| `MDSplus.BEGIN_OF(arg0,arg1)` |

MDS Operation.
Get the begin field.
Arguments Optional: N.
A as below.
N integer scalar, for slopes from 1 to the number of
segments less one. The first segment has no beginning
if the axis is infinite.
Result.. A is searched for these:
DSC$K_DTYPE_RANGE, the begin field (may be an array).
DSC$K_DTYPE_SLOPE, N-th segment's begin field !deprecated!.
DSC$K_DTYPE_WINDOW, the startidx field.
Otherwise, an error.
Example. BEGIN_OF(1..10) is 1.


### `BIT_SIZE` (Opcode 411)
|||
|-|-|
|TDI Syntax | `BIT_SIZE(arg0)` |
|C Syntax | `Tdi3BitSize` |
|Python Syntax| `MDSplus.BIT_SIZE(arg0)` |

F90 Inquiry.
The length of integer or other type (extension) in bits.
Argument. I is any type, scalar or array.
Signals. None.
Units... None.
Form.... Integer scalar.
Result.. The number of bits in I if it is scalar or in
an element of I if it is an array.
Example. BIT_SIZE(1) is 32.


### `BREAK` (Opcode 66)
|||
|-|-|
|TDI Syntax | `BREAK` |
|C Syntax | `Tdi3Break` |
|Python Syntax| `MDSplus.BREAK` |

CC Statement.
Break from FOR or WHILE loops or SWITCH.
Usual Form BREAK;
Function Form BREAK(). May be syntatically invalid.
Arguments None.
Result.. None.
Example. FOR (_J=DSIZE(_X); --J>=0; ) IF (_X[_J]) BREAK;
IF (_J < 0) ABORT();
is a lousy way to do IF (!ALL(_X)) ABORT();.


### `BSEARCH` (Opcode 67)
|||
|-|-|
|TDI Syntax | `BSEARCH(arg0,arg1,arg2,arg3)` |
|C Syntax | `TdiBsearch` |
|Python Syntax| `MDSplus.BSEARCH(arg0,arg1,arg2,arg3)` |

Numeric and Character Elemental.
Binary search in a sorted table.
Arguments Optional: MODE.
X integer, real, or text, scalar or array. No complex.
TABLE ascending-sorted, scalar or array. Should be integer,
real, or text.
MODE integer scalar, default is 0.
Signals. Same as X.
Units... None.
Form.... Integer offset in table of match.
Result.. The offset in TABLE whose value matches X.
For each list element k and matching table element j:
(1) MODE=0, TABLE[j] == X[k] with result range 0 to n-1,
where n is the number of elements in TABLE
or -1 if no exactly matching element number.
(2) MODE=+1, TABLE[j] <= X[k] < TABLE[j+1]
with result range -1 to n.
(3) MODE=-1, TABLE[j-1] < X[k] < TABLE[j]
with result range 0 to n+1.
Effectively, TABLE[-1] is negative infinity and TABLE[n]
is positive infinity.
Examples. BSEARCH(3,1:10) is 2.
BSEARCH(1..8,3..5) is [-1,-1,0,1,2,-1,-1,-1].
MAP(1:10,BSEARCH(3.9,1:10,1)) is 3.
See also. SORT and SORTI for data and index sorting.
MAP to pick the selected elements.


### `BTEST` (Opcode 69)
|||
|-|-|
|TDI Syntax | `BTEST(arg0,arg1)` |
|C Syntax | `Tdi3Btest` |
|Python Syntax| `MDSplus.BTEST(arg0,arg1)` |

F90 Bit-wise Elemental.
Test a bit of a number.
Arguments
I any. F90 requires integer.
POS integer offset within the element of I. Must be
nonnegative and less than BIT_SIZE(I).
Signals. Same as I.
Units... Same as I.
Form.... Logical of compatible shape.
Result.. True if POS is proper and the element is 1;
otherwise, false.
Examples. BTEST(8,3) is $TRUE. if _A = Set_range(2,2,[1,3,2,4])
BTEST(_A,2) is
Set_Range(2,2,[$FALSE,$FALSE,$FALSE,$TRUE]).
BTEST(2,_A) is
Set_Range(2,2,[$TRUE,$FALSE,$FALSE,$FALSE]).
See also. IBCLR to clear, BITS to extract, and IBSET to set.


### `BUILD_ACTION` (Opcode 70)
|||
|-|-|
|TDI Syntax | `BUILD_ACTION(arg0,arg1,arg2,arg3,arg4)` |
|C Syntax | `Tdi3BuildAction` |
|Python Syntax| `MDSplus.BUILD_ACTION(arg0,arg1,arg2,arg3,arg4)` |

MDS Operation.
Make an action descriptor.
Arguments
DISPATCH dispatch descriptor.
TASK procedure, program, routine, or method descriptor.
ERRORLOGS a character scalar for error reports.
COMPLETION notification list.
PERFORMANCE unsigned long vector of statistics from execution.
Result.. Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Example. BUILD_ACTION(BUILD_DISPATCH("ident","phase","when",
"completion"),BUILD_ROUTINE(timeout,image,routine))
has only dispatch and task.


### `BUILD_CALL` (Opcode 397)
|||
|-|-|
|TDI Syntax | `BUILD_CALL(arg0,arg1,argn,...)` |
|C Syntax | `Tdi3BuildCall` |
|Python Syntax| `MDSplus.BUILD_CALL(arg0,arg1,argn,...)` |

MDS Operation.
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
Result.. Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Use this form if IMAGE or ROUTINE must be expressions.
Example. BUILD_CALL(24,'TDISHR','TDI$SIND',DESCR(30.)) is
the slow and hard way to do SIND(30.).
See also. CALL for info on argument form and type of output.


### `BUILD_CONDITION` (Opcode 71)
|||
|-|-|
|TDI Syntax | `BUILD_CONDITION(arg0,arg1)` |
|C Syntax | `TdiBuildCondition` |
|Python Syntax| `MDSplus.BUILD_CONDITION(arg0,arg1)` |

MDS Operation.
Make a condition descriptor.OBSOLETE. NO LONGER SUPPORTED.
Arguments
MODIFIER word unsigned, evaluated:
TREE$K_NEGATE_CONDITION 7
TREE$K_IGNORE_UNDEFINED 8
TREE$K_IGNORE_STATUS 9
CONDITION MDS event or path.
Result.. Class-R descriptor.
Use BUILD_xxx for immediate structure building.
Use MAKE_xxx in FUNs for evaluated non-PUBLIC variables.
Example. None, normally done by COMPILE_DEPENDENCY.
See also. BUILD_DEPENDENCY BUILD_EVENT and COMPILE_DEPENDENCY.







### `TitleGoesHere` (Opcode )
|||
|-|-|
|TDI Syntax | `take_from_Compiler_syntax` |
|C Syntax | `take_from_TdiShrFunction_except_instead_of_Tdi_it_should_say_Tdi3` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |

Description goes here










### `BUILD_WITH_UNITS` (Opcode 88)

MDS Operation. Make a describe data with units.

Example: `_S = BUILD_WITH_UNITS($VALUE*6,'m/s^2')` can be used in a `BUILD_SIGNAL(_S,BUILD_WITH_UNITS(5./1024*raw_node,'V'`) or similar. Note this could also have been `BUILD_WITH_UNITS(BUILD_SIGNAL($VALUE*6, BUILD_WITH_UNITS(5./1024*raw_node,'V')),'m/s^2')`. |

|||
|-|-|
| TDI syntax | `BUILD_WITH_UNITS(arg0,arg1)` |
| C Syntax | `Tdi3BuildWithUnits(arg0,arg1)` |
| Python Syntax | `MDSplus.BUILD_WITH_UNITS(arg0,arg1)` TODO: Confirm |


|**Arguments**||
|-|-|
| Min Arguments | 2 |
| Max arguments | 2 |
|DATA | any expression that DATA(this) will be valid. |
|UNITS | character string. See the primary section on "Units".|
|Result | Class-R descriptor. <BR> Use `BUILD_xxx` for immediate structure building. <BR> Use `MAKE_xxx` in FUNs for evaluated non-PUBLIC variables.|



### `MAKE_WITH_ERROR` (Opcode 447)

|||
|-|-|
|TDI syntax | MAKE_WITH_ERROR(arg0,arg1)|
|C Syntax| `Tdi3MakeWithError` |
|Python Syntax| `Mdsplus.TdiMakeWithError(arg0,arg1)` |
|Max arguments | 2 |
|Min Arguments | 2 |

|**Arguments**||
|-|-|
|DATA |any expression that DATA(this) will be valid.|
|ERROR |Error value.|
|Result | Class-R descriptor.|
||Use `BUILD_xxx` for immediate structure building.|
||Use `MAKE_xxx` in FUNs for evaluated non-PUBLIC variables.|

MDS Operation; makes a structure that holds data with error.

Example: `_A0 = Build_With_Error(52.9177E-12, 2400E-21)`



### `IF` (Opcode 189)

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

CC Statement.

Do statement if expression true, else possibly do another.

Example: `IF (_A) _B=2; ELSE _B=3;`.


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

|||
|-|-|
| **Arguments** | Optional: BOUND,....|
|Min Arguments | 2|
|Max arguments | 9|
|| BOUND,... integer scalar or range, they are taken from ARRAY where omitted.|
| ARRAY | any type scalar, vector, or array.|
| Signals| Same as ARRAY.|
| Units | Same as ARRAY.|
| Form | Same type as ARRAY with shape from the bounds list. Any omitted bounds are picked from the corresponding bounds of ARRAY.|
| Result | Elements in array order from ARRAY. Immediate at compilation even if all but last argument are ranges and provided last argument is an array.|




