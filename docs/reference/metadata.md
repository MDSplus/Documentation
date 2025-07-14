# Node & Tree Metadata

MDSplus stores metadata for each node and tree. Data metadata is different--listed in our contents as "with units" and will be addressed elsewhere in this documentation.

3 terms to know:
* **DBI**: DataBase Information&mdash;rarely used

* **NCI**: Node Characteristic Information&mdash;hugely important

* **XNCI**: eXtensible NCI&mdash;middle importance. won't need often, but when you do it'll be important

**How It Works**
  * look up "**bit field**"
  * basically imagine a 32 bit number, but instead of treating it as a single number, it's treated as 32 binary digits, enabling you to answer 32 questions. 
  * it's a 32 bit number because back in the day, VMS computers were 32 bit machines, so that was the max size. 4 bytes is a very reasonable size for 32-bit. when unused, they are always set to zero. 
  * **bitwise operators** are the way you operate and you deal with it. Treat each as a separate digit, compare the first part of the expression to the second part, not a whole number. These are the operators `& | ~ ^`
    * `&` bitwise AND (aka both need to be true)

        `1110 & 0101 = 0100`
    * `|` bitwise OR (aka either.)
    
        `1110 | 0101 = 1111`
    * `^` bitwise XOR (aka either but NOT both)
    
        `1110 ^ 0101 = 1011`

        fun fact, this is also how parity disks work in RAID
    * `~` bitwise NOT

        `~1110 = 0001`

**BITFIELD, OPERATOR, MASK**

The syntax is `bitfield` `operator` `mask`, separated by spaces

```c
// Maps names to bits.
#define NciSTATE       0b0001 // "#define" is how you assign a constant
#define NciWRITE_ONCE  0b0010 // the zeros mask the digits you don't want
#define NciWRITE_MODEL 0b0100 // the "0b" indicates that "the following is a binary number"
#define NciSOMETHING   0b1000

// An actual flags from a node in the tree
int flags;

// Query the state
bool state = (flags & NciSTATE);

// Set the write once flag
flags = (flags | NciWRITE_ONCE);
```

so:
* And every node in the tree has an NCI
* And every NCI has a flag bitfield
* And it's all stored in the *.characteristics file. 
* This optimizes for both speed and storage size--having a single number answer multiple questions is very cheap and fast. This lets you store and retrieve information from individual bits.

People setting up their trees will be setting the bitfields through Traverser or TCL



## NCI

* Flags: will have other things in it (Stephen to look up)

