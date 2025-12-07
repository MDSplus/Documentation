
# File and Console I/O

### `fopen` (Opcode 265)

|||
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


### `fclose` (Opcode 96)

|||
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

### `fseek` (Opcode 309)

|||
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



### `ftell` (Opcode 417)

|||
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


### `WRITE`
|||
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



# ???

### `WAIT`
|||
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

### `SPAWN`
|||
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

TODO: Stephen and Tim. `!bash`

### `DATE_TIME` (Opcode 114)

|||
|-|-|
|TDI Syntax   | `DATE_TIME(arg0)` |
|Python Syntax| `MDSplus.DATE_TIME(arg0)` |
|Min arguments| 0 |
|Max arguments| 1 |

* Returns the current/specified data and time as a text string.
* Arguments (Optional): TIME must be a quadword (64-bit), VMS time stamp positive absolute time or negative delta time.

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

### `DSQL` (Opcode 415)

|||
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
