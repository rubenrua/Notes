# Internet of Things (IoT)

## Arduino

 * https://www.arduino.cc/
 * http://escornabot.com/web/


## RaspberryPi

 * https://www.raspberrypi.org/
 * https://www.jeffgeerling.com/

### SSH

https://www.raspberrypi.org/documentation/remote-access/ssh/

For headless setup, SSH can be enabled by placing a file named ssh, without any extension, onto the boot partition of the SD card from another computer

### Setting up Pi Zero OTG

https://blog.gbaman.info/?tag=g_ether

 - Add to the bottom of the `config.txt` file dtoverlay=dwc2 on a new line
 - Insert modules-load=dwc2,g_ether after rootwait in `cmdline.txt`
 - Wait 90s and `ssh pi@raspberrypi.local` (debug with avahi-browse -art)

## Chip

 * https://getchip.com/pages/chip
 * http://docs.getchip.com/chip.html
 * https://github.com/NextThingCo

### WiFi Connection

http://docs.getchip.com/chip.html#wifi-connection

```
nmcli device wifi list
sudo nmcli device wifi connect 'NAME' password 'PASSWORD' ifname wlan0
nmcli device status
nmcli connection show --active
sudo route add default gw 192.168.1.1 wlan0
```

### Headless CHIP

http://docs.getchip.com/chip.html#headless-chip

```
screen /dev/tty.usbmodem2413 115200
```


## UDOO

 * http://www.udoo.org
 * http://www.udoo.org/tutorial/how-to-connect-udoos-camera-module/
 * http://www.udoo.org/docs-neo/Hardware_Reference/VADC_Analog_Camera.html

## ESP8266

 * TODO

## V4L2 M2M

https://bootlin.com/
https://static.sched.com/hosted_files/ossna2020/2b/2020-06%20ELCNA%20-%20Nicolas%20Dufresne.pdf
https://linux-sunxi.org/Table_of_Allwinner_based_boards

## OTHER

 * https://www.kickstarter.com/projects/onion/omega2-5-iot-computer-with-wi-fi-powered-by-linux?lang=es
 * https://www.amazon.com/Dash-Buttons/b?ie=UTF8&node=10667898011
 * https://www.hackster.io
 * https://aiyprojects.withgoogle.com/
 * https://hologram.io/introducing-the-developer-plan/
 * https://www.blinkstick.com
 * https://sonoff.tech
 * https://bootlin.com/
 * https://pikvm.org/ and https://mtlynch.io/tinypilot/
