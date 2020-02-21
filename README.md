![GitHub Logo](https://github.com/gnea/gnea-Media/blob/master/Grbl%20Logo/Grbl%20Logo%20250px.png?raw=true)

Started with the aim of getting a cleaner build with the non relevant functions removed from the code and compiled to a smaller memory size running on a Arduino Nano "MKS-DLC V2" cnc board or possibly the generic Arduino Nano cnc shield / boards instead of the supplied Chinese K40 Laser Engraver "6C6879-LASER-M2" clone board

![mks_dlc_v2 controller](https://github.com/CBDesignS/grbl/blob/master/doc/mks_dlc_v2.png?raw=true)

```
A few changes need to be made within the config.h to reflect the strange setup that some of the K40 chinese Laser seems to use.
The spindle enable needs to be split from pwm signal to use Digital pin 13 (D13) as a trigger to fire Lo (laser on) with either a relay or npn signal inverting setup.

If a 5v relay is used then the D13 might need to be inverted as it was setup to run the onboard Led by default so may be turned on when the pin is off/low instead of on/high. 

Endstop / Limit switches is K40 machine dependant. if they are mechanical switches (Normally open) then the they do not need to be inverted but if you have the newer Optical sensors/switches that are Normally Closed (NC) then you need to invert the signal or you will not be able to use the endstops to set Home and Origin.

Stepper Motor settings are different accros machines, There is a DEFAULT_K40laser that has a generic set of settings that should work once compiled and uploaded to the board/shield and can also be tweaked before flashing if you know certain settings work better than the defaults on your board.

```

-------------
Grbl is an open-source project and fueled by the free-time of our intrepid administrators and altruistic users. If you'd like to donate, all proceeds will be used to help fund supporting hardware and testing equipment. Thank you!

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CUGXJHXA36BYW)
