                   .:                     :,                                          
,:::::::: ::`      :::                   :::                                          
,:::::::: ::`      :::                   :::                                          
.,,:::,,, ::`.:,   ... .. .:,     .:. ..`... ..`   ..   .:,    .. ::  .::,     .:,`   
   ,::    :::::::  ::, :::::::  `:::::::.,:: :::  ::: .::::::  ::::: ::::::  .::::::  
   ,::    :::::::: ::, :::::::: ::::::::.,:: :::  ::: :::,:::, ::::: ::::::, :::::::: 
   ,::    :::  ::: ::, :::  :::`::.  :::.,::  ::,`::`:::   ::: :::  `::,`   :::   ::: 
   ,::    ::.  ::: ::, ::`  :::.::    ::.,::  :::::: ::::::::: ::`   :::::: ::::::::: 
   ,::    ::.  ::: ::, ::`  :::.::    ::.,::  .::::: ::::::::: ::`    ::::::::::::::: 
   ,::    ::.  ::: ::, ::`  ::: ::: `:::.,::   ::::  :::`  ,,, ::`  .::  :::.::.  ,,, 
   ,::    ::.  ::: ::, ::`  ::: ::::::::.,::   ::::   :::::::` ::`   ::::::: :::::::. 
   ,::    ::.  ::: ::, ::`  :::  :::::::`,::    ::.    :::::`  ::`   ::::::   :::::.  
                                ::,  ,::                               ``             
                                ::::::::                                              
                                 ::::::                                               
                                  `,,`


http://www.thingiverse.com/thing:3063845
AiO Ender 3 Octoprint Set Up with Power and Light Remote Control by giacomo30196 is licensed under the Creative Commons - Attribution license.
http://creativecommons.org/licenses/by/3.0/

# Summary

UPDATE 16/04/2019

Hi everyone, fisrt of all i'd like to apologize for my absence due to university and work, finally i'm releasing solidworks files for this project so that you can modify them as you want. I can't wait to see how you will improve everything! 

Solidworks files can be found inside a zip called "SolidworksFiles.zip"

Regarding relais upgrade i'm not sure if I have the time to do it, so if anyone wants to do it and share the design, that would be amazing!


AiO Ender 3 Octoprint Set Up
=================
Features:
------------
- Easy to set up.
- Printer on/off remote switch.
- Light on/off remote switch.
- Switches work with Octoprint telegram plugin.
- NO CABLE MESS under the printer.
- Articulated camera arm

Bill of material:
-------------------
- Raspberry Pi 3 with Octopi installed (https://octoprint.org/download/)
- Raspberry Pi Camera V2
- At least 30 cm CSI ribbon cable for the camera
- LM2596 voltage regulator: https://www.amazon.it/WINOMO-regolabile-regolatore-convertitore-Step-Down/dp/B01B7BQZJK/
- 3 Relays !!!!!!!!!!!!!!!!!
- 2 XT60 Male connector
- 2 XT60 Female connector
- 2 30x30x10mm 5V Fan (but only 1 is really required)
- At least 15 M3x12 screws and 11 nuts
- 24V led strip
- USB A to mini-USB cable.

!!!!!!!!!!!!!!!!! this are those wich fit in position (https://www.amazon.it/WINGONEER-KY-019-schermo-BRACCIO-arduino/dp/B06XHJ2PBJ) but they may be UNSAFE to use for printer line. So I strongly suggest to use relays rated for at least 15Amps @ 24VDC such as theese https://www.aliexpress.com/item/30A-5V-1-Channel-Relay-Module-Board-With-Optocoupler-H-L-Level-Triger/32814917488.html?spm=2114.search0604.3.15.4aa5a460h2mb5K&ws_ab_test=searchweb0_0,searchweb201602_4_10065_10068_319_10059_10884_317_10887_10696_100031_321_322_10084_453_10083_454_10103_10618_10307_538_537_536_10134,searchweb201603_51,ppcSwitch_0&algo_expid=e76047e1-23dc-4ed4-8798-50eb01d58eb3-2&algo_pvid=e76047e1-23dc-4ed4-8798-50eb01d58eb3
wich are rated 30 Amps @ 30VDC. 
Many thanks to Repraph for the suggestion.

As soon as i can i'll update the design with holes that fits into safer relays



Ok, Let's build It!
-----------------------
- _The Circuit:_

The first thing to do is to make sure that the LM2596 output is 5V-5.3V once 24v is provided. (measur output voltage with a voltmeter) If not adjust voltage output by rotating the potentiometer on the board. 
CONNECT THE RASPBERRY AFTER DOING THIS or you'll probably destroy it.
After this you can start doing the wiring as shown in the picture.

Note that we _NEED_ 2 relays for the printer connection otherwise the USB cable will close the circuit even if the relay is "off" resulting in the raspberry powering printer wich is not good at all. (Believe me, i fried a raspberry and the usb port on the printer but that is another story...)
In order to avoid that problem you need to modify the USB cable: expose the 4 internal wires inside the cable and cut the red one (don't worry colors are unified so you'll always cut the 5v line, wich is what we want)

Only one fan is strictly necessary and that one is near the voltage regulator beacuse it warms up a lot. 

I included a Fritzing schematics if you want to make your own modification (http://fritzing.org/home/).
____________________________________________________

- _The software_ 

To make relays accessible trough Octoprint UI we actually need to tell him how to control it.
Just follow this really good tutorial made by Jeffeb3 https://www.thingiverse.com/thing:1428478 but instead of using pin GPiO23 use GPiO04.
Note that we are using pin 18 to control the printer and pin 04 to control the light.
After completing that tutorial you can test relays by plugging in the led strip and the printer.

_Here is my code for those who asked:_

_printer\_on.sh:_

    #!/bin/bash
    gpio export 18 out
    gpio -g write 18 0

_printer\_off.sh:_

    #!/bin/bash
    gpio export 18 out
    gpio -g write 18 1

_light\_on.sh:_

    #!/bin/bash
    gpio export 18 out
    gpio -g write 04 0

_light\_off.sh:_

    #!/bin/bash
    gpio export 18 out
    gpio -g write 04 1

_/home/pi/.octoprint/config.yaml:_

    system:
     actions:
      - action: pon
        command: printer_on.sh
        name: PrinterOn
      - action: poff
        command: printer_off.sh
        confirm: Are you sure you want to turn off the printer?
        name: PrinterOff
      - action: lon
        command: light_on.sh
        name: LightOn
      - action: loff
        command: light_off.sh
        name: LightOff

____________________________________________________

- _Raspberry,relays and LM2596 case_

It is quite simple to put pieces together with screws. if you need any help look at the pictures.
TO FIX IN POSITION XT60 CONNECTORS JUST USE A BIT OF HOT GLUE. It's not optimal but it works really well.

The final assembly should look like this.
![final assembly](https://cdn.thingiverse.com/renders/3c/b0/aa/26/94/26bb7e90a174b52a2c7101c13a3be28a_preview_featured.JPG "Finale Assembly")
![final assembly](https://cdn.thingiverse.com/renders/64/17/62/30/f4/92902ca7632f680e82262e994dd17842_preview_featured.JPG "Finale Assembly")

Now you just need to unscrew the display and slide into the chassis the whole thing.
____________________________________________________
- _Camera arm_

Same as my previous project without leds: https://www.thingiverse.com/thing:3017729
____________________________________________________
- _24V Led Strip Support_

to be made...




If you have any doubt, do not hesitate to contact me, I'll try my best to help you.

_____________________________________________________________

__If you like what I do and want to support me, head to https://www.paypal.me/giacomo30196 every bit helps me to make more things for you.__
__THANK YOU!__
_____________________________________________________________