# On-Demand `mdsip` Services

For this purpose you must choose either **systemd** or **xinetd**, but you cannot do both.

## systemd
TODO: next time Stephen and Fernando are available together

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

