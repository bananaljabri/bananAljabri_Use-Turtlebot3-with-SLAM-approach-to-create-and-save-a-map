# bananAljabri_Use-Turtlebot3-with-SLAM-approach-to-create-and-save-a-map

This task requires using Turtlebot3 (ROS standard platform robot) with SLAM approach (simultaneous localization and mapping) to create a map using Lidar sensor and then save the map.
_______________________
So, I followed these steps:

1- Download Oracle Virtual Machine

If we want download ROS system on windows computer thus brings a lot of problems, for that we download virtual Box that enable us install ROS system by easy way.

Download from this link : https://www.virtualbox.org/

![image](https://user-images.githubusercontent.com/81714161/130931258-7a7cda82-d33b-4ed6-b74d-145c4ab7343d.png)


2- Download UBUNTU 18.04.5

Ubuntu is a Linux distribution based on Debian and composed mostly of free and open-source software.

Download from this link : https://releases.ubuntu.com/18.04.5/

3- Install and run a UBUNTU on Virtual Machine

![image](https://user-images.githubusercontent.com/81714161/130931321-18b49762-9874-4483-83f5-bf342792a847.png)

![image](https://user-images.githubusercontent.com/81714161/130931349-e6bcac0d-515b-4c47-b65c-742048ae3b1e.png)


 
4- Download ROS MELODIC

From this link : http://wiki.ros.org/melodic/Installation/Ubuntu

Then follow this steps on cmd terminal

• sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

• sudo apt install curl

• curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

• sudo apt-get update

• sudo apt install ros-melodic-desktop-full

• apt search ros-melodic

• echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc

• source ~/.bashrc

• sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

• sudo apt install python-rosdep

• sudo rosdep init

• rosdep update

5- set a password

![image](https://user-images.githubusercontent.com/81714161/130931453-31e84033-8057-4dae-97b4-8b29f4ec6baf.png)


**All previous steps, I am already doing it in previous task (Installing-the-arm-package-on-ROS-system)
__________________

6- Install Dependent ROS 1 Packages

 
$ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy \

  ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc \
  
  ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan \
  
  ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python \
  
  ros-kinetic-rosserial-server ros-kinetic-rosserial-client \
  
  ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server \
  
  ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro \
  
  ros-kinetic-compressed-image-transport ros-kinetic-rqt* \
  
  ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers
  
7- Install TurtleBot3 Packages

Install TurtleBot3 via Debian Packages.

$ sudo apt-get install ros-kinetic-dynamixel-sdk

$ sudo apt-get install ros-kinetic-turtlebot3-msgs

$ sudo apt-get install ros-kinetic-turtlebot3

 8- Set TurtleBot3 Model Name
 
Set the default TURTLEBOT3_MODEL name to your model. Enter the below command to a terminal.

•	In case of TurtleBot3 Burger

$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc

•	In case of TurtleBot3 Waffle Pi

$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc

9- We will choose one of the previous robot which is waffle and we weill cintrol it usit the keybored keys W: Forward, A: Left, S:Stop, D: Right, X:Backward. So, Run the previous comand for waffle robot then open new terminal and run the following command:

o	roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

10-	Now, close everthing and lets use SLAM simulation to creat the a map for our world, and then save the map with help of lidar sensor. There are 3 Gazebo environments are prepared , but for creating a map with SLAM, it is recommended to use either TurtleBot3 World or TurtleBot3 House. So, I will use TurtleBot3 World with a robot called "waffle" to creat the map and save it.

o	Lunch the Gazebo environment with waffle robot export TURTLEBOT3_MODEL=waffle then roslaunch turtlebot3_gazebo turtlebot3_world.launch

o	Open new terminel to Run SLAM Node export TURTLEBOT3_MODEL=waffle then roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

o	Open a new terminal to control the waffel robot and scan the area using lidar sensor export TURTLEBOT3_MODEL=waffle then roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch. (in the terminal we will control the robot direction using W,A,S,D,X keybored keys).


![image](https://user-images.githubusercontent.com/81714161/130931602-a77602b7-34b9-4830-be4b-6fca6e011c50.png)


11-	When the map is created successfully in Rviz, open new terminal and save it using the command rosrun map_server map_saver -f ~/map


![image](https://user-images.githubusercontent.com/81714161/130931680-2b47b2fd-c65d-48ee-9e1d-12f5dea43538.png)

 



