## Setup Proxy ARP with Subnetting

[go to website](https://raspberrypi.stackexchange.com/questions/88954/workaround-for-a-wifi-bridge-on-a-raspberry-pi-with-proxy-arp/88955#88955)

## Edit files in /etc/systemd/network directory
#
###  For 04-wired.network
These addresses must be part of the same subnet but outside the dhcp range of your router.   In the below example, the wifi router's dhcp range is 100-149 so 241-255 is chosen for the rascsi's subnet.  The pi will be given address 192.168.3.241 and the mac will be given an address from the range 242-255.

    [Match]
    Name=rascsi_bridge

    [Network]
    # Have attention to the bit mask at the end of the address
    Address=192.168.3.241/28
    
    DHCPServer=yes

    [DHCPServer]
    DNS=84.200.69.80 1.1.1.1

### For 08-wifi.network

    [Match]
    Name=wl*

    [Network]
    DHCP=yes
    IPForward=ipv4
    IPv4ProxyARP=yes

