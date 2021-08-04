sudo systemctl status rc-local

sudo systemctl enable rc-local

#Create rc-local unit file
sudo vim /etc/systemd/system/rc-local.service

[Unit]
Description=/etc/rc.local Compatibility
ConditionPathExists=/etc/rc.local

[Service]
Type=forking
ExecStart=/etc/rc.local start
TimeoutSec=0
StandardOutput=tty
RemainAfterExit=yes
SysVStartPriority=99

[Install]
WantedBy=multi-user.target


#Create a rc.local script file
sudo vim /etc/rc.local

#!/bin/bash
exit 0

#Give executible permission
sudo chmod +x /etc/rc.local

sudo systemctl enable rc-local

sudo systemctl start rc-local.service

sudo systemctl status rc-local.service

#Edit rc.local script file
sudo vim /etc/rc.local

#!/bin/bash

pulseaudio -kill

exit 0

#Restart
sudo shutdown -r now

#Static sound should be gone
