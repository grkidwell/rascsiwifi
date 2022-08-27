# Install Raspberry PI OS image 
on an SD card or USB flash drive 



Follow [Getting Started](https://www.raspberrypi.com/documentation/computers/getting-started.html) instructions on official raspberrypi.com website

Strongly recommend using the Raspberry PI Imager and selecting
"Raspberry Pi OS Lite (32-bit)"


![Screenshot](img/raspios1.png){:style="height:200px;width:300px"}

select "Raspberry Pi OS (other)"

![Screenshot](img/raspios2.png){:style="height:200px;width:300px"}

select "Raspberry Pi OS Lite (32-bit)"

![Screenshot](img/raspios3.png){:style="height:200px;width:300px"}





    
## Launch Raspi-Config
from raspberry pi terminal
#
    pi@raspberrypi:~$ sudo raspi-config
   

![Screenshot](img/raspios4.png){:style="height:200px;width:300px"}

## System Options
you may want to change Password and Hostname

![Screenshot](img/raspios5.png){:style="height:200px;width:300px"}

## Interface Options
enable SSH for remote access

![Screenshot](img/raspios6.png){:style="height:200px;width:300px"}

## Localization Options
![Screenshot](img/raspios7.png){:style="height:200px;width:300px"}
#
Under Locale, use spacebar to deselect "en_GB.UTF-8 UTF-8"

![Screenshot](img/raspios8.png){:style="height:200px;width:300px"}

and select "en_US.UTF-8 UTF-8 

![Screenshot](img/raspios9.png){:style="height:200px;width:300px"}

none

![Screenshot](img/raspios10.png){:style="height:200px;width:300px"}

Timezone

![Screenshot](img/raspios11.png){:style="height:200px;width:300px"}

US

![Screenshot](img/raspios12.png){:style="height:200px;width:300px"}

As we are favored enough to live in the The Republic of Texas

![Screenshot](img/raspios13.png){:style="height:200px;width:300px"}

Keyboard

![Screenshot](img/raspios14.png){:style="height:200px;width:300px"}

Generic 105-key PC (intl.)

![Screenshot](img/raspios15.png){:style="height:200px;width:300px"}

Other

![Screenshot](img/raspios16.png){:style="height:200px;width:300px"}

English (US)

![Screenshot](img/raspios17.png){:style="height:200px;width:300px"}

Scroll up to English (US)

![Screenshot](img/raspios18.png){:style="height:200px;width:300px"}

Default "Enter" the 2 screens then Finish

![Screenshot](img/raspios19.png){:style="height:200px;width:300px"}
## Remote ssh login 
from PC terminal you can now remote login to your rascsi
##
    alex@xanadu_pc:~$ ssh pi@rascsi.local
    pi@rascsi:~$ 

## Update and Upgrade
##
    sudo apt update
    sudo apt upgrade