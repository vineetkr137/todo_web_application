# Capture and Stream Software for ALIA Version 2.0 For LOGITECH Cameras
This repository contains sources code for ALIA Version 2.0 software for logitech cameras. This Software is used to capture, local stream and live stream the frames for ALIA. This repository also contains extra utility packages needed for making efficent and comfortable live stream for Human Vision purpose.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. 

For development purposes, open the code with .cpp and .hpp in [source_code](source_code/) 


## Prerequisites and Camera Setup ALIA Version 2.0 For LOGITECH Cameras

All the cameras are marked as 1L, 2L, 3L, 4L, 1R, 2R, 3R and 4R. Connect the cameras to the USB port in the same order. Also, check the ```dev``` folder in the root.

### Installion required for ALIA Version 2.0 LOGITECH Cameras

Following are the installations required for the ALIA V2 LOGITECH:
1. Install UBUNTU 16.04 64-bit LTS" (other versions might not be working well with audio(though have to check)
2. Installing Gstreamer version 1.8.3
```
sudo apt-get install libgstreamer1.0-dev 
sudo apt-get install libgstreamer-plugins-*1.0-dev 
sudo apt-get install libgstreamer-plugins-ugly1.0-dev 
sudo apt-get install gstreamer1.0-plugins-bad (for rtmpsink)
sudo apt-get install gstreamer1.0-plugins-ugly (for x264enc)
```
3. Installing Opencv 3.1.0 with  [python 2.7](http://www.pyimagesearch.com/2016/10/24/ubuntu-16-04-how-to-install-opencv)
4. If during installation you get an error stating libglademm-2.4-dev not found, do the following: 
```
sudo apt-get -f install 
sudo apt-get install libglademm-2.4-dev 
```
5. While configuring USBFS , set the maximum USBFS memory permanently.
6. Installing QT 5.7.0 FOLLOW THE SAME STEPS AS [QT](https://wiki.qt.io/Install_Qt_5_on_Ubuntu)
7. Installing and Setting up Wowza Streaming Engine
Create an account for Wowza and install the Streaming Engine Once Installed localhost:8088 for engine manager go to:
> applications -> live -> source_security -> disable-rtmp-authentication

8. Configuring Wowza Streaming Cloud Create a seperate account for Wowza Streaming Cloud(rajat account already created with all the settings no need to create a new one. Go through the settings of the stream in that account to create a live stream with a new account in case)

## Compile and run the ALIA Version 2.0 for LOGITECH Cameras
1. Add the path to all the parameters in blend.pro file
```
TEMPLATE = app
TARGET = run
INCLUDEPATH += .
QT += widgets gui core
# Input
HEADERS += ./*.hpp

INCLUDEPATH += /usr/include/gstreamer-1.0/
INCLUDEPATH += /usr/include/glib-2.0/
INCLUDEPATH += /usr/lib/x86_64-linux-gnu/glib-2.0/include/
INCLUDEPATH += /usr/lib/gstreamer-1.0/include/
INCLUDEPATH += /usr/lib/x86_64-linux-gnu/gstreamer-1.0/include/
INCLUDEPATH += /usr/include/libxml2/
INCLUDEPATH += ./include/

PKGCONFIG += gstreamer-1.0 opencv
SOURCES += ./*.cpp
LIBS += /usr/local/lib/libopencv*.so
LIBS += /usr/lib/x86_64-linux-gnu/libgobject*.so
LIBS += /usr/lib/x86_64-linux-gnu/libglib*.so
LIBS += /usr/lib/x86_64-linux-gnu/libgst*-1.0*.so
LIBS += /usr/lib/x86_64-linux-gnu/libv4l*.so
OBJECTS_DIR= ./obj
linux-g++ | linux-g++-64 | linux-g++-32 {
    QMAKE_CXX = g++-5 -std=c++11 
    QMAKE_CC = gcc-5
}
```

2. Qmake the blend.pro file. This should create the Makefile in the project.
```
qmake blend.pro
```

3. Make the project. This should create the ```run``` as executable file
```
make
```

4. Run the executable created above.
```
./run
```

## Multi_Thread_Feed_capture
Goto: [multithread-capture](extra_utility_packages/multithread-feed-capture)

This package contains source files for capturing images from multiple cameras in parallel manner and otputs 360 stereo panoramas. This package use multi-threading approach to capture images. Each thread will capture images from a single camera, so the number of threads will be determined by the number of cameras.

### Dependencies

- OpenCV

### Compilation

Compile all the files using the following commands.

```bash
mkdir build && cd build
cmake ..
make
```

Make sure your are in the `build` folder to run the executables.

### Data
Download `calibration.yml` file and  `offsets_corrected.bin` file from below link and store it in `data` folder.

`Link: https://drive.google.com/open?id=1OMgb0oea1_rElVZ9dI9BwTkECfUXQuDJ`

### Output format

This package will ouputs live 360 stereo panoramas. 

### Running calibration

Run the executable with the following command

```bash
./MultiCamera
```

##BLEND related OpenCV changes
There are some files that were modified in the opencv code.
Copy these files from "opencv_blend_changes" folder into their respective folders and compile opencv

```
opencv\modules\stitching\src\cuda\multiband_blend.cu 
opencv\modules\stitching\test\test_main.cpp 
opencv\modules\stitching\include\opencv2\stitching\detail\blenders.hpp 
opencv\modules\stitching\src\blenders.cpp 
```

## Versioning in ALIA Version 2.0 For LOGITECH Cameras

We use [SemVer](http://semver.org/) for versioning. 


## Current Project Team Members

* **[Rajat Aggarwal](https://github.com/rajat974/)**
* **[Ankit Chaurasia](https://github.com/ankit-dreamvu)**
* **[Aniket](https://gadwe.aniket@dreamvu.com)**

**This project is bound by Code of Conduct of [DreamVu.inc](http://dreamvu.com/).**

![Dream Vu](/dreamvu_logo.png)
