
## Steps for setting up the UR5e to work with Ros2

### Back up the UR5-E

1. turn on
1. go to manual mode
1. safety / admin password: idealab
1. backup system to usb stick
1. save to idealab equipment

### Update the UR5E

1. go to universal robots website
    1. select 5.12.6 lts update (or newer, may require sign-in)

        * <https://www.universal-robots.com/download/software-ur20ur30/image/robot-image-e-series-and-ur20ur30-sw-5200/>
        * <https://www.universal-robots.com/articles/ur/documentation/legacy-download-center/>
        * <https://www.universal-robots.com/download/software-e-series/image/robot-image-e-series-sw-5126-lts/>

    1. download
    1. move to usb stick
    1. insert the usb stick in the top of the pendant.
    1. In the pendant's interface, go to settings --> update
    1. search
    1. select
1. wait for the install to finish and for the system to reboot

> Once rebooted, don't forget to enable motors.  You can test by moving them around

### Running the Universal Robots Driver

1. Download the repo from the humble branch: <https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/tree/humble>
1. Follow the readme for the version of ros2 that you're using to install the controller
1. In ROS:
    1. Start the ROS driver on the PC

        ```bash
        ros2 launch ur_robot_driver ur_control.launch.py ur_type:=ur5e robot_ip:=192.168.1.103    
        ```

    1. start the driver

    1. go to usage documentation
    1. list controllers

        > What is a controller? <https://control.ros.org/master/doc/getting_started/getting_started.html>

1. On the UR5-E
    1. enable motors
    1. go to settings
    1. add a new URCap plugin (if it does not exist)
    1. update settings reflecting the particular host you will be communicating with (the pc running ros2)
    1. go to programs
        1. make a new URCap program (if not already created)
            1. save it
            1. run it
1. Back on the PC side, open up moveit

    ```bash
    ros2 launch ur_moveit_config ur_moveit.launch.py ur_type:=ur5e launch_rviz:=true
    ```

    1. Drag the end effector a bit. Plan and execute (bottom left) to test it out.

> **Note:** If the driver is stopped and restarted, the URCap program may also need to be restarted on the UR5.
The controllers' state is a good indication of whether everything is working properly.
