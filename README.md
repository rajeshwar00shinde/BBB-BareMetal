# Flashing steps
 
> Install the dsnmasq utility in linux and enable the service.
```
sudo apt install dnsmasq -y
```
> Copy the following configuration in `/etc/dnsmasq.conf`
```
port=0
interface=usb0 #or whatever interface you discover using ifconfig after plugging usb.
dhcp-range=192.168.0.50,192.168.0.150,12h
bootp-dynamic
enable-tftp
tftp-root=/srv/tftp
dhcp-boot=beagle.img
```

> Set the ip address of an interface.

```
ifconfig usb0 192.168.0.51
```

> Copy the compiled binary `beagle.img` in /srv/tfp/
> Restart dnsmasq.service
> Press and hold S2 switch of BBB and connect the USB power supply to PC.
> Verify the service is started successfully and BOOTP log exists 

```
systemctl status dnsmasq.service
sudo cat /var/log/syslog | grep dnsmasq | grep BOOTP
```
