# multiple-robots-for-ROS  

PS.仿真部分说明请进入simulation文件夹

启动机器人： 

通过SSH连接各机器人（以tb3_0为例） 

ssh burger@{机器人的ip} 

打开终端 输入 roscore 

～～或～～ 

ROS_NAMESPACE=tb3_0 roslaunch turtlebot3_bringup turtlebot3_robot.launch（运行这一条如果检测到roscore没开启会自动开启roscore的，这条命令的用处是启动turtlebot3运行所需的所有相关组件，如果只是需要开启ROS而不需要遥控机器人运动的话可以只用roscore）

打开新终端（PC上） 

运行 roslaunch explore_lite multi_explore.launch 可以启动三个turtlebot3的explore程序 

运行 roslaunch explore_lite double_explore.launch 可以启动两个turtlebot3的explore程序 
 
PS. 在运行之前在 ~/.bashrc 中增加 export TURTLEBOT3_MODEL=burger 

这个软件包主要配置文件都在 /explore/param 文件夹当中，已经配置好了，基本不用动（除非需要更换机器人模型和修改tf tree）

启动explore之前需要先把机器人都启动了，并且机器人的namespace必须是 tb3_0,tb3_1,tb3_2（如果需要修改，修改文件包括launch文件，param里面的global_costmap_params.yaml, local_costmap_params.yaml）

我在这里使用的激光SLAM方法是gmapping,如果不想用gmapping的话也可以使用其他的slam方法，具体修改为在对应的launch文件中的 <--SLAM--> 那一部分 

