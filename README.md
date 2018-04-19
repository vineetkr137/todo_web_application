## INSTALLATION GUIDE OF MONODEPTH (CPP WRAPPER)
## TOOLS AND REQUIREMENTS:
    OpenCv 3.3.0
 
    Flycapture sdk 2.11.3.*
 
    Tensorflow 1.3.0
## INSTALLATION STEPS:
### 1. Clone from github repository
    git clone -b vineet_devlop https://github.com/DreamVu/MVP_Software.git 


### 2. Get into directory.
    $   cd Monodepth_CPP_interface/


### 3. Download Models(KITTI) from google drive.
    $   wget https://drive.google.com/open?id=11l6WhJ8WwI15pRO_jJdurZwWM-_Avh8a


### 4. Compiling CPP code Interface_python.cpp

    $   g++ -c -fPIC interface_python.cpp -o foo.o `pkg-config --cflags opencv` `pkg-config --libs opencv` -L./lib -lflycapture${D} ${FC2_DEPS} 
### 5. Creating shared libraray file (libfoo.so)
    $   g++ -shared -Wl,-soname,libfoo.so -o libfoo.so foo.o `pkg-config --cflags opencv` `pkg-config --libs opencv` -L./lib -lflycapture${D} ${FC2_DEPS}


 ### 6. Run Monodepth algorithm using Pointgrey camera
    $   python monodepth.py --flyimage_path IMAGE_FLYCAPTURE_CPP.png --checkpoint_path models/model_kitti
