## Create Systemd bridge files
in /etc/systemd/network

### 10-rascsi_bridge.netdev
    [NetDev]
    Name=rascsi_bridge
    Kind=bridge

### 11-rascsi_bridge.network
This will also bridge the ethernet port to rascsi_bridge and will provide an ip address to a client

    [Match]
    Name=eth0


    [Network]
    Bridge=rascsi_bridge


###  Reboot raspberry pi