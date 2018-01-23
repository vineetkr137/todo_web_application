# Installation Steps for Camera Software on Jetson TX2.

### 1) INSTALL UBUNTU 16.04 64-bit LTS (Tegra-ubuntu for Jetson TX2)  (other versions might not be working well with audio)

### 2) Installing Gstreamer version 1.8.3
       sudo apt-get install libgstreamer1.0-dev 
       sudo apt-get install libgstreamer-plugins-*1.0-dev
       sudo apt-get install libgstreamer-plugins-ugly1.0-dev  (This command may not work )
       sudo apt-get install gstreamer1.0-plugins-bad (for rtmpsink)
       sudo apt-get install gstreamer1.0-plugins-ugly (for x264enc)
    
    

### 3) Installing Opencv 3.3.0 with both python 2.7.12 and python 3.5.2 
       Follow same steps from:-
       [https://jkjung-avt.github.io/opencv3-on-tx2/]


***FOLLOW EVERY INSTRUCTION OF THE ABOVE BLOG - DO NOT MISS ANY STEPS***


### 4) Installing FLYCAPTURE2 with USB 3.0 
       [https://www.ptgrey.com/support/downloads]

       While Downloading FlyCapture use:- 

       Product Family: Grasshopper3
 
       Camera Model: Gs3-u3-41c6c-c
 
       Operating System: Ubuntu 16.04 arm
 
       Download -  FlyCapture 2.11.3.425 SDK - ARM64

     
       Configuring the Operating System and Installing the Required Libraries:-
  	   http://www.ptgrey.com/KB/10357

  ##### Configuring USBFS
        sudo sh -c 'echo 1000 > /sys/module/usbcore/parameters/usbfs_memory_mb'

        To confirm that you have successfully updated the memory limit, run the following command:

        cat /sys/module/usbcore/parameters/usbfs_memory_mb


***FOLLOW EVERY INSTRUCTION OF THE ABOVE BLOGS - DO NOT MISS ANY STEPS***


### 5) Installing Qt 5.5 on the Jetson TX2
        FOLLOW THE SAME STEPS AS
        http://www.jetsonhacks.com/2017/01/31/install-qt-creator-nvidia-jetson-tx1/
 


### 6) Installing and Setting up Wowza Streaming Engine 

       Download Debian package for Wowza.
 
       Create an account for Wowza and install the Streaming Engine

       Once Installed
       localhost:8088 for engine manager

       go to applications->live->sourcesecurity>disable rtmp authentication


### 7) Configuring Wowza Streaming Cloud
       Create a seperate account for Wowza Streaming Cloud(rajat account already created with all the settings no need 
       to create a new one. go through the settings of the stream in that account to create a live stream with a new 
       account in case)


### INSTRUCTIONS FOR USING THE SOFTWARE

       launch the "run" executable using "./run" in the main directory
       and for the STREAMING ENGINE URL and CLOUD STREAMING URL and adjusting other properties related to the software can 
       be adjusted in the "macros.hpp" file ( TO BE CHANGED TO A FILE BASED IMPLEMENTATION)

       for FULL FPS STREAMING WITH AUDIO CHANGE PROCESSED_WIDTH PROCESSED_HEIGHT to 1080 and 720 respectively


       copy the dev_dreamvu.pro file in temporary file. 
       Once into the dev_dreamvu directory having the makefile run "make" <br/>
       In case of any dependency errors check if every installation as mentioned above is done.<br/>
       In case of any errors related to path (" xyz.h" not found) change the corresponding path of the package in the 
       ".pro" file and then run "make"

       In case you want to build completely by yourself with the necessary paths 
       run the following commands

       qmake -project <br/>
       qmake <br/>
       copy the temporary file to .pro file <br/>

##### Add the necessary paths for the required packages(Refer to the exisiting .pro file for the required packages) <br/>
       run make

       ./run to execute

