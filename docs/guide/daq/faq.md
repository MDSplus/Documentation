# Debugging / FAQ

## When to Restart Services
Be careful when to restart services because this could break dependencies: end all active MDSplus work and close all current connections.

Examples of when a services restart is recommended:
* Whenever MDSplus is updated. 
* Whenever the `envsyms` (environment variables) are changed. 
* Whenever the service is consuming 100% CPU (and has been for some time).
* Periodically during maintenance periods.

## How to Restart Services
If all of your services are named as we recommend (i.e., prefixed with `mdsip_`) then you can restart them all using this command:

```sh
sudo systemctl restart 'mdsip_*'
```

Note: This will not catch processes handling on-demand connections (e.g., systemd or xinetd TODO: link to those pages). In order to ensure that new MDSplus versions or configuration changes are applied to these, you will need to find and kill all `mdsip` processes. Or simply reboot.


## Beware of Python threads
At the time of this writing (July 2025), Python threads are not real threads. They allow you to organize your program and more fully utilize one single thread, but do not allow you to actually execute code in parallel. When writing Python devices, you will often want to use the whole computer (or at least two threads simultaneously). Python threads won't allow you to do this. As a result, it is recommended to run one pydevice for each mdsip server.


## Issues with on-demand connections for everything
It may be appealing to only use the on-demand systemd/xinetd connections for both data analysis and acquisition. These connections are perfectly fine for data analysis. However, if your code failing to connect means losing data, then it should be using static services instead.


## Issues with aborting / reusing a shot number
If you are planning to reuse shot numbers, there are some additional considerations:
* before recreating a pulse, please ensure that no process has the old shot files open.
* be careful not to write over "good" shots as there is no way to recover them.

Note: `lsof` can be used to track down processes with specific files open.