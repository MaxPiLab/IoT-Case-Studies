# Hands-on with Arduino and LDR (Solar Panel Tracker)

Here, we are going to make a Solar Panel Tracker using Arduino, in which we will use two LDRs to sense the light and a servo motor to automatically rotate the solar panel in the direction of the sun light. Advantage of this project is that Solar panel will always follow the sun light and will always face towards the sun to get charged all the time ,so that, it can provide the supply the maximum power.  
 
Here,LDR’s are working as light detectors. **LDR (Light Dependent Resistor)** also known as photo resistor is the light sensitive device. Its resistance decrease when the light falls on it and that’s why it is frequently used in Dark or Light Detector Circuit.  

The two LDR’s are placed at the two sides of solar panel and the Servo Motor is used to rotate the solar panel. The servo will move the solar panel towards the LDR whose resistance will be low, mean towards the LDR on which more light is falling, that way it will keep following the light. And if there is same amount of light falling on both the LDR, then servo will not rotate. The servo will try to move the solar panel in the position where both LDR’s will have the same resistance means where same amount of light will fall on both the LDR's and if resistance of one of the LDR will change then it rotates towards lower resistance LDR.

#### Hardware Required

**1.)** Arduino-board(UNO)
**2.)** Servo motor  
**3.)** LDR -Light dependent resistor(2)  
**4.)** Wires  
**5.)** 10k resistors(2)  
