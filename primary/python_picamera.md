### Camera programming: capture an image
This has already been done for you:

Start by installing the Python `picamera` and GPIO library packages:

```
sudo apt-get install python-picamera python3-picamera python-rpi.gpio
```

1. At the command prompt enter `startx` to start the graphical desktop environment
2. Double click on `LXTerminal` to start a command line, and enter `sudo idle &` to start the Python environment
3. Select `File > Open > Recent Files > camera.py` from the menu to start a text editor
4. You should see the following code (case is important!):

```
#!/usr/bin/python
#####################################################
#### We might need to the program to go to sleep
from time import sleep
#### We need to use python picamera
import picamera
with picamera.PiCamera() as camera:
    camera.start_preview()
    sleep(5)
    camera.capture('/home/pi/Desktop/image.jpg')
    camera.stop_preview()
```

5. Select `Run > Run Module` from the menu (or just press `F5`) to run the script

### Camera programming: capture when activated
    
1. Connect the Pi to the button as shown in the diagram below:

    ![](../picamera-gpio-setup_tng.png)


2. At the command prompt enter `startx` to start the graphical desktop environment
3. Double click on `LXTerminal` to start a command line, and enter `sudo idle &` to start the Python environment
4. Select `File > Open > Recent Files > camera_gpio.py` from the menu to start a text editor
```
#!/usr/bin/python
#####################################################
#### We might need to the program to go to sleep
from time import sleep
#####################################################
#### We need to use the Input pins
import RPi.GPIO as GPIO
prev_state = "unknown"
GPIO.setmode(GPIO.BCM)
GPIO.setup(24, GPIO.IN, pull_up_down=GPIO.PUD_UP)
#####################################################
#### We need to use python picamera
import picamera

# This is called an infinite loop. Repeats forever###
while True:
     if GPIO.input(24):
         print ("Button is not pressed")
         sleep(1)
     else:
         print ("Button is pressed")
         with picamera.PiCamera() as camera:
             camera.start_preview()
             sleep(5)
             camera.capture('/home/pi/Desktop/image.jpg')
             camera.stop_preview()

# Clean up afterwards
GPIO.cleanup()
exit();
    ```

3. Delete `image.jpg` from the desktop
4. Save and run your script
5. Once the script has started, press the button connected to your Pi to capture an image

## Licence

Unless otherwise specified, everything in this repository is covered by the following licence:

![Creative Commons License](http://i.creativecommons.org/l/by-sa/4.0/88x31.png)

***Python Picamera Setup*** by [Dave Jones](https://github.com/waveform80) and the [Raspberry Pi Foundation](http://raspberrypi.org) is licenced under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

Based on a work at https://github.com/raspberrypilearning/python-picamera-setup
