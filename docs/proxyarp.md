## Setup Proxy ARP with Subnetting

below instructions were modified from this [website](https://raspberrypi.stackexchange.com/questions/88954/workaround-for-a-wifi-bridge-on-a-raspberry-pi-with-proxy-arp/88955#88955)

### Configure the WiFi client connection

Create this file for wpa_supplicant with your settings for `country=`, `ssid=` and `psk=`:

    sudo -Es    # if not already done
    cat > /etc/wpa_supplicant/wpa_supplicant-wlan0.conf <<EOF
    
    country=US
    ctrl_interface=DIR=/run/wpa_supplicant GROUP=netdev
    update_config=1

    network={
        ssid="TestNet"
        psk="testingPassword"
    }
    EOF

    chmod 600 /etc/wpa_supplicant/wpa_supplicant-wlan0.conf
    systemctl disable wpa_supplicant.service
    systemctl enable wpa_supplicant@wlan0.service
    rfkill unblock 0

### Enable promiscuous mode on wlan0 to see broadcasts on both subnets.

    sudo systemctl edit wpa_supplicant@wlan0.service

    ### Editing /etc/systemd/system/wpa_supplicant@wlan0.service.d/override.conf
    ### Anything between here and the comment below will become the new contents of the file

    [Service]
    ExecStartPre=/sbin/ip link set %i promisc on
    ExecStopPost=/sbin/ip link set %i promisc off

    ### Lines below this comment will be discarded

    ### /lib/systemd/system/wpa_supplicant@.service
    # [Unit]
    # Description=WPA supplicant daemon (interface-specific version)
    # Requires=sys-subsystem-net-devices-%i.device
    # After=sys-subsystem-net-devices-%i.device
    # Before=network.target
    # Wants=network.target
    # 
    # # NetworkManager users will probably want the dbus version instead.
    # 
    # [Service]
    # Type=simple
    # ExecStart=/sbin/wpa_supplicant -c/etc/wpa_supplicant/wpa_supplicant-%I.conf -Dnl80211,wext -i%I
    # 
    # [Install]
    # Alias=multi-user.target.wants/wpa_supplicant@%i.service


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

