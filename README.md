![GitHub Logo](https://github.com/gnea/gnea-Media/blob/master/Grbl%20Logo/Grbl%20Logo%20250px.png?raw=true)

Started with the aim of getting 255 steps of P.W.M powered Laser engraving by using an Arduino Nano "MKS-DLC V2" cnc board or possibly other generic Arduino Nano cnc shield / boards instead of the supplied Chinese K40 Laser Engraver "6C6879-LASER-M2" clone board

![mks_dlc_v2 controller](https://github.com/CBDesignS/grbl/blob/master/doc/mks_dlc_v2.png?raw=true)

```
A few changes need to be made within the config.h to reflect the strange setup that some of the 
K40 chinese Laser Engravers seems to use.
The spindle enable needs to be split from pwm signal to use Digital pin 13 (D13) as a trigger to 
fire Lo (laser on) with either a relay or npn signal inverting setup since the psu needs 0v to fire.

If a 5v relay is used then the D13 may also need to be inverted as it was setup to run the onboard Led 
by default so may be turned on when the pin is off/low instead of on/high. 

Endstop / Limit switches is K40 machine dependant. 
If you have mechanical switches (Normally open) then you are good to go and (the default setup for grbl)
but if you have the newer Optical sensors/switches that are Normally Closed (NC) then you will need to invert
the signal or you will not be able to use the endstops to set Home and Origin. Either set in config.h or via
a command entered of $5=1

Stepper Motor settings.
These may be different in other machines, There is a DEFAULT_K40laser entry in default.h that has a 
generic set of settings that should work once compiled and uploaded to the board/shield and can also
be tweaked before flashing if you know certain settings work better than the defaults on your board.

```

-------------
Grbl is an open-source project and fueled by the free-time of our intrepid administrators and altruistic users. If you'd like to donate, all proceeds will be used to help fund supporting hardware and testing equipment. Thank you!

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CUGXJHXA36BYW)
