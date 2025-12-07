
# Character

Refers to a single ASCII character (letter, symbol, etc.) or string of ASCII characters (text).

This can also refer to an [Array](#array) of characters or strings, unless otherwise specified.

### `TEXT` (To String)

|||
|-|-|
|TDI Syntax   | `TEXT(_X, [_LENGTH])` |
|Python Syntax| `MDSplus.TEXT(x, [length])` |
|Opcode|344|

Converts and returns `_X` as a [Character](#character) string.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

```tdi
TDI> text([1,2,3],1)
["1","2","3"]
```

Conversion Elemental.
Convert to text of given length.
Arguments Optional: LENGTH. X numeric or character. LENGTH integer scalar.
|Signals      |Same as X. |Units        |Same as X. |Form         |Character of given length or length associated with the
type of X. These are used B/BU 4, W/WU 8, L/LU 12, Q/QU 20, O/OU 36, F 16, D/G 24, H 40, FC 32, DC/GC 48, and HC 80.
|Result       |A character string that represent the number. (As of now, quadword and octaword are converted to hex.)>>>>>>>>>WARNING, truncation does not cause an error.
|Examples     |TEXT(1.2) is " 0.1200000E+02".

# Conversions

### `ACHAR` (ASCII Character from Integer)

|||
|-|-|
|TDI Syntax   | `ACHAR(_X, [_KIND])` |
|Python Syntax| `MDSplus.ACHAR(x, [kind])` |
|Opcode|35|

Returns the equivalent ASCII character(s) of `_X`.

`_X` must be [Numeric](#numeric). If `_X` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

Optional `_KIND`, see [`Kind`](#kind).

Note: This is equivalent to [`CHAR()`](#char-character-from-integer).

```tdi
TDI> achar(42)
*

TDI> achar([87, 111, 114, 108, 100, 33])
["W","o","r","l","d","!"]

TDI> achar(97 .. 103)
["a","b","c","d","e","f","g"]
```

See also:
* [`IACHAR()`](#iachar-integer-from-ascii-character)

### `IACHAR` (Integer from ASCII Character)

|||
|-|-|
|TDI Syntax   | `IACHAR(_C)` |
|Python Syntax| `MDSplus.IACHAR(c)` |
|Opcode|184|

Returns the equivalent ASCII integer value(s) of `C`.

`_C` must contain character value(s), and can be a scalar, array, or `Signal`. If `_C` is an array or `Signal`, the shape will be preserved.

Note: This is equivalent to [`ICHAR()`](#ichar-integer-from-character).

```tdi
TDI> iachar('*')
42BU

TDI> iachar(["H", "e", "l", "l", "o"])
Byte_Unsigned([72,101,108,108,111])

TDI> iachar(["a","b","c","d","e","f","g"])
Byte_Unsigned([97,98,99,100,101,102,103])
```

See also:
* [`ACHAR()`](#achar-ascii-character-from-integer)

### `CHAR` (Character from Integer)

|||
|-|-|
|TDI Syntax   | `CHAR(_X, [_KIND])` |
|Python Syntax| `MDSplus.CHAR(x, [kind])` |
|Opcode|94|

See [`ACHAR()`](#achar-ascii-character-from-integer).

### `ICHAR` (Integer from Character)

|||
|-|-|
|TDI Syntax   | `ICHAR(_C)` |
|Python Syntax| `MDSplus.ICHAR(c)` |
|Opcode|187|

See [`IACHAR()`](#iachar-integer-from-ascii-character)

# Formatting

### `TRIM` (Remove Trailing Whitespace)

|||
|-|-|
|TDI Syntax   | `TRIM(_STRING)` |
|Python Syntax| `MDSplus.TRIM(string)` |
|Opcode|349|

Return `_STRING` with the trailing whitespace removed.

To remove both leading and trailing whitespace, use [`ADJUSTL`](#adjustl-adjust-to-the-left-left-align-text) and `TRIM` together.

`_STRING` doesn't need to be [Character](#character), but any other types will be converted using [`TEXT`](#text-to-string). If `_STRING` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

Note: This does not remove newlines (`\n`) or carriage returns (`\r`).

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> trim("  word  ")
"  word"

TDI> trim("\tword\t")
"\tword"

TDI> trim("line\n")
"line\n"

# Remove leading and trailing spaces
TDI> trim(adjustl("  hello  "))
"hello"
```

See also:
* [`ADJUSTL`](#adjustl-adjust-to-the-left-left-align-text)
* [`ADJUSTR`](#adjustr-adjust-to-the-right-right-align-text)
* [`TRIM`](#trim-remove-trailing-whitespace)

### `ADJUSTL` (Adjust to the Left, Left-Align Text)

|||
|-|-|
|TDI Syntax   | `ADJUSTL(_STRING)` |
|Python Syntax| `MDSplus.ADJUSTL(string)` |
|Opcode|39|

Return `_STRING` adjusted/aligned to the left. This is done by removing any leading whitespace, and inserting the same number of trailing spaces instead.

To adjust to the right, use [`ADJUSTR`](#adjustr-adjust-to-the-right-right-align-text).

`_STRING` doesn't need to be [Character](#character), but any other types will be converted using [`TEXT`](#text-to-string). If `_STRING` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

Note: Consumed tab (`\t`) characters will be replaced by single spaces.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> adjustl("  word  ")
"word    "

TDI> adjustl(42)
"42         "

TDI> adjustl(["  hello  ", "  world  ","test"])
["hello    ","world    ","test     "]

# The leading '\t' is replaced by a trailing ' '
TDI> adjustl("\tword\t")
"word\t "
```

See also:
* [`ADJUSTR`](#adjustr-adjust-to-the-right-right-align-text)
* [`TRIM`](#trim-remove-trailing-whitespace)

### `ADJUSTR` (Adjust to the Right, Right-Align Text)

|||
|-|-|
|TDI Syntax   | `ADJUSTR(_STRING)` |
|Python Syntax| `MDSplus.ADJUSTR(string)` |
|Opcode|40|

Return `_STRING` adjusted/aligned to the right. This is done by removing any trailing whitespace, and inserting the same number of leading spaces instead.

To adjust to the left, use [`ADJUSTL`](#adjustl-adjust-to-the-left-left-align-text).

`_STRING` doesn't need to be [Character](#character), but any other types will be converted using [`TEXT`](#text-to-string). If `_STRING` is an [Array](#array) or [Signal](#signal), the shape will be preserved.

Note: Consumed tab (`\t`) characters will be replaced by single spaces.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```tdi
TDI> adjustr("  word  ")
"    word"

# The same as TEXT(42)
TDI> adjustr(42)
"         42"

TDI> adjustr(["  hello  ", "  world  ","test"])
["    hello","    world","     test"]

# The trailing '\t' is replaced by a leading ' '
TDI> adjustr("\tword\t")
" \tword"
```

See also:
* [`ADJUSTL`](#adjustl-adjust-to-the-left-left-align-text)
* [`TRIM`](#trim-remove-trailing-whitespace)


### `UPCASE` (Uppercase)

|||
|-|-|
|TDI Syntax   | `UPCASE(_TEXT)` |
|Python Syntax| `MDSplus.UPCASE(text)` |
|Opcode|383|

Uppercase.


### `LCASE` (Lowercase)

|||
|-|-|
|TDI Syntax| `LCASE(_TEXT)`  |
|Filepath  | [`tdi/lcase.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/lcase.fun) |

Lowercase.

### `concat`
|||
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

### `element` (Opcode 374)

|||
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

### `extract` (Opcode 409)

|||
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

### `REPEAT`
|||
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


### `index` (Opcode 195)

|||
|-|-|
|TDI Syntax   | `index(_STRING,_SUBSTRING,[_BACK]) ` |
|Python Syntax| `MDSplus.index(_STRING,_SUBSTRING,[_BACK]) ` |
|Min arguments| 2 |
|Max arguments| 3 |

The starting position of a substring within a string. Note the result is 1 less than for F90.

TODO: test for arrays

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

### `LEN` (Byte Size, String Length)

|||
|-|-|
|TDI Syntax   | `LEN(_X) ` |
|Python Syntax| `MDSplus.LEN(x) ` |
|Opcode|217|

Returns one of the following:
* The size of `_X` in bytes, if it is a [Scalar](#scalar).
* The size of an element of `_X` in bytes, if it is an [Array](#array) or [Signal](#signal).
* The number of [Characters](#character) in `_X`, if it is a string.

To get the number of elements in an [Array](#array), use [`SIZE()`](#size-number-of-elements).

To get the size in bits, use [`BIT_SIZE()`](#bit_size-bit-size-number-of-bits).

```tdi
TDI> len(1BU)
1

TDI> len(1)
4

TDI> len(1Q)
8

TDI> len([1.0, 2.0])
4

TDI> len(Quadword([1, 2, 3]))
8

TDI> len('hello world')
11
```

See also:
* [`BIT_SIZE()`](#bit_size-bit-size-number-of-bits)


### `len_trim` (Opcode 218)

|||
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

### `SCAN`
|||
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

### `TRANSLATE`
|||
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

### `VERIFY`
|||
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

# Comparison Operators

### `lge` (Opcode 219)

|||
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

|||
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

|||
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

|||
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
