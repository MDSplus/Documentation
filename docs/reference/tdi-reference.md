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

## A

### `abort` (Opcode 31)
|||
|-|-|
|TDI Syntax | `ABORT(arg0,arg1,argn,...)` |
|C Syntax | `Tdi3Abort` |
|Python Syntax| `MDSplus.ABORT` |
|Java mdsplus-api Syntax| `CONST.ifitexistsitgoeshere()`|

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
|Python Syntax| `abs(arg0)` |
|Java mdsplus-api Syntax| `CONST.ifitexistsitgoeshere()`|

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
|Python Syntax| `ABS1(arg0)` |
|Java mdsplus-api Syntax| `CONST.ifitexistsitgoeshere()`|

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








### `TitleGoesHere` (Opcode )
|||
|-|-|
|TDI Syntax | `take from Compiler syntax` |
|C Syntax | `take from `TdiShr Function` except instead of `Tdi` it should say `Tdi3` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith**d**___ANDMAKEITLOWERCASE` |
|Java mdsplus-api Syntax| `CONST.ifitexistsitgoeshere()`|

Description goes here



















## Functions

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




