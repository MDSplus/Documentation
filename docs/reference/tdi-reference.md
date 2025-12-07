# TDI Reference



TODO: Confirm whether to leave the scientific notation as it is in when you ping the program, or into standard:
e.g., the program lists $A0 as 52.9177E-12m, but the normal way to write that is 5.29177E-11m

TODO: make a table or something of all the different precision types of numbers you can have (F, G, H, D0 etc) and what they ultimately mean like how many bytes each ones takes up or whatever. the decimal precision is calculated by 1/(2^x) because of binary. plus all the functions to convert between them (like fs/ft_float, etc.)

TODO: regroup entries by theme rather than one big alphabetical heap
* bit-wise functions/operators (inor,inornot,inot)
* build/make functions
* text manip/fun with ascii (char, ichar, achar, iachar, etc)
* bitwise functions
* Trig functions(cos,sin,tan,all the variations)
* array manipulatino

TODO: remove references to what VAX returns

TODO for Mark:
* ~~remove min arguments/max arguments unless it's "interesting" (not interesting: min-max 1, min1-max2)~~ (stephen will do this via script)
* ~~change arg0, arg1 (etc) to more useful things like `_NUM`, or [_NUM] if optional. use backticks~~ (we'll do that piecemeal)
* examples should be rewritten as triple backtick (```) code blocks
* DONE! ~~remove c syntax from all the entries (should not be called by a human)~~
* move opcode, use natural language headings--try options for each. use LT and log10 as examples
* global explanation of mismatched units (if they don't match, it just returns `?`)
* move all the deprecated/broken/unimplemented to their own section
* read through the glossary for clarity 
* back burner consideration: generic variable name. strictly a readability thing
    * generic variable (_X)
    * generic variable pairs (_X, _Y)
    * generic text (_STRING)
    * generic array (_ARRAY)
    * MASK and DIM (_MASK, _DIM)
    * KIND (_KIND...replace with dtype?)
    * generic signal (_SIGNAL)
    * trig (angle or theta instead of x/y?)
    * complex? 




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
* all the "..._OF" functions

TODO: section on type coersion: like, all the logical functions will always return BU regardless of input. Shouldn't be difficult, if two inputs mismatch, the output will match the bigger one

TODO: section on constants / literals. If you say "0b1010" it's a binary number,  `0xABCD` is hex, `0o_____` for octal
```
TDI> 0o123
83
TDI> 0x123
291
TDI> 0b110
6
```

TODO: section on using suffixes to control the type
1D0 makes it a double float
BU is byte unsigned, etc.
```
TDI> 0b1100BU
12BU
TDI> 0B1100BU
12BU
```

