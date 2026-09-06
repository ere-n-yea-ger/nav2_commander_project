# nav2_commander_project

# ROS 2 Nav2 Simple Commander: Autonomous Patrol & Waypoint Navigation

An autonomous navigation project utilizing the **ROS 2 Humble** Navigation 2 (Nav2) stack and the Nav2 Simple Commander API. This repository demonstrates programmatic control of a TurtleBot3 robot, enabling it to autonomously navigate, patrol, and follow complex waypoint routes within custom Gazebo simulation environments.

![Nav2 Navigation Demo](link-to-your-gif-or-image.gif) *(Highly recommended: Record a 10-second screen capture of your robot moving in RViz/Gazebo and replace this line with the link to the GIF)*

## 🚀 Key Features
* **Programmatic Nav2 Control:** Custom Python scripts leveraging the `nav2_simple_commander` API to set initial poses, send action goals, and process action feedback.
* **Autonomous Waypoint Following:** Implementation of a waypoint follower routine to navigate complex layouts.
* **Custom Simulation Worlds:** Integrated testing within the TurtleBot3 House and Maze Gazebo environments.
* **SLAM & Mapping:** Pre-generated static maps (`.yaml` and `.pgm`) utilized by the AMCL server for precise localization.

## 📁 Repository Structure
While this workspace includes the standard TurtleBot3 simulation packages in `src/`, the core custom developments are located in:

* `scripts/` - Contains the Python Commander APIs.
  * `waypoint_follower.py` - Script commanding the robot through a predefined series of poses.
  * `robot_patrol.py` - Autonomous patrolling logic using Nav2 action servers.
* `maps/` - SLAM-generated maps of the House and Maze worlds.

## 🛠️ Prerequisites & Tech Stack
* **OS:** Ubuntu 22.04
* **Middleware:** ROS 2 Humble
* **Core Libraries:** `nav2_simple_commander`, `rclpy`, `geometry_msgs`
* **Simulation:** Gazebo & RViz2

## ⚙️ Build Instructions

1. Clone this repository into your ROS 2 workspace:
   ```bash
   git clone [https://github.com/ere-n-yea-ger/nav2_commander_project.git](https://github.com/ere-n-yea-ger/nav2_commander_project.git)
   ```
2. Install dependencies using `rosdep`:
   ```bash
   rosdep install --from-paths src --ignore-src -r -y
   ```
3. Build the workspace:
   ```bash
   colcon build --symlink-install
   ```
4. Source the environment:
   ```bash
   source install/setup.bash
   ```

## 🏃‍♂️ Execution Guide

### 1. Launch the Simulation and Nav2 Stack
To launch the robot in the TurtleBot3 House environment with the Nav2 stack running:
```bash
ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=maps/my_house.yaml
```

### 2. Run the Commander Scripts
Open a new terminal, source your workspace, and execute the Python commander script:
```bash
python3 scripts/robot_patrol.py
```
