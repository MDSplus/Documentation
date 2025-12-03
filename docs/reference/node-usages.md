`action`, `any`, `axis`, `compound_data`, `device`, `dispatch`, `numeric`, `signal`, `structure`, `subtree`, `text`, or `window`. If not specified, a member node `(:name)` will default to usage `any`, and a child node `(.name)` will default to usage `structure`. [TODO: explain each type]


ANY = Unspecified. Can contain any type of data.

STRUCTURE = it is a node that serves to organize other nodes in the tree hierarchy: a child node that cannot contain data. Used for tree structure only.

ACTION = Contains an MDSplus action: describes a task or operation to be carried out during an experimental sequence

DEVICE = a composite node specifically designed for representing data acquisition  

DISPATCH = Contains the dispatch portion of an action. A node that define the information required for executing an action during an experimental sequence 

NUMERIC = contains simple numerical data (including arrays)

SIGNAL = designed to store and manage the composite Signal data, which stores data along with its independent axis. E.g, a time-series measurements.

TASK = contains task portion of an action.

TEXT = designed to store character data, or text strings.

WINDOW = designed to contain window portion of a dimension specification .

AXIS = The independent axis data. A signal in MDSplus consists of data (the dependent variable) and its dimensions (the independent axes). An AXIS node represents its dimension, such as digitizer clock output.

SUBTREE = designed to store a tree within a tree

COMPOUND_DATA = a structure that groups related data items together, similar to DEVICE node.

MAXIMUM
SUBTREE_REF
SUBTREE_TOP


reference: this list is from `usagedef.h`

TODO: more to come from Stephen/Fernando

|Usage||
|-|-|
|ANY          ||
|STRUCTURE    ||
|ACTION       ||
|DEVICE       ||
|DISPATCH     ||
|NUMERIC      ||
|SIGNAL       ||
|TASK         ||
|TEXT         ||
|WINDOW       ||
|AXIS         ||
|SUBTREE      ||
|COMPOUND_DATA||
|MAXIMUM      |upper limit for valid usage_t|
|SUBTREE_REF  |Runtime only special usage |
|SUBTREE_TOP  ||
