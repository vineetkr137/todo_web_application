## INSTALLATION GUIDE OF SEMENTIC SEGMENTATION (CPP WRAPPER)
## TOOLS AND REQUIREMENTS:
    OpenCv 3.3.0
 
    Flycapture sdk 2.11.3.*
 
    Tensorflow 1.3.0
    
    Cmake-gui
        
    Scikit
    
    COCOAPI
    
    Cython
    
    Keras 2.1.3
    
    Ipython
    
    h5py
    
## INSTALLATION STEPS:
### 1. Clone from github repository
    git clone -b vineet_devlop https://github.com/DreamVu/MVP_Software.git 

### 2. Install required tools and libraries.
    $   sudo apt-get install cmake-gui
    $   sudu pip install scikit-learn
    $   sudo pip install scikit-image
    $   sudo pip install cython
    $   sudo pip install keras==2.1.3
    $   sudo pip install Ipython
    $   sudo pip install h5py

### 3. Get into directory for build and Compiling process.
        -cd Sementic_segmentation_FLY/pyboostcvconverter
        -Run CMake and/or CMake-gui with the git repository as the source and a build folder of your choice
        (in-source builds supported.) Choose desired generator, configure, and generate. Remember to set 
        PYTHON_DESIRED_VERSION to 2.X for python 2 and 3.X for python 3.                   
        -Add flycapture shared object file to the cmake. 
        -Build (run make on from within the build folder)
        -On Linix systems, make install run with root privileges will install the compiled library file. 
        Alternatively, you can manually copy it to the pythonXX/dist-packages directory (replace XX with desired python version).  

### 4. Download Models(Sementic Segmentation) from google drive.
    $  https://drive.google.com/file/d/12Sgi_qH61Qp8vU_xachlpoT7nYqCS6m1/view?usp=sharing


### 5. Run sementic Segmentation.
    $  python demo.py


