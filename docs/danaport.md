## Mount Danaport
using commandline
#

    sudo rasctl -i 5 -c attach -t scdp -f eth0:192.168.3.0/24


# Verify ~/.config/rascsi/default.json file

    {
        "version": "22.7.2",
        "devices": [
            {
                "id": 4,
                "unit": 0,
                "device_type": "SCDP",
                "image": null,
                "params": {
                    "inet": "192.168.3.0/24",
                    "interface": "eth0"
                },
                "vendor": "Dayna",
                "product": "SCSI/Link",
                "revision": "1.4a",
                "block_size": null,
                "size": 0
            },
            {
                "id": 6,
                "unit": 0,
                "device_type": "SCHD",
                "image": "/home/pi/images/HD0-OpenRetroSCSI-7.5.3.hda",
                "params": {},
                "vendor": "QUANTUM",
                "product": "FIREBALL",
                "revision": "2207",
                "block_size": 512,
                "size": 524288000
            }
        ],
        "reserved_ids": [
            {
                "id": "7",
                "memo": ""
            }
        ]
    }

