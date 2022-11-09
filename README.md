# CircuitPython
This repository will actually serve as a aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Hello_CircuitPython

### Description & Code
Makeing our serial montior print the words Hello World to test that Code pyhtponn is working properally.

```
from time import sleep

while True:
    print("Hello world!")
    sleep(1)****
```


### Evidence

![name](https://github.com/Ncrawfo72/CircuitPython/blob/master/mediA/ezgif-5-484376f59a.gif?raw=true)



### Wiring
This is not nessacry or usefull

### Reflection
There was nothing difficult about this one it was rather straight forward and well explained in the instructions for the assignment. I also really cant make more than 2 sentences for this.



## CircuitPython_Servo

### Description & Code
to make a servo spin 180 degrees back and forther over and over again.

```
#SPDX-FileCopyrightText: 2018 Kattni Rembor for Adafruit Industries
#
# SPDX-License-Identifier: MIT

"""CircuitPython Essentials Servo standard servo example"""
import time
import board
import pwmio
from adafruit_motor import servo

# create a PWMOut object on Pin A2.
pwm = pwmio.PWMOut(board.D3, duty_cycle=2 ** 15, frequency=50)

# Create a servo object, my_servo.
my_servo = servo.Servo(pwm)

while True:
    for angle in range(0, 180, 10):  # 0 - 180 degrees, 5 degrees at a time.
        my_servo.angle = angle
        time.sleep(0.05)
    for angle in range(180, 0, -10): # 180 - 0 degrees, 5 degrees at a time.
        my_servo.angle = angle
        time.sleep(0.05)
```

### Evidence

![name](https://github.com/Ncrawfo72/CircuitPython/blob/master/mediA/ezgif-1-6d209f0424.gif)

### Wiring
![name](https://github.com/Ncrawfo72/CircuitPython/blob/master/mediA/spinnerwiring.png)

### Reflection

The most difficult part of this assignment was probably honestly figuring out how to make the servo spin only 180 degrees before turing around and doing another 180 over and over again. I could get the servo to spin no problem, but making constraints for it was diffucult. I would eventually figure it out though with help from peers.


## CircuitPython_LCD

### Description & Code
Making an LCD sense distance and change color gradually as said object comes closer.

```
import board
import math
import time
from lcd.lcd import LCD                                     #[4-14] code to connect 
from lcd.i2c_pcf8574_interface import I2CPCF8574Interface   #input pins to board
from digitalio import DigitalInOut, Direction, Pull
i2c = board.I2C()
lcd = LCD(I2CPCF8574Interface(i2c, 0x3f), num_rows=2, num_cols=16)
btn = DigitalInOut(board.D3)
btn2 = DigitalInOut(board.D2)
btn.direction = Direction.INPUT
btn2.direction = Direction.INPUT
btn.pull = Pull.UP
btn2.pull = Pull.UP
num = 0                         #Display Variable
Redo = True                     #[16-17] Variable to "debounce" button

lcd.print("Starting")
while True:                                 #[19-30] Code to add and subtract 
    if btn.value == True and Redo == True:  #from variable and 
        if btn2.value == True:              #"debounce" the  #buttons.         
            num = num - 1
        else:
            num = num + 1                                   
        lcd.clear()
        lcd.print(str(num))
        Redo = False
        time.sleep(.1)
    elif btn.value == False and Redo == False:
        Redo = True
```

### Evidence

![name](https://github.com/Ncrawfo72/CircuitPython/blob/master/mediA/ezgif-5-6bbf43e87e.gif)

### Wiring
![name](https://github.com/Ncrawfo72/CircuitPython/blob/master/mediA/Screenshot%202022-09-16%20153844.png)

### Reflection
This assignment was really difficult and I barley had it working in the video it foes work, but goes to the wrong color at the very end and doesnt change. Meaning the highest color calue is also the lowewst color value in extreme cases. This was also confusing in just how the code actually works cause I barley understand how its actually is working.




### Description
make and LCD count up and down with two diffrerent button controls 

### code
```
import board
import math
import time
from lcd.lcd import LCD                                     #[4-14] code to connect 
from lcd.i2c_pcf8574_interface import I2CPCF8574Interface   #input pins to board
from digitalio import DigitalInOut, Direction, Pull
i2c = board.I2C()
lcd = LCD(I2CPCF8574Interface(i2c, 0x3f), num_rows=2, num_cols=16)
btn = DigitalInOut(board.D3)
btn2 = DigitalInOut(board.D2)
btn.direction = Direction.INPUT
btn2.direction = Direction.INPUT
btn.pull = Pull.UP
btn2.pull = Pull.UP
num = 0                         #Display Variable
Redo = True                     #[16-17] Variable to "debounce" button

lcd.print("Starting")
while True:                                 #[19-30] Code to add and subtract 
    if btn.value == True and Redo == True:  #from variable and 
        if btn2.value == True:              #"debounce" the  #buttons.         
            num = num - 1
        else:
            num = num + 1                                   
        lcd.clear()
        lcd.print(str(num))
        Redo = False
        time.sleep(.1)
    elif btn.value == False and Redo == False:
        Redo = True

```

### evidence
![name](https://github.com/Ncrawfo72/CircuitPython/blob/master/mediA/ezgif-1-d0e755ffc6.gif)


### wiring



### reflection
This was by far the most difficult one to do and I struggled to do it, but with assistance from peers I was able to get through it. Making it count up was easy, but making it count down was the more difficult than expected. 



## Motor Control


### Description

### Code

```
import board
import time
from analogio import AnalogOut, AnalogIn
import simpleio

motor = AnalogOut(board.A1)
pot = AnalogIn(board.A0)

while True:
    print(simpleio.map_range(pot.value, 96, 65520, 0, 65535))
    motor.value = int(simpleio.map_range(pot.value, 96, 65520, 0, 65535))
    time.sleep(.1)  ```
    
    
    ### wow
