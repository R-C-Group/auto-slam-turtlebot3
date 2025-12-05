 <h1 align="center"> 基于Turtlebot3的自主建图
  </h1>

[comment]: <> (  <h2 align="center">PAPER</h2>)
  <h3 align="center">
  <a href="https://github.com/fanegg/Human3R">Blog</a>
  </h3>
  <div align="center"></div>

<br>

<!-- 原版代码[Github](https://github.com/R-C-Group/single_robot_explore_lite_slam) -->


* 代码下载

```bash

git clone --recursive https://github.com/mywisdomfly/Clean-robot-turtlebot3.git

# 编译
cd ~/catkin_ws && catkin_make
```

* 开启仿真模型,并用键盘控制建图

```bash
# export TURTLEBOT3_MODEL=burger
TURTLEBOT3_MODEL=waffle roslaunch turtlebot3_gazebo turtlebot3_world.launch

# 开启SLAM
TURTLEBOT3_MODEL=waffle  roslaunch turtlebot3_slam turtlebot3_slam.launch set_base_frame:=base_footprint set_odom_frame:=odom set_map_frame:=map

# 开启键盘控制
TURTLEBOT3_MODEL=waffle roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

```


* 开启仿真模型，并采用`explore_lite`实现自动探索

```bash
TURTLEBOT3_MODEL=waffle roslaunch turtlebot3_gazebo single_world.launch

TURTLEBOT3_MODEL=waffle roslaunch explore_lite explore.launch
# sudo apt install ros-noetic-dwa-local-planner
```

* `rosrun rqt_tf_tree rqt_tf_tree`TF关系如下图： 

<div align="center">
  <img src="./assert/2025-12-05 08-13-19 的屏幕截图.png" width="80%" />
<figcaption>  
</figcaption>
</div>

* 采用`rrt_exploration`实现自动探索

```bash
TURTLEBOT3_MODEL=waffle roslaunch rrt_exploration_tutorials single_simulated_house.launch

# cd auto-slam-turtlebot3/multi-exploration-rrt-method--master/rrt_exploration-master
# chmod +x scripts/filter.py scripts/assigner.py
# sudo pip3 install -U scikit-learn  or  sudo apt-get install python-sklearn
TURTLEBOT3_MODEL=waffle roslaunch rrt_exploration single.launch 
```
