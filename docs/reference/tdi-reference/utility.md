
# File and Console I/O

## File Unit

A file unit is a [`POINTER`](#) to a C [`FILE`](https://en.cppreference.com/w/c/io/FILE.html) struct that serves as a unique ID for an open file.

## `FOPEN` (Open File)

|||
|-|-|
|TDI Syntax   | `FOPEN(_FILENAME, _MODE)` |
|Python Syntax| `MDSplus.FOPEN(filename, mode)` |
|Opcode|265|

Opens the file specified by `_FILENAME` with the given `_MODE` and returns the [file unit](#file-unit), if successful. Otherwise, this returns [`$MISSING`](./language.md#missing-missing-valueargument-null).

`_MODE` must be valid [file access flags](https://en.cppreference.com/w/c/io/fopen.html#File_access_flags).

This is a wrapper around [`fopen()`](https://en.cppreference.com/w/c/io/fopen.html) in C.

```tdi
TDI> _file = fopen('example.txt', 'r')
Pointer(0x63abc39a5770)

TDI> _file = fopen('does-not-exist.txt', 'r')
*
```

## `FCLOSE` (Close File)

|||
|-|-|
|TDI Syntax   | `FCLOSE(_UNIT)` |
|Python Syntax| `MDSplus.FCLOSE(unit)` |
|Opcode|96|

Closes the file specified by `_UNIT`, which was opened with [`FOPEN`](#fopen-open-file). Returns the result of [`fclose()`](https://en.cppreference.com/w/c/io/fclose.html).

`_UNIT` must be a valid [file unit](#file-unit) and cannot be [`$MISSING`](./language.md#missing-missing-valueargument-null).

This is a wrapper around [`fclose()`](https://en.cppreference.com/w/c/io/fclose.html) in C.

```tdi
TDI> _file = fopen('example.txt', 'r')
Pointer(0x63abc39a5770)

TDI> fclose(_file)
0


TDI> _file = fopen('does-not-exist.txt', 'r')
*

# Cannot close a file that wasn't opened
TDI> if (_file) { fclose(_file); }
```

## `FSEEK` 

|||
|-|-|
|TDI Syntax   | `FSEEK(_UNIT, [_OFFSET], [_ORIGIN]) ` |
|Python Syntax| `MDSplus.FSEEK(unit, [offset], [origin]) ` |
|Opcode|309|

Sets the file position indicator for the file specified by `_UNIT`, which was opened with [`FOPEN`](#fopen-open-file). Returns the result of [`fseek()`](https://en.cppreference.com/w/c/io/fseek.html).

If `_OFFSET` is specified, it must be a `Scalar` offset in bytes from the `_ORIGIN`. Otherwise, the default is 0.

If `_ORIGIN` is specified, it must be one of:
* 0 (for `SEEK_SET`, the beginning of the file)
* 1 (for `SEEK_CUR`, the current position)
* 2 (for `SEEK_END`, the end of the file)
Otherwise, the default is 0 (`SEEK_SET`).

Note: These values are libc-dependent, please check the documentation for your system for the correct values.

This is a wrapper around [`fseek()`](https://en.cppreference.com/w/c/io/fseek.html) in C.

```tdi
TDI> _file = fopen('example.txt', 'r+')
Pointer(0x63abc39a5770)

TDI> read(_file)
"first line"
TDI> read(_file)
"second line"

# Rewind
TDI> fseek(_file, *, 0)
0
TDI> read(_file)
"first line"

# Get the file size
TDI> fseek(_file, *, 2)
0
TDI> _size = ftell(_file)
123

# Append to the end
TDI> fseek(_file, *, 2)
0
TDI> write(_file, "appending a line\n")
18
```

## `FTELL` (Get File Position Indicator)

|||
|-|-|
|TDI Syntax   | `FTELL(arg0) ` |
|Python Syntax| `MDSplus.FTELL(arg0) ` |
|Opcode|417|

Gets the file position indicator for the file specified by `_UNIT`, which was opened with [`FOPEN`](#fopen-open-file). Returns the result of [`ftell()`](https://en.cppreference.com/w/c/io/ftell.html).

This is a wrapper around [`ftell()`](https://en.cppreference.com/w/c/io/ftell.html) in C.

```tdi
TDI> _file = fopen('example.txt', 'r')
Pointer(0x63abc39a5770)

TDI> read(_file)
"first line"
TDI> read(_file)
"second line"
TDI> write(, "Read ", ftell(_file), " bytes")
Read          23 bytes

# Get the file size
TDI> fseek(_file, *, 2)
0
TDI> _size = ftell(_file)
123
```

## `READ` (Read from File or Console)

|||
|-|-|
|TDI Syntax   | `READ(_UNIT)` |
|Python Syntax| `MDSplus.READ(unit)` |
|Opcode|295|

Reads from the file specified by `_UNIT` until a newline (`\n`) is found or until EOF, then returns the string with the last character removed.

Note: If the line is empty (other than the newline), `READ()` will throw an error. This can be caught with [`IF_ERROR()`](./language.md#if_error-handle-error-trycatch), see the example below.

Note: This does not check if the last character was a newline, it simply removes it. Make sure your input files have a trailing newline.

This is a wrapper around [`fgets()`](https://en.cppreference.com/w/c/io/fgets.html) in C.

```tdi
TDI> _name = read(*)
Tom
"Tom"

TDI> write(*, "Hello, ", _name);
Hello, Tom


TDI> _file = fopen("example.txt", "r")
TDI> read(_file)
"first line"
TDI> read(_file)
"second line"
```

Reading lines from a file
```tdi
_file = fopen("example.txt", "r")
if (!_file) {
    abort();
}

/* Get the file size */
fseek(_file, *, 2);
_end = ftell(_file);
fseek(_file, *, 0);

while (ftell(_file) < _end) {
    /* Ignore errors from empty lines */
    _line = if_error(read(_file), '');

    write(*, _line);
}

```

## `WRITE` (Write to File or Console)

|||
|-|-|
|TDI Syntax   | `WRITE(_UNIT, [_ARGS...])` |
|Python Syntax| `MDSplus.WRITE(unit, [args...])` |
|Opcode|370|

Writes `_ARGS` to the file specified by `_UNIT`, or [`stdout`](#) if `_UNIT` is [`$MISSING`](./language.md#missing-missing-valueargument-null). Returns the number of bytes written.

Items in `_ARGS` don't need to be [Text](#), but any other types will be converted using [`TEXT`](./text.md#text-to-string).

Note: While there are no formatting options, you can use `CVT` or `TEXT` to control the output. Be careful, as they can and will remove important digits. e.g., `TEXT(42, 1) == "2"`.

```tdi
TDI> write(*, "Hello, World!")
Hello, World!
14

TDI> write(*, "The number is", 42)
The number is         42
25

TDI> write(, [1, 2, 3])
          1          2          3
34

TDI> write(, 5, " +", 7, " is", 12)
          5 +          7 is         12
39

# Using TEXT()
TDI> write(, text(5, 1), " + ", text(7, 1), " is ", text(12, 2))
5 + 7 is 12
12

# Using CVT()
TDI> write(, cvt(4, ' '), " + ", cvt(5, ' '), " is ", cvt(12, '  '))
4 + 5 is 12
12
```

Writing data to a file:
```tdi
_data = [[1,2,3], [4,5,6], [7,8,9]]

_file = fopen("data.tsv", "w")
if (!_file) {
    abort();
}

for (_i = 0; _i < size(_data[0]); ++_i) {
    write(_file, _data[,_i]);
}

fclose(_file)
```

The resulting `data.tsv`:
```
          1          2          3
          4          5          6
          7          8          9

```

# Database I/O

## `SET_DATABASE` (Connect to SQL Database using Sybase Login)

|||
|-|-|
|TDI Syntax| `SET_DATABASE(_NAME)` |
|Filepath  | [`tdi/mdssql/set_database.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/mdssql/set_database.fun) |

Connects to the database described in the sybase login file identified by `_NAME`. The sybase login file must be located in your `$HOME`/`%USERPROFILE%` directory. The file name must be `_NAME` (either case-sensitive or lowercase), followed by `.sybase_login`.

For a database named `MyLogbook` the following paths would be valid:
* `$HOME/MyLogbook.sybase_login`
* `$HOME/mylogbook.sybase_login`

The sybase login file must be 5 lines (with a trailing newline `"\n"`) indicating:
* The MDSplus proxy host, this is not supported by `SET_DATABASE` but this line must still exist.
* The database host (`_DBHOST`).
* The database name (`_DBNAME`).
* The username to use (`_USERNAME`).
* The password to use (`_PASSWORD`).

Once the sybase login file is parsed, this will call:
```tdi
dblogin(_DBHOST, _USERNAME, _PASSWORD);
dsql('USE ' // _DBNAME);
dsql('set textsize 8192');
```

For example, `MyLogbook.sybase_login` could look like:
```

dbsrv01
mylogbook
username
pa$$w0rd
```

```tdi
TDI> set_database('MyLogbook')
0

TDI> dsql('SELECT column FROM table', _values)
1
```

See also:
* [`DSQL`](#dsql-execute-sql-query)
* [`DBLOGIN`](#dblogin-connect-to-sql-database)

## `DBLOGIN` (Connect to SQL Database)

|||
|-|-|
|TDI Syntax| `DBLOGIN(_HOST, _USER, _PASS)` |
|Filepath  | [`tdi/mdssql/dblogin.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/mdssql/dblogin.fun) |

See also:
* [`DSQL`](#dsql-execute-sql-query)
* [`DBLOGIN`](#dblogin-connect-to-sql-database)

## `DSQL` (Execute SQL Query)

|||
|-|-|
|TDI Syntax   | `DSQL(_QUERY, [_ARGS...], [_OUTPUTS...])` |
|Python Syntax| `MDSplus.DSQL(query, [args...], [outputs...])` |
|Opcode|415|

Run the SQL `_QUERY` on a connection created by [`SET_DATABASE`](#set_database-connect-to-sql-database-using-sybase-login) or [`DBLOGIN`](#dblogin-connect-to-sql-database). Any `?`s in the `_QUERY` will be replaced by the corresponding value from `_ARGS`. Each column of the result will be stored in the corresponding variable in `_OUTPUTS`. Returns the number of rows retrieved.

`_QUERY` must be a string and should be a valid SQL query.

The number of `_ARGS` must match the number of `?`s. Items in `_ARGS` don't need to be [Text](#), but any other types will be converted using [`TEXT`](./text.md#text-to-string).

Items in `_OUTPUTS` can either be variables or strings containing variable names. The variables don't need to be already defined.

> TODO: Stephen, contrive more examples
```tdi
TDI> set_database('MyLogbook')

TDI> _rows = dsql('SELECT COUNT(*) FROM entries WHERE value < ?', 42, _count)
1

TDI> write(*, _count)
123
```

# Miscellaneous 

## `WAIT` (Wait, Sleep)

|||
|-|-|
|TDI Syntax   | `WAIT(_SECONDS)` |
|Python Syntax| `MDSplus.WAIT(seconds)` |
|Opcode|363|

Waits (sleeps) for `_SECONDS` seconds.

```tdi
TDI> wait(2.5)
# 2.5 seconds later
*
```

## `SPAWN` (Spawn, Execute Command)

|||
|-|-|
|TDI Syntax   | `SPAWN(_COMMAND) or !COMMAND` |
|Python Syntax| `MDSplus.SPAWN(command)` |
|Opcode|327|

Spawn an external command specified by `_COMMAND`.

`_COMMAND` must be a string with the target program and arguments separated by spaces. The program should either be available on the system search (`$PATH`) or a full path to the executable. Returns the exit code from the external process.

This is disabled when the sandbox is enabled with [`MdsEnableSandbox()`](#).

Note: This previously took `_INPUT` and `_OUTPUT`, but this functionality has been removed.

```tdi
TDI> spawn("whoami")
mdsplus
0

TDI> spawn("exit 42")
42

TDI> !pwd
/path/to/working/directory

TDI> !ls -la
<output here>

TDI> !bash
bash$ echo "Hello, World!"
Hello, World!
bash$ exit
exit
```

## `DATE_TIME` (String Timestamp)

|||
|-|-|
|TDI Syntax   | `DATE_TIME([_TIMESTAMP])` |
|Python Syntax| `MDSplus.DATE_TIME([timestamp])` |
|Opcode|114|

Returns a 23-character string representing the `_TIMESTAMP` if specified, otherwise the current time. The current time zone will be used.

If specified, `_TIMESTAMP` must either be a 64-bit VMS timestamp, or 0. VMS timestamps are counts of 100ns clunks since the VMS EPOCH (17 Nov 1858).  If `_TIMESTAMP` is 0, the result will be the UNIX epoch `" 1-JAN-1970 00:00:00.00"`, regardless of the current time zone.

```tdi
TDI> date_time()
" 9-DEC-2025 18:54:47.00"

TDI> date_time(0)
" 1-JAN-1970 00:00:00.00"

TDI> date_time(45067167999999999Q)
" 9-SEP-2001 01:46:39.99"

TDI> date_time(getnci(:TREE_NODE, 'TIME_INSERTED'))
"28-FEB-2007 12:37:20.83"
```

See also:
* [`GETNCI`](./trees.md#getnci-get-node-characteristic-information)

getenv
setenv