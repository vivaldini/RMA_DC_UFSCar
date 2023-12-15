# Configure your ROS Environment for ROS Noetic

If you haven't already, you can follow the installation instructions of `Step 0`.

## Step 0: Install the Robot Operating System (Noetic)

1. Open a terminal. You can do this by pressing `Ctrl + Alt + T` or searching for "Terminal" in your application menu.
2. Use the following commands to add the ROS repository and install the full desktop version:

```bash
curl https://ctu-mrs.github.io/ppa-unstable/add_ros_ppa.sh | bash

sudo apt install ros-noetic-desktop-full
```

Now that you have ROS Noetic installed, configure your environment:


## Step 1: Initialize ROS Environment

In the terminal, run the following command to initialize the ROS environment:

```bash
source /opt/ros/noetic/setup.bash
```

> [!NOTE]
> This command will load the necessary environment variables for ROS Noetic.

> [!WARNING]
> You must run this command in every new shell you open to access the ROS commands unless you add this line to your ".bashrc." 

```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
```

#### Check `.bashrc` 
To open and check/edit your `.bashrc` file manually, you can use any text editor and add the command

```bash
gedit ~/.bashrc
```

Add the following line to the end of the file:

```bash
source /opt/ros/noetic/setup.bash
```

Save the file and exit the text editor.

Make sure you have ROS Noetic installed on your system. Check your version in a terminal.

```bash
rosversion -d
```

## Step 2: Set up your Catkin Workspace

You can use the Catkin build system to manage packages in ROS Noetic. To create a Catkin workspace, follow these steps:


> [!NOTE]
> You can use any name for your workspace; just replace 'catkin_ws' with 'your_workspace_name' in the commands. For example, if you want to name your workspace 'my_workspace,' you would replace 'catkin_ws' with 'my_workspace' in the commands.

```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin build
source ~/catkin_ws/devel/setup.bash
```
> [!NOTE]
> You can also use `catkin_make` here if you prefer. Check the better command for you (packages used).


## Step 3: Create a ROS Package

To start developing with ROS Noetic, you can create a package within your workspace. Replace `my_package` with the name of your package:

```bash
cd ~/catkin_ws/src
catkin_create_pkg my_package std_msgs rospy roscpp
```

In this example, `std_msgs`, `rospy`, and `roscpp` are package dependencies. 

> [!WARNING]
> Make sure to add any other dependencies your package may have.


## Step 4: Build the Workspace

After creating your package, compile the workspace using Catkin:

```bash
cd ~/catkin_ws
catkin build
```

## Step 5: Environment package Initialization


To automatically initialize the ROS environment every time you open a new terminal, add the following line to the end of your `~/.bashrc` file:

```bash
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
```

Done!! 
For detailed information, access ROS Noetic and Catkin documentation [ROS Noetic Tutorials](http://wiki.ros.org/noetic/Tutorials)
