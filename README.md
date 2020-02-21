![GitHub Logo](https://github.com/gnea/gnea-Media/blob/master/Grbl%20Logo/Grbl%20Logo%20250px.png?raw=true)

## Started with the aim of getting 255 steps of P.W.M powered Laser engraving by using an Arduino Nano "MKS-DLC V2" cnc board or possibly other generic Arduino Nano cnc shield / boards instead of the supplied Chinese K40 Laser Engraver "6C6879-LASER-M2" clone board

![mks_dlc_v2 controller](https://github.com/CBDesignS/grbl/blob/master/doc/mks_dlc_v2.png?raw=true)

```
A few changes need to be made within the config.h to reflect the strange setup that some of the 
K40 chinese Laser Engravers seems to use.
The spindle enable needs to be split from pwm signal to use Digital pin 13 (D13) as a trigger to 
fire Lo (laser on) with either a relay or npn signal inverting setup since the psu needs 0v to fire.
*#define USE_SPINDLE_DIR_AS_ENABLE_PIN*
*#define SPINDLE_ENABLE_OFF_WITH_ZERO_SPEED*

If a 5v relay is used then the D13 may also need to be inverted as it was setup to run the onboard Led 
by default so may be turned on when the pin is off/low instead of on/high. 
*#define INVERT_SPINDLE_ENABLE_PIN*

Endstop / Limit switches. (This is K40 machine dependant) 
If you have mechanical switches (Normally open) then you are good to go and (the default setup for grbl)
but if you have the newer Optical sensors/switches that are Normally Closed (NC) then you will need to 
invert the signal or you will not be able to use the endstops to set Home and Origin. 
either set in config.h or via a command entered of $5=1

Homing & Origin.
by default Z axis will home first and since there is No Z axis you can not use this option that is 
unless it is reconfigured in config.h (which it is now by default set to home X & Y at the same time
*#define HOMING_CYCLE_0 ((1<<X_AXIS)|(1<<Y_AXIS))*
*#define HOMING_INIT_LOCK* (every time you reset or power up the machine this setting locks the system
until you manually press or issue the Unlock code then you can perform a Home and an origin move
so in theory if the machine errors out you can home and move to origin and continue from where it
stopped (not sure about this one !!!))

Stepper Motor settings.
These may be different in other machines, There is a DEFAULT_K40laser entry in default.h that has a 
generic set of settings that should work once compiled and uploaded to the board/shield and can also
be tweaked before flashing if you know certain settings work better than the defaults on your board.

```

-------------
Grbl is an open-source project and fueled by the free-time of our intrepid administrators and altruistic users. If you'd like to donate, all proceeds will be used to help fund supporting hardware and testing equipment. Thank you!

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CUGXJHXA36BYW)