* `time_inserted` when data was inserted as a VMS timestamp (we'll get into that later)

* `owner_identifier` who wrote it, stored as uid:gid (UserID:GroupID) as two 16-bit numbers glued together

* `class` and `dtype` these describe the datatype. they are tightly coupled and basically go together.

* `length` size in bytes of the data

* `compression_method` a single character used to show what compression method would be used to compress the data. but we only support a single method (MdsCmprs). it's already the best.

* `status` -- ??? TODO STEPHEN

* "The rest of it" is data location. It's internal and shouldn't be touched. No human will be touching most of this anyway. 

All the flags in `ncim_t`:
| Get | Set | Code | Python/Java/C equivalent | Description |
|-----|-----|------|--------------------------|-------------|
|&check;|     | NciM_STATE = 0x00000001 | |
|     |     | NciM_PARENT_STATE = 0x00000002 | |
|     |     | NciM_ESSENTIAL = 0x00000004 | |
|     |     | NciM_CACHED = 0x00000008 | |
|     |     | NciM_VERSIONS = 0x00000010 | |
|     |     | NciM_SEGMENTED = 0x00000020 | |
|     |     | NciM_SETUP_INFORMATION = 0x00000040 | |
|     |     | NciM_WRITE_ONCE = 0x00000080 | |
|     |     | NciM_COMPRESSIBLE = 0x00000100 | |
|     |     | NciM_DO_NOT_COMPRESS = 0x00000200 | |
|     |     | NciM_COMPRESS_ON_PUT = 0x00000400 | |
|     |     | NciM_NO_WRITE_MODEL = 0x00000800 | |
|     |     | NciM_NO_WRITE_SHOT = 0x00001000 | |
|     |     | NciM_PATH_REFERENCE = 0x00002000 | |
|     |     | NciM_NID_REFERENCE = 0x00004000 | |
|     |     | NciM_INCLUDE_IN_PULSE = 0x00008000 | |
|     |     | NciM_COMPRESS_SEGMENTS = 0x00010000 | |


Here's all the (queries? flags?) in `nci_t:`
| Get | Set | Code | Python/Java/C equivalent | Description |
|-----|-----|------|--------------------------|-------------|
|     |     | NciEND_OF_LIST = 0 | |
|     |     | NciSET_FLAGS = 1 | |
|     |     | NciCLEAR_FLAGS = 2 | |
|     |     | NciTIME_INSERTED = 4 | |
|     |     | NciOWNER_ID = 5 | |
|     |     | NciCLASS = 6 | |
|     |     | NciDTYPE = 7 | |
|     |     | NciLENGTH = 8 | |
|     |     | NciSTATUS = 9 | |
|     |     | NciCONGLOMERATE_ELT = 10 | |
|     |     | NciGET_FLAGS = 12 | |
|     |     | NciNODE_NAME = 13 | |
|     |     | NciPATH = 14 | |
|     |     | NciDEPTH = 15 | |
|     |     | NciPARENT = 16 | |
|     |     | NciBROTHER = 17 | |
|     |     | NciMEMBER = 18 | |
|     |     | NciCHILD = 19 | |
|     |     | NciPARENT_RELATIONSHIP = 20 | |
|     |     | NciCONGLOMERATE_NIDS = 21 | |
|     |     | NciORIGINAL_PART_NAME = 22 | |
|     |     | NciNUMBER_OF_MEMBERS = 23 | |
|     |     | NciNUMBER_OF_CHILDREN = 24 | |
|     |     | NciMEMBER_NIDS = 25 | |
|     |     | NciCHILDREN_NIDS = 26 | |
|     |     | NciFULLPATH = 27 | |
|     |     | NciMINPATH = 28 | |
|     |     | NciUSAGE = 29 | |
|     |     | NciPARENT_TREE = 30 | |
|     |     | NciRLENGTH = 31 | |
|     |     | NciNUMBER_OF_ELTS = 32 | |
|     |     | NciDATA_IN_NCI = 33 | |
|     |     | NciERROR_ON_PUT = 34 | |
|     |     | NciRFA = 35 | |
|     |     | NciIO_STATUS = 36 | |
|     |     | NciIO_STV = 37 | |
|     |     | NciDTYPE_STR = 38 | |
|     |     | NciUSAGE_STR = 39 | |
|     |     | NciCLASS_STR = 40 | |
|     |     | NciVERSION = 41 | |
|     |     | NciCOMPRESSION_METHOD = 42 | |
|     |     | NciCOMPRESSION_METHOD_STR = 43 | |


look at `<ncidef.h>`
* `ncim_t` shows all the bits in the flag
* `getnci()` these are the questions we can ask
* `setnci()` lets you set the NCIs
* `nci_t` the full list of NCI questions. we'll want to document all 44 of them!

side note: `#include <blah.h>` when it comepiles, it just copies and pastes the whole thing into the code you wrote

You can ask these questions about every node, but some answers are computed on-the-fly
e.g. NciFULLPATH, which computes the path to the node when asked

Getting the value of a flag is a two step process, first you ask for `NciGET_FLAGS` (all 32 bits) and then you decide which `ncim_t` bit(s) (aka Binary digIT)  you care about and then you see whether it's a zero or one (this is called "testing the bit"). 

## DBI

DBIs have almost the same interface, except it's about the whole tree (aka The Database)

we'll document these for completeness, but it's very rarely used


## XNCI

This is where you will go when you get metadata you want to store but it's not already part of the built-in set. 

It's stored as a "key value" as in every key points to a value. So this is stored with the key. whereas before, the key is implicit in the structure
this inherently has a bigger footprint and is slower because you have to store the full text or whatever, rather than have it point to a simple number and pulling out a digit to 

fun fact it all lives in the *.datafile because it's data about the data that doesn't belong anywhere else

fun side effect: `no_write_shot` / `no_write_model` will prevent you from writing your XNCI. you'll have to turn off `no_write_`, write your XNCI, and turn it back on again. The `no_write_` is really more of a guardrail than a cop.

example use cases:
* resampled segments
* storing where the data was retrieved from
* storing a reference some other database

> Stephen will link me to the *.h file so I can start buildig the definition tables, and then we can sit down and figure out/document the definitions for each one

https://github.com/MDSplus/mdsplus/blob/alpha/include/dbidef.h

https://github.com/MDSplus/mdsplus/blob/alpha/include/ncidef.h