# detail-problems-on-quadrotors

# 飞控权限  
chmod a+rw /dev/ttyUSB0 #只要不拔出串口一般就能一直使用，参考https://www.yisu.com/ask/5545.html  
不过目前已经修改为直接用USB连接飞控，并且可以基于远程直接读取QGC数据，且USB只需要配置一次，具体配置流程参考https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html  
mavros安装
https://docs.px4.io/main/en/  
# 飞机改进
飞机目前仍太重，NUC外壳可以去掉，同时保护壳可以改为亚克力板，整体可以减轻200g
# 飞控固件
飞控固件目前已经修改，参考了zzy的修改，同时也要具备自己修改，编译飞控固件的能力，飞控目前版本固件源码已经上传github，编译方法参考  
https://docs.px4.io/main/en/dev_setup/dev_env_linux_ubuntu.html  

# 飞行控制
目前飞行控制已经改为MPC控制，控制频率为100hz，预测为0.1 ~ 0.5时刻的五个点，具体代码已经上传github

# slam
目前slam运行稳定，定点飞行效果不错，但是相机imu不靠谱，可以将飞控的imu与双目进行融合

# 状态机
目前已经修改为不需要使用mavros，参考zzy的px4_bridge修改当前的fsm，在它的基础上移植flag_fsm的功能（定点，定高）

# ubuntu下科学上网
配置参考https://portal.shadowsocks.nz/login 
具体使用  
```
cd 下载/Clash\ for\ Windows-0.19.29-x64-linux/  
./cfw
```

这个目前还有点问题，先不要使用

# fatal error: Eigen/Core: 没有那个文件或目录
sudo ln -s /usr/include/eigen3/Eigen /usr/include/Eigen
```
#load_px4_gazebo
export FIRMWARE_DIR=~/PX4_tools/PX4-Autopilot #path_to_Firmware是你的firmware路径，如~/PX4_tools/PX4-Autopilot
source $FIRMWARE_DIR/Tools/setup_gazebo.bash $FIRMWARE_DIR $FIRMWARE_DIR/build/posix_sitl_default
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$FIRMWARE_DIR
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$FIRMWARE_DIR/Tools/sitl_gazebo
```
