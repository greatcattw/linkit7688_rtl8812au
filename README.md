# openwrt_rtl8812au
Note : 
	Extracted from openwrt BSP. For studying package build.
	It needs to adjust 2 of Makefile.

WiFi dongle:
	rtl8812au

Openwrt Linux :
	5.4.154

Openwrt platform :
	mt7688 LinkIt Smart 7688

Driver version :
	v4.3.14_13455.20150212_BTCOEX20150128-51

//---make 891aau.ko
//---pacakge build
untar 
copy rtl8812au-ct/ to openrt/package/kernel
make openrt/package/kernel/rtl8812au-ct/compile V=s

rtl8812au.ko at 
	openwrt/staging_dir/target-mipsel_musl/root-ramips/lib/modules/5.4.154/

//---verify

#vi /etc/hostapd.conf                                           
interface=wlan2
driver=nl80211
ssid=greatcat7
hw_mode=g
channel=1
bridge=br-lan


hostapd -d -B /etc/hostapd.conf &

#PC Wifi find a AP named greatcat7
#PC login AP and get IP 192.168.1.x
