# Dispatcher

> TODO: Finish page

The dispatcher is the state machine of MDSplus

`phase_table()` is the function that lists the states in your experiment
* it comes with defaults
* we'll also go over this in setting up daq server

2 ways to think of state machines:
1. run this code when you enter this state

    simpler, cheaper, easier, limited

2. run this code when you transition between two states

    e.g., `abort to init` is very different from `success to init`, so there are decision trees that have to be written that cover every possible transition you expect.
    
It's actually not possible to switch between types. Dispatcher was programmed as a #1, but there are various TCL scripts to make it behave like a #2 one. This is why we are working to deprecate the dispatcher&mdash;so we can rewrite it as #2 type. CMOD had a type 2 one built on top of it to handle the various contingencies, but this is inefficient.

If you were designing an experiment, it's a good idea to set up a state machine.

## Building a dispatch table

A dispatch table makes things run in a specific order. The algorithm can be described as such:

1. find all the action nodes in order (top to bottom)

2. filter out the ones not in the current phase

3. order them by priority (1 to 100. default is 50. if everything is 50, it goes by order of NID or Node ID or internal number. if the model doesn't change at all, all shots will go in the same order. if we make a new dispatcher, many of these characteristics would carry over)

4. save that table. this is called the dispatch table. The dispatch table is built fresh for every new shot since parameters may change from one shot to the next depending on the experiment. This is not automatic, there's a command that needs to be run.

