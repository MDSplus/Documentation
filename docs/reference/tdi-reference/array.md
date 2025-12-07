
# Arrays

Refers to an array of values, which can be [Integer](#integer), [Floating Point](#floating-point), or [Complex Number](#complex-number), unless otherwise specified.

Note: In most cases, a [Signal](#signal) can be used in place of an array.

TODO: explain `_dim` and `_mask` since these often appear together with functions that deal with arrays

`_DIM`: dimensions of sub array(s).
* If (null): flat array--sub-dimension boundaries are ignored
* If _DIM = 0, each sub-array is its own thing
* If _DIM = 1, takes the first element of each sub-array
* If _DIM = 2, takes the 

```tdi

# here is dimension null
TDI> [[[1,2],[3,4]],[[5,6],[7,8]]][,,]
[[[1,2], [3,4]], [[5,6], [7,8]]]

/* or: [[[1,2], [3,4]],
        [[5,6], [7,8]]]
*/

# here is dimension 0
TDI> [[[1,2],[3,4]],[[5,6],[7,8]]][0,,]
[[[1], [3]], [[5], [7]]]

# here is dimension 1
TDI> [[[1,2],[3,4]],[[5,6],[7,8]]][,0,]
[[[1,2]], [[5,6]]]

# Here is dimension 2
TDI> [[[1,2],[3,4]],[[5,6],[7,8]]][,,0]
[[1,2], [3,4]]
```




`_MASK`: essentially true/false, but other parameters possible

Also you can request row/column of sub-arrays like this:

```tdi
TDI> [[11,2],[3,4]][0,0]
11
TDI> [[11,2],[3,4]][0,1]
3
TDI> [[11,2],[3,4]][1,0]
2
```

```tdi
TDI> [[11,2],[3,4]][0][0]
[[11], [3]]
```

```tdi
TDI> [[11,2],[3,4]][,0]
[11,2]
TDI> [[11,2],[3,4]][,1]
[3,4]


[[11,2],[3,4]][0]
[[11], [3]]

[[11], [3]][,0]
[11]
```

## Constructors

### `ARRAY` 

|||
|-|-|
|TDI Syntax   | `ARRAY([_SHAPE], [_KIND])` |
|Python Syntax| `MDSplus.ARRAY([_SHAPE], [_KIND])` |
|Opcode|52|

Generates an unitialized array. The values are not defined and will depend on previous memory usage.
* The `_SHAPE` argument goes from innermost to outermost. Can make up to an 8th dimensional array.
* If `_SHAPE` is absent, the result is a scalar. 
* If `_TYPE` is absent, the result will be floats.


Examples

```TDI
TDI> array([2])
[0.,0.]
TDI> array([2, 2])
[[0.,0.], [0.,0.]]
TDI> array([2, 2, 2])
[[[0.,0.], [0.,0.]], [[0.,0.], [0.,0.]]]


TDI> array([1])
[0.]
TDI> array([1,2])
[[0.], [0.]]
TDI> array([1,2,3])
[[[0.], [0.]], [[0.], [0.]], [[0.], [0.]]]



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



### `RAMP`
|||
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
|||
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

### `diagonal` (Opcode 124)

|||
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

### `SET_RANGE`
|||
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

### `VECTOR`
|||
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

### `ZERO`
|||
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

## Accessors

### `SUBSCRIPT`
|||
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


|Return Type  |F90 Transformation |
Sum of all the elements of ARRAY along dimension DIM corresponding to the true elements of MASK.
Arguments Optional: DIM, MASK. ARRAY numeric array. DIM integer scalar from 0 to n-1, where n is rank of ARRAY. MASK logical and conformable to ARRAY.
|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. |Units        |Same as ARRAY. |Form         |Same type as ARRAY. It is a scalar if DIM is absent or
ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.
|Result       |The result without DIM is the sum of the elements of ARRAY, using only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the sum of the ARRAY elements with dimension DIM fixed as the element number of the result. If no value is found, 1 is given.
Examples. SUM([1,2,3]) is 6. SUM(_C,,_C GT 0) finds the sum of all positive element of C.
If _B=[[1, 3, 5],[2, 4, 6]] SUM(_B,0) is [9,12] and SUM(_B,1) is [3,7,11].

### `LBOUND` (Opcode 130)

|||
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

### `elbound` (Opcode 143)

|||
|-|-|
|TDI Syntax   | `elbound(_ARRAY, [_DIM])` |
|Python Syntax| `MDSplus.elbound(_ARRAY, [_DIM])` |
|Min arguments| 1 |
|Max arguments| 2 |

Same as `LBOUND`. [link]

See also:
* UBOUND for upper bound, SHAPE for number of elements, SIZE for total elements, and E... for signals.
* LBOUND (alternate spelling, same function)


### `UBOUND`
|||
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


### `eubound` (Opcode 157)

|||
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



### `SHAPE`
|||
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
Examples.
SHAPE(_A[2:5,-1:1]) is [4,3]. SHAPE(3) is [], a zero-length vector.
See also LBOUND for lower bound, UBOUND for upper bound, SIZE for total elements, and E... for signals.

```TDI
# Better example
TDI> shape(array([1,2,3]))
[1,2,3]

#so basically:
# [number_of_elements_in_each_subarray, number_of_columns, number_of_rows]
```


### `eshape` (Opcode 155)

|||
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

### `SIZE` (Number of Elements)

To get the length of a string, use [`LEN()`](#len-byte-size-string-length).

|||
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


### `esize` (Opcode 156)

|||
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

### `RANK`

|||
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

## Modifiers

### `conditional`
|||
|-|-|
|TDI Syntax   | `conditional(_TSOURCE, _FSOURCE, _MASK)` |
|Python Syntax| `MDSplus.conditional(_TSOURCE, _FSOURCE, _MASK)` |
|Min arguments| 3 |
|Max arguments| 3 |
|Opcode|102|

TODO: investigate further--is this broken?
`conditional (3>4, $true, $false)` seems to always return `$true` no matter what
Works fine for me
```tdi
TDI> conditional([1,2,3], [4,5,6], [0,1,0])
[4,2,6]
```

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

### `CULL` (Opcode 390)

|||
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

### `dim` (Opcode 126)

|||
|-|-|
|TDI Syntax   | `DIM(_NUM0, _NUM1)` |
|Python Syntax| `MDSplus.DIM(_NUM0, _NUM1)` |
|Min arguments| 2| 
|Max arguments| 2| 
|Native python|False|

Not to be confused with `dim_of`.

Returns difference of `X-Y` if `X>Y` and zero otherwise.
Both arguments must be integer or real.
Complex numbers result in error.

Examples
* `dim(3.0,2.0)`  returns `1.`
* `dim(3.0,-2.0)` returns `5.`
* `dim(-3.0,2.0)` returns `0.`


### `ACCUMULATE` (Running Sum)

|||
|-|-|
|TDI Syntax   | `ACCUMULATE(_ARRAY, [_DIM], [_MASK])` |
|Python Syntax| `MDSplus.ACCUMULATE(array, [dim], [mask])` |
|Opcode|439|

Returns a running sum of each element of `_ARRAY`, meaning each element will become the sum of itself and all previous elements.

To get the total sum of an array, use [`SUM()`](#sum-total-sum) instead.

`_ARRAY` must be [Numeric](#numeric) and should be an [Array](#array) or a [Signal](#signal). The result will be the same type as `_ARRAY`.

If `_DIM` is specified, then the elements of that dimension will be summed; otherwise the array will be treated as a flat array. If specified, `_DIM` must be an positive integer and must be within the range of [0, `DIM_OF(_ARRAY)`].

If `_MASK` is specified, only the elements where `_MASK` is true will be summed. If specified, `_MASK` must be a logical array with the same length as `_ARRAY`.

Any `$ROPRAND` values of `_ARRAY` will not be included in the sum.

If no values are found in `_ARRAY`, the result will be 0.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```TDI
TDI> accumulate([1, 2, 3])
[1,3,6]


TDI> _array = [1, -2, -3, 4, 5]
[1,-2,-3,4,5]

TDI> _mask = _array > 0
Byte_Unsigned([1,0,0,1,1])

TDI> accumulate(_array, *, _mask)
[1,-2,-3,5,10]


TDI> _array = [[[1,2], [3,4]], [[5,6], [6,7]]]
[[[1,2], [3,4]], [[5,6], [6,7]]]

# 1 + 2 = 3
# 3 + 3 = 6
# 6 + 4 = 10
# ...
TDI> accumulate(_array)
[[[1,3], [6,10]], [[15,21], [27,34]]]

# 1 + 2 = 3
# 3 + 4 = 7
# 5 + 6 = 11
# 6 + 7 = 13
TDI> accumulate(_array, 0)
[[[1,3], [3,7]], [[5,11], [6,13]]]

# [1,2] + [3,4] = [4,6]
# [5,6] + [7,8] = [11,13]
TDI> accumulate(_array, 1)
[[[1,2], [4,6]], [[5,6], [11,13]]]

# [[1,2], [3,4]] + [[5,6], [6,7]] = [[6,8], [9,11]]
TDI> accumulate(_array, 2)
[[[1,2], [3,4]], [[6,8], [9,11]]]
```

See also:
* [`SUM()`](#sum-total-sum)

### `SUM` (Total Sum)

|||
|-|-|
|TDI Syntax   | `SUM(_ARRAY, [_DIM], [_MASK])` |
|Python Syntax| `MDSplus.SUM(array, [dim], [mask])` |
|Opcode|337|

Returns a total sum of the elements in `_ARRAY`.

To get a running sum of an array, use [`ACCUMULATE()`](#accumulate-running-sum) instead.

`_ARRAY` must be [Numeric](#numeric) and should be an [Array](#array) or a [Signal](#signal). The result will be the same type as `_ARRAY`.

If `_DIM` is specified, then the elements of that dimension will be summed; otherwise the array will be treated as a flat array. If specified, `_DIM` must be an positive integer and must be within the range of [0, `DIM_OF(_ARRAY)`].

If `_MASK` is specified, only the elements where `_MASK` is true will be summed. If specified, `_MASK` must be a logical array with the same length as `_ARRAY`.

Any `$ROPRAND` values of `_ARRAY` will not be included in the sum.

If no values are found in `_ARRAY`, the result will be 0.

[`BUILD_WITH_UNITS()`](#build_with_units) will be preserved, however mismatched units will be replaced with '?'.

[`BUILD_WITH_ERROR()`](#build_with_error) will be discarded.

```TDI
TDI> sum([1, 2, 3])
6


TDI> _array = [1, -2, -3, 4, 5]
[1,-2,-3,4,5]

TDI> _mask = _array > 0
Byte_Unsigned([1,0,0,1,1])

TDI> sum(_array, *, _mask)
10


TDI> _array = [[[1,2], [3,4]], [[5,6], [6,7]]]
[[[1,2], [3,4]], [[5,6], [6,7]]]

# 1 + 2 = 3
# 3 + 3 = 6
# 6 + 4 = 10
# ...
TDI> sum(_array)
34

# 1 + 2 = 3
# 3 + 4 = 7
# 5 + 6 = 11
# 6 + 7 = 13
TDI> sum(_array, 0)
[[3,7], [11,13]]

# [1,2] + [3,4] = [4,6]
# [5,6] + [7,8] = [11,13]
# TODO: Broken, see Issue #2989
TDI> sum(_array, 1)
[[4,6], [4,6]]

# [[1,2], [3,4]] + [[5,6], [6,7]] = [[6,8], [9,11]]
TDI> sum(_array, 2)
[[6,8], [9,11]]
```

See also:
* [`ACCUMULATE()`](#accumulate-running-sum)




### `PRODUCT` (Total Product)
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 280
|Min arguments| 1
|Max arguments| 3
******Compiler syntax: PRODUCT(arg0,arg1,arg2)
|Native python|False|

> TODO: Broken, see Issue #2989

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

### `decompress` (Opcode 120)

|||
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

### `DOT_PRODUCT` (Opcode 132)

|||
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


### `extend` (Opcode 391)

|||
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


### `fix_roprand` (Opcode 166)

|||
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


### `firstloc` (Opcode 164)

|||
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

### `LASTLOC` (Opcode 215)

|||
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


### `i_to_x` (Opcode 392)

|||
|-|-|
|TDI Syntax   | `i_to_x(_DIMENSION, [_I])` |
|Python Syntax| `MDSplus.i_to_x(_DIMENSION, [_I])` |
|Min arguments| 1 |
|Max arguments| 2 |


Converts index into axis values.

Arguments:
* `_DIMENSION` a dimension with optional window and required axis. If DIMENSION is missing, the unchanged I is returned.
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


### `X_TO_I`
|||
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

### `MAP`
|||
|-|-|
|TDI Syntax   | `MAP(_ARRAY, _OFFSET)` |
|Python Syntax| `MDSplus.MAP(_ARRAY, _OFFSET)` |
|Min arguments| 2 |
|Max arguments| 2 |
|Opcode|394|

Element selection from an array. Basically, it lets you grab sub-samples from an array or sort it out. See examples

Arguments
* `_ARRAY` (A) an array of any type considered to be a vector.
* `_OFFSET` (B) a list of offsets into the `_ARRAY`.  
    * Values in the offset should be in the range of `0` to `size(_ARRAY)-1`.  
    * Out-of-bounds values pull from the closest limit.
* Note: multidimensional arrays referenced by bad offsets will likely be junk.

Examples

```tdi
TDI> map([1,2,3,4,5,6,7,8,9,10], [3, 2, 1, -1, 20, 5])
[4,3,2,1,10,6]
# 1, 2, 3, and 5 pull from the array at the offset
# since 20 is out of bounds above the last offset it pulls the last element in the array
# since -1 is out of bounds below the first offset it pulls the first element in the array
 
_A=5:1:-1

TDI> map(_A,sort(_A))
[1,2,3,4,5]
# note that this is the same as sortval(_A).

TDI> map(build_with_units([1, 2, 3, 4, 5, 6, 7, 8], 'm'), make_signal([[1, 2, 3], [3, 4, 5]], *))
Build_Signal(Build_With_Units([[2,3,4], [4,5,6]], "m"), *)
```

See also:

* `CULL` to remove bad B values. 
* `SUBSCRIPT` for dimensional indexing into signal and multiple index access to arrays.



### `MERGE`
|||
|-|-|
|TDI Syntax   | `MERGE(_TSOURCE, _FSOURCE, _MASK) ` |
|Python Syntax| `MDSplus.MERGE(_TSOURCE, _FSOURCE, _MASK) ` |
|Opcode|239|


Choose alternative value according to a mask. If the mask is true, it'll take from array 1, if false it'll take from array 2.

Arguments
* `_TSOURCE` any type compatible with FSOURCE.
* `_FSOURCE` any type compatible with TSOURCE.
* `_MASK` logical, conformable with TSOURCE and FSOURCE.

|Signals      |Single signal or smaller data. 
|Units        |Single or common units (excluding MASK), else bad. 
|Form         |The type is the compatible type of FSOURCE and TSOURCE.
The shape conformable to FSOURCE, TSOURCE, and MASK.
|Result       |If the MASK value is true, the TSOURCE value is use; otherwise, the FSOURCE value is use.

Examples
MERGE([1,2,3],[4,5,6],[$TRUE,$FALSE,$TRUE])
[1,5,3].


```tdi
# Manual example showing how it works
TDI> _array0 = [1,2,3,4]
[1,2,3,4]
TDI> _array1 = [5,6,7,8]
[5,6,7,8]
TDI> merge(_array0, _array1, [1,0,1,0])
[1,6,3,8]

# more applicable example
TDI> _array0 = [1,6,3,8]
[1,6,3,8]
TDI> _array1 = [5,2,7,4]
[5,2,7,4]
TDI> merge(_array0, _array1, _array0 > _array1)
[5,6,7,8]
```

See also: 
CONDITIONAL with form: `MASK ? TSOURCE : FSOURCE`, for scalar mask test.



### `UNION`
|||
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

### `PACK`
|||
|-|-|
|TDI Syntax   | `PACK(_ARRAY, _MASK, [_VECTOR])` |
|Python Syntax| `MDSplus.PACK(_ARRAY, _MASK, [_VECTOR])` |
|Opcode|270|

Pack an array into a vector under control of a mask.
* The elements as selected by `_MASK` from `_ARRAY`. The remaining elements are filled from `_VECTOR`.

Arguments 
* `_ARRAY` any type.
* `_MASK` [logical](#logical) conformable to `_ARRAY`.
* `_VECTOR` Optional: ARRAY's type, length at least equal to last true element of MASK.


Examples
```tdi
TDI> _A = [1,2,3,4,5,6]
[1,2,3,4,5,6]
TDI> _B = [9,9,9,9,9,9,9,9]
[9,9,9,9,9,9,9,9]

TDI> pack(_A, _A % 2 == 0)
[2,4,6]

TDI> pack(_A, _A % 2 == 0, _A)
[2,4,6,4,5,6]
TDI> pack(_A, _A % 2 == 0, _B)
[2,4,6,9,9,9,9,9]
```

### `REPLICATE`
|||
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

### `SPREAD`
|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
|Python Syntax| `MDSplus.takefromCOMPILERSYNTAX__ReplaceDollarSignsWith___d___ANDMAKEITLOWERCASE` |
(Opcode 328
|Min arguments| 3
|Max arguments| 3
******Compiler syntax: SPREAD(_ARRAY,_DIM,_COUNT)

|Native python|False|

 |Return Type  |F90 Transformation |
Replicates an array by adding a dimension. Broadcasts several copies of source along a specified dimension.
Arguments SOURCE any type, rank (n) must be less than 254. DIM integer scalar from 0 to n. NCOPIES integer scalar.
|Signals      |Same as ARRAY except that dimensions DIM and above are
moved up one and dimension DIM is empty. |Units        |Same as ARRAY. |Form         |Same type as SOURCE with shape [E[0:DIM-1],
MIN(NCOPIES,0),E[DIM:n]] where E is the shape of SOURCE.
|Result       |The value of an element with subscripts [r0,r1,...rn] is the value of the element of source with subscripts [s0,...sn-1], where [s0,...sn-1] is [r0,...rn] with subscript DIM omitted.
|Examples     |SPREAD([2,3,4],0,3) is the array [2 3 4]. [2 3 4][2 3 4]

### `SORT`
|||
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



### `SORTVAL`
|||
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

### `UNARY_MINUS`
|||
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

### `UNARY_PLUS`
|||
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

### `SCALE`
|||
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


# Searching

### `bsearch` 
|||
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


### `MAXLOC`
|||
|-|-|
|TDI Syntax   | `MAXLOC(_ARRAY, [_MASK], [_arg3])` |
|Python Syntax| `MDSplus.MAXLOC(_ARRAY, [_MASK], [_arg3])` |
|Min arguments| 1|
|Max arguments| 3|
|Opcode|235|


Determine the location of an element of ARRAY with the maximum value of the elements identified by MASK.

Arguments 
* `_ARRAY` numeric array. 
* `[_MASK]` Optional: logical and conformable with ARRAY.
* `[_arg3]`: TODO: investigate further 

> TODO: Come back for further investigation. We think this is what it's trying to say:

This returns the location for the first instance of the highest element in an array

> original description below

The result is the vector of subscripts of an element whose value equals the maximum of all elements of ARRAY or all elements for which MASK is true. Reserved operands ($ROPRAND) are ignored. Each subscript will be in the extent of its dimension. For zero size, no true elements in MASK, or all $ROPRAND the result is undefined. If more than one element has the maximum value the result is the first in array order. The result is an offset vector even if there is a lower bound.

>TODO: THere seems to be a bug with `[MASK]` parameter. The example given below (`TDI> MAXLOC(_A, _A < 6)`) does not return what it says it should

Examples
```
TDI> MAXLOC([4,6,5])
1

maxloc([6,6,6])
0

# example per original doc. but this is untrue
_A=[1, -5, 8, -3]          # Arrays need commas
TDI> MAXLOC(_A, _A < 6)
[2,1]. [3 4-1 2][1 5 6-4]  # WHAT EVEN IS THIS???!?! 

# This is what actually happens when you input the "correct" version of the above
TDI> _A=[1, -5, 8, -3]
[1,-5,8,-3]
TDI> _A < 3
Byte_Unsigned([1,1,0,1])
TDI> MAXLOC(_A)
2
TDI> MAXLOC(_A, _A < 3)
%TDI Error in MAXLOC(_A, _A < 3)
```

|See also     |MAXVAL for the value.


### `MAXVAL`
|||
|-|-|
|TDI Syntax   | `MAXVAL(_ARRAY, [_DIM], [_MASK])` |
|Python Syntax| `MDSplus.MAXVAL(_ARRAY, [_DIM], [_MASK])` |
|Opcode|236|

Maximum value of the elements of `_ARRAY` along dimension `[_DIM]` corresponding to true elements of `[_MASK]`.

Arguments
* `_ARRAY` numeric array. 
* `[_DIM]` optional: integer scalar from 0 to n-1, where n is rank of ARRAY. 
* `[_MASK]` optional: logical and conformable to ARRAY.

Results
* Without `_DIM` the result is the largest value in the `_ARRAY`, testing only those with true `_MASK` values and value not equal to the reserved operand (`$ROPRAND`). 
* With `_DIM`, the value of an element of the result is the maximum of `ARRAY` elements with dimension `_DIM` fixed as the element number of the result. 
* If no value matches the criteria, `-HUGE(_ARRAY)` is returned.

|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. 
|Units        |Same as ARRAY. 
|Form         |Same type as ARRAY. It is a scalar if DIM is absent or ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.

Examples
```tdi
TDI> maxval([1,2,3])
3

TDI> _A = [[1,9,2,8],[7,4,6,3]]
[[1,9,2,8], [7,4,6,3]]
TDI> maxval(_A, *, _A < 5)
4
TDI> maxval(_A, 0, _A < 5)
[2,4]
TDI> maxval(_A, 1, _A < 5)
[1,4,2,3]


# If no arguments fit the mask, the return is -HUGE()
TDI> _A = [5,6,7]
[5,6,7]
TDI> maxval(_A, *, _A < 3)
-2147483648


```
See also: `MAXLOC` for the location.


### `MINLOC`
|||
|-|-|
|TDI Syntax   | `MINLOC(_ARRAY, [_MASK], [_arg3])` |
|Python Syntax| `MDSplus.MINLOC(_ARRAY, [_MASK], [_arg3])` |
|Opcode|243|

Determine the location of an element of `_ARRAY` having the minimum value of the elements identified by `_MASK`.

Arguments 
`_ARRAY` numeric array.
`_MASK` Optional: logical and conformable with ARRAY.
`[arg3]` optional: probably `KIND`


TODO: Come back to this after further investigation

|Signals      |None. 
|Units        |None. 
|Form         |Long vector of size equal to rank of ARRAY.

The result is the vector of subscripts of an element whose value equals the minimum of all elements of ARRAY or all elements for which MASK is true. Reserved operands ($ROPRAND) are ignored. Each subscript will be in the extent of its dimension. For zero size, no true elements in MASK, or all $ROPRAND the result is undefined. If more than one element has the maximum value the result is the first in array order. The result is an offset vector even if there is a lower bound.

Examples. 
MINLOC([2,4,6]) is [0].

For _A=[0 -5 8 -3]
MINLOC(_A,_A GT -4) is [0,3].
[3 4-1 2][1 5 6-4]
|See also     |MINVAL for the value.


Examples
```
TDI> minloc([5,4,6])
1

TDI> minloc([5,5,5])
0

TDI> _A=[1, -5, 8, -3] 
[1,-5,8,-3]

TDI> minloc(_A)
1

TDI> minloc(_A, _A > 0)
%TDI Error in MINLOC(_A, _A > 0)
%TDI Error in EXECUTE("minloc(_A, _A > 0)")

```

> TODO: Mask is broken and needs to be fixed along with maxloc


### `MINVAL`
|||
|-|-|
|TDI Syntax   | `MINVAL(_ARRAY, [_DIM], [_MASK])` |
|Python Syntax| `MDSplus.MINVAL(_ARRAY, [_DIM], [_MASK])` |
|Opcode|244|


Minimum value of the elements of ARRAY alongdimension DIM corresponding to true elements of MASK.

Arguments
* `_ARRAY` numeric array. 
* `[_DIM]` optional: integer scalar from 0 to n-1, where n is rank of ARRAY. 
* `[_MASK]` optional: logical and conformable to ARRAY.

TODO: Come back to this after finishing maxval

|Signals      |Same as ARRAY if DIM-th or all dimensions omitted. 
|Units        |Same as ARRAY. 
|Form         |Same type as ARRAY. It is a scalar if DIM is absent or
ARRAY is scalar or vector. Otherwise, the result is an array of rank n-1 and shaped like ARRAY with DIM subscript omitted.

The result without DIM is the minimum value of the elements of ARRAY, testing only those with true MASK values and value not equal to the reserved operand ($ROPRAND). With DIM, the value of an element of the result is the minimum of ARRAY elements with DIM dimension fixed as the element number of the result. If no value is found, +HUGE(ARRAY) is returned.
Examples. MINVAL([1,2,3]) is 3. MINVAL(_C,,_C GT 0) finds the minimum positive element of C. If _B=[[1, 3, 5],[2, 4, 6]] MINVAL(_B,0) is [1,2] and MINVAL(_B,1) is [1,3,5].
|See also     |MINLOC for the location.

Examples
```tdi
TDI> minval([1,2,3])
1

# Mask
TDI> _A = [[1,-6,3]]
[[1,-6,3]]

TDI> minval(_A, *, _A > 0)
1

# Out of bounds
TDI> minval(_A, *, _A > 5)
2147483647

# Dimensions
TDI> _A = [[1,9,2,8],[7,4,6,3]]
[[1,9,2,8], [7,4,6,3]]

TDI> minval(_A, *)
1
TDI> minval(_A, 0)
[1,3]
TDI> minval(_A, 1)
[1,4,2,3]

```


