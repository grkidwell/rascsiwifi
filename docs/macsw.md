## Install Mac software


### Open Transport and Daynaport drivers
[Mac Librarian video tutorial - Ethernet Adapter Setup](https://www.youtube.com/watch?v=-qRG-0Pne-I&t=720s)

[RaSCSI wiki](https://github.com/akuker/RASCSI/wiki/Dayna-Port-SCSI-Link#open-transport)

[RaSCSI HD images](https://macintoshgarden.org/apps/rascsi-reloaded)

### OTTool
[RaSCSI wiki](https://github.com/akuker/RASCSI/wiki/Dayna-Port-SCSI-Link#ottool)


### TCP/IP Config 
Is located in the macintosh TCP/IP control panel

Select DHCP

![screenshot](img/tcpip1.png){:style="height:200px;width:300px"}
    
If you run into problems getting an address, a static IP might be required.  Remember to use an address outside your router's DHCP range. 192.168.3.242 or greater should work

![screenshot](img/tcpip2.jpg){:style="height:200px;width:400px"}

Test your internet connection with OTTool by pinging 8.8.8.8

![screenshot](img/tcpip3.jpg){:style="height:200px;width:400px"}