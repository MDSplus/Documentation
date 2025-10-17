# On-Demand `mdsip` Services

For this purpose you must choose either **systemd** or **xinetd**, but you cannot do both.

## systemd
The recommended way to provide on-demand mdsip services is with systemd's `at` services. These consist of two parts:
1. the `.socket`, which describes how to listen for incoming connections.
2. the `.service`, which describes how to start a process to handle new connection.

We provide usable versions of these files in the MDSplus installation located in `$MDSPLUS_DIR/rpm`. To use them, simply copy both `mdsip@.socket` and `mdsip@.service` to `/etc/systemd/system/int` and enable them.


TODO: Stephen to verify all the commands in this section

```sh
sudo cp $MDSPLUS_DIR/rpm/mdsip@.socket /etc/systemd/system/int
sudo cp $MDSPLUS_DIR/rpm/mdsip@.service /etc/systemd/system/int

sudo systemctl enable mdsip@.socket
sudo systemctl start mdsip@.socket
```

In order to inspect and debug these services, run:

```sh
sudo systemctl status 'mdsip@*'
```


## xinetd

Deprecated, recommend that you use systemd instead

When MDSplus is installed and xinetd is present on the system, config files will be put into `/etc/xinetd.d/` but will need to be enabled before they can be used. 

TODO: Multiple services

`/etc/xinetd.d/mdsip`
```
# default: off
#       standard mdsip.hosts and logs into /var/log/mdsplus.
service mdsip
{
        disable         = yes
        socket_type     = stream
        wait            = no
        cps             = 10000 1
        instances       = UNLIMITED
        per_source      = UNLIMITED
        user            = root

### NOTE: If you installed MDSplus to a different location than
###       /usr/local/mdsplus make sure you change the following
###       line to use the directory where you installed MDSplus.

        server          = /usr/local/mdsplus/bin/mdsipd
        server_args     = mdsip /var/log/mdsplus/mdsipd
        log_on_failure  += HOST
        log_on_success  += HOST
        flags           = KEEPALIVE NODELAY NOLIBWRAP
}

```

NOTE: this calls a shell script called `mdsipd` which is a wrapper for `mdsip`. The comments at the top of the file describe how to use it.

In order to use this, change `disable = yes` to `no` and restart xinetd:

```
# for systems managed by systemd
sudo systemctl restart xinetd

# for systems mananged by initd
sudo service xinetd restart
```

