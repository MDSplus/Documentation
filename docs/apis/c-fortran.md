# C / Fortran

## MdsLib

### Linking

#### C

Link with `-lMdsLib` (or `-lMdsLib_client`)

```c
#include <mdslib.h>
```

#### Fortran

Link with `-lMdsLib_fortran`

```f
integer descr, MdsValue, MdsOpen, MdsPut

integer IDTYPE_LONG, IDTYPE_FLOAT, IDTYPE_CSTRING

parameter (IDTYPE_LONG=8, IDTYPE_FLOAT=10, IDTYPE_CSTRING=14)
```

### Usage

> TODO: describe these functions

`descr()`
`MdsConnect(char * host)`
`MdsOpen(char * tree, int * shot)`
`MdsClose(char * tree, int * shot)`
`MdsValue(char * expression, ...)` / `MdsValue2(char * expression, ...)`
`MdsPut(char * node, char * expression, ...)` / `MdsPut2(char * node, char * expression, ...)`

## TreeShr, TdiShr, etc.

> TODO: Using the libraries directly

> TODO: Link to C++ APIs
