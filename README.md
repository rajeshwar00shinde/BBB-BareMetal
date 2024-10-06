# Flashing steps
 
> Install the dsnmasq utility in linux and enable the service.
> Copy the following configuration in `/etc/dnsmasq.conf`
```
port=0
interface=usb0
dhcp-range=192.168.0.50,192.168.0.150,12h
bootp-dynamic
enable-tftp
tftp-root=/srv/tftp
dhcp-boot=beagle.img
```
> Copy the compiled binary `beagle.img` in /srv/tfp/
> Restart dnsmasq.service
> Press and hold S2 switch of BBB and connect the USB power supply to PC.
> Verify the service is started successfully and BOOTP log exists 
```
systemctl status dnsmasq.service
sudo cat /var/log/syslog | grep dnsmasq | grep BOOTP
```
