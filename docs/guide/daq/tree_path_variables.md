
# Tree Path Variables

To store and retrieve shot files from multiple directories, without searching them sequentially, you may want to define variable tree paths. These allow you to programatically determine parts of the directory structure where you store your shots. This is mostly done with either the tree name or individual digits of the shot number. 

To access the individual digits, we first format it into a 10-digit, zero-padded string. For example: 
* `210731001` becomes `"0210731001"`
* `54321` becomes `"0000054321"`

Then you can address the digits using the following scheme. 

|term|definition| example |
|----|----------|---------|
|`~a`| `shot[9]` | 021073112**3** |
|`~b`| `shot[8]` | 02107311**2**3 |
|`~c`| `shot[7]` | 0210731**1**23 |
|`~d`| `shot[6]` | 021073**1**123 |
|`~e`| `shot[5]` | 02107**3**1123 |
|`~f`| `shot[4]` | 0210**7**31123 |
|`~g`| `shot[3]` | 021**0**731123 |
|`~h`| `shot[2]` | 02**1**0731123 |
|`~i`| `shot[1]` | 0**2**10731123 |
|`~j`| `shot[0]` | **0**210731123 |
|`~t`| tree name | `cmod` |
|`~n`|TODO for Stephen| Please and Thank You|

You would then define your tree path using some combination of the above. Here are some examples:

```sh
# e.g., /path/to/trees/cmod
default_tree_path=/path/to/trees/~t

$ tree /path/to/trees
/path/to/trees/
├── expr
│   ├── expr_210730001.tree
│   ├── expr_210730001.datafile
│   ├── expr_210730001.characteristics
│   ├── expr_210731001.tree
│   ├── expr_210731001.datafile
│   └── expr_210731001.characteristics
└── diag
    ├── diag_210730001.tree
    ├── diag_210730001.datafile
    ├── diag_210730001.characteristics
    ├── diag_210731002.tree
    ├── diag_210731002.datafile
    └── diag_210731002.characteristics
```

```sh
# e.g., /path/to/trees/21/07/31/cmod
default_tree_path=/path/to/trees/~i~h/~g~f/~e~d/~t

$ tree /path/to/trees
/path/to/trees
└── 21
    └── 07
        ├── 30
        |   ├── expr
        |   │   ├── expr_210730001.tree
        |   │   ├── expr_210730001.datafile
        |   │   └── expr_210730001.characteristics
        |   └── diag
        |       ├── diag_210730001.tree
        |       ├── diag_210730001.datafile
        |       └── diag_210730001.characteristics
        └── 31
            ├── expr
            │   ├── expr_210731001.tree
            │   ├── expr_210731001.datafile
            │   └── expr_210731001.characteristics
            └── diag
                ├── diag_210731001.tree
                ├── diag_210731001.datafile
                └── diag_210731001.characteristics
```

```sh
# e.g., /path/to/trees/054/cmod
default_tree_path=/path/to/trees/~f~e~d/~t

$ tree /path/to/trees
/path/to/trees
└── 054
    ├── expr
    |   ├── expr_54320.tree
    |   ├── expr_54320.datafile
    |   ├── expr_54320.characteristics
    |   ├── expr_54321.tree
    |   ├── expr_54321.datafile
    |   └── expr_54321.characteristics
    └── diag
        ├── diag_54320.tree
        ├── diag_54320.datafile
        ├── diag_54320.characteristics
        ├── diag_54321.tree
        ├── diag_54321.datafile
        └── diag_54321.characteristics
```
