# 🤖 Franka Emika Panda 7 DOF Robot

A **ROS 2 Humble-based autonomous pick-and-place system** using the **Franka Emika Panda robotic arm**. This project integrates **OpenCV computer vision**, **MoveIt 2 motion planning**, and **Gazebo simulation** to detect colored objects and sort them with precision.

---

## ✨ Features

 
- 🦾 **Motion Planning**: Trajectory planning and execution with MoveIt 2  
- 🎯 **Autonomous Operation**: Pick-and-place automation with gripper control  
- 🔄 **Dynamic Target Selection**: Choose target color interactively at runtime
- 🎨 **Color Detection**: Real-time OpenCV-based vision system for Red, Green, and Blue objects 
- 📊 **Visual Feedback**: RViz visualization for motion planning and execution  

---

## 📦 Packages

- **franka_description** → Robot URDF/Xacro and meshes  
- **franka_bringup** → Launch files for simulation and controllers  
- **franka_moveit** → MoveIt 2 configuration and planning interface  
- **franka_vision** → Color detection and perception node  
- **franka_execution** → Pick-and-place logic and action execution  

---

## 🏗️ Installation

### 1. Create Workspace
```bash
mkdir -p ~/franka_ws/src
cd ~/franka_ws/src
git clone https://github.com/Mugilan-Theroboticist/7DOF-Autonomous-Pick-and-Place-Robot.git .
```

### 2. Install Dependencies
```bash
cd ~/franka_ws
rosdep install --from-paths src --ignore-src -r -y
```

### 3. Build
```bash
colcon build
source install/setup.bash
```

---

## 🎮 Running the Project

Open **two terminals**:

### Terminal 1: Launch Simulation
```bash
source ~/franka_ws/install/setup.bash
ros2 launch franka_bringup pick_and_place.launch.py
```

This starts:
- Gazebo simulation with Franka Panda  
- RViz motion planning visualization  
- Camera and color detection node  
- MoveIt 2 planning server  
- Robot controllers  

### Terminal 2: Run Pick-and-Place (Interactive)
```bash
source ~/franka_ws/install/setup.bash
ros2 run franka_execution pick_and_place.py
```

👉 Once you run this command, the node will **prompt you to enter a color** (`R`, `G`, or `B`).  
- Enter `R` → Robot sorts Red objects  
- Enter `G` → Robot sorts Green objects  
- Enter `B` → Robot sorts Blue objects  

The robot will then detect, pick, and place the chosen color automatically.

---

## 🔍 Useful ROS 2 Commands

```bash
ros2 node list              # List active nodes
ros2 topic list             # List topics
ros2 run rqt_image_view rqt_image_view   # View camera feed
ros2 topic echo /detected_color          # Echo detected colors
ros2 topic echo /joint_states            # Check robot joint states
ros2 run rqt_tf_tree rqt_tf_tree         # View TF tree
ros2 run rqt_graph rqt_graph             # Visualize computation graph
```

---

## 📚 Project Description

This project demonstrates a **Vision-Language-Action pipeline simplified to color-based perception**. The Franka Panda robot detects colored blocks, plans trajectories using MoveIt 2, and executes pick-and-place actions in Gazebo. It showcases modular ROS 2 package design, integration of perception and control, and autonomous manipulation under ROS 2 Humble.
