# SD Card

## Download Noobs

https://www.raspberrypi.org/downloads/noobs/

Takes >26 min

## Format SD card with Disk Utility

https://www.raspberrypi.org/learning/noobs-install/elcapitan/

MS-DOS (FAT) 

## Copy FIles

Drag all files from the NOOBS folder onto the sd card


## Connecting

Hostnames:

* raspberrypi.local 
* raspberrypi.

change

recovery.cmdline



	runinstaller quiet ramdisk_size=32768 root=/dev/ram0 init=/init vt.cur_default=1 elevator=deadline
	silentinstall runinstaller quiet ramdisk_size=32768 root=/dev/ram0 init=/init vt.cur_default=1 elevator=deadline
	

Connect the cable
	
You will see the activity LEDs flash while the OS installs.  Depending on your SD-Card this can take up to 40-60 minutes.

## Update

	sudo apt-get upgrade
	sudo apt-get update
	sudo apt-get install emacs

	curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash
	
add to ~/.bash_profile	
	
	export PATH="/home/pi/.pyenv/bin:$PATH"
	eval "$(pyenv init -)"
	eval "$(pyenv virtualenv-init -)"

source 


## VLC on OSX

* [https://www.raspberrypi.org/learning/getting-started-with-picamera/worksheet/](https://www.raspberrypi.org/learning/getting-started-with-picamera/worksheet/)
* [http://www.videolan.org/vlc/index.en_GB.html](http://www.videolan.org/vlc/index.en_GB.html)
* [http://get.videolan.org/vlc/2.2.6/macosx/vlc-2.2.6.dmg](http://get.videolan.org/vlc/2.2.6/macosx/vlc-2.2.6.dmg)
* [http://www.mybigideas.co.uk/RPi/RPiCamera/](http://www.mybigideas.co.uk/RPi/RPiCamera/)
* 
## Camera on Pi

	sudo apt-get install vlc

* [https://www.hackster.io/bestd25/pi-car-016e66](https://www.hackster.io/bestd25/pi-car-016e66)

## STreaming video

* [https://blog.miguelgrinberg.com/post/stream-video-from-the-raspberry-pi-camera-to-web-browsers-even-on-ios-and-android](https://blog.miguelgrinberg.com/post/stream-video-from-the-raspberry-pi-camera-to-web-browsers-even-on-ios-and-android)

# Linux commandline

* [http://www.computerworld.com/article/2598082/linux/linux-linux-command-line-cheat-sheet.html](http://www.computerworld.com/article/2598082/linux/linux-linux-command-line-cheat-sheet.html)



# Setup

	mkdir github
  	cd github
  	git clone https://github.com/cloudmesh/cloudmesh.robot.git
  	ssh-keygen
  	sudo apt-get install -y emacs
	sudo apt-get install -y cmake
	sudo apt-get install -y libqt4-dev
  	git config --global user.name "Gregor von Laszewski"
  	git config --global user.email laszewski@gmail.com
  	git config --global core.editor emacs
	git config --global push.default matching

# Enable SPI

go to the configuration interfaces and enable
   
# RTIMUlib2

  git clone https://github.com/RTIMULib/RTIMULib2.git
  cd RTIMULib

Add the following two lines to /etc/modules

	i2c-bcm2708
	i2c-dev

reboot

	ls /dev/i2c-*
	sudo apt-get install i2c-tools

	sudo i2cdetect -y 1
     	     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
	00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
	10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
	20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
	30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
	40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
	50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
	60: -- -- -- -- -- -- -- -- 68 -- -- -- -- -- -- -- 
	70: -- -- -- -- -- -- -- --

![Pinout](images/rasp3.png)

create a file /etc/udev/rules.d/90-i2c.rules and add the line:

    KERNEL=="i2c-[0-7]",MODE="0666"

note: does not work

instead we do

    sudo chmod 666 /dev/i2c-1 


Set the I2C bus speed to 400KHz by adding to /boot/config.txt:

    dtparam=i2c1_baudrate=400000

reboot


   cd /home/pi/github/RTIMULib2/RTIMULib/IMUDrivers
   emacs RTIMUDefs.h

Change

#define MPU9250_ID 0x71

To

#define MPU9250_ID 0x73



	cd /home/pi/github/RTIMULib2/RTIMULib

	mkdir build
	cd build
	cmake ..
	make -j4
	sudo make install
	sudo ldconfig

## compile RTIMULib Apps

   cd /home/pi/github/RTIMULib2/Linux/RTIMULibCal
   make clean; make -j4
   sudo make install
   cd /home/pi/github/RTIMULib2/Linux/RTIMULibDrive
   make clean; make -j4
   sudo make install
   cd /home/pi/github/RTIMULib2/Linux/RTIMULibDrive10
   make clean; make -j4
   sudo make install
   cd /home/pi/github/RTIMULib2/Linux/RTIMULibDrive11
   make clean; make -j4
   sudo make install


   cd /home/pi/github/RTIMULib2/Linux/RTIMULibDemo    
   qmake clean
   make clean
   qmake
   make -j4
   sudo make install
   cd /home/pi/github/RTIMULib2/Linux/RTIMULibDemoGL
   qmake clean
   make clean
   qmake
   make -j4
   sudo make install



## Camera

* [Camera Tutorial](https://www.raspberrypi.org/learning/getting-started-with-picamera/worksheet/)


# Lessons and projects

*[Gui](https://www.raspberrypi.org/learning/getting-started-with-guis/worksheet/)
*[Solder](https://www.raspberrypi.org/learning/getting-started-with-guis/)
*[PI Camera Line Follower](https://www.raspberrypi.org/blog/an-image-processing-robot-for-robocup-junior/)
* [Pi car flask](https://circuitdigest.com/microcontroller-projects/web-controlled-raspberry-pi-surveillance-robot)