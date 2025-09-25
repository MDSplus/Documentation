Setting up a Data Acquisition (DAQ) Server
==========================================

Overview
A data acquisition (DAQ) server stores the data you generate from your experiments and provides data and calculations when queried. A DAQ server can also run the software that acquires the data. MDSplus provides a high degree of flexibility for setting up a DAQ server, offering a modular structure that can be customized for any experimental design. Creating a DAQ server will require you as the administrator to make a series of decisions; the goal of this document is to help those be informed decisions. It is recommended that you read this guide before purchasing any hardware necessary for your setup.

Here are the general steps, with contents links below.



    step 1. `Install MDSplus`_
    .. :doc:`Install MDSplus`<../install>

    step 2. These steps are closely intertwined and are listed in no particular order. Multiple passes may be needed to 
    * Configure `access`_: (``mdsip.hosts``, tree access, on-demand-mdsip, static-mdsip)
    .. _access: configure-access

    * configure `environment variables`_ (``setup.sh`` and ``envsyms``)
    .. _environment variables: setup-environment

    * set up `tree path variables`_
    .. _tree path variables:tree_path_variables


This could be its own list
        * design your `shot numbers`_
        .. _shot numbers: shot_numbers

        * design your `trees`_
        .. _trees: trees

        * design your `data acquisition cycle`_ (mdsip services, dispatch table, devices)
        .. _experiment: experiment

.. toctree::
    :titlesonly:
    :maxdepth: 1

    access
    on-demand-mdsip
    static-mdsip
    setup-environment
    shot_numbers
    trees
    tree_path_variables
    experiment
    faq
    


.. TODO: fix the links