# RASPBERRY-PI-BT-NC-05
This demonstrates the use of the HC-05 Bluetooth Module to send and receive data bytes .

Components Used:

Raspberry Pi 3 (any model shall work)
Bluetooth Module HC-06
Bread board
100 ohm Resistors (3)
LED’s (blue, red, green)
Connecting wire
Power Supply
Ethernet cable
Android Phone

After it if you send AT to module then module will respond with OK
AT à Test Command

AT+ROLE=0 à Slave Mode select
AT+ROLE=1 à Master Mode select
AT+NAME=xyz  à Set Bluetooth Name
AT+PSWD=xyz à Set Password
AT+UART=<value1>,<value2>,<value3>  à set Baud rate
Eg. AT+UART=9600,0,0
  
Working Explanation:

Working of this Voice Controlled LEDs project is very easy. In this project we have used three LEDs of different colors (Blue, Red and Green). A HC-06 Bluetooth Module is used for receiving voice commands output in string format. Raspberry Pi receives that incoming string from Bluetooth Module and compares with predefined string and performs respective task.

In this project, to provide the voice commands to Raspberry Pi from our Smart Phone, we have used AMR Voice App in Android Phone (Android Meets Robots : Voice Recognition).

Now user can tap over the Mic symbol on mobile screen and speak predefined Voice commands to operate the LEDs:

1. “blue light on”   (only blue LED turned on)
2. “blue light off”  (only blue LED turned off)
3. “red light on”     (only red LED turned on)
4. “red light off”    (only red LED turned off)
5. “green light on”  (only green LED turned on)
6. “green light off” (only green LED turned off)
7. “all lights on”     (blue, red and green LEDs turned on)
8. “all lights off”    (blue, red and green LEDs turned off)
9. “blink”                (all LEDs start blinking with a 100 millisecond time period)


Circuit Explanation:

Circuit of this project is very simple, which contains Raspberry Pi 3 Board, LEDs and Bluetooth Module (HC-06). Raspberry Pi reads the Bluetooth Module and control the LEDs accordingly. LEDs Blue, Red and Green are connected at GPIO 17, 27 and 22. Rx and Tx of Bluetooth Module are directly connected to Tx and Rx pins of Raspberry Pi. Remaining connections are shown in circuit diagram.



Raspberry Pi Configuration and Python Program:
We are using Python language here for the Program. Before coding, user needs to configure Raspberry Pi. You can check our previous tutorials for Getting Started with Raspberry Pi and Installing & Configuring Raspbian Jessie OS in Pi.

 

After that you need to run following commands to run latest updates on Raspbian Jessie:

sudo apt-get update
sudo apt-get upgrade
 

After it we need to install Raspberry Pi GPIO development tool, it can be installed by following commands:

sudo apt-get install python-dev
sudo apt-get install python-rpi.gpio
Then user needs to configure serial port of Raspberry Pi. Here we have used Raspberry Pi 3 for this project. So user needs to configure serial port according to their Raspberry Pi version. For Raspberry Pi 3, first user needs to disable console login via serial port, through RPi Software Configuration Tool. Open it by using below command:

sudo raspi-config
Then go to ‘Advance Options’, select ‘Serial’ and ‘Disable’ it.



 

After this we need to disable inbuilt Bluetooth of Raspberry Pi 3 by adding dtoverlay=pi3-miniuart-bt at the end of  /boot/config.txt file:

sudo nano /boot/config.txt

After adding the line reboot Raspberry Pi by issuing sudo reboot command.

 

Finally login in Raspberry Pi again and configure /boot/comline.txt file:

sudo nano /boot/comline.txt
And edit the file as below:

dwc_otg.lpm_enable=0 console=tty1 console=serial0,115200 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait

Now you can run the Python program given below in Raspberry Pi and you are done! Program is easy and can be easily understandable.

So here we have completed building our Voice Controlled Devices using Raspberry Pi. You can further enhance it and modify it for controlling AC home appliances by adding relays. 

  
 
 
