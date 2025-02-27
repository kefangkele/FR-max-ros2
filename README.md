### English | [中文](README(中文).md)

# FR-max-ros

## 1. Environment confirmation:
      1.1. System:
            Ubuntu 16.04 / Ubuntu 18.04
      1.2. ROS version:
            Kinetic / melodic

2.The subsequent section will address the process of establishing a connection between the CAN card and the system.
      2.1. Chassis CAN card connection:
            Specifically, Chassis CAN-H is to be connected to CANH of the CAN card connector plug, while Chassis CAN-L is to be connected to CANL of the CAN card connector plug. The following diagram illustrates the recommended configuration:
            
![CAN_Connection](https://github.com/leej-j/FR-max-ros/blob/main/images/CAN_Connection.png?raw=true)

      2.2. Computer and robot communication connection:
            Subsequent to the completion of the aforementioned connection, the USB end of the CAN card cable should be inserted directly into the computer's USB port, thereby establishing a connection between the CAN card and the computer. Upon completion of the connection, the PWR light will illuminate.
      2.3. Methodology for checking the success of USB connection:
            To initiate this process, one must access the terminal and enter the command: 
                  lsusb
            If the output information displays content resembling that depicted in the following image, it can be deduced that CAN can be utilized without issue.

![CAN_Connection](https://github.com/leej-j/FR-max-ros/blob/main/images/terminal_state.png?raw=true)

      2.4. Communication initiation:
            To initiate this process, it is necessary to open a new terminal and enter the following commands: "sudo ip link set can0 type can bitrate 500000 & sudo ip link set can0 up."
            If the chassis is in the power-up state, the blue RX light will blink, and the red TX light will be on at the same time.The blinking of the RX light indicates that the Can0 card receives data, and the blinking of the TX light indicates that it sends data.

## 3. Communication Data Viewing
      3.1 To install the can-utils tool, the following command should be executed:
            sudo apt-get install can-utils
      3.2 View data command:
            candump can0
      3.3. Terminal print the information normally:
      

4. ROS program operation
      4.1. File structure:  
      
      4.2.Compile workspace:  
            Open the terminal in your workspace/enter your workspace in the terminal, let the terminal be in the workspace level, then execute the command: catkin build
            
      4.3.Setting temporary environment variables:
            Execute the command in the terminal where you want to run the program:  
               source ~/your workspace (example: catkin_ws)/devel/setup.bash  
            Or, to keep the terminal where you want to run the program at the workspace level, execute the command:    
               source devel/setup.bash  
            

      4.4. Run:  
            Execute the command: roslaunch yhs_can_control yhs_can_control.launch in the terminal where you have just entered the temporary environment variable.  
      4.5. The terminal prints out a successful run message:  



      
      
      
