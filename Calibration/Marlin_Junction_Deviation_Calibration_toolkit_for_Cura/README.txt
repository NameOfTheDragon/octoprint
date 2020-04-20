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


http://www.thingiverse.com/thing:3463159
Marlin Junction Deviation Calibration toolkit for Cura by DrywFiltiarn is licensed under the Creative Commons - Attribution license.
http://creativecommons.org/licenses/by/3.0/

# Summary

**THIS THING IS TOO PRELIMINARY TO BE USED AT THIS POINT! AS I GET TO GET MORE INTO THE DETAILS AND MAKE IMPROVED TEST MODELS THAT WILL GIVE MORE CLEAR AND CONCLUSIVE RESULTS I WILL BE UPDATING THIS THING... TILL THAT TIME FEEL FREE TO EXPERIMENT WITH WHAT IS PUBLISHED HERE AND SHARE YOUR EXPERIENCES**
--

**NOTE: This tool is only useful when you have activated junction deviation in your firmware (#define JUNCTION_DEVIATION available in both bugfix-1.1.x and bugfix-2.0.x branches)**

In order to successfully use junction deviation on current Marlin releases (I developed this to work with Marlin-2.0.x latest daily) it needs calibration and finetuning of this setting. As I found it quite tedious doing multiple prints with different settings for junction deviation and occasionally found it hard to compare the different prints, I created a model and Cura postprocessing script to help doing a test print for calibration using various values for junction deviation in a single model, where the value will change over the course of the print. This way you have a print that shows the effects of the values selected split over a series of sections (20 layers for each junction deviation value) on top of each other.

Please read full instructions below before using
---

If you used this tool, please leave me a comment on your experience of using it and your results, so I can make improvements if needed.

# How I Designed This

## Installation instructions

To allow Cura to adjust the value for junction deviation on exporting the gcode after slicing, you will have to install the JunctionDeviationCalibration.py script for the "Post Processing" extension.

Note that this script is designed to work with the Cura 3.x versions.

Use the following steps:
1. Open Cura
2. Help -> Show Configuration Folder
3. Copy the JunctionDeviationCalibration.py script into the "scripts" folder
4. Restart Cura to load the new script

## Usage instructions

After above installation of the "Post Processing" script, start a new project and insert the JunctionDeviationCalibration.stl into the project.

Set the following configurations for printing:
* Quality
 * Layer Height: 0.2mm
* Shell
 * Wall Line Count: 1
 * Top Layers: 0
 * Bottom Layers: 2 or 3 (whatever you prefer)
* Infill
 * Infill density: 0%

Then go to the "Extensions" menu of Cura and select "Post Processing" -> "Modify G-Code"

![Alt text](https://cdn.thingiverse.com/assets/87/10/69/8e/24/add-script.jpg)

![Alt text](https://cdn.thingiverse.com/assets/cf/c9/f0/d7/dc/configure.jpg)

**Configuration options**

* Starting value - This is the value for junction deviation that will be set at the start of the print at layer one.
* Stepping size - The increment by which the junction deviation will be increased every 20th layer (so at layer 20, 40, 60, 80, 100, 120, 140, 160 and finally at layer 180). Each of these changes can be identified on the printed model as a small recess on the 20mm wide surfaces.
* Display details on LCD - Turning this on will use M117 to show on the LCD what the current junction deviation value it is currently printing with. Displayed as "Junction Dev - 0.xxx"

With the values of above screenshot you would get the following junction values used along the print:
* Layer 000 - 019: 0.020
* Layer 020 - 039: 0.025
* Layer 040 - 059: 0.030
* Layer 060 - 079: 0.035
* Layer 080 - 099: 0.040
* Layer 100 - 119: 0.045
* Layer 120 - 139: 0.050
* Layer 140 - 159: 0.055
* Layer 160 - 179: 0.060
* Layer 180 - 199: 0.065

**Personal experience**
Some experimentation is required to find the perfect range of testing for your specific machine.

In my personal experience it helps to do an exaggerated configuration first as this will identify the value ranges that are definitely far out of range of the perfect calibration.  In my case I did a print with a starting value of 0.025 with a stepping size of 0.025, which resulted in values from 0.025 through 0.250 being tested. See photo below to see the result of this print.

![Alt text](https://cdn.thingiverse.com/assets/10/ff/c8/98/fc/exaggerated-example.jpg)

So from above exaggerated print, we can conclude that the optimal junction deviation value for the machine (in my case an Ender-3) lies somewhere between 0.050 - 0.100.

From this point you can reconfigure the post processing script to use a Starting value of 0.05 with a stepping size of 0.005. Doing so will result in the following junction deviation values to be used:
* Layer 000 - 019: 0.050
* Layer 020 - 039: 0.055
* Layer 040 - 059: 0.060
* Layer 060 - 079: 0.065
* Layer 080 - 099: 0.070
* Layer 100 - 119: 0.075
* Layer 120 - 139: 0.080
* Layer 140 - 159: 0.085
* Layer 160 - 179: 0.090
* Layer 180 - 199: 0.095

When this print would be inspected (I don't have a photo for this yet, but will add later) you can inspect the results on the print again, and you can again pick the best result value  for the junction deviation. If needed you can repeat a third time with an even more close target starting value and even smaller stepping size.