# Why Kura?

We chose Eclipse Kura to manage the gateway components of our system. Kura helps us to manage data and also the sensors while it also supports data transfer to other components. Kura integrates with the open-source Kapua framework which is also a huge advantage. Our goal in this project was to experiment with these techniques and develop a scalable and manageable system for data collection. In the following we introduce our experience of using Kura in an open-source environment, namely on Rapsberry Pi gateways.


## Eclipse Kura Quick Start Guide on Raspberry Pi 3
 The emergence of an Internet of Thing (IoT) service gateway model running modern software stacks, operating on the edge of an IoT deployment as an aggregator and controller, has opened up the possibility of enabling enterprise level technologies to IoT gateways. Eclipse Kura is an Eclipse IoT project that provides a platform for building IoT gateways. It is a smart application container that enables remote management of such gateways and provides a wide range of APIs for allowing you to write and deploy your own IoT application. MoDeS3 team made this tutorial, because after we followed the [official tutorial](http://eclipse.github.io/kura/intro/raspberry-pi-quick-start.html), we got an *Error 500 The call failed on the server* message.


## Requirements

* Raspberry Pi 3 (or 2)
* Keyboard
* Mouse
* Internet connection
* 8GB SD card

## Steps

1. Download [Raspbian Stretch with desktop](https://www.raspberrypi.org/downloads/raspbian/) to your PC
2. UnZip the downloaded file
3. Format your SD card using [SD Card Formatter](https://www.sdcard.org/downloads/formatter_4/). You will need to use an image writing tool to install the image you have downloaded on your SD card. **Etcher** is a graphical SD card writing tool that works on Mac OS, Linux and Windows, and is the easiest option for most users. Etcher also supports writing images directly from the zip file, without any unzipping required. To write your image with Etcher:

* Download [Etcher](https://etcher.io/) and install it.
* Connect an SD card reader with the SD card inside.
* Open Etcher and select from your hard drive the Raspberry Pi .img or .zip file you wish to write to the SD card.
* Select the SD card you wish to write your image to.
* Review your selections and click *Flash!* to begin writing data to the SD card.

### Install Raspbian system

1. Boot the Raspberry Pi with the latest Raspbian image (starting from release 2.1.0 Kura only supports Debian 8 or above).
2. Open terminal
	* The dhcpcd5 package is not compatible with Kura and needs to be removed performing the following command:
	```sudo apt-get purge dhcpcd5```
	* NetworkManager conflicts with Kura network management, make sure that it is not installed performing the following command:
	```sudo apt-get remove network-manager```
	* Install the gdebi command line tool:
	```sudo apt-get update
	sudo apt-get install gdebi-core
	sudo apt-get purge openjdk*
	sudo apt-get install openjdk-8-jdk```
 
	* if you run `java –version` the output will be:
	```openjdk version”1.8.x_xxx”
	OpenJDK Runtime Environment(…)
	OpenJDK Client VM (…)```
3. Download the Kura package:
```wget http://download.eclipse.org/kura/releases/<version>/kura_<version>_raspberry-pi-2-3_installer.deb```
*Note: replace <version> in the URL above with the version number of the latest release (e.g. 3.1.0)*
4. Install Kura:
```sudo gdebi kura_<version>_raspberry-pi-2-3_installer.deb```
5. Reboot the Raspberry Pi:
```sudo reboot```
6. Kura setups a local web ui that is available using a browser via: http://<device-ip>
	
	* Default username is: admin
	* Default password is: admin