# Tree Hooks

TODO: more to come!

> Below is the start of tree-hooks.md

Basically, a hook allows you to run some custom functionality whenever some preset event happens. There are like a dozen+ possible triggers. Lets say you wanted something to happen when a tree gets opened. You would set `TreeHooks=OpenTree` and [redacted b/c Stephen doesn't remember off-hand] and then your function would be called with the type="OpenTree" and the tree and shot. The idea is not only to do things when this happens but also prevent things from happening (eg, if you don't want a tree to be opened, it can return an error). This can be very slow, so is not recommended for frequent use. Because this has to be configured on all clients for it to happen, you either really need it and are using it, or you shouldn't touch it (SLW 2025).

```
> type: name
TreeHook: OpenTree, WriteTree, CloseTree, RetrieveTree, OpenTreeEdit
TreeNidHook: GetNci, GetData, PutData, MakeSegment, MakeTimestampedSegment, UpdateSegment, PutTimestampedSegment
TreeNidDataHook: PutDataFull, MakeSegmentFull, MakeTimestampedSegmentFull, PutSegmentFull, PutTimestmapedSegmentFull

> Parameters are passed as dictionaries
TreeHook(type=, tree=, shot=)
TreeNidHook(type=, tree=, shot=, nid=)
TreeNidDataHook(type=, tree=, shot=, nid=, data=)
```

See [`tdi/treeshr/TreeShrHook.py.example`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeShrHook.py.example)