# Introduction to Raspberry Pi Sense HAT
This notebook is to learn Raspberry Pi Sense HAT. 

This notebook is created using a [Raspberry Pi 3 Model B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) and a [Sense HAT](https://www.raspberrypi.org/products/sense-hat/).
---

### Contents:
This notebook covers      
* Setting up Sense HAT   
* SenseHat Hello World   
* Using LED Matrix 
* Using environmental sensors: Temperature, Humidity, Atmospheric pressure   
* Generating a temperature graph  
* Using IMU Sensor: Magnetometer, Gyroscope, Accelerometer   
* Using Joystick  

---

### Run Jupyter Notebook on Raspberry Pi 

* **Local resource** (Raspberry Pi) and use locally
  Within Terminal Window: ```Pi:~ $ jupyter-notebook```

* **Remote resource** (running locally on Raspberry Pi) but accessed from a remote machine
    
    * on remote machine logged into the Raspberry Pi: 

     ```Pi:~ $ jupyter notebook --no-browser --port=8889```    
      
  Then it will print *_The Jupyter Notebook is running at: http://localhost:8889 /?token=c8ea02070...._* [Please note **c8ea02070** is specific to this example and your value will be different]
      
    * in a second remote terminal of your remote machine logged into the Raspberry Pi: 

  ```Pi:~ $ ssh -L 8889:localhost:8889 pi@<IP address>```      
  
     Then copy and paste http://localhost:8889/?token=c8ea02070.... to your local browser.
     
     


* To use Jupyter Notebooks on local machine, it is easy to use with [Anaconda Cloud](https://anaconda.org) package. 
   This is the [Download link](https://www.anaconda.com/download/#macos) for Anaconda.
