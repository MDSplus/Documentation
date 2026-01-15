# Administration

A data acquisition (DAQ) server stores the data you generate from your experiments and provides data and calculations when queried. A DAQ server can also run the software that acquires the data. MDSplus provides a high degree of flexibility for setting up a DAQ server, offering a modular structure that can be customized for any experimental design. Creating a DAQ server will require you as the administrator to make a series of decisions; the goal of this document is to help those be informed decisions. It is recommended that you read this guide before purchasing any hardware necessary for your setup.

Here are the general steps, with contents links below.

Step 1. :doc:`../install/index`.
    
Step 2. These steps are closely intertwined and are listed in no particular order. Multiple passes may be needed to complete these portions of the setup process.

* :doc:`access`: (``mdsip.hosts``, tree access, on-demand-mdsip, static-mdsip)

* :doc:`setup-environment` (``setup.sh`` and ``envsyms``)

* set up :doc:`tree-path-variables`


Step 3. Think through other considerations

* :doc:`shot-numbers`

* :doc:`trees`
    
* :doc:`experiment`: (mdsip services, dispatch table, devices)

* :doc:`faq`


Full contents are listed below for indexing purposes

```{toctree}
:titlesonly:
:maxdepth: 1

setup-experiment
setup-daq-server
setup-archive-server
access
on-demand-mdsip
static-mdsip
setup-environment
shot-numbers
trees
tree-path-variables
experiment
faq
```
