# Ubuntu-Raspberry-Pi-4-secure-sysctl.conf

## About
This is my personal sysctl.conf file in Ubuntu Server 20.04 running on my Raspberry Pi4 secure Web/Email Server. It has been modified to increase security, add TCP BBR (which speeds up Ubunt's Network connection), and (if uncommented) disable IPv6 (for more security and less IPv6 problems). I use this on my secure Ubuntu Web/Email Server running on a Raspberry Pi 4 to secure it and speed up things using TCP BBR. You can use this and/or modify it too! Feel free to make a fork and update with even more secure settings if you want! 

#### Note:
In this configuration, IPv6 is still enabled (when it mostly should not be). You should disable it yourself in one of two ways:
1) Add `ipv6.disable=1` to the end of the first line in `/boot/firmware/cmdline.txt` (recommended)
or
2) Uncomment 
```
#net.ipv6.conf.all.disable_ipv6 = 1
#net.ipv6.conf.default.disable_ipv6 = 1
#net.ipv6.conf.lo.disable_ipv6 = 1
#net.ipv6.conf.eth0.disable_ipv6 = 1
#net.ipv6.conf.wlan0.disable_ipv6 = 1
```
in `/etc/sysctl.conf` (`sudo nano /etc/sysctl.conf` should open up your file to edit it).

## Install (on your Ubuntu 20.04 Server using a symlink)
```
sudo cp /etc/sysctl.conf /etc/sysctl.conf.orig && sudo git clone https://github.com/Danrancan/Ubuntu-Raspberry-Pi-4-secure-sysctl.conf.git /etc/ && sudo chown root:root /etc/Ubuntu-Raspberry-Pi-4-Secure-sysctl.conf/sysctl.conf && sudo ln -nsf /etc/Ubuntu-Raspberry-Pi-4-secure-sysctl.conf/sysctl.conf /etc/sysctl.conf && sudo sysctl -p
```
### Update (with the latest version on your Ubuntu 20.04 Server)
```
cd /etc/Ubuntu-Raspberry-Pi-4-secure-sysctl.conf/ && sudo git pull origin main && sudo chown root:root /etc/Ubuntu-Raspberry-Pi-4-Secure-sysctl.conf/sysctl.conf && sudo sysctl -p
```
### Uninstall and restore original (/etc/sysctl.conf.orig) configuration (on your Ubuntu 20.04 Server).
```
sudo rm /etc/sysctl.conf && sudo rm -r /etc/Ubuntu-Raspberry-Pi-4-secure-sysctl.conf && sudo mv /etc/sysctl.conf.bak /etc/sysctl.conf && sudo sysctl -p
```
