
# Mathematical Constants

> TODO: Mark, structure/improve/order

|Constants|||
|-|-|-|
| [`$2PI`](#2pi-two-pi)           | [`$FARADAY`](#faraday-opcode-9) | [`$MU0`](#mu0-opcode-408)        |
| [`$A0`](#a0-opcode--1)              | [`$G`](#g-opcode-10)            | [`$N0`](#n0-opcode-19)           |
| [`$ALPHA`](#alpha-opcode-2)         | [`$GAS`](#gas-opcode-11)        | [`$NA`](#na-opcode-20)           |
| [`$AMU`](#amu-opcode-3)             | [`$GN`](#gas-opcode-11)         | [`$P0`](#p0-opcode-21)           |
| [`$ATM`](#atm-opcode-405)           | [`$H`](#h-opcode-12)            | [`$PI`](#pi-opcode-22)           |
| [`$C`](#c-opcode-4)                 | [`$HBAR`](#hbar-opcode-13)      | [`$QE`](#qe-opcode-23)           |
| [`$CAL`](#cal-opcode-5)             | [`$I`](#i-opcode-14)            | [`$RE`](#re-opcode-24)           |
| [`$DEGREE`](#degree-opcode-6)       | [`$K`](#k-opcode-15)            | [`$RYDBERG`](#rydberg-opcode-26) |
| [`$EPSILON0`](#epsilon0-opcode-406) | [`$ME`](#me-opcode-16)          | [`$T0`](#t0-opcode-27)           |
| [`$EV`](#ev-opcode-7)               | [`$MP`](#mp-opcode-18)          | [`$TORR`](#torr-opcode-28)       |

## `$A0` (Bohr Radius)

|||
|-|-|
| TDI Syntax | `$A0` |
| Python Syntax | `MDSplus.dA0()` |
| Java mdsplus-api Syntax | `CONST.dA0()` |
|Opcode       | 1 (0x01)|

The Bohr radius constant (<em>a<sub>0</sub></em>): 52.9177 x 10<sup>-12</sup> m, with an error of 1168.02 x 10<sup>-21</sup>

```tdi
TDI> $a0
Build_With_Units(Build_With_Error(52.9177E-12, 1168.02E-21), "m")
```

## `$ALPHA` (Fine-Structure Constant)

|||
|-|-|
| TDI syntax| `$ALPHA`|
| Python Syntax| `MDSplus.dALPHA()`|
|Java mdsplus-api Syntax| `CONST.dAlpha()`|
|Opcode       | 2 (0x02)|

The Fine-Structure constant (<em>α</em>): 0.00729735, with an error of 143.276 x 10<sup>-12</sup>

```tdi
TDI> $alpha
Build_With_Error(.00729735, 143.276E-12)
```

## `$AMU` (Atomic Mass Unit)

|||
|-|-|
|TDI syntax| `$AMU`|
|Python Syntax | `MDSplus.dAMU()`|
|Java mdsplus-api Syntax| `CONST.dAmu()` |
|Opcode       | 3 (0x03)|

One unified atomic mass unit (<em>Da</em> or <em>u</em>): 1660.54 x 10<sup>-30</sup> kg, with an error of 43.0666 x 10<sup>-36</sup>

```tdi
TDI> $amu
Build_With_Units(Build_With_Error(1660.54E-30, 43.0666E-36), "kg")
```

## `$ATM` (Atmospheric Pressure Constant)

|||
|-|-|
|TDI Syntax   | `$ATM`|
|Python Syntax| `MDSplus.dATM()`|
|Java mdsplus-api Syntax| `CONST.dAtm()` |
|Opcode       | 405 (0x195)|

The atmospheric pressure constant (<em>atm</em>): 101325.0 Pa

Note: This is equivalent to [`$P0`](#p0-atmospheric-pressure-constant).

```tdi
TDI> $atm
Build_With_Units(101325., "Pa")
```

## `$C` (Speed of Light Constant)

|||
|-|-|
|TDI Syntax   | `$C`|
|Python Syntax| `MDSplus.dC()`|
|Java mdsplus-api Syntax| `CONST.dC()` |
|Opcode|4 (0x04)|

The speed of light (<em>c</em>): 299792458.0 m/s

```tdi
TDI> $c
Build_With_Units(299792458D0, "m/s")
```

## `$CAL` (Calorie)

|||
|-|-|
|TDI Syntax   | `$CAL`|
|Python Syntax| `MDSplus.dCAL()` |
|Java mdsplus-api Syntax| `CONST.dCal()`|
|Opcode|5 (0x05)|

One calorie (<em>cal</em>): 4.1868 J

```tdi
TDI> $cal
Build_With_Units(4.1868, "J")
```

## `$DEGREE` (Degrees to Radians)

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

## `$EPSILON0` (Vacuum Permittivity Constant)

|||
|-|-|
|TDI Syntax   | `$EPSILON0` |
|Python Syntax| `MDSplus.dEPSILON0()` |
|Java mdsplus-api Syntax| `CONST.dEpsilon0()`|
|Opcode|406 (0x196)|

The vacuum permittivity constant (<em>ε<sub>0</sub></em>): 8854.187817620389 x 10<sup>-15</sup> F/m

```tdi
TDI> $epsilon0
Build_With_Units(8854.187817620389D-15, "F/m")
```

## `$EV` (Electron-Volt)

|||
|-|-|
|TDI Syntax   | `$EV` |
|Python Syntax| `MDSplus.dEV()` |
|Java mdsplus-api Syntax| `CONST.dEv()`|
|Opcode|7 (0x07)|

One Electron-volt (<em>eV</em>): 160.218 x 10<sup>-21</sup> J/eV, with an error of 3654.14 x 10<sup>-30</sup>
> TODO: Change units to just "J"

```tdi
TDI> $ev
Build_With_Units(Build_With_Error(160.218E-21, 3654.14E-30), "J/eV")
```

## `$FARADAY` (Faraday Constant)

|||
|-|-|
|TDI Syntax   | `$FARADAY` |
|Python Syntax| `MDSplus.dFARADAY()` |
|Java mdsplus-api Syntax| `CONST.dFaraday()`|
|Opcode|9 (0x09)|

The Faraday constant (<em>F</em>): 96485.3 C/mol, with an error of .00381419

```tdi
TDI> $faraday
Build_With_Units(Build_With_Error(96485.3, .00381419), "C/mol")
```

## `$G` (Gravitational Constant)

|||
|-|-|
|TDI Syntax   | `$G` |
|Python Syntax| `MDSplus.dG()` |
|Java mdsplus-api Syntax| `CONST.dG()`|
|Opcode|10 (0x0A)|

The gravitational constant (<em>G</em>): 66.743 x 10<sup>-12</sup> m<sup>3</sup>/s<sup>2</sup>/kg, with an error of 1500.02 x 10<sup>-18</sup>

```tdi
TDI> $g
Build_With_Units(Build_With_Error(66.743E-12, 1500.02E-18), "m^3/s^2/kg")
```

## `$GAS` (Ideal Gas Constant)

|||
|-|-|
|TDI Syntax   | `$GAS` |
|Python Syntax| `MDSplus.dGAS()` |
|Java mdsplus-api Syntax| `CONST.dGas()`|
|Opcode|11 (0x0B)|

The ideal gas constant (<em>R</em>): 8.31446 J/K/mol, with an error of 43.5899 x 10<sup>9</sup>

```tdi
TDI> $gas
Build_With_Units(Build_With_Error(8.31446, 43.5899E-9), "J/K/mol")
```

## `$GN` (Gravity Acceleration Constant)

|||
|-|-|
|TDI Syntax   | `$GN` |
|Python Syntax| `MDSplus.dGN()` |
|Java mdsplus-api Syntax| `CONST.dGn()`|
|Opcode|407 (0x197)|

The acceleration of gravity (<em>g</em>): 9.80665 m/s<sup>2</sup>

```tdi
TDI> $gn
Build_With_Units(9.80665, "m/s^2")
```

## `$H` (Planck Constant)

|||
|-|-|
|TDI Syntax   | `$H` |
|Python Syntax| `MDSplus.dH()` |
|Java mdsplus-api Syntax| `CONST.dH()`|
|Opcode|12 (0x0C)|

The Planck constant (<em>h</em>): 662.607 x 10<sup>36</sup> J*s, with an error of 2857.25 x 10<sup>45</sup>

```tdi
TDI> $h
Build_With_Units(Build_With_Error(662.607E-36, 2857.25E-45), "J*s")
```

## `$HBAR` (Reduced Planck Constant)

|||
|-|-|
|TDI Syntax   | `$HBAR` |
|Python Syntax| `MDSplus.dHBAR()` |
|Java mdsplus-api Syntax| `CONST.dHbar()`|
|Opcode|13 (0x0D)|

The reduced Planck constant (<em>H/2pi</em> or <em><span style="text-decoration: overline">H</span></em>): 105.457 x 10<sup>36</sup> J*s, with an error of 1967.42 x 10<sup>45</sup>

```tdi
TDI> $hbar
Build_With_Units(Build_With_Error(105.457E-36, 1967.42E-45), "J*s")
```

## `$I` (Imaginary)

|||
|-|-|
|TDI Syntax   | `$I` |
|Python Syntax| `MDSplus.dI()` |
|Java mdsplus-api Syntax| `CONST.dI()`|
|Opcode|14 (0x0E)|

Imaginary (<em>i</em>): `Cmplx(0.0, 1.0)`

```tdi
TDI> $i
Cmplx(0.,1.)
```

## `$K` (Boltzmann Constant)

|||
|-|-|
|TDI Syntax   | `$K` |
|Python Syntax| `MDSplus.dK()` |
|Java mdsplus-api Syntax| `CONST.dK()`|
|Opcode|15 (0x0F)|

The Boltzmann constant (<em>k</em> or <em>k<sub>B</em></em>): 13.8065 x 10<sup>24</sup> J/K, with an error of 276.341 x 10<sup>33</sup>

```tdi
TDI> $k
Build_With_Units(Build_With_Error(13.8065E-24, 276.341E-33), "J/K")
```

## `$ME` (Electron Mass)

|||
|-|-|
|TDI Syntax   | `$ME` |
|Python Syntax| `MDSplus.dME()` |
|Java mdsplus-api Syntax| `CONST.dMe()`|
|Opcode|16 (0x10)|

The mass of an electron (<em>m<sub>e</sub></em>): 910.938 x 10<sup>33</sup> kg, with an error of 25.8874 x 10<sup>39</sup>

```tdi
TDI> $me
Build_With_Units(Build_With_Error(910.938E-33, 25.8874E-39), "kg")
```

## `$MP` (Proton Mass)

|||
|-|-|
|TDI Syntax   | `$MP` |
|Python Syntax| `MDSplus.dMP()` |
|Java mdsplus-api Syntax| `CONST.dMp()`|
|Opcode|18 (0x12)|

The mass of a proton (<em>m<sub>p</sub></em>): 1672.62 x 10<sup>30</sup> kg, with an error of 85.2717 x 10<sup>36</sup>

```tdi
TDI> $mp
Build_With_Units(Build_With_Error(1672.62E-30, 85.2717E-36), "kg")
```

## `$MU0` (Vacuum Permeability)

|||
|-|-|
|TDI Syntax   | `$MU0` |
|Python Syntax| `MDSplus.dMU0()` |
|Java mdsplus-api Syntax| `CONST.dMu0()`|
|Opcode|408 (0x198)|

The permeability of a vacuum (<em>μ<sub>0</sub></em>): 1256.637061435917 x 10<sup>-9</sup> N/A<sup>2</sup>

```tdi
TDI> $mu0
Build_With_Units(1256.637061435917D-9, "N/A^2")
```

## `$N0` (Loschmidt's Number)

|||
|-|-|
|TDI Syntax   | `$N0` |
|Python Syntax| `MDSplus.dN0()` |
|Java mdsplus-api Syntax| `CONST.dN0()`|
|Opcode|19 (0x13)|

Loschmidt's number (<em>n<sub>0</sub></em>): 26.8678 x 10<sup>24</sup> /m<sup>3</sup>, with an error of 743.623 x 10<sup>15</sup>
> TODO: Verify units should start with /

```tdi
TDI> $n0
Build_With_Units(Build_With_Error(26.8678E24, 743.623E15), "/m^3")
```

## `$NA` (Avogadro's Number)

|||
|-|-|
|TDI Syntax   | `$NA` |
|Python Syntax| `MDSplus.dNA()` |
|Java mdsplus-api Syntax| `CONST.dNa()`|
|Opcode|20 (0x14)|

Avogadro's number (<em>N<sub>A</sub></em>): 602.214 x 10<sup>21</sup> /mol, with an error of 11.645 x 10<sup>15</sup>
> TODO: Verify units should start with /

```tdi
TDI> $na
Build_With_Units(Build_With_Error(602.214E21, 11.645E15), "/mol")
```

## `$P0` (Atmospheric Pressure Constant)

|||
|-|-|
|TDI Syntax   | `$P0` |
|Python Syntax| `MDSplus.dP0()` |
|Java mdsplus-api Syntax| `CONST.dP0()`|
|Opcode|21 (0x15)|

See [`$ATM`](#atm-atmospheric-pressure-constant).

## `$PI` (Pi)

|||
|-|-|
|TDI Syntax   | `$PI` |
|Python Syntax| `MDSplus.dPI()` |
|Java mdsplus-api Syntax| `CONST.dPi()`|
|Opcode|22 (hex(0x16)|

Pi, the circumference divided by the radius (<em>π</em>): 3.141592653589793

```tdi
TDI> $pi
3.141592653589793D0
```

## `$2PI` (Two Pi)

|||
|-|-|
|TDI Syntax   | `$2PI`|
|Python Syntax| `MDSplus.d2PI()`|
|Java mdsplus-api Syntax| `CONST.d2Pi()` |
|Opcode       | 372 (0x174)|

Two times pi (<em>2π</em>): 6.283185307179586

```tdi
TDI> $2pi
6.283185307179586D0
```

## `$QE` (Elementary Charge)

|||
|-|-|
|TDI Syntax   | `$QE` |
|Python Syntax| `MDSplus.dQE()` |
|Java mdsplus-api Syntax| `CONST.dQe()`|
|Opcode|23|

The negative charge of an electron (<em>e</em>): 160.218 x 10<sup>21</sup> C, with an error of 3654.14 x 10<sup>30</sup>

```tdi
TDI> $qe
Build_With_Units(Build_With_Error(160.218E-21, 3654.14E-30), "C")
```

## `$RE` (Classical Electron Radius)

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

## `$RYDBERG` (Rydberg Constant)

|||
|-|-|
|TDI Syntax   | `$RYDBERG` |
|Python Syntax| `MDSplus.dRYDBERG()` |
|Java mdsplus-api Syntax| `CONST.dRydberg()`|
|Opcode|26|

The Rydberg constant (<em>R<sub>∞</sub></em>): 10.9737 x 10<sup>6</sup> /m, with an error of 0.443876
> TODO: Verify units should start with /

```tdi
TDI> $rydberg
Build_With_Units(Build_With_Error(10.9737E6, .443876), "/m")
```

## `$T0` (Standard Temperature)

|||
|-|-|
|TDI Syntax   | `$T0` |
|Python Syntax| `MDSplus.$T0` |
|Java mdsplus-api Syntax| `CONST.dT0()`|
|Opcode|27|

The standard temperature: 273.15 K

```tdi
TDI> $t0
Build_With_Units(273.15, "K")
```

## `$TORR` (Torr)

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


## `$ROPRAND` (NaN, Infinity, Reserved Operand)

|||
|-|-|
|TDI Syntax   | `$ROPRAND` |
|Python Syntax| `MDSplus.dROPRAND()` |
|Java mdsplus-api Syntax| `CONST.dRoprand()`|
|Opcode       | 25|

Represents NaN or Infinity from floating point math.

```tdi
TDI> 1.0 / 0.0
$ROPRAND
```


## `epsilon` (Opcode 150)

|||
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



### `huge` (Opcode 181)

|||
|-|-|
|TDI Syntax   | `huge(_X)` |
|Python Syntax| `MDSplus.huge(_X)` |
|Min arguments| 1 |
|Max arguments| 1 |



Returns the largest possible [Number](#numeric) that can be stored in the type (See [integer](#integer), [floating point](#floating-point)).

Argument:
* `_X` must be numeric scalar or array.

> TODO: come back to this
The result is `r^q -1` if X is integer and `(1-(b^-p))b^emax` if X is real, where:
* `r` is the integer base,
* `q` is the number of digits,
* `b` is the real base, 
* `p` is the number of digits, 
* `emax` is the maximum exponent in model numbers like X.

Examples
```
#TODO: Come back to this

TDI> HUGE(1B)
127B
TDI> HUGE(1BU)
255BU


* HUGE(1.0) is (1-(2^-24))*2^127 and HUGE(0) is 2^31-1 on the VAX.
* huge(1.0) returns `340.282E36`
* huge(1) returns `2147483647`
* huge(1F0) returns `170.141F36`
```

See also: [tiny()](#tiny) for the smallest possible value.

### `TINY`
|||
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

# Basic Math

### `ADD` (Add)

|||
|-|-|
|TDI Syntax| `_X + _Y` or `ADD(_X, _Y)`|
|Python Syntax| `MDSplus.ADD(x, y)`|
|Opcode|38|

Returns the result of `_X` added to `_Y`.

`_X` and `_Y` must be [Numeric](#numeric). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

> TODO: Mark, help reword
If `_X` and `_Y` are both a [Signal](#signal), the result will not be; The data parts of the signal will be added together ignoring the time base. However, if only one is a [Signal](#signal), the result will be as well.

Integer overflows will be truncated.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 3 + 4
7

TDI> [2, 3, 4] + 5
[7,8,9]

TDI> [[1, 2], [3, 4]] + [[5, 6], [7, 8]]
[[6,8], [10,12]]

TDI> [1, 2, 3, 4] + [5, 6]
[6,8]

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) + 5
Build_Signal([6,7,8,9], *, [.1,.2,.3,.4])

TDI> cmplx(3, 4) + 5
Cmplx(8.,4.)

TDI> cmplx(3, 4) + cmplx(5, 6)
Cmplx(8.,10.)

# Overflow
TDI> 255BU + 1BU
0BU

TDI> build_with_units(1, 'm') + 5
Build_With_Units(6, "m")

TDI> build_with_units(1, 'm') + build_with_units(5, 'm')
Build_With_Units(6, "m")

# The ? indicating a unit mismatch
TDI> build_with_units(1, 'm') + build_with_units(5, 'ft')
Build_With_Units(6, "?")

TDI> build_with_error(1, 0.1) + 5
6

```

See also:
* [`SUM()`](#sum-total-sum)


### `SUBTRACT` (Subtract)

|||
|-|-|
|TDI Syntax   | `_X - _Y` or `SUBTRACT(_X, _Y)` |
|Python Syntax| `MDSplus.SUBTRACT(x, y)` |
|Opcode|336|

Returns the result of `_Y` subtracted from `_X`.

`_X` and `_Y` must be [Numeric](#numeric). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

> TODO: Mark, help reword
If `_X` and `_Y` are both a [Signal](#signal), the result will not be. However, if only one is a [Signal](#signal), the result will be as well.

Integer underflows will be truncated.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 3 - 4
-1

TDI> [2, 3, 4] - 5
[-3,-2,-1]

TDI> [3, 4] - [2, 1]
[1,3]

TDI> [[4, 3], [2, 1]] - [[5, 6], [7, 8]]
[[-1,-3], [-5,-7]]

TDI> [4, 3, 2, 1] - [5, 6]
[-1,-3]

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) - 5
Build_Signal([-4,-3,-2,-1], *, [.1,.2,.3,.4])

TDI> cmplx(3, 4) - 5
Cmplx(-2.,4.)

TDI> cmplx(3, 4) - cmplx(5, 6)
Cmplx(-2.,-2.)

# Underflow
TDI> 0BU - 1BU
255BU

TDI> build_with_units(1, 'm') - 5
Build_With_Units(-4, "m")

TDI> build_with_units(1, 'm') - build_with_units(5, 'm')
Build_With_Units(-4, "m")

# The ? indicating a unit mismatch
TDI> build_with_units(1, 'm') - build_with_units(5, 'ft')
Build_With_Units(-4, "?")

TDI> build_with_error(1, 0.1) - 5
-4
```

### `MULTIPLY`

|||
|-|-|
|TDI Syntax   | `_X * _Y` or `MULTIPLY(_X, _Y)` |
|Python Syntax| `MDSplus.MULTIPLY(x, y)` |
|Opcode|247|

Returns the result of `_X` multiplied by `_Y`.

`_X` and `_Y` must be [Numeric](#numeric). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

> TODO: Mark, help reword // I think this is fine!
If `_X` and `_Y` are both a [Signal](#signal), the result will not be. However, if only one is a [Signal](#signal), the result will be as well.

Integer overflows will be truncated.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however:
* If `_X` has units, but `_Y` does not, the units will be `UNITS_OF(_X)`.
* If `_Y` has units, but `_X` does not, the units will be `UNITS_OF(_Y)`.
* If `_X` and `_Y` both have units, the units will be `UNITS_OF(_X) // "*" // UNITS_OF(_Y)`.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 3 * 4
12

TDI> [2, 3, 4] * 5
[10,15,20]

TDI> [1, 2] * [3, 4]
[3,8]

TDI> [1, 2, 3, 4] * [5, 6]
[5,12]

TDI> make_signal([[1, 2], [3, 4]], *) * 5
Build_Signal([[5,10], [15,20]], *)

TDI> make_signal([[1, 2], [3, 4]], *) * make_signal([[5, 6], [7, 8]], *)
[[5,12], [21,32]]

TDI> cmplx(3, 4) * 5
Cmplx(15.,20.)

TDI> cmplx(3, 4) * cmplx(5, 6)
Cmplx(-9.,38.)

# Overflow
TDI> 128BU * 2BU
0BU

TDI> build_with_units(1, 'm') * 5
Build_With_Units(5, "m")

TDI> build_with_units(1, 'm') * build_with_units(5, 'm')
Build_With_Units(5, "m*m")

TDI> build_with_units(1, 'm') * build_with_units(5, 'ft')
Build_With_Units(5, "m*ft")

TDI> build_with_error(1, 0.1) * 5
6

TDI> build_with_error(1, 0.1) * build_with_error(5, 0.2)
6
```

See also:
* [`PRODUCT()`](#product-total-product)

### `dprod` (Opcode 133)

> TODO: Move?

|||
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


### `DIVIDE` (Divide)

|||
|-|-|
|TDI Syntax   | `_X / _Y` or `DIVIDE(_X, _Y)` |
|Python Syntax| `MDSplus.DIVIDE(x, y)` |
|Opcode|129|

Returns the result of `_X` divided by `_Y`.

`_X` and `_Y` must be [Numeric](#numeric). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

> TODO: Mark, help reword
If `_X` and `_Y` are both a [Signal](#signal), the result will not be. However, if only one is a [Signal](#signal), the result will be as well.

> TODO: Rounding

Integer division will result in truncation.

Floating point division by zero will return `$ROPRAND`. Integer division by zero will return `0`.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however:
* If `_X` has units, but `_Y` does not, the units will be `UNITS_OF(_X)`.
* If `_Y` has units, but `_X` does not, the units will be `"/" // UNITS_OF(_Y)`.
* If `_X` and `_Y` both have units, the units will be `UNITS_OF(_X) // "/" // UNITS_OF(_Y)`.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 3.0 / 4.0
.75

TDI> [2, 3, 4] / 5.0
[.4,.6,.8]

TDI> [1.0, 2.0] / [3, 4]
[.333333,.5]

TDI> [1, 2, 3, 4] / [5.0, 6.0]
[.2,.333333]

TDI> make_signal([[1, 2], [3, 4]], *) / 5.0
Build_Signal([[.2,.4], [.6,.8]], *)

TDI> make_signal([[1.0, 2.0], [3.0, 4.0]], *) / make_signal([[5, 6], [7, 8]], *)
[[.2,.333333], [.428571,.5]]

TDI> cmplx(3, 4) / 5
Cmplx(.6,.8)

TDI> cmplx(3, 4) / cmplx(5, 6)
Cmplx(.639344,.0327869)

# Integer division
TDI> 3 / 4
0

TDI> build_with_units(1, 'm') / 5
Build_With_Units(6, "m")

TDI> 5 / build_with_units(1, 's')
Build_With_Units(5, "/s")

TDI> build_with_units(5, 'm') / build_with_units(1, 's')
Build_With_Units(5, "m/s")

TDI> build_with_error(1.0, 0.1) / 5.0
.2

TDI> build_with_error(1.0, 0.1) / build_with_error(5.0, 0.2)
.2
```

See also:
* [`MOD()`](#mod-modulus-remainder)

### `MOD` (Modulus, Remainder)

|||
|-|-|
|TDI Syntax   | `_X % _Y` or `_X MOD _Y` or `MOD(_X, _Y)` |
|Python Syntax| `MDSplus.MOD(x, y)` |
|Opcode|245|

Returns the remainder of `_X` divided by `_Y`.

`_X` and `_Y` must be [Numeric](#numeric). If either argument is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` and `_Y` are both an [Array](#array) or a [Signal](#signal), but do not have the same length, the result will be truncated to the shorter one.

If `_X` and `_Y` are both [Signal](#signal)s, the result will not be. However, if only one is a [Signal](#signal), the result will be a [Signal](#signal).

The value(s) of `_X` and `_Y` must be [Real](#real).

Floating point division by zero will return `0`. Integer division by zero will result in a segfault.

> TODO: Floating point / 0 should return `$ROPRAND` according to original docs

> TODO: GitHub Issue # for segfault

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> 4 % 3
1

TDI> [5, 6, 7] % 5
[0,1,2]

TDI> [[5, 6], [7, 8]] % [[2, 3], [4, 5]]
[[1,0], [3,3]]

TDI> [5, 6, 7, 8] % [2, 3]
[1,0]

TDI> make_signal([1, 2, 3, 4], *, [0.1, 0.2, 0.3, 0.4]) % 2
Build_Signal([1,0,1,0], *, [.1,.2,.3,.4])

TDI> build_with_units(4, 'm') % 3
Build_With_Units(1, "m")

TDI> build_with_units(4, 'm') % build_with_units(3, 'm')
Build_With_Units(1, "m")

# The ? indicating a unit mismatch
TDI> build_with_units(4, 'm') % build_with_units(3, 'ft')
Build_With_Units(1, "?")

TDI> build_with_error(4, 0.1) % 3
1
```

See also:
* [`DIVIDE()`](#divide-divide)


### `POST_DEC` (Decrement After)
|||
|-|-|
|TDI Syntax   | `_VAR--` or `POST_DEC(_VAR)`|
|Python Syntax| `MDSplus._VAR--` |
|Opcode|272|

Evaluates the expression with the current value then decreases the value by 1.
* Equivalent to `_VAR--`
* argument _VAR must be a variable with numeric value or operator on variable.

Result: Old value of NAME.
Side Effect. NAME is now one less than before.

Examples
```tdi
TDI> _A = 5
5
TDI> write(*, _A)
          5
12
TDI> write(*, _A--) /* _A is decremented after the function is evaluated. */
          5
12
TDI> _A
4

TDI> _A = 5.5
5.5
TDI> --_A
4.5

--5 /* This is an error, argument must contain a variable to write back into */

```

see also: `pre_dec` for pre, `post_inc` for increment

### `POST_INC` (Increment After)
|||
|-|-|
|TDI Syntax   | `_VAR++` |
|Opcode|273|

Evaluates the expression with the current value then increases the value by 1.
* Equivalent to `_VAR++`
* argument _VAR must be a variable with numeric value or operator on variable.


```tdi
TDI> _A = 5
5
TDI> write(*, _A)
          5
12
TDI> write(*, _A++) /* _A is incremented after the function is evaluated */
          5
12
TDI> _A
6

TDI> _A = 5.5
5.5
TDI> ++_A
6.5

```

PRE_DEC

### `PRE_DEC`
|||
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

### `PRE_INC`
|||
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

### `ABS` (Absolute Value)

|||
|-|-|
|TDI Syntax   | `ABS(_X)` |
|Python Syntax| `MDSplus.ABS(x)` |
|Opcode       | 32 (0x20)|

Returns the absolute value of `_X`.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` contains [Complex Numbers](#complex-number), the result will be the square root of the sum of the squares of the real and imaginary parts. The real and imaginary parts will be scaled to avoid overflow. Use [`ABS1()`](#abs1-absolute-value-with-l1-norm) or [`ABSSQ()`](#abssq-absolute-value-squared) to avoid the square root for for complex numbers.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

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

TDI> abs(build_with_units(-2, 'C'))
Build_With_Units(2, "C")

TDI> abs(build_with_error(-2, 0.1))
2
```

See also:
* [`ABS1()`](#abs1-absolute-value-with-l1-norm)
* [`ABSSQ()`](#abssq-absolute-value-squared)

### `ABS1` (Absolute Value with L<sup>1</sup> Norm)

|||
|-|-|
|TDI Syntax   | `ABS1(_X)` |
|Python Syntax| `MDSplus.ABS1(x)` |
|Opcode|33|

Returns the absolute value of the L<sup>1</sup> norm of `_X`.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` contains [Complex Numbers](#complex-number), the result will be the sum of the absolute values of the real and imaginary parts; otherwise, this will behave the same as [`ABS()`](#abs-absolute-value).

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> abs1(cmplx(-3.0, 4.0))
7.

TDI> abs1([cmplx(-3.0, 4.0), cmplx(-4.0, 5.0)])
[7.,9.]

TDI> abs1(-2)
2

TDI> abs1([[-1, 2], [-3, 4]])
[[1,2], [3,4]]

TDI> abs1(build_with_units(-2, 'C'))
Build_With_Units(2, "C")

TDI> abs1(build_with_error(-2, 0.1))
2
```

See also:
* [`ABS()`](#abs-absolute-value)
* [`ABSSQ()`](#abssq-absolute-value-squared)


### `ABSSQ` (Absolute Value Squared)

|||
|-|-|
|TDI Syntax   | `ABSSQ(_X)` |
|Python Syntax| `MDSplus.ABSSQ(x)` |
|Opcode|34|

Returns the absolute value of `_X * _X`.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

If `_X` contains [Complex Numbers](#complex-number), the result will be square of the sum of the real and imaginary parts.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved as `UNITS_OF(_X) // "*" // UNITS_OF(_X)`.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```TDI
TDI> abssq(cmplx(-3.0, 4.0))
25.

TDI> abssq([cmplx(-3.0, 4.0), cmplx(-4.0, 5.0)])
[25.,41.]

TDI> abssq(-2)
4

TDI> abssq([[-1, 2], [-3, 4]])
[[1,4], [9,16]]

TDI> abssq(build_with_units(-2, 'C'))
Build_With_Units(4, "C*C")

TDI> abssq(build_with_error(-2, 0.1))
4
```

See also:
* [`ABS()`](#abs-absolute-value)
* [`ABS1()`](#abs1-absolute-value-with-l1-norm)

### `MEAN`
|||
|-|-|
|TDI Syntax   | `MEAN(_ARRAY, [_DIM], [_MASK])` |
|Python Syntax| `MDSplus.MEAN(_ARRAY, [_DIM], [_MASK])` |
|Opcode|237|

Average value of the elements of `_ARRAY` along dimension `_DIM` corresponding to the true elements of `_MASK`.

Arguments:
* `_ARRAY` numeric array.
* [`_DIM`] optional: integer scalar from 0 to n-1, where n is rank of ARRAY. 
* [`_MASK`] optional: logical and conformable to ARRAY.

|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. 
|Units        |Same as ARRAY. 
|Form         |Same type as ARRAY. It is a scalar if DIM is absent or
ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.

TODO: Come back to this
The result without DIM is the mean value of the elements of ARRAY, testing only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the mean of ARRAY elements with dimension DIM fixed as the element number of the result. If no value is found, zero is given.

Examples
```tdi
TDI> mean([1,7,9])
5

TDI> mean([1.,7.,9.])
5.66667

# Here is how to use _DIM
TDI> _A = [[1, 5, 3],[12, 11, 10]]
[[1,5,3], [12,11,10]]
TDI> mean(_A, *)
7
TDI> mean(_A, 0)
[3,11]
TDI> mean(_A, 1)
[6,8,6]

# Here is how to use _MASK
TDI> _A = [1., -2., 7., -5., 9.]
[1.,-2.,7.,-5.,9.]
TDI> mean(_A, *, _A > 0)
5.66667
TDI> mean(_A, *, _A < 0)
-3.5

```


### `exp` 

|||
|-|-|
|TDI Syntax   | `exp(arg0) ` |
|Python Syntax| `MDSplus.exp(arg0)` |
|Opcode|160|

Exponential
Arguments can be real or complex.
Returns processor approximation to `e^X`. 
If `_X` is complex, the imaginary part is in radians.

Example:
* `EXP(1.0)` returns `2.71828`, approximately.

### `POWER`
|||
|-|-|
|TDI Syntax   | `_A ^ _B` or `_A ** _B` or `POWER(_A, _B)`|
|Python Syntax| `MDSplus.POWER(a, b)` |
|Opcode|274|

Raise number to a power. Converts integer exponents to long and takes integral power.
* Arguments A and B must be [numeric](#numeric).
* Warning, long unsigned and longer [integer](#integer) types are truncated.
* Warning, quad-precision complex `HC^HC` is truncated to `GC^GC`.
* Warning, `0.0^0` is not detected as an error and results in 1.0.
* Warning, do not use `-X^2.` aka `(-X)^2.0`, when you mean `-(X^2)`, because it will bomb. Note that negation binds tighter than power.
* Warning, use integer exponents when you mean that. For example, `X^2.0` is an order of magnitude slower than `X^2`.

TODO: ...what...?
* For real numbers, or complex powers gives `EXP(LOG(X)*Y)`. This will be `$ROPRAND` if `X` is not positive.


```tdi

TDI> 9 ** .5
3.

TDI> 2 ^ 4
16

# better written as SQRT(2)
TDI> 2 ** .5
1.41421

TDI> _x = 5
5

TDI> -_x^2
25

TDI> -(_x^2)
-25

TDI> (-_x)^2
25

TDI> cmplx(3,4)^2
Cmplx(-7.,24.)

TDI> EXP(LOG(2)*4) # TODO: ...what...?
16.

TDI> cmplx(0,1)^2
Cmplx(-1.,0.)

TDI> cmplx(0,1)^3
Cmplx(0.,-1.)

TDI> cmplx(0,1)^4
Cmplx(1.,0.)

```

### `log` (Opcode 223)

|||
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

### `LOG10` (Base-10 Logarithm)

> (version 2--opcode moved, natural language title)  

|||
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

|||
|-|-|
|TDI Syntax   | `LOG2(_NUM)` |
|Python Syntax| `MDSplus.LOG2(_NUM)` |

Logarithm, base 2.
* Argument `_NUM` must be real. Complex numbers result in error.
* Units are disregarded

Examples
* `log2(8.0)` returns `3.0`.




### `MAX`
|||
|-|-|
|TDI Syntax   | `MAX(_NUM0, _NUM1, [_NUM2], ...)` |
|Python Syntax| `MDSplus.MAX(_NUM0, _NUM1, [_NUM2], ...)` |
|Min arguments| 2  |
|Max arguments| 254|
|Opcode|233|

Returns the maximum (highest?) value from the arguments given.
* Arguments must be integer or real. Complex numbers cause error.

Examples

```tdi
TDI> max(-9.0,7.0,2.0) 
7.0

max(make_signal([[-1, 7, 4], [12, 1, -2]], *),make_signal([[1, 2, 3], [3, 4, 5]], *))
[[1,7,4], [12,4,5]]

max([1, 2, 3],[4, -2, 1])
[4,2,3]
```


### `MIN`
|||
|-|-|
|TDI Syntax   | `MIN(arg0,arg1,argn,...)` |
|Python Syntax| `MDSplus.MIN(arg0,arg1,argn,...)`|
|Opcode|241|

Minimum value.
* Arguments: Integer or real. Complex numbers cause error.


|Signals      |The single signal or the smallest.
|Units        |The single or matching units, else bad.
|Form         |The compatible form of all the arguments. Conversion is
done pairwise.

|Result       |The smallest 
|Arguments, Results|A reserved operand will dominate.

Examples
```
min(-9.0,7.0,2.0) 
-9.

TDI> min([1,2,3],[-1,-2,-3], [4,4,4]) 
[-1,-2,-3]

```



### `SQRT`
|||
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

### `SQUARE`
|||
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

## Rounding

> (does this need to be a heading?)

### `CEILING` (Round Up)

|||
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

### `FLOOR` (Round Down)

|||
|-|-|
|TDI Syntax   | `floor(_NUM) ` |
|Python Syntax| `MDSplus.floor(_NUM) ` |
|Opcode|168|

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


### `AINT` (Truncate Floating Point Number)

|||
|-|-|
|TDI Syntax   | `AINT(_X)` |
|Python Syntax| `MDSplus.AINT(x)` |
|Opcode|42|

Returns `_X`, with all numbers after the decimal point removed (not rounded), and converted to a [Floating Point Number](#floating-point).

> TODO: Mark, check/reword all of these references.

To round, use [`ANINT`](#anint-nearest-integer-round-floating-point-number). To round up, use [`CEILING`](#ceiling-round-up). To round down, use [`FLOOR`](#floor-round-down).

To round and convert to an integer, use [`NINT`](#nint-nearest-integer-rounded-integer-cast).

To truncate and convert to an integer, use [`INT`](#int-integer-cast) or any of the [Integer](#integer) constructors.

`_X` must be [`Real`](#real-number). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

> TODO: Kind seems to be broken
Optional `_KIND`, see [`Kind`](#kind).

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> aint(-4.5)
-4.

TDI> aint(0.999)
0.

TDI> aint($PI)
3D0

TDI> aint([1.1, 2.2, 3.3])
[1.,2.,3.]

TDI> aint(42)
42.
```

See also:
* [`ANINT`](#anint-nearest-integer-round-floating-point-number)
* [`CEILING`](#ceiling-round-up)
* [`FLOOR`](#floor-round-down)
* [`NINT`](#nint-nearest-integer-rounded-integer-cast)
* [`INT`](#int-integer-cast)


### `ANINT` (Nearest Integer, Round Floating Point Number)

|||
|-|-|
|TDI Syntax   | `ANINT(_X)` |
|Python Syntax| `MDSplus.ANINT(x)` |
|Opcode|47|

Returns `_X` rounded to the nearest whole number, and converted to a [Floating Point Number](#floating-point).

> TODO: Mark, check/reword all of these references.

To round up, use [`CEILING`](#ceiling-round-up). To round down, use [`FLOOR`](#floor-round-down). To truncate, use [`AINT`](#aint-truncate-floating-point-number).

To round and convert to an integer, use [`NINT`](#nint-nearest-integer-rounded-integer-cast).

To truncate and convert to an integer, use [`INT`](#int-integer-cast) or any of the [Integer](#integer) constructors.

`_X` must be [`Real`](#real-number). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> anint(-4.5)
-5.

TDI> anint(0.999)
1.

TDI> anint($PI)
3D0

TDI> anint([1.1, 5.5, 9.9])
[1.,6.,10.]

TDI> anint(42)
42.
```

See also:
* [`AINT`](#aint-truncate-floating-point-number)
* [`CEILING`](#ceiling-round-up)
* [`FLOOR`](#floor-round-down)
* [`NINT`](#nint-nearest-integer-rounded-integer-cast)
* [`INT`](#int-integer-cast)




### `NINT` (Nearest Integer, Rounded Integer Cast)

|||
|-|-|
|TDI Syntax   | `NINT(_X)` |
|Python Syntax| `MDSplus.NINT(x)` |
|Opcode|255|

Returns `_X` rounded to the nearest whole number, and converted to an [Integer](#integer).

If `_X` is already an [Integer](#integer) type, the type will be preserved. Otherwise, the result will be converted to a [`LONG`](#long-32-bit-signed-integer-cast).

To round up, use [`CEILING`](#ceiling-round-up). To round down, use [`FLOOR`](#floor-round-down). To truncate, use [`AINT`](#aint-truncate-floating-point-number).

To round and convert to an integer, use [`NINT`](#nint-nearest-integer-rounded-integer-cast).

To truncate and convert to an integer, use [`INT`](#int-integer-cast) or any of the [Integer](#integer) constructors.

`_X` must be [`Real`](#real-number). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> nint(-4.5)
-5

TDI> nint(0.999)
1

TDI> nint($PI)
3

TDI> nint([1.1, 5.5, 9.9])
[1,6,10]

TDI> nint(42)
42
```

Examples. NINT(2.783) is 3. NINT(-2.783) is -3.

```tdi
TDI> nint(cmplx(2.5, 4.5))
3

TDI> nint(1:3:.3333)
[1,1,2,2,2,3,3]

```


## Trigonometry

### `SIN` (Sine)

|||
|-|-|
|TDI Syntax   | `SIN(_X)` |
|Python Syntax| `MDSplus.SIN(x)` |
|Opcode|318|

Returns the sine of `_X` in radians.

To use degrees, use [`SIND()`](#sind-sine-degrees).

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however the units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> sin(1.5708)
1.

TDI> sin([1.5708, 4.7123, 7.8539, 10.9956])
[1.,-1.,1.,-1.]

TDI> sin(cmplx(1.0, 2.0))
Cmplx(3.16578,1.9596)

TDI> sin(make_signal([1.5708, 4.7123, 7.8539, 10.9956], *, [0.1, 0.2, 0.3, 0.4]))
Build_Signal([1.,-1.,1.,-1.], *, [.1,.2,.3,.4])

TDI> sin(build_with_units(1.5708, 'rad'))
Build_With_Units(1., "?")

TDI> sin(build_with_error(1.5708, 0.1))
1.
```

See also:
* [`SIND()`](#sind-sine-degrees)
* [`SINH()`](#sinh-hyperbolic-sine)

### `COS` (Cosine)

|||
|-|-|
|TDI Syntax   | `COS(_X)` |
|Python Syntax| `MDSplus.COS(x)` |
|Opcode|106|

Returns the cosine of `_X` in radians.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however the units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> cos(3.14159)
-1.

TDI> cos([3.1415, 6.283, 9.4245, 12.566])
[-1.,1.,-1.,1.]

TDI> cos(cmplx(1.0, 2.0))
Cmplx(2.03272,-3.0519)

TDI> cos(make_signal([3.1415, 6.283, 9.4245, 12.566], *, [0.1, 0.2, 0.3, 0.4]))
Build_Signal([-1.,1.,-1.,1.], *, [.1,.2,.3,.4])

TDI> cos(build_with_units(3.14159, 'rad'))
Build_With_Units(-1., "?")

TDI> cos(build_with_error(3.14159, 0.1))
-1.
```

See also:
* [`COSD`](#cosd-cosine-degrees)
* [`COSH`](#cosh-hyperbolic-cosine)

### `TAN`

|||
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

### `SIND` (Sine Degrees)

|||
|-|-|
|TDI Syntax   | `SIND(_X)` |
|Python Syntax| `MDSplus.SIND(x)` |
|Opcode|319|

Returns the sine of `_X` in degrees.

To use radians, use [`SIN()`](#sin-sine).

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

The value(s) of `_X` must be [Real](#real).

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however the units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> sind(90)
1.

TDI> sind([90, 270, 450, 630])
[1.,-1.,1.,-1.]

TDI> sind(make_signal([90, 270, 450, 630], *, [0.1, 0.2, 0.3, 0.4]))
Build_Signal([1.,-1.,1.,-1.], *, [.1,.2,.3,.4])

TDI> sind(build_with_units(90, 'deg'))
Build_With_Units(1., "?")
```

See also:
* [`SIN()`](#sin-sine)

### `COSD` (Cosine Degrees)

|||
|-|-|
|TDI Syntax   | `COSD(_X)`         |
|Python Syntax| `MDSplus.COSD(x)` |
|Opcode|107|

Returns the cosine of `_X` in degrees.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

The value(s) of `_X` must be [Real](#real).

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however the units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> cosd(180)
-1.

TDI> cosd([180, 360, 540, 720])
[-1.,1.,-1.,1.]

TDI> cosd(make_signal([180, 360, 540, 720], *, [0.1, 0.2, 0.3, 0.4]))
Build_Signal([-1.,1.,-1.,1.], *, [.1,.2,.3,.4])

TDI> cosd(build_with_units(180, 'deg'))
Build_With_Units(-1., "?")

TDI> cosd(build_with_error(180, 0.1))
-1.
```

See also:
* [`COS`](#cos-cosine)

### `TAND`

|||
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

### `SINH` (Hyperbolic Sine)

|||
|-|-|
|TDI Syntax   | `SINH(_X)` |
|Python Syntax| `MDSplus.SINH(x)` |
|Opcode|320|

Returns the hyperbolic sine of `_X` in radians.

Use [`SIN()`](#sin-sine) to get the sine of a complex number.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

The value(s) of `_X` must be [Real](#real).

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however the units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> sinh(1.5708)
2.30131
```

See also:
* [`SIN`](#sin-sine)

### `COSH` (Hyperbolic Cosine)

|||
|-|-|
|TDI Syntax   | `COSH(_NUM)` |
|Python Syntax| `MDSplus.COSH(_NUM)` |
|Opcode|108|

Returns the hyperbolic cosine of `_X` in radians.

Use [`COS()`](#cos-cosine) to get the sine of a complex number.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

The value(s) of `_X` must be [Real](#real).

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however the units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> cosh(3.14159)
11.5919

TDI> cosh(cmplx(1.0, 2.0))
11.5919
```

See also:
* [`COS`](#cos-cosine)

### `TANH`

|||
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


### `ASIN` (Arcsine or Inverse Sine, in Radians)

|||
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

|||
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


### `ACOS` (Arccosine)

|||
|-|-|
|TDI Syntax   | `ACOS(_X)` |
|Python Syntax| `MDSplus.ACOS(x)` |
|Opcode|36|

Returns the arccosine (inverse cosine) in radians of `_X`.

Use [`ACOSD()`](#acosd-arccosine-degrees) to get the results in degrees.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

The value(s) of `_X` must be [Real](#real) and in the range of [-1, 1], values outside this range will return `$ROPRAND`.

[`BUILD_WITH_UNITS()`](#build_with_units) will be replaced with '?'.  
[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> acos(-1)
3.14159

TDI> acos([0.1, 0.2, 0.3, 0.4])
[1.47063,1.36944,1.2661,1.15928]

TDI> acos(make_signal([[0.1, 0.2], [0.3, 0.4]], *))
Build_Signal([[1.47063,1.36944], [1.2661,1.15928]], *)

TDI> acos(build_with_units(-1, 'm'))
Build_With_Units(3.14159, "?")

TDI> acos(build_with_error(-1, 0.1))
3.14159
```

See also:
* [`COS()`](#cos-cosine)
* [`ACOSD()`](#acosd-arccosine-degrees)

### `ACOSD` (Arccosine Degrees)

|||
|-|-|
|TDI Syntax   | `ACOSD(_X)` |
|Python Syntax| `MDSplus.ACOSD(x)` |
|Opcode|37|

Returns the arccosine (inverse cosine) in degrees of `_X`.

Use [`ACOS()`](#acos-arccosine) to get the results in radians.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

The value(s) of `_X` must be [Real](#real) and in the range of [-1, 1], values outside this range will return `$ROPRAND`.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however the units will be replaced with '?'.  
[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> acosd(-1)
180.

TDI> acosd([0.1, 0.2, 0.3, 0.4])
[84.2608,78.463,72.5424,66.4218]

TDI> acosd(make_signal([[0.1, 0.2], [0.3, 0.4]], *))
Build_Signal([[84.2608,78.463], [72.5424,66.4218]], *)

TDI> acosd(build_with_units(-1, 'm'))
Build_With_Units(180., "?")

TDI> acosd(build_with_error(-1, 0.1))
180.
```

See also:
* [`COS()`](#cos-cosine)
* [`ACOS()`](#acos-arccosine)

### `ATAN` (Arctangent, in Radians, for Real Numbers)

|||
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

### `atand` (Arctangent, in Degrees, for Real Numbers)

|||
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

|||
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

### `ATAN2` (Arctangent, in Radians, for Complex Numbers)

|||
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

|||
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

### `ARG` (Complex number to radians)

|||
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

|||
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



# Integer

Refers to an integer (whole) number.

Can be one of the following types. The type will be determined by the `Suffix` below, or you can use the `Function` below to explicitly cast.

|Name   |Kind|Bits|Signed|Suffix     |Function                                   |
|Int8   |6   |8   |Yes   |`B`        |[`Byte()`](#byte)                          |
|Uint8  |2   |8   |No    |`BU`       |[`Byte_Unsigned()`](#byte_unsigned)        |
|Int16  |7   |16  |Yes   |`W`        |[`Word()`](#word)                          |
|Uint16 |3   |16  |No    |`WU`       |[`Word_Unsigned()`](#word_unsigned)        |
|Int32  |8   |32  |Yes   |`L` or None|[`Long()`](#long)                          |
|Uint32 |4   |32  |No    |`LU`       |[`Long_Unsigned()`](#long_unsigned)        |
|Int64  |9   |64  |Yes   |`Q`        |[`Quadword()`](#quadword)                  |
|Uint64 |5   |64  |No    |`QU`       |[`Quadword_Unsigned()`](#quadword_unsigned)|
|Int128 |26  |128 |Yes   |`O`        |[`Octaword()`](#quadword)                  |
|Uint128|25  |128 |No    |`OU`       |[`Octaword_Unsigned()`](#quadword_unsigned)|

### `INT` (Integer Cast)

|||
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
|||
|-|-|
|TDI Syntax   | `INT_UNSIGNED(_NUM) ` |
|Python Syntax| `MDSplus.INT_UNSIGNED(_NUM) ` |
|Opcode|205|

Convert to unsigned integer.
Argument must numeric.

A is integer or real, the result is the truncated approximation to the low-order part of the integer.
A is complex, the result is the approximation to the real part. 
WARNING: truncation does not cause an error.

Examples
* `INT_UNSIGNED(2.783)` is `2LU`.

To get specific unsigned integer types see also:
* `BYTE_UNSIGNED`, `WORD_UNSIGNED`, `LONG_UNSIGNED`, `QUADWORD_UNSIGNED`, or `OCTAWORD_UNSIGNED`.

### `BYTE` (8-bit Signed Integer)

|||
|-|-|
|TDI Syntax   | `BYTE(_VALUE)` |
|Python Syntax| `MDSplus.BYTE(value)` |
|Opcode|90|

Return `_VALUE` as an 8-bit signed integer.

Values outside of the range `[-127, 127]` will be truncated.

```tdi
TDI> 42B
42B

TDI> byte(42)
42B

# Truncated
TDI> byte(1000)
-24B

TDI> byte(3.14)
3B

# Limits
TDI> [-huge(1B), huge(1B)]
Byte([-127,127])
```

See also:
* [`HUGE`](#huge)

### `BYTE_UNSIGNED` (8-bit Unsigned Integer)

|||
|-|-|
|TDI Syntax   | `BYTE_UNSIGNED(_VALUE)` |
|Python Syntax| `MDSplus.BYTE_UNSIGNED(value)` |
|Opcode|91|

Return `_VALUE` as an 8-bit signed integer.

> TODO: Add this to all integer types and add examples
`_VALUE` must be [Numeric](#), and can be a [Scalar](#), [Array](#) or [Signal](#).

Values outside of the range `[0, 255]` will be truncated.

```tdi
TDI> 42BU
42B

TDI> -1BU
-1B

TDI> byte_unsigned(42)
42BU

TDI> byte_unsigned(-1)
255BU

# Truncated
TDI> byte_unsigned(1000)
232BU

TDI> byte_unsigned(3.14)
3BU

# Limits
TDI> [0BU, huge(1BU)]
Byte_Unsigned([0,255])
```

See also:
* [`HUGE`](#huge)

### `WORD` (16-bit Signed Integer)

|||
|-|-|
|TDI Syntax   | `WORD(_VALUE)` |
|Python Syntax| `MDSplus.WORD(value)` |
|Opcode|368|

Return `_VALUE` as an 16-bit signed integer.

Values outside of the range `[-32767, 32767]` will be truncated.

```tdi
TDI> 42W
42W

TDI> word(42)
42W

# Truncated
TDI> word(100000)
-31072W

TDI> word(3.14)
3W

# Limits
TDI> [-huge(1W), huge(1W)]
Word([-32767,32767])
```

See also:
* [`HUGE`](#huge)

### `WORD_UNSIGNED` (16-bit Unsigned Integer)

|||
|-|-|
|TDI Syntax   | `WORD(_VALUE)` |
|Python Syntax| `MDSplus.WORD(value)` |
|Opcode|369|

Return `_VALUE` as an 16-bit signed integer.

Values outside of the range `[0, 255]` will be truncated.

```tdi
TDI> 42WU
42WU

TDI> -1WU
-1W

TDI> word_unsigned(42)
42WU

TDI> word_unsigned(-1)
65535WU

# Truncated
TDI> word_unsigned(100000)
34464WU

TDI> word_unsigned(3.14)
3WU

# Limits
TDI> [0WU, huge(1WU)]
Word_Unsigned([0,65535])
```

See also:
* [`HUGE`](#huge)
### `LONG` (32-bit Signed Integer)

|||
|-|-|
|TDI Syntax   | `LONG(_VALUE)` |
|Python Syntax| `MDSplus.LONG(value)` |
|Opcode|227|

Return `_VALUE` as an 32-bit signed integer.

Values outside of the range `[-2147483647, 2147483647]` will be truncated.

```tdi
TDI> 42L
42

# Long is the default integer type
TDI> 42
42

TDI> long(42)
42

# Truncated
TDI> long(10000000000Q)
1410065408

TDI> long(3.14)
3

# Limits
TDI> TDI> [-huge(1L), huge(1L)]
[-2147483647,2147483647]
```

See also:
* [`HUGE`](#huge)

### `LONG_UNSIGNED` (32-bit Unsigned Integer)

|||
|-|-|
|TDI Syntax   | `LONG_UNSIGNED(_VALUE) ` |
|Python Syntax| `MDSplus.LONG_UNSIGNED(value)` |
|Opcode|228|

### `QUADWORD` (64-bit Signed Integer)

|||
|-|-|
|TDI Syntax   | `QUADWORD(_VALUE)` |
|Python Syntax| `MDSplus.QUADWORD(value)` |
|Opcode|285|

Return `_VALUE` as an 64-bit signed integer.

Values outside of the range `[-9223372036854775807, 9223372036854775807]` will be truncated.

```tdi
TDI> 42Q
42Q

TDI> quadword(42)
42Q

# Truncated
TDI> quadword(10000000000000000000O)
-8446744073709551616Q

TDI> quadword(3.14)
3Q

# Limits
TDI> [-huge(1Q), huge(1Q)]
[-9223372036854775807Q,9223372036854775807Q]
```

See also:
* [`HUGE`](#huge)

### `QUADWORD_UNSIGNED` (64-bit Unsigned Integer)

|||
|-|-|
|TDI Syntax   | `QUADWORD_UNSIGNED(_VALUE)` |
|Python Syntax| `MDSplus.QUADWORD_UNSIGNED(value)` |
|Opcode|286|

### `OCTAWORD` (128-bit Signed Integer)

|||
|-|-|
|TDI Syntax   | `OCTAWORD(_VALUE)` |
|Python Syntax| `MDSplus.OCTAWORD(value)` |
|Opcode|260|

Return `_VALUE` as an 128-bit signed integer.

Values outside of the range `[-170141183460469231731687303715884105727O, 170141183460469231731687303715884105727O]` will be truncated.

```tdi
# Note: The suffix is an O, not a zero
TDI> -1O
-1O

TDI> 9999999999999999999O
9999999999999999999O

TDI> octaword(42)
42O

# Truncated
TDI> octaword(3.14)
3O

# Limits
TDI> [-huge(1O), huge(1O)]
[-170141183460469231731687303715884105727O,170141183460469231731687303715884105727O]
```

See also:
* [`HUGE`](#huge)

### `OCTAWORD_UNSIGNED` (128-bit Unsigned Integer)
|||
|-|-|
|TDI Syntax   | `OCTAWORD_UNSIGNED(_NUM)` |
|Python Syntax| `MDSplus.OCTAWORD_UNSIGNED(_NUM)` |
|Opcode|261|

```tdi
TDI> octaword_unsigned(123)
123OU
TDI> octaword_unsigned(65537.4)
65537OU
TDI> octaword_unsigned(-1)
340282366920938463463374607431768211455OU
```


### `SIGNED`
|||
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

### `UNSIGNED`
|||
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

# Floating Point

Refers to a floating point (fractional) number.

> TODO: Possibly reword
Note: Floating point comparisons and arithmetic may not match expectations due to floating point approximation.

Can be one of the following types. The type will be determined by the `Suffix` below, or you can use the `Function` below to explicitly cast.

|Name           |Kind|Bits|Suffix      |Function                 |
|IEEE-754 Float |52  |32  |`E0` or None|`FS_FLOAT()` or `FLOAT()`|
|IEEE-754 Double|53  |64  |`D0`        |`FT_FLOAT()`             |

Floating point numbers can also be expressed in scientific notation:

```tdi
# Float, same as 3.2 x 10^5
TDI> 3.2E5
320000.

# Double, same as 3.2 x 10^5
TDI> 3.2D5
320000D0
```

The following types are deprecated, and should not be used, but might already be stored as data in trees. When used, they will naturally convert to the modern floating point types above.

|Name          |Kind|Bits|Suffix|Function   |
|VMS F-Floating|10  |32  |`F0`  |`F_FLOAT()`|
|VMS D-Floating|11  |64  |`V0`  |`D_FLOAT()`|
|VMS G-Floating|27  |64  |`G0`  |`G_FLOAT()`|
|VMS H-Floating|28  |128 |`H0`  |`H_FLOAT()`|

## `FLOAT` (32-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `FLOAT(_VALUE, [_KIND])` |
|Python Syntax| `MDSplus.FLOAT(value, [kind])` |
|Opcode|167|

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

### `DBLE` (64-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `DBLE(_VALUE)` |
|Python Syntax| `MDSplus.DBLE(_VALUE)` |
|Opcode|115|

Double the precision of a number.
* Argument must be numeric and must not be octaword or H floating because they are already maximum precision.
* Returns twice the precision of the argument:
Byte becomes word, word becomes long, long becomes quadword, quadword becomes octaword, F floating becomes D, D or G floating becomes H. 

Actually these are all deprecated. These all become double now.

* Unsigned, signed, real, and complex types remain so.
* Warning: F90 always converts to a double-precision real `D_FLOAT`.

Examples.
* `DBLE(3)` is 3Q.
* `DBLE(3.0)` is 3D0.

### `FS_FLOAT` (IEEE-754 32-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `FS_FLOAT(_VALUE)` |
|Python Syntax| `MDSplus.FS_FLOAT(value)` |
|Opcode|450|

Convert to IEEE single precision floating real (32-bit)
* Arguments must be numeric.
* Integers, reals and the real part of complex numbers are converted to F-precision reals. Immediate at compilation.
* Warning: truncation does not cause an error.

Example:
* `fs_float(12)`, `fs_float(12.)`, and `fs_float(12D0)` return `12.0`.

### `FT_FLOAT` (IEEE-754 64-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `FT_FLOAT(_NUM)` |
|Python Syntax| `MDSplus.ft_float(_NUM)` |
|Opcode|452|

Convert to IEEE double precision floating real (64-bit)
* Arguments must be numeric.
* Integers, reals and the real part of complex numbers are converted to double precision reals. Immediate at compilation.
* Warning, truncation does not cause an error.

Examples
* `FT_FLOAT(12)`, `FT_FLOAT(12.)`, and `FT_FLOAT(12D0)` return `12.0`.

### `F_FLOAT`(VMS F-Precision 32-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `F_FLOAT(_VALUE) ` |
|Opcode|173|

Deprecated, use [`FS_FLOAT`](#fs_float-ieee-754-32-bit-floating-point-number) instead.

### `D_FLOAT`(VMS D-Precision 64-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `D_FLOAT(_VALUE)` |
|Opcode|140|

Deprecated, use [`FT_FLOAT`](#ft_float-ieee-754-64-bit-floating-point-number) instead.

### `G_FLOAT`(VMS G-Precision 64-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `G_FLOAT(_VALUE)` |
|Opcode|179|

Deprecated, use [`FT_FLOAT`](#ft_float-ieee-754-64-bit-floating-point-number) instead.

### `H_FLOAT` (VMS H-Precision 64-bit Floating Point Number)

|||
|-|-|
|TDI Syntax   | `H_FLOAT(_VALUE)` |
|Opcode|183|

Deprecated, use [`FT_FLOAT`](#ft_float-ieee-754-64-bit-floating-point-number) instead.

### `FINITE` (Opcode 410)

|||
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

# Complex Number

Refers to a complex floating point number, containing both real and imaginary parts.

Use [`REAL()`](#real) to access the real part, and [`AIMAG()`](#aimag-imaginary-part-of-a-complex-number) to access the imaginary part.

See [`CMPLX()`](#cmplx-complex-number) and [`$I`](#i-imaginary) for more information.

```tdi
TDI> cmplx(3.0, 4.0)
Cmplx(3.,4.)

TDI> ($I * 4.0) + 3.0
Cmplx(3.,4.)
```

Can be one of the following types. The type will be determined by the component types, or you can use the `Function` below to explicitly cast.

|Name                   |Kind|Bits|Function|
|IEEE-754 Complex Float |54  |64  |`FS_COMPLEX()`|
|IEEE-754 Complex Double|55  |128 |`FT_COMPLEX()`|

The following types are deprecated, and should not be used, but might already be stored as data in trees. When used, they will naturally convert to the modern floating point types above.

|Name                  |Kind|Bits|Function   |
|VMS Complex F-Floating|12  |64  |`F_COMPLEX()`|
|VMS Complex D-Floating|13  |128 |`D_COMPLEX()`|
|VMS Complex G-Floating|29  |128 |`G_COMPLEX()`|
|VMS Complex H-Floating|30  |256 |`H_COMPLEX()` TODO: Segfault|

### `CMPLX` (Complex Number)

|||
|-|-|
|TDI Syntax   | `CMPLX(_REAL, _IMAG, [_KIND])` |
|Python Syntax| `MDSplus.CMPLX(real, imag, [kind])` |
|Opcode|97|

Creates a complex number.
* First argument is the real part. 
* Second argument is the imaginary part. If function is called with only one argument, it is assumed that the second number will be zero. 
* (Optional) third argument is the Kind. TODO: Come back to this. If KIND is absent, it is ignored; otherwise, CMPLX(X,Y,KIND) has real part REAL(X,KIND) and imaginary part REAL(Y,KIND).
* Immediate at compilation.
* WARNING: truncation does not cause an error.

Examples:
TDI> cmplx(-3)` is `cmplx(-3.0,0.0)`. 
TDI> cmplx(3,4,5d6)` is `cmplx(3d0,4d0)`.

> TODO: When creating one with two different types, it breaks
> TDI> cmplx(3.0, 4D0)
> Cmplx(5325.712092559326D-318,0D0)

### `REAL` (Real Part of Complex Number)

|||
|-|-|
|TDI Syntax   | `REAL(_COMPLEX)` |
|Python Syntax| `MDSplus.REAL(complex)` |
|Opcode|296|

Returns the real part of `_COMPLEX`.

To get the imaginary part, use [`AIMAG`](#aimag-imaginary-part-of-complex-number).

`_COMPLEX` must be [Numeric](#numeric), and should be a [Complex Number](#complex-number). If `_COMPLEX` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

> TODO: Mark, help reword, "if complex is not complex"
If `_COMPLEX` is a [Real Number](#real-number), it will be converted [Floating Point](#floating-point) and returned.

Note: Passing a second argument to this will cause a segmentation fault.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> real($I)
0.

TDI> real(cmplx(3, 4))
3.

TDI> real([cmplx(1, 2), cmplx(3, 4), cmplx(5, 6)])
[1.,3.,5.]

TDI> real([[cmplx(1, 2), cmplx(3, 4)], [cmplx(5, 6), cmplx(7, 8)]])
[[1.,3.], [5.,7.]]
```

See also:
* [`AIMAG`](#aimag-imaginary-part-of-complex-number)
* [`CMPLX`](#cmplx-complex-number)

### `AIMAG` (Imaginary Part of Complex Number)

|||
|-|-|
|TDI Syntax   | `AIMAG(_COMPLEX)` |
|Python Syntax| `MDSplus.AIMAG(complex)` |
|Opcode|41|

Returns the imaginary part of a `_COMPLEX`.

To get the real part, use [`REAL`](#real-real-part-of-complex-number).

`_COMPLEX` must be [Numeric](#numeric), and should be a [Complex Number](#complex-number). If `_COMPLEX` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

> TODO: Mark, help reword, "if complex is not complex"
If `_COMPLEX` is a [Real Number](#real-number), the result will be 0.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> aimag($I)
1.

TDI> aimag(cmplx(3, 4))
4.

TDI> aimag([cmplx(1, 2), cmplx(3, 4), cmplx(5, 6)])
[2.,4.,6.]

TDI> aimag([[cmplx(1, 2), cmplx(3, 4)], [cmplx(5, 6), cmplx(7, 8)]])
[[2.,4.], [6.,8.]]
```

See also:
* [`REAL`](#real-real-part-of-complex-number)
* [`CMPLX`](#cmplx-complex-number)

### `FS_COMPLEX` (Complex Number FS_FLOAT)

|||
|-|-|
|TDI Syntax   | `FS_COMPLEX(_REAL, _IMAG)` |
|Opcode|451|

See [`CMPLX`](#cmplx-complex-number).

Equivalent to calling `CMPLX(_REAL, _IMAG, KIND(FS_FLOAT(0)))`.

### `FT_COMPLEX` (Complex Number FT_FLOAT)

|||
|-|-|
|TDI Syntax   | `FT_COMPLEX(_REAL, _IMAG)` |
|Opcode|453|

See [`CMPLX`](#cmplx-complex-number).

Equivalent to calling `CMPLX(_REAL, _IMAG, KIND(FT_FLOAT(0)))`.

### `F_COMPLEX` (Complex Number F_FLOAT)

|||
|-|-|
|TDI Syntax   | `F_COMPLEX(_REAL, _IMAG) ` |
|Opcode|172|

See [`CMPLX`](#cmplx-complex-number).

Deprecated, use [`FS_COMPLEX`](#fs_complex-complex-number-fs_float).

Equivalent to calling `CMPLX(_REAL, _IMAG, KIND(F_FLOAT(0)))`.

### `D_COMPLEX` (Complex Number D_FLOAT)

|||
|-|-|
|TDI Syntax   | `d_complex(_REALPART, [_IMAGINARYPART])` |
|Opcode|139|

See [`CMPLX`](#cmplx-complex-number).

Deprecated, use [`FT_COMPLEX`](#ft_complex).

Equivalent to calling `CMPLX(_REAL, _IMAG, KIND(D_FLOAT(0)))`.

### `G_COMPLEX` (Complex Number G_FLOAT)

|||
|-|-|
|TDI Syntax   | `G_COMPLEX(_REAL, _IMAG)` |
|Opcode|178|

See [`CMPLX`](#cmplx-complex-number).

Deprecated, use [`FT_COMPLEX`](#ft_complex).

Equivalent to calling `CMPLX(_REAL, _IMAG, KIND(G_FLOAT(0)))`.

### `H_COMPLEX` (Complex Number H_FLOAT)

|||
|-|-|
|TDI Syntax   | `H_COMPLEX(_REAL, _IMAG) ` |
|Opcode|182|

See [`CMPLX`](#cmplx-complex-number).

Deprecated, use [`FT_COMPLEX`](#ft_complex).

Equivalent to calling `CMPLX(_REAL, _IMAG, KIND(H_FLOAT(0)))`.

### `CONJG` 
|||
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
