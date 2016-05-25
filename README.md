## Alan's InMoov ROS Introduction
![enter image description here](http://i.imgur.com/bweApZH.png)

**This is very much a work in progress.**  I'll periodically push updates based on things that I've done, but there's no guarantee that everything works.

---------

###What Is It?
This is a ROS software stack that connects a dedicated PC to an InMoov robot.  
It currently implements the following:

 - a fully articulated URDF model of InMoov
 - inmoov firmware that integrates rossserial_arduino for communication
 - inmoov_msgs that define communication between host pc and arduino
 - trainer module to set arduino eeprom values and calibrate each servo

###What You Need To Get Started
> This works with a specific technology stack.  It can be run natively on a PC, or in VMWare Player.  Everything is tied to compatibility with MoveIt!.  
>  
>  MoveIt! is currently available for ROS Indigo, and Indigo is tied to Ubuntu 14.04 LTS, so everything fits together from there.  
>   
>   As soon as they release MoveIt! packages for ROS Kinetic, the stack will be updated to Ubuntu 16.04 + ROS Kinetic + MoveIt!

####What you'll need:

 - VMWare Player
 (https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0)
 - Ubuntu 14.04 LTS (http://www.ubuntu.com/download/alternative-downloads) 
 - ROS Indigo (http://wiki.ros.org/indigo/Installation/Ubuntu)
 - MoveIt! (http://moveit.ros.org/install/)

###How to Install It:
copy these packages into your {inmoov_ros}/src folder
Run the following commands from the root of your {inmoov_ros} folder:
  
    catkin_make              #build/rebuild all projects
    source devel/setup.bash  #let ROS know about all of your new packages

###How to use it:
Run the following commands:

    rosrun inmoov_tools set_parameters.py        #loads parameters into server
    roslaunch inmoov_tools servobus.launch       #launches arduino interfaces
    roslaunch inmoov_description display.launch  #launches rviz
    rosrun inmoov_tools trainer.py               #launches trainer module


###Next Steps (todo list)
 - urdf:  fix right shoulder out rotation
 - urdf:  fix right wrist rotation
 - trainer:  move all arduino communication to service calls
 - trainer:  only publish joint commands to joint_command topic
 - node:  write node that sends joint commands to arduino through service calls
 - pose:  migrate pose module to pyqt4
 - headdemo:  migrate headdemo module to pyqt4
