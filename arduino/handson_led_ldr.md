# What is Arduino???

Arduino is an open-source electronics platform based on hardware (single-board microcontroller) and software (arduino software-**I**ntegrated **D**evelopement **E**nvironment aka **IDE**).  

Generally, arduino-boards are Atmel 8-bit AVR microcontroller based . Arduino-boards have facillity of **analog and digital I/O pins** making it able to interact with the physical world. This is acheived by sending instruction to arduino-boards. This is done with Arduino programming language (typically like C nad C++) and Ardino software (**IDE**).  

<p align="center"> 
<img src="https://user-images.githubusercontent.com/35935951/37903485-bc8891c6-3115-11e8-8074-6a7041c03da9.jpg">
</p>

## why to choose Arduino??

1.) Inexpensive  
2.) Cross-platform  
3.) Simple, clear programming environment  
4.) Open source and extensible software  
5.) Open source and extensible hardware  

There are many Arduino-boards designed for different purposes.  

There are many appliactions you can use with Arduino.   

## Arduino and LED



#### Code

```
// the setup function runs once when you press reset or power the board  

void setup()  
{  
  pinMode(LED_BUILTIN, OUTPUT);     // initialize digital pin LED_BUILTIN as an output.  
}  

// the loop function runs over and over again forever  

void loop()  
{  
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)  
  delay(1000);                       // wait for a second  
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW  
  delay(1000);                       // wait for a second  
}  

```

##  Arduino and LDR

### Hands-on with Ardino and LDR (Solar Panel Tracker)

Here, we are going to make a Solar Panel Tracker using Arduino, in which we will use two LDRs to sense the light and a servo motor to automatically rotate the solar panel in the direction of the sun light. Advantage of this project is that Solar panel will always follow the sun light and will always face towards the sun to get charged all the time ,so that, it can provide the supply the maximum power.  
 
Here,LDR’s are working as light detectors. **LDR (Light Dependent Resistor)** also known as photo resistor is the light sensitive device. Its resistance decrease when the light falls on it and that’s why it is frequently used in Dark or Light Detector Circuit.  

The two LDR’s are placed at the two sides of solar panel and the Servo Motor is used to rotate the solar panel. The servo will move the solar panel towards the LDR whose resistance will be low, mean towards the LDR on which more light is falling, that way it will keep following the light. And if there is same amount of light falling on both the LDR, then servo will not rotate. The servo will try to move the solar panel in the position where both LDR’s will have the same resistance means where same amount of light will fall on both the LDR's and if resistance of one of the LDR will change then it rotates towards lower resistance LDR.

#### Hardware Required

**1.)** Arduino-board(UNO)
**2.)** Servo motor  
**3.)** LDR -Light dependent resistor(2)  
**4.)** Wires  
**5.)** 10k resistors(2)  

#### Circuit Diagram

<p align="center"> 
<img src="https://user-images.githubusercontent.com/35935951/37902808-3efdadba-3113-11e8-99cb-9f5ed9e78f0a.png">
</p>  

#### Code

```
#include <Servo.h>           //including the library of servo motor   
Servo sg90;                  //initializing a variable for servo named sg90  
int initial_position = 90;   //Declaring the initial position at 90  
int LDR1 = A0;               //Pin at which LDR is connected  
int LDR2 = A1;               //Pin at which LDR is connected  
int error = 5;               //initializing variable for error  
int servopin=9;  

void setup()  
{   
  sg90.attach(servopin);     // attaches the servo on pin 9  
  pinMode(LDR1, INPUT);      //Making the LDR pin as input  
  pinMode(LDR2, INPUT);
  sg90.write(initial_position);   //Move servo at 90 degree  
  delay(2000);               // giving a delay of 2 seconds  
}  
 
void loop()  
{  
  int R1 = analogRead(LDR1);  // reading value from LDR 1  
  int R2 = analogRead(LDR2);  // reading value from LDR 2  
  int diff1= abs(R1 - R2);    // Calculating the difference between the LDR's  
  int diff2= abs(R2 - R1);  
  
  if((diff1 <= error) || (diff2 <= error))  
  {  
    //if the difference is under the error then do nothing
  } 
  else  
  {    
    if(R1 > R2)  
    {  
      initial_position = --initial_position;  //Move the servo towards 0 degree  
    }  
    if(R1 < R2)  
    {
      initial_position = ++initial_position;  //Move the servo towards 180 degree  
    }  
  }  
  sg90.write(initial_position);               // write the position to servo  
  delay(100);  
}  

```
