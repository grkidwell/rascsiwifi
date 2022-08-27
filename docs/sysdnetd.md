## SystemD-NetworkD transition
Switch over to systemd-networkd for general networking
#

## Follow Quick Step instructions

[go to website](https://raspberrypi.stackexchange.com/questions/108592/use-systemd-networkd-for-general-networking/108593#108593)


    # deinstall classic networking
    pi@raspberrypi:~ $ sudo -Es   # if not already done
    root@raspberrypi:~ # systemctl daemon-reload
    root@raspberrypi:~ # systemctl disable --now ifupdown dhcpcd dhcpcd5 isc-dhcp-client isc-dhcp-common rsyslog
    root@raspberrypi:~ # apt --autoremove purge ifupdown dhcpcd dhcpcd5 isc-dhcp-client isc-dhcp-common rsyslog
    root@raspberrypi:~ # rm -r /etc/network /etc/dhcp

    # setup/enable systemd-resolved and systemd-networkd
    root@raspberrypi:~ # systemctl disable --now avahi-daemon libnss-mdns
    root@raspberrypi:~ # apt --autoremove purge avahi-daemon
    root@raspberrypi:~ # apt install libnss-resolve
    root@raspberrypi:~ # ln -sf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
    root@raspberrypi:~ # apt-mark hold avahi-daemon dhcpcd dhcpcd5 ifupdown isc-dhcp-client isc-dhcp-common libnss-mdns openresolv raspberrypi-net-mods rsyslog
    root@raspberrypi:~ # systemctl enable systemd-networkd.service systemd-resolved.service
    root@raspberrypi:~ # exit
    pi@raspberrypi:~ $


