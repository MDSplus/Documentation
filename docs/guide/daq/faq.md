
# Debugging / FAQ
* when to restart services
* python threads and why they suck
* issues with using port 8000 for everything
* issues with aborting / reusing a shot number
* etc


## When to restart services
You can't just do it whenever, it could break dependencies. 
* Whenever MDSplus is updated. 
* Whenever the `envsyms` (environment variables) are changed. 
* Whenever the service is consuming 100% CPU (and has been for some time).
* Periodically during maintenance periods.


## Beware of Python threads
At the time of this writing (July 2025), Python threads are not real threads. They allow you to organize your program and more fully utilize one single thread, but do not allow you to actually execute code in parallel. When writing Python devices, you will often want to use the whole computer (or at least two threads simultaneously). Python threads won't allow you to do this. As a result, it is recommended to run one pydevice for each mdsip server.

