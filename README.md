[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](http://www.repostatus.org/badges/latest/active.svg)](http://www.repostatus.org/#active)
[![Build Status](https://travis-ci.org/adityavaishampayan/SFM_cpp.svg?branch=master)](https://github.com/adityavaishampayan/SFM_cpp)
[![Coverage Status](https://coveralls.io/repos/github/adityavaishampayan/SFM_cpp/badge.svg?branch=master)](https://coveralls.io/github/adityavaishampayan/SFM_cpp?branch=master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


# Boiler plate for C++ projects

This is a boiler plate for C++ projects. What you get:

-   Sources, headers and mains separated in distinct folders
-   Use of modern [CMake](https://cmake.org/) for much easier compiling
-   Setup for tests using [doctest](https://github.com/onqtam/doctest)
-   Continuous testing with [Travis-CI](https://travis-ci.org/) and [Appveyor](https://www.appveyor.com), with support for C++17.
-   Code coverage reports, including automatic upload to [Coveralls.io](https://coveralls.io/) and/or [Codecov.io](https://codecov.io)
-   Code documentation with [Doxygen](http://www.stack.nl/~dimitri/doxygen/)

## Authors
 - Aditya Vaishampayan
 - Amrish Baskaran

## Development Process
This module will be developed using the Solo Iterative Process(SIP), Test Driven Development and agile development in a 3 week sprint method.
The spreadsheet for the Product log, iteration backlog, work log and sprint details can be found in this link-[Agile Development Spreadsheet](https://docs.google.com/spreadsheets/d/1gTq1l9RCe6zuMW0L57cpaaCt8EEMOVuNtgeplXd2HEI/edit?usp=sharing)

Notes from the sprint review sessions can be found in the link-[Sprint review Doc](https://docs.google.com/document/d/1T2uCC2Ef_-l1TtSUzq2ocHxJed9Jsc1g0zjSTBZt-sQ/edit?usp=sharing)

## Structure
``` text
.
├── app
│   └── main.cpp
├── cmake
│   ├── CodeCoverage.cmake
│   ├── Colors.cmake
│   ├── ConfigSafeGuards.cmake
│   ├── Doctest.cmake
│   ├── Documentation.cmake
│   ├── LTO.cmake
│   ├── Misc.cmake
│   └── Warnings.cmake
├── CMakeLists.txt
├── Doxyfile.in
├── include
│   ├── exampleConfig.h.in
│   └── example.h
├── LICENSE
├── README.md
├── setup.sh
├── src
│   └── example.cpp
└── tests
    ├── CMakeLists.txt
    ├── dummy.cpp
    └── main.cpp

```

Sources go in [src/](src/), header files in [include/](include/), main programs in [app/](app), and
tests go in [tests/](tests/) (compiled to `unit_tests` by default).

If you add a new executable, say `app/hello.cpp`, you only need to add the following two lines to [CMakeLists.txt](CMakeLists.txt):

``` cmake
add_executable(main app/main.cpp)   # Name of exec. and location of file.
target_link_libraries(main PRIVATE ${LIBRARY_NAME})  # Link the executable to lib built from src/*.cpp (if it uses it).
```

You can find the example source code that builds the `main` executable in [app/main.cpp](app/main.cpp) under the `Build` section in [CMakeLists.txt](CMakeLists.txt).
If the executable you made does not use the library in [src/](src), then only the first line is needed.

## License
License file can be found [here](https://github.com/adityavaishampayan/SFM_cpp/blob/master/LICENSE)

```
MIT License

Copyright (c) 2018 Aditya Vaishampayan, Amrish Bhaskaran

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
## Dependencies
Simple starter C++ project with:

- OpenCV - (OpenCV uses a BSD license and hence can be used for production with modification to the code.)
- cmake
- googletest [Gtest](http://wiki.ros.org/gtest)
- Travis CI [Documentation](https://docs.travis-ci.com/user/for-beginners/)
- Coveralls [Documentation](https://docs.coveralls.io/about-coveralls)

## OpenCV installation
```
Update packages
sudo apt-get update
sudo apt-get upgrade
```
We will install required dependencies
```
sudo apt-get install build-essential checkinstall cmake pkg-config yasm
sudo apt-get install git gfortran
sudo apt-get install libjpeg8-dev libjasper-dev libpng12-dev
 ```
If you are using Ubuntu 14.04
```
sudo apt-get install libtiff4-dev
```
If you are using Ubuntu 16.04
```
sudo apt-get install libtiff5-dev
```

```
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
sudo apt-get install libxine2-dev libv4l-dev
sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
sudo apt-get install qt5-default libgtk2.0-dev libtbb-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libfaac-dev libmp3lame-dev libtheora-dev
sudo apt-get install libvorbis-dev libxvidcore-dev
sudo apt-get install libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt-get install x264 v4l-utils
 ```
Optional dependencies
```
sudo apt-get install libprotobuf-dev protobuf-compiler
sudo apt-get install libgoogle-glog-dev libgflags-dev
sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen
```
Clone OpenCV and OpenCV_contrib
```
git clone https://github.com/opencv/opencv.git
cd opencv
git checkout 3.3.1
cd ..

git clone https://github.com/opencv/opencv_contrib.git
cd opencv_contrib
git checkout 3.3.1
cd ..
```
Make build directory
```
cd opencv
mkdir build
cd build
```
Run Cmake
```
cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local \
      -D INSTALL_C_EXAMPLES=ON \
      -D INSTALL_PYTHON_EXAMPLES=ON \
      -D WITH_TBB=ON \
      -D WITH_V4L=ON \
      -D WITH_QT=ON \
      -D WITH_OPENGL=ON \
      -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
      -D BUILD_EXAMPLES=ON ..
```
Find out number of CPU cores in your machine
```
nproc

# substitute 4 by output of nproc
make -j4
sudo make install
sudo sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf.d/opencv.conf'
sudo ldconfig
```
For installation related issues.

A complete OpenCV installation guide in Ubuntu can be found [here](http://www.codebind.com/cpp-tutorial/install-opencv-ubuntu-cpp/).


## Running tests-
Go to Catkin Workspace
```
cd ~/catkin_ws/
catkin_make run_tests intelli_bot_test
```

## Building

Build by making a build directory (i.e. `build/`), run `cmake` in that dir, and then use `make` to build the desired target.

Example:

``` bash
> mkdir build && cd build
> cmake .. -DCMAKE_BUILD_TYPE=[Debug | Coverage | Release]
> make
> ./main
> make test      # Makes and runs the tests.
> make coverage  # Generate a coverage report.
> make doc       # Generate html documentation.
```


## Setup
When starting a new project, you probably don't want the history of this repository. To start fresh you can use
the [setup script](setup.sh) as follows:
``` bash
> git clone https://github.com/bsamseth/cpp-project  # Or use ssh-link if you like.
> cd cpp-project
> sh setup.sh
```
The result is a fresh Git repository with one commit adding all files from the boiler plate.

## Doxygen Documentation

The doxygen documentation can be generated manually using the following commands
- Installation
```
sudo apt-get install doxygen
sudo apt-get install doxygen-gui
```
- Open Doxywizard and follow the instructions to generate the required files
```
doxywizard
```

Or one can also follow the steps given below:

Doxygen Documentation generation steps:
```
cd <path to repository>
mkdir Doxygen
cd Doxygen
doxygen -g <config_file_name>
```

Open configuration file and update the following:

```
PROJECT_NAME = 'your project name'
INPUT = ../LaneDetector ../include ../test
```

Run and generate the documents by running the next command:
```
doxygen <config_file_name>
```

## Plugins

- CppChEclipse

    To install and run cppcheck in Eclipse

    1. In Eclipse, go to Window -> Preferences -> C/C++ -> cppcheclipse.
    Set cppcheck binary path to "/usr/bin/cppcheck".

    2. To run CPPCheck on a project, right click on the project name in the Project Explorer
    and choose cppcheck -> Run cppcheck.


- Google C++ Sytle

    To include and use Google C++ Style formatter in Eclipse

    1. In Eclipse, go to Window -> Preferences -> C/C++ -> Code Style -> Formatter.
    Import [eclipse-cpp-google-style][reference-id-for-eclipse-cpp-google-style] and apply.

    2. To use Google C++ style formatter, right click on the source code or folder in
    Project Explorer and choose Source -> Format

[reference-id-for-eclipse-cpp-google-style]: https://raw.githubusercontent.com/google/styleguide/gh-pages/eclipse-cpp-google-style.xml
