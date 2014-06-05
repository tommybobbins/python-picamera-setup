# Python Picamera Setup

A camera workshop written by [Dave Jones](https://github.com/waveform80) (author of `python-picamera`), with some example projects.

## Workshop

This workshop guides you through setting up the Raspberry Pi camera module, taking pictures and video using the Python `picamera` module, connecting a physical button with the GPIO (General Purpose Input Output) pins and programming it to control the camera.

### Connecting the camera

1. Locate the camera port next to the ethernet port
2. Lift the tab on the top
3. Place the strip in the connector (blue side facing the ethernet port)
4. While holding the strip in place, push down the tab
    
    ![](../attach_cameraboard.jpg)

### Activate the camera

1. Connect a USB cable to the power
2. Login with username `pi` and password `raspberry`
3. At the command prompt enter `sudo raspi-config`
4. At the menu, navigate to `Enable Camera`
5. Select `Enable`
6. Select `Finish`
7. Select `Yes` to reboot

### Test the camera

1. Login again with username `pi` and password `raspberry`
2. At the command prompt enter `raspistill -o image.jpg`
3. On the screen you should see a preview appear for a few seconds, and then change briefly while the image is captured


## Licence

Unless otherwise specified, everything in this repository is covered by the following licence:

![Creative Commons License](http://i.creativecommons.org/l/by-sa/4.0/88x31.png)

***Python Picamera Setup*** by [Dave Jones](https://github.com/waveform80) and the [Raspberry Pi Foundation](http://raspberrypi.org) is licenced under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

Based on a work at https://github.com/raspberrypilearning/python-picamera-setup
