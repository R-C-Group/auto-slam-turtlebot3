/******************************多机器人SLAM和地图整合的仿真******************************/

在仿真之前确认已下载编译好turtlebot3_simulations，turtlebot3这两个包

仿真之前需要在bashrc中设置好使用的机器人模型是什么，不然的话每次启动都要确认一次：

gedit ~/.bashrc

export TURTLEBOT3_MODEL=waffle(ps. waffle, waffle_pi, burger都可以，按个人喜好选择)

1.启动gazebo的三机器人场景：roslaunch simulation multi_turtlebot3.launch

2.分别打开三个新建终端，启动三个机器人的SLAM：

ROS_NAMESPACE=tb3_0 roslaunch turtlebot3_slam turtlebot3_gmapping.launch set_base_frame:=tb3_0/base_footprint set_odom_frame:=tb3_0/odom set_map_frame:=tb3_0/map

ROS_NAMESPACE=tb3_1 roslaunch turtlebot3_slam turtlebot3_gmapping.launch set_base_frame:=tb3_1/base_footprint set_odom_frame:=tb3_1/odom set_map_frame:=tb3_1/map

ROS_NAMESPACE=tb3_2 roslaunch turtlebot3_slam turtlebot3_gmapping.launch set_base_frame:=tb3_2/base_footprint set_odom_frame:=tb3_2/odom set_map_frame:=tb3_2/map

3.打开新终端，启动地图合并：

roslaunch turtlebot3_gazebo multi_map_merge.launch

4.打开新终端，启动rviz：

rosrun rviz rviz -d `rospack find turtlebot3_gazebo`/rviz/multi_turtlebot3_slam.rviz

5.打开三个新终端，启动键盘控制机器人：

ROS_NAMESPACE=tb3_0 roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

ROS_NAMESPACE=tb3_1 roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

ROS_NAMESPACE=tb3_2 roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

6.用map_server保存地图

打开新终端，rosrun map_server map_saver -f ~/map

/**************************************************************************************/

/******************************单个机器人进行explore************************************/

1.启动gazebo 

roslaunch simulation turtlebot3_world.launch

2.启动explore程序

roslaunch explore_lite explore

3.接下来机器人会自动探索，探索完之后停下来
