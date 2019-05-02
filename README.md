# FallDetection
A fall detection system is a device designed to help the elderly and disadvantaged individuals. This device will help the individual in the case that they may fall, in order for the individual to be helped on time reducing the time the individual may have been left unattended. 
It alerts concerned friends, family or carers of the individual. The detection is due to an accelerometer to detect a person's movements. The accelerometer sensor gives detection of sudden speed directions in three dimensions and gives signals. The device may be mounted on the individual's person. E.g. Hand

The Fall Detection System is a device designed to specially detect the impact of +momentums which are at rest, walking, standing and fall. The system is programmed to alert certain personalised individuals through a tweet. 
 The device’s main intuitive is to send a tweet to concerned close family, friends or guardians of the monitored individual. The device is able to track the movement data of the monitored individual with a gyro-sensor/accelerometer. 
The device will be of great help to the elderly and to those who are most likely to suffer from any kind of fall impact.


Fall Detection device
The fall Detection System is composed of  a RaspberryPi and a Sensehat.   
                             Raspberry Pi 3 Model B.
 
                               Raspberry Pi Sense HAT. 

Sense Hat

The Sense HAT is an add-on electronic board for the Raspberry Pi computer. It contains : 
•	A gyroscope sensor
•	A Accelerometer
•	A Magnetometer 
•	Temperature, Humidity ,barometric Pressure sensor
•	A Joystic
•	8*8 LED Matrix

The fall detection System will be based on the accelerometer sensor on the SenseHat.
The Accelerometer detects motion in 3 axial directions X, Y and Z. The Accelerometer will programmed to detect the axial directions during the events of walking, standing and at fall. The main research on the principles of fall detection focuses on the changes in acceleration that occur when a human is falling.
Changes in acceleration that occur when (a) walking downstairs, (b) walking upstairs, (c) sitting down, and (d) standing up from a chair. The fall detector Will be  mounted to a belt on the individual’s body. The Y-axis (vertical) acceleration is –1 g  equilibrium. X-axis (forward) and Z-axis (sideways) accelerations are both 0 gat equilibrium. 

Wia
This is a Iot cloud platform that helps developers build and connect things through the internet.
This is the Iot Platform in which the data will be stored which will then be exported onto another platform called twilio which will then help send a tweet to a programmed individual. 






Code
 This is the code I Used to demonstrate and see the X, Y and Z   
Accelerometer at equilibrium.
```
from sense_hat import SenseHat
sense = SenseHat

while True:
    x, y, z = sense.get_accelerometer_raw().values()
            x=round(x,0)
            y=round(y,0)
            z=(round(z,0)
            print("x%s, y%s, z%s" % (x, y, z))
 ```
      
 this shows a live axial movement of the accelerometer.
The data was then supposed to be imported onto wia.

This is the code taking the data onto wia. There’s an error in the code.
```
from wia import Wia
import time 
import random
import requests
from sense_hat import SenseHat

sense = SenseHat
wia = Wia()
wia.access_token = "xxxxxxxxxxxxxxx"
while True:
    x, y, z = sense.get_accelerometer_raw().values()
            x=round(x,0)
            y=round(y,0)
            z=(round(z,0)
            
         wia.Event.publish(name="Accelerometer Values", data="x%s"%(x))
         wia.Event.publish(name="Accelerometer Values", data="y%s"%(y))
         wia.Event.publish(name="Accelerometer Values", data="z%s"%(z))
 ```        
 
Theres an error , in which inhibits for the data to be sent over to wia .


This then became an alternative option , When the accelerometer value drops beside equilibrium the LED Matrix Will Print A letter E to say that The individual may not be okay.
 

Conclusion

The fall Detection System Uses an accelerometer from a Sense hat , which has three axial dimensions.
When the axial values are below or aboves a certain point this may trigger the program to send a message to those concerned about the individual.
The accelerometer readings were a success but getting data from sense hat to the pi was not a success therefore taking the data from Wia to Twilio was not successful. The accelerometer worked well with the RaspberyPi. 
