MDSplus Devices
=====================

The `MDSplus device` framework is what MDSplus uses to integrate an experiment's hardware into the software. In the simplest terms, a device is a collection of nodes in the data tree containing all of the necessary setup parameters, task descriptions, and raw data associated with each physical data acquisition module in an experiment. This collection of nodes can be used to interface with the hardware, both controlling the hardware and collecting data from it.

If you are looking to use an existing MDSplus device driver, go here [using_devices]

If you are looking to write a new MDSplus device driver, go here [writing_devices]

.. toctree::
    :maxdepth: 1

    using_devices
    writing_devices

