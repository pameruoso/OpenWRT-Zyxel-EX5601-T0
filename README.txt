Porting EX5601-T0 into Openwrt

In this repo I've been preparing DTS and DTSI files to be able to run clean Openwrt builds on the EX5601-T0 router


Working functionalities
1. 3 gbit lan ports
2. Wifi
3. Zyxel partitioning for Zloader 
4. WAN SFP port (only after starting zyxel sfp_wan.sh script for exporting the gpio)
5. leds
6. reset button
7. serial interface
8. usb port
9. lan ethernet 2.5 gbit port
10. wan ethernet 2.5 gbit port

Not implemented
1. voip (missing drivers or proper zyxel platform software)


Useful scripts:
gen_zyfwinfo.sh: This script can be used to generate a valid zyfwinfo file for flashing openwrt firmwares with Zloader (zyxel proprietary boot loader)

Zyfwinfo file usage:
1. Download the sysupgrade.bin from the Openwrt firmware selector or build your own via source code.
2. In the same folder as the sysupgrade.bin file create a new directory with the following name: "sysupgrade-zyxel_ex5601-t0-stock"
3. Put the generated zyfwinfo file into the "sysupgrade-zyxel_ex5601-t0-stock" directory
4. Run the following command in the folder where the sysupgrade.bin file has been downloaded
"tar -rf sysupgrade.bin sysupgrade-zyxel_ex5601-t0-stock/"

sfp_wan.sh : this script exports pin 57 and 10 and swaps automatically between an sfp and the ethernet port on the router. Place the script into /bin and give execute permissions.

zy_sfp_init.sh: init script to be placed into /etc/init.d. this script will automatically start sfp_wan.sh at boot.
