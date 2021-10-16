# RealSense2-D435
Author: Prasanth Sengadu Suresh.

Owned By: THINC Lab, Department of Computer Science,
          University of Georgia.

Currently Managed By: Prasanth Sengadu Suresh.

Realsense D435 camera package customized to publish static transforms of current pose.

In order to get Realsense camera installed and integrated with ROS, perform the following steps:

  - Register the server's public key:  
    `sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE`
In case the public key still cannot be retrieved, check and specify proxy settings: `export http_proxy="http://<proxy>:<port>"`  
, and rerun the command. See additional methods in the following [link](https://unix.stackexchange.com/questions/361213/unable-to-add-gpg-key-with-apt-key-behind-a-proxy).  

- Add the server to the list of repositories:  
  Ubuntu 16 LTS:  
`sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo xenial main" -u`  
  Ubuntu 18 LTS:  
`sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo bionic main" -u`  
  Ubuntu 20 LTS:  
`sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo focal main" -u`

- Install the libraries (see section below if upgrading packages):  
  `sudo apt-get install librealsense2-dkms`  
  `sudo apt-get install librealsense2-utils`  
  The above two lines will deploy librealsense2 udev rules, build and activate kernel modules, runtime library and executable demos and tools. 

Reconnect the Intel RealSense depth camera and run: `realsense-viewer` to verify the installation.

Verify that the kernel is updated :    
`modinfo uvcvideo | grep "version:"` should include `realsense` string

Cd into your catkin_ws/src folder and clone this package:
  `git clone https://github.com/thinclab/RealSense2-D435.git`
  
Cd back into your catkin_ws and do a catkin_make install. If you encounter a ddynamic-reconfigure error, one of the following two ways should fix it:

  - `sudo apt-get update && sudo apt install ros-<YOUR-ROS-DISTRO>-ddynamic-reconfigure`

  - If that did not work, delete your build, devel and install folder in catkin_ws, clone [this](https://github.com/pal-robotics/ddynamic_reconfigure) package into your src folder and do a catkin_make install from your catkin_ws folder level.
