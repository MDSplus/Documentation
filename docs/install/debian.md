
# Installation on Debian (Ubuntu)

## Enabling the Repository

```
# 24, alpha release
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"

# 24, stable release
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus stable' > /etc/apt/sources.l
```