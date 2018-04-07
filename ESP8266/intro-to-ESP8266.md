# Hands on with ESP8266 using LED & LDR

## What is ESP8266??

The ESP8266 WiFi Module is a self contained SOC with integrated TCP/IP protocol stack that can give any microcontroller access to your WiFi
network. Each ESP8266 module comes pre-programmed with an AT command set firmware, meaning, you can simply hook this up to your Arduino
device and get about as much WiFi-ability as a WiFi Shield offers.  

This module has a powerful enough on-board processing and storage capability that allows it to be integrated with the sensors and other 
application specific devices through its GPIOs with minimal development up-front and minimal loading during runtime. Its high degree of
on-chip integration allows for minimal external circuitry, including the front-end module, is designed to occupy minimal PCB area. 
The ESP8266 supports APSD for VoIP applications and Bluetooth co-existance interfaces, it contains a self-calibrated RF allowing it to 
work under all operating conditions, and requires no external RF parts.  


Here, we are going to use ESP8266 (ESP-07/ESP-12) wifi-module .  

### ESP-07/ESP-12

The ESP-07/ESP-12 is a generic ESP8266 module which have no bootstapping resistors on board, insufficient decoupling capacitors, no reset circuit, and no USB-serial adapter. This is an article shows you how to connect the bootstapping resistor to the ESP-07 module and upload sketches onto the ESP-07/ESP-12 using the familiar Arduino IDE.  

## Setting up of Arduino IDE

1.) Click on link and https://goo.gl/Cxa9rX download Arduino IDE  
2.) Install Arduino IDE on your system  
3.) Open Arduino IDE & Click on tab **File > Preferences**  
4.) Now add the following URL in the **Additional Board Manager** URLs field & click OK.  
5.) URL :- http://arduino.esp8266.com/stable/package_esp8266...  
6.) Open the tab **Tools > Boards > Board Manager**  
7.) Search for esp8266 & install the esp8266 community packages  
8.) Now go to **Tools > Boards** & select Generic ESP8266 Module  
9.) Open **Sketch > Library > Manage Libraries**  
10.) Search for arduino json & install arduino json library by Benoît Blanchon  

## ESP-07 and LED 

This project isto take digital output from  ESP-07(ESP8266) on Arduino IDE. The output is taken on LED, It glows for a second and remain off for a second.

<p align="center"> 
<img src="https://user-images.githubusercontent.com/35935951/38386316-e279a914-3931-11e8-82f8-f698b2035175.png">
</p>

<p align="center"> 
<img src="">
</p>
