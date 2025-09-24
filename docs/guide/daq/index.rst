Setting up a Data Acquisition (DAQ) Server
==========================================

Overview
A data acquisition (DAQ) server stores the data you generate from your experiments and provides data and calculations when queried. A DAQ server can also run the software that acquires the data. MDSplus provides a high degree of flexibility for setting up a DAQ server, offering a modular structure that can be customized for any experimental design. Creating a DAQ server will require you as the administrator to make a series of decisions; the goal of this document is to help those be informed decisions. It is recommended that you read this guide before purchasing any hardware necessary for your setup.

`mdsip` is the MDSplus service.

    step 0. Install MDSplus

    step 1. configure `<access>`_access: `mdsip.hosts`
        :ref:`access<access>`

    step 2. configure environment (setup.sh and envsyms)

        .. _setup-environment:

    step 3. other considerations:
    
        * design your trees
            .. _trees:

        * learn about tree_path_variables
            .. _tree_path_variables:

        * design your shot_numbers
            .. _shot_numbers:

        * design your experiment
            .. _experiment:

.. toctree::
    :titlesonly:
    :maxdepth: 1

    access
    on-demand-mdsip
    static-mdsip
    setup-environment
    trees
    shot_numbers
    tree_path_variables
    experiment
    faq
    


