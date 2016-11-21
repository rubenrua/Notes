# Internet of Things (IoT)

## Arduino

 * https://www.arduino.cc/
 * http://escornabot.com/web/


## RaspberryPi

 * https://www.raspberrypi.org/

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
