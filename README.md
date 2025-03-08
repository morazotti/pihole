# pihole
Ad and adult content blocking lists for PiHole

## Setting up hardware:

* Raspberry Pie Zero (not W):  https://www.amazon.com/gp/product/B01L3IU6XS
* MicroSD card (>=16Gb): https://www.amazon.com/gp/product/B07NW48JWP
* Micro-USB Ethernet Adapter:  https://www.amazon.com/gp/product/B01AT4C3KQ
* FLIRC Case:  https://www.amazon.com/gp/product/B08837L144
* Power Supply:  https://www.amazon.com/gp/product/B071YD8JLM

## Create standard "minimal" RaspberryOS image on microSD card:

https://ubuntu.com/blog/how-to-install-ubuntu-with-the-new-raspberry-pi-imager

## Files to modify (on image microSD card):

/boot/config.txt  (networking, overclocking, HDMI video resolution 1024x600)
/boot/cmdline.txt (networking)
/boot/ssh (can be empty file, but if exists will create ssh server)
/etc/dhcpcd.conf

## Default SSH/Login credentials:

ssh command:  ssh pi@raspberrypi.local (or 192.168.0.10 static IP in config)
username:  pi
password:  raspberry

## pihole install command:

curl -sSL https://install.pi-hole.net | bash
(follow prompts to set eth0 interface, servers, ip, etc.)
Only select the first of the two ad lists (it's the only one that works)

## Browse to pihole admn site

http://192.168.0.10/admin  (or address you chose)

Almost everything can be done here in this web UI.
Go to Group Management | Adlists, and add the following to block nasty porn:

https://raw.githubusercontent.com/jeffgrover/pihole/master/parent_hosts
or https://nsfw.oisd.nl


## Re-configure the router to use your pihole as DNS for DHCP clients

You may have to enter the same IP address for both primary and secondary,
because it needs to NOT fail-over to some other DNS server (or it won't block)
