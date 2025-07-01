# Environment Variables: Glossary

# Core
## MDSPLUS_DIR
Path to MDSplus installation. This is used for setting a lot of other variables through `envsyms`.

## MDS_PATH
TDI Search Path. One or more paths separated by semicolons. TDI will search left-to-right for `.fun` or `.py` files matching the name of the function being searched for.

# Trees
## $${tree}_path
The path to search for the tree files for a given tree name (where `${tree}` is the name of your tree). If present, this will be used instead of `default_tree_path`. This variable can contain one or more paths separated by semicolons. Each path to search can be anything defined elsewhere in this documentation.

These two separate variables (`$${tree}_path` and `default_tree_path`) may be useful if you are creating your own tree outside of a tree owned by your organization; the this allows you to quickly access both.


## default_tree_path
The path to search for the tree files for a tree that does not have `${tree}_path` defined. One or more paths separated by semicolons. Each path to search can be anything defined elsewhere in this documentation.


## mds_event_target
If set, TCP events will be used instead of UDP events. This contains the event server to send the TCP events to.

