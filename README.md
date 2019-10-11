#developer
+82 10-6282-3838
#env
ubuntu 18.04

#solution1
#install bluetooth packages
sudo apt-get install bluetooth bluez bluez-tools rfkill -y
#check the Bluetooth env
sudo rfkill list
#unblock bluetooth
sudo rfkill unblock bluetooth
#install blueman
sudo apt-get install blueman -y

#find bluetooth
blueman-manager

#solution2
#url: http://www.hardcopyworld.com/gnuboard5/bbs/board.php?bo_table=lecture_rpi&wr_id=100
#install bluetooth packages
sudo apt-get install bluez libbluetooth-dev
#add serial port
sudo sdpool add SP
#start bluetooth service
sudo vi /lib/systemd/system/bluetooth.service
ExecStart=/usr/lib/bluetooth/bluetoothd -C
sudo systemctl daemon-reload
sudo systemctl restart bluetooth
sudo systemctl enable bluetooth
#install module
sudo pip install pybluez pybleno
#search BT-devices
sudo bluetoothctl
scan on ~ scan off
#pair and connection
agent NoInputNoOutput
pair MAC-ADDR
connect MAC-ADDR
disconnect MAC-ADDR

#solution2 troubleshooting
1. org.bluez.Error.Authenticationfailed
https://github.com/blueman-project/blueman/issues/677
2. https://stackoverflow.com/questions/23985163/python3-error-no-module-named-bluetooth-on-linux-mint
