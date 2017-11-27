# ChromaTag: A Colored Marker and Fast Detection Algorithm


## Introduction ##
ChromaTag is a colored fiducial marker and fast detection algorithm. It was originally published in ICCV 2017 (see citation below). This is the location of the source that is actively being developed. If you want the latest stable version, you can download it from [here](http://degol2.web.engr.illinois.edu/pages/ChromaTag_ICCV17.html). The current set of priority development tasks for ChromaTag are:
1. Testing multi-marker detection
2. Testing inter-marker confusion
3. Tag generation tools
4. Color calibration tool to generate markers for specific lighting conditions
You can contact Joseph DeGol (degol2@illinois.edu) with any questions, problems, or suggestions.


## License ##
ChromaTag is released under the MIT License (see the LICENSE file for details). [OpenCV](https://opencv.org/), which is required to build and run ChromaTag, is released under the [BSD 3-Clause license](https://opencv.org/license.html).


## Citing ChromaTag ##
If you find ChromaTag useful, please consider citing:
	
@inproceedings{DeGol:ICCV:17,
  author    = {Joseph DeGol and Timothy Bretl and Derek Hoiem},
  title     = {ChromaTag: A Colored Marker and Fast Detection Algorithm},
  booktitle = {ICCV},
  year      = {2017}
}


## Data ##
Some toy data is provided with the repository to ensure things are running correctly. Additional test data can be found [here](http://degol2.web.engr.illinois.edu/pages/ChromaTag_ICCV17.html).


## Tags ##


## Source ## 
Follow the steps below to install dependencies (common and OpenCV) before building ChromaTag.

#### Common ####
These are common Unix libraries used to acquire and build c++ programs from source. In particular, ChromaTag uses cmake.
```
sudo apt-get install git
sudo apt-get install build-essential
sudo apt-get install cmake
sudo apt-get install pkg-config
```

#### OpenCV ####
OpenCV is required to build and run ChromaTag. These instructions are adapted from the [this OpenCV tutorial](http://docs.opencv.org/3.1.0/d7/d9f/tutorial_linux_install.html).

First, download OpenCV 3.1.0 or higher: https://github.com/Itseez/opencv/archive/3.1.0.zip.

Next, Install these packages:
```
sudo apt-get install libgtk2.0-dev 
sudo apt-get install libavcodec-dev 
sudo apt-get install libavformat-dev 
sudo apt-get install libswscale-dev
sudo apt-get install python-dev python-numpy 
sudo apt-get install libtbb2 libtbb-dev 
sudo apt-get install libjpeg-dev 
sudo apt-get install libpng-dev 
sudo apt-get install libtiff-dev 
sudo apt-get install libjasper-dev 
sudo apt-get install libdc1394-22-dev
```

Finally, build OpenCV
```
unzip opencv-3.1.0.zip
cd opencv-3.1.0
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local ..
make -j4
sudo make install
```

OpenCV should now be installed in your system. If you choose to download a different version from 3.1.0, change the text above appropriately. If these instructions do not work for your version of OpenCV, please check the OpenCV provided tutorial for your version because there may be small differences.


### ChromaTag ###
To clone and build ChromaTag, move to a directory where you want the ChromaTag source to live and then run the following commands in a Unix terminal.
```
git clone https://gitlab.engr.illinois.edu/degol2/ChromaTag.git
cd ChromaTag
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make -j
```

The built executables will be in `.../build/bin` and the libraries will be in `.../build/lib`.
```
cd build/bin
ls
```


## Usage ##
A run script is provided to process the toy images. This script uses the `Run_ChromaTag_Detector` program in `.../build/bin`. To run the script, type:
```
cd ChromaTag/Scripts
bash run_chromatag.sh
```

The script is useful in seeing the default way to process images in a folder. There are other options for processing (e.g. processing a list of images or an LCM stream). To run with no images and see the menu, type:
```
cd ChromaTag/build/bin
./Run_ChromaTag_Detector --help
```