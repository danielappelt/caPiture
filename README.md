# caPiture
Headless multitrack audio recording for your Raspberry Pi.

capPiture uses [jack_capture](https://github.com/kmatheussen/jack_capture) to headlessly multitrack record the input of the [Behringer XR18 Mixer](http://www.musictribe.com/Categories/Behringer/Mixers/Digital/XR18/p/P0BI8). For now, it is hardcoded to work with the XR18. If you want to use it with another audio interface, please modify the startcapiture script accordingly.

From another computer
- Download the latest version of [Raspbian Lite](https://raspberrypi.org/downloads/raspbian) and install it to an SD card (bigger is better). For Linux users, the command is:
```bash
sudo dd bs=4M if=nameoftheimage of=/dev/yoursdcard status=progress conv=fsync
```
- Once the image is on the SD card, copy the bin folder containing the caPiture scripts to /home/pi/

On the Raspberry Pi
- In raspi-config set the Rpi to autologin in console mode
- Run these two commands :
```bash
sudo apt install --no-install-recommends jackd2 jack_capture dbus-x11
echo "startcapiture" >> /home/pi/.profile
```

GPIO
- Connect GPIO 18 to the + leg of an LED with a 330 Ohm resistor in between, other leg to gnd
- Attach buttons to GPIO 3 and 4. 3 starts and stops recording, 4 deletes the last recording. 3+4 powers off the Rpi.
