Rover Control Project
=====================
(Charles Sedgwick)
[charlessedgwick.com]

RoverDaemons exits as a test bed for learning how to implement control
software for autonomous land based vehicles. The core computing platforms
supported are the BeagleBone Blue. The BeagleBone Black and Green are
supported via the BeagleBoneBlack branch. An alternative version that uses ACH
instead of ROS is supported via the feature-ach branch.

Dependancies
------------
@master:
 - robotics_cape_installer:
   https://github.com/StrawsonDesign/Robotics_Cape_Installer
 - Latest Debian Stretch IoT image for BeagleBone Blue
 - OpenCV 3.2
 - ROS kinetic

@feature-ach:
 - ACH: https://github.com/golems/ach

@BeagleBoneBlack
 - ROS kinetic
 - mraa: https://github.com/intel-iot-devkit/mraa
 - bb.org-overlays: https://github.com/RobertCNelson/bb.org-overlays
 - BMP180 Beaglebone Black C++ driver
 - LSM303 Beaglebone Black C++ driver
 - L3DG20 Beaglebone black C++ driver

Compilation
-----------
1. clone directory
    ```
    https://github.com/sedgwickc/RoverDaemons.git
    ```
2. navigate to newly created RoverDaemons directory

@master:
3. source your ROS environment
4. run ```catkin_make```

@feature-ach:
3. run make
    ```
    make all
    ```

Startup
-------

@master:
1. start roscore
2. Nodes built in step 4 should be in devel/lib/. Start them via roslaunch.


@feature-ach:
0. Ensure pwm pins are setup:
    ``` 
    sudo setupPWM.sh
    ```

1. create channels 
    ```
    sudo ./create_channels.sh -c
    ```
2. start daemons
    ```
    sudo ./build/sub_nav
    ```
3. start rover controller
    ```
    sudo ./build/control
    ```

Shutdown
--------

@master:

@feature-ach:
1. Kill daemons
    ```
    sudo kill $DAEMON_PID
    ```

Troubleshooting
---------------

@master:

@feature-ach:
1. delete channels
    ```
    sudo ./create_channels.sh -d
    ```
2. logging
    - logs are stored in the following directory: 
        ```
        /var/log/rover_logs/nav_log.txt
        ```
