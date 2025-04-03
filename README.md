# Odometry for HomeR
## Objectives
- Practice [transformation broadcasting](https://docs.ros.org/en/jazzy/Tutorials/Intermediate/Tf2/Writing-A-Tf2-Broadcaster-Py.html)
- Review ROS [node](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html)
- Review [topic](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html).
- Review Manage a ROS [package](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Creating-Your-First-ROS2-Package.html) with an [executable](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Publisher-And-Subscriber.html).

## Pre-requisite
Upload MicroPython scripts to your pico board so that your robot is driven by a apt PID controller.
Feel free to use sample code from [HomeR](https://github.com/linzhangUCA/homer/tree/2425/homer_control/pico_scripts).

## Requirements: 
1. (5%) Download and build the ROS package. 
   1. (Optional) [Create a ROS workspace](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html#create-a-new-directory). 
   2. Clone this repository down to the `/src` dirctory in your ROS workspace, then `colcon build`.

2. (58%) Complete the [odom_talker.py](homer8_odom_pkg/homer8_odom_pkg/odom_talker.py).
   Fill code between the commented lines:
   ```python
   ### START CODING HERE ###

   ### END CODING HERE ###
   ```
   - (9%) Correctly initialize:
     - a `/odom` topic publisher
     - a tf broadcaster for transform between `odom` frame and `base_link` frame.
     - a timer running at 50 Hz with `announce_odometry` to be its callback function.
   - (9%) Correctly compute the HomeR's pose at each instance.
   - (20%) Correctly format `Odometry` message and **publish** it under the `/odom`.
   - (20%) Correctly format `TransformStamped` message and **broadcast** this transform.
   - HomeR's actual velocity is stored in `self.real_lin_vel` and `self.real_ang_vel`.
   


3. (10%) Let the turtle complete at least five laps then upload your figure 8 to the [images/](/images/) directory.
   Illustrate Your turtle's execution below (edit next line in this [README](README.md)):
   
   ![fig8_practice](turtlesim_play_pkg/images/fig8_practice.png)
   
4. (5%) Fill the `<description>`, `<maintainer>`, `<maintainer_email>` fields with your own information in [package.xml](turtlesim_play_pkg/package.xml) and [setup.py](turtlesim_play_pkg/setup.py).
Look for the fields marked with `TODO` in these files.

### Hints
- Build `homer8_odom_pkg` package.
  1. Open a terminal window and run following commands:
   ```console
   cd <ros workspace path>
   colcon build --packages-select homer8_odom_pkg
   source install/local_setup.bash  # CRITICAL, or ROS can't find your package
   ```
  2. Start the `turtlesim`
   ```console
   ros2 run turtlesim turtlesim_node
   ```
  3. Run executable `paint_8` in another terminal
   ```console
   source <ros workspace path>/install/local_setup.bash
   ros2 run homer8_odom_pkg paint_8
   ```

  ![homer8_demo](/images/homer8_demo.gif)

  The velocity commands to drive the robot is predefined in [homer_figure8.py](homer8_odom_pkg/homer8_odom_pkg/homer_figure8.py).
  The robot is supposed to paint a figure 8 on its movable plane, but you'll observe the deviance between theory and reality.
   
- `turtlesim` is used to visualize the robot's trajectory in this assignment.
  We'll read the robot's actual velocity from the Pico, fill it to the `Twist` message then publish to`/turtle1/cmd_vel` topic.
  Check [homer_figure8.py](homer8_odom_pkg/homer8_odom_pkg/homer_figure8.py) for a detailed management.
   

   
## Study Resources


## AI Policies
Please acknowledge AI's contributions according to the policies in the [syllabus](https://linzhanguca.github.io/_docs/robotics2-2025/syllabus.pdf).
