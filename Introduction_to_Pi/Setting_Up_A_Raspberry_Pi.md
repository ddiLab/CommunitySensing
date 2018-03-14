# [Raspberry Pi](https://www.raspberrypi.org)
* A small and affordable computer that can be used to learn programming through fun and practical projects
* Raspberry Pi has [different models and accessories](https://www.raspberrypi.org/products/)
* There are many available [resources for Raspberry Pi](https://www.raspberrypi.org) such as [blog](https://www.raspberrypi.org/blog/), [community](https://www.raspberrypi.org/community/),  [forums](https://www.raspberrypi.org/forums/) and [projects](https://www.raspberrypi.org/forums/)
* [Raspberry Pi GitHub](https://github.com/raspberrypi)
* Raspberry Pi is developed in the United Kingdom by the [Raspberry Pi Foundation](https://en.wikipedia.org/wiki/Raspberry_Pi_Foundation) to promote the teaching of basic computer science in schools and in developing countries.

<img src='https://www.raspberrypi.org/app/uploads/2017/05/Raspberry-Pi-2-1-1621x1080.jpg' style='width: 500px;' > 

### <div style="text-align: center">[Raspberry Pi 3 Model B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) </div>
<div style="text-align: center"> Third-generation Raspberry Pi </div>
<div style="text-align: center"> [Single-board computer](https://www.raspberrypi.org/documentation/hardware/raspberrypi/schematics/Raspberry-Pi-3B-V1.2-Schematics.pdf) with wireless LAN and Bluetooth connectivity</div>

# Raspberry Pi Set Up 
**Material adapted from: [Raspberry Pi Documentation](https://www.raspberrypi.org/documentation/).**

### What you will need 
* Raspberry Pi 
* Monitor or TV
* HDMI cable 
* USB keyboard
* USB mouse
* Power supply
* 8GB SD card    
 * The original Raspberry Pi Model A and Raspberry Pi Model B require full-size SD cards.   
 * The newer Raspberry Pi Model A+, Raspberry Pi Model B+, Raspberry Pi 2 Model B, Raspberry Pi Zero, and Raspberry Pi 3 Model B require micro SD cards.

### Let's get started 

#### Option 1 : Buy A Pre-Installed SD Card 
There are pre-installed SD cards with operating system for Raspberry Pi.

#### Option 2 : Set Up Your Own [SD Card](https://www.raspberrypi.org/documentation/installation/sd-cards.md)
* Format SD Card which is 8GB or larger as FAT 
* Download [NOOBS Zip file](https://www.raspberrypi.org/downloads/noobs/) - New Out Of the Box Software     
NOOBS is an easy operating system installer which contains [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) and other operating system.     
You can download the [operating systems](https://www.raspberrypi.org/downloads) for Raspberry Pi directly as well.
* Extract the NOOBS files from the zip 
* Drag all the files in the extracted NOOBS folder and drop them onto the formatted SD card
* The necessary files will be transferred to SD card 
* Safely remove the SD card and insert it into Raspberry Pi

### After having a pre-installed SD card or setting up your own SD card
### Plug in Raspberry Pi 
* Slot the SD card into the SD card slot on Raspberry Pi 
* Plug the USB keyboard and mouse into the USB slots on Raspberry Pi 
* Connect HDMI cable from Raspberry Pi to monitor 
* Make sure that monitor is turned on and the right input is selected (e.g. HDMI 1, DVI, etc.).
* Plug in the micro USB power supply 
* Then the action will turn on and boot the Raspberry Pi

### First time power on using NOOBS 
* The monitor will be started after the previous steps
* Select an operating system and let it install on Raspberry Pi
* Raspbian is selected for the rest of the tutorial
 
### NOOBS is not working???
* You formatted your SD card correctly and followed all the steps.    
And you turn your Raspberry Pi on, the power light turns on but nothing else happens?   
* Nothing is displayed on your monitor? 

####  Solution
* Take out the SD card and add a file on the disk called config.txt
* Add the following line of code in ```config.txt```
> ```hdmi_edid_file=1```

# Remote-Access 
**SSH (Secure Shell) to Raspberry Pi**

### Make sure that Raspberry Pi is connected to local network or Wifi
* If you are using Wifi, 
  * You can set Wifi when you were first installing Raspbian using NOOBS    
  **... Or ...**   
  * You can also set it later, following [these steps](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md) ....
     
     
* If you are not using Wifi, plug the Raspberry Pi directly into the router

### Get IP address
* On terminal: ```Pi:~ $ if config```    
This will display information about the current network status including the IP address
* On terminal: ```Pi:~ $ hostname -I ```    
This will display the IP addresses associated with the Raspberry Pi    

### Enable SSH
* On terminal: ```Pi:~ $ sudo raspi-config```
* Select ```5 Interfacing Options```
* Navigate and select ```SSH```
* Choose ```Yes```
* Select ```OK```   
**... Or ...**    
* Go to ```Preferences``` menu and click ``` Raspberry Pi Configuration ```
* Choose ```Interfaces```tab
* Select ``` Enabled ``` next to SSH
* Click ```Ok```

### Use SSH to connect to Raspberry Pi 
* To connect to Raspberry Pi from a different computer remotely,    
  On remote terminal: ```Pi:~ $ ssh pi@<IP address> ``` 
* Replace ```<IP address>``` with the IP address of the Raspberry Pi 
* If there's ```Connection timed out``` error, it is likely because of the wrong IP address  
> * Raspberry Pi's default user name: ```pi```    
  Raspberry Pi's default password : ```raspberry```
  
# Change Raspberry Pi password

* On terminal: ```Pi:~ $  passwd```
* Then, type current password and new password 
* If password is changed correctly, there will be a success message: ```passwd: password updated successfully```

# Create a new user 
* On terminal: ```Pi:~ $ sudo adduser user_name```
* Type new password for new user and fill the information
* If process works correctly, there will be a confirmation :  ```Is the information correct?```

# Add new sudoers
* By default, sudoer is only: pi 
* On terminal: ```Pi:~ $  sudo visudo ```
* In the file, copy  ```root    ALL=(ALL:ALL) ALL```  under # User privilege specification 
* Paste the code under it, and change  ```root```  to  ```user_name```  of a new sudoer

> For example:    

```   
# User privilege specification   
root    ALL=(ALL:ALL) ALL   
user_name   ALL=(ALL:ALL) ALL 
``` 


# Delete a user
* On terminal: 

```
Pi:~ $sudo userdel -r user_name
```

# Time and date

* On terminal: 
* ```
* Pi:~ $ sudo raspi-config
* ```   

Select ```4 Localisation Options```

Select ```I2 Change Timezone```   

Select your ```country``` and your ```the nearest city``` to set up local timezone  

Select ```Finish```

Within Terminal Window: ```Pi:~ $ sudo reboot```

Within Terminal Window: ```Pi:~ $ date``` to check the current date and time

# Install Jupyter Notebook & other packages

**Material adapted from: [Install Jupyter Notebook on Pi](http://www.instructables.com/id/Jupyter-Notebook-on-Raspberry-Pi/)**

Install matplotlib package for python3
Within Terminal Window: ```Pi:~ $ sudo apt-get install python3-matplotlib```

Install scipy package for python3
Within Terminal Window: ```Pi:~ $ sudo apt-get install python3-scipy```

Upgrade pip command
Within Terminal Window: ```Pi:~ $ sudo pip3 install --upgrade pip```

Install jupyter notebook using pip3
Within Terminal Window: ```Pi:~ $ sudo pip3 install jupyter```

Clean up the software packages 
Within Terminal Window: ```Pi:~ $ sudo apt-get clean```

Reboot the Raspberry Pi 
Within Terminal Window: ```Pi:~ $sudo reboot```
 
 
### Run Jupyter Notebook on Raspberry Pi 

Local resource (Raspberry Pi) and use locally
Within Terminal Window: ```Pi:~ $ jupyter-notebook```

Remote resource (running locally on Raspberry Pi) but accessed from a remote machine
    
* on remote machine logged into the Raspberry Pi: 

    ```Pi:~ $ jupyter notebook --no-browser --port=8889```    
      
Then it will print *_The Jupyter Notebook is running at: http://localhost:8889 /?token=c8ea02070...._* [Please note **c8ea02070** is specific to this example and your value will be different]
      
* in a second remote terminal of your remote machine logged into the Raspberry Pi: 

```Pi:~ $ ssh -L 8889:localhost:8889 pi@<IP address>```    
      
Then copy and paste http://localhost:8889/?token=c8ea02070.... to your local browser
      
# Raspberry Pi Camera

<img src='https://www.raspberrypi.org/app/uploads/2017/05/Pi-Camera-hero-1-1394x1080.jpg' >
### <div style="text-align: center">Camera Module V2</div>   

### Raspberry Pi camera resources  
- [Camera Set Up](https://www.raspberrypi.org/documentation/usage/camera/)  
- [Raspberry Pi camera module](https://www.raspberrypi.org/documentation/raspbian/applications/camera.md)   
- [Picamera python package](http://picamera.readthedocs.io/en/release-1.13/)  
- [Picamera Github](https://github.com/waveform80/picamera)  

# Raspberry Pi camera set up 

### Set up the camera hardware
* Insert the camera cable into the Raspberry Pi.    
  The cable slots is between the Ethernet and HDMI ports. 
 
<img src='https://i.ytimg.com/vi/4vAz0eRXyWQ/maxresdefault.jpg' style='width: 400px;' >
### <div style="text-align: center">Raspberry Pi Camera Setup </div>   
 
* On terminal: ```Pi:~ $ sudo apt-get update```
* On terminal: ```Pi:~ $ sudo apt-get upgrade```
* On terminal: ```Pi:~ $ sudo raspi-config```
	* Navigate to 5 Interfacing Options 
	* Navigate to P1 Camera and Enter yes to enable Camera
* Then reboot the Raspberry Pi 
* To test the Camera system => On terminal: ```Pi:~ $ raspistill -v -o test.jpg  ```

# Taking a photo

This material was adapted from the documentation found at [Python PICamera](https://www.raspberrypi.org/documentation/usage/camera/python/README.md).

```python
# Import picamera package and required libraries
from picamera import PiCamera
from time import sleep

# Start the PiCamera
camera = PiCamera()

# Display the camera preview
camera.start_preview()

# Keep the camera preview for 3 seconds
sleep(3)

# Take the photo
camera.capture('/home/pi/Desktop/my_first_photo_with_Pi.jpg')

# Close the preview
camera.stop_preview()

# Turn off the camera to release the resources
camera.close()

# You can keep using the previous camera that you started; to start a new camera with a different name, it is required to close the previous camera.
# Only one camera open at a time.
```

# Recording a video

```python
# Import required libraries
from picamera import PiCamera
from time import sleep

# Start a new camera: vicamera
vicamera = PiCamera()

# Display the vicamera preview
vicamera.start_preview()

# Start the video recording
vicamera.start_recording('/home/pi/Desktop/my_first_video_with_Pi.h264')

# Take the video record for 10 seconds
sleep(10)

# Stop the video recording
vicamera.stop_recording()

# Close the vicamera preview
vicamera.stop_preview()

# Turn of the vicamera
vicamera.close()
```

### Watching the video
On terminal : ```Pi:~ $ omxplayer Desktop/my_frist_video_with_Pi.h264 ```    

This will play the video on the Raspberry Pi monitor.    

The video may play at a faster speed because of [omxplayer](https://www.raspberrypi.org/documentation/raspbian/applications/omxplayer.md)'s fast frame rate.

# Shut down the Raspberry Pi

If you just pull the plug to turn off the power, this can cause problems with the SD card and file system.      
And the mess on the memory card will not be cleaned up regularly. 

To shut down the Raspberry Pi properly,    

* On terminal: ```Pi:~ $ sudo shutdown -h now```   

**... Or ...**

* On terminal: ```Pi:~ $ sudo halt  ```    

**... Or ...** 

* On terminal: ```Pi:~ $ sudo poweroff ```   

These commands will shutdown the Raspberry Pi.    
Wait until the blinking or flickering light stops, and turn off the power supply.
