### [English](README.md) | 中文

# FR-max-ros

## 1.环境确认：
      1.1、系统：
            Ubuntu 16.04 / Ubuntu 18.04
      1.2、ROS版本：
            Kinetic / melodic

## 2.CAN卡连接与设置
      2.1、底盘CAN卡连接：
            底盘的CAN-H连接到CAN卡接插头的CANH，底盘的CAN-L连接到Can卡接插头的CANL，如下图：
            
![](https://github.com/leej-j/FR-max-ros/blob/main/images/CAN_Connection.png?raw=true)  

      2.2、电脑与机器人通信连接：
            底盘CAN卡连接完成后，将CAN卡usb线一端直接插到电脑usb口，完成CAN卡与电脑的连接，连接完成后，PWR灯亮。
      2.3、USB是否连接成功检查：
            打开终端，输入指令：  lsusb  在输出信息中看到以下图片所示内容，则表示CAN能够正常使用。
            
![](https://github.com/leej-j/FR-max-ros/blob/main/images/terminal_state.png?raw=true)  

      2.4、通信启动：
            打开一个新的终端，输入指令：sudo ip  link  set  can0  type  can  bitrate  500000 & sudo ip  link  set  can0  up
            此时，若底盘处于上电状态，蓝色RX灯会闪烁，同时红色TX灯也会亮，RX灯闪烁表示Can卡接收到数据，TX灯闪烁表示发送数据。

## 3.通信数据查看
      3.1 安装can-utils工具，请执行以下指令：
            sudo apt-get install can-utils
      3.2 查看数据指令：
            candump can0
      3.3、正常打印信息：
      
![](https://github.com/leej-j/FR-max-ros/blob/main/images/candump_print.png?raw=true) 

## 4.ROS程序运行
      4.1、文件结构：
      
![](https://github.com/leej-j/FR-max-ros/blob/main/images/doc_tree.png?raw=true) 

      4.2、编译工作空间：
            在你的工作空间中打开终端/在终端中进入你的工作空间，让终端处于工作空间级，再执行指令：catkin build
      4.3、设置临时环境变量：
            在要运行程序的终端中执行指令：source ~/你的工作空间(例：catkin_ws)/devel/setup.bash
            或者让要运行程序的终端处于工作空间级，执行指令：source devel/setup.bash
            
![](https://github.com/leej-j/FR-max-ros/blob/main/images/source.png?raw=true)

      4.4、运行：
            在你刚才输入了临时环境变量的终端中执行指令：roslaunch yhs_can_control yhs_can_control.launch
      4.5、终端打印出的运行成功信息：

![](https://github.com/leej-j/FR-max-ros/blob/main/images/node_print.png?raw=true)  



      
      
      
