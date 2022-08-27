# RaSCSI Install
###

Follow the RASCSI [setup instructions](https://github.com/akuker/RASCSI/wiki/Setup-Instructions) 
and ./easyinstall.sh.  The steps are copied below:

### Perform updates and add libraries

    sudo apt-get update && sudo apt-get install git libspdlog-dev protobuf-compiler libpcap-dev

### Clone the rascsi repository

    cd ~  
    git clone https://github.com/akuker/RASCSI.git  

### Perform easy install for a Full Spec board

    cd ~/RASCSI
    ./easyinstall.sh

### Or, if you have a __STANDARD__ board

    cd ~/RASCSI
    ./easyinstall.sh -c=STANDARD

### Choose "1" to install or update RaSCSI Service + Web Interface

    Choose among the following options:
    INSTALL/UPDATE RASCSI (FULLSPEC version)
    1) install or update RaSCSI Service + Web Interface
    2) install or update RaSCSI Service
    3) install or update RaSCSI OLED Screen (requires hardware)
    CREATE HFS FORMATTED (MAC) IMAGE WITH LIDO DRIVERS
    ** For the Mac Plus, it's better to create an image through the Web Interface **
    4) 600MB drive (suggested size)
    5) custom drive size (up to 4000MB)
    NETWORK BRIDGE ASSISTANT
    6) configure network bridge for Ethernet (DHCP)
    7) configure network bridge for WiFi (static IP + NAT)
    INSTALL COMPANION APPS
    8) install AppleShare File Server (Netatalk)
    9) install Web Proxy Server (Macproxy)
    ADVANCED OPTIONS
    10) compile and install RaSCSI stand-alone
    11) configure the RaSCSI Web Interface stand-alone
    EXPERIMENTAL FEATURES
    12) install or update RaSCSI Control Board UI (requires hardware)
    Enter your choice (0-12) or CTRL-C to exit: 1

### Restart the syslog and configure systemd to start RaSCSI at boot

    sudo systemctl restart rsyslog
    sudo systemctl enable rascsi # optional - start rascsi at boot
    sudo systemctl start rascsi
    sudo systemctl status rascsi