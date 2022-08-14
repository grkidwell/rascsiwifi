## Create Bridge systemd files
in /etc/systemd/network

### 10-rascsi_bridge.netdev
    [NetDev]
    Name=rascsi_bridge
    Kind=bridge

### 11-rascsi_bridge.network
    [Match]
    Name=eth0


    [Network]
    Bridge=rascsi_bridge


##  Reboot raspberry pi