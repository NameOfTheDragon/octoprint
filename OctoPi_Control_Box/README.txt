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


http://www.thingiverse.com/thing:3483446
OctoPi Control Box by Ragheera is licensed under the Creative Commons - Attribution - Non-Commercial license.
http://creativecommons.org/licenses/by-nc/3.0/

# Summary

OctoPi with PSU control using the printers power supply. With this setup the printer can be turned on using OctoPi and the entire system can be turned on/off with the printer's power switch for longer periods of inactivity. 

I've designed this control box to accommodate a Raspberry Pi 3 B+, one or two LM2596 buck converters, one or two relay boards, and a 30mm fan. There are mounting holes for any combination of the above. The adapter has the same footprint as a one of the relays to fit a small power rail that i've made, but you could just solder the connections and forego the adapter all together.

I'm using the LM2596 to convert the printers 24v to 5.2v in order to power the Raspberry Pi  and relay. The fan could also be connected to this, but i've opted to use the 3v supply from the Raspberry's board which keeps the fan a bit quieter. It is important to test the voltage of the converter before connecting accessories and under load to make sure that the voltage is within tolerance.

In order to control the relay i've installed the PSU Control plugin for OctoPi from the following link and set the switching options to control GPIO 40. https://plugins.octoprint.org/plugins/psucontrol/ (but you could use whichever pin you like) 

Something else to consider is installing uhubctrl to disable power on the USB ports to avoid damaging the Raspberry Pi when the printer is turned off. Follow the readme at this GitHub link https://github.com/mvp/uhubctl, or download a new plugin from here https://github.com/OutsourcedGuru/OctoPrint-USBControl. 

I've uploaded two STL files for the box. One has the case cut out for a stand alone fan and one is cut to use with a shroud. The one pictured is my design and can be found here https://www.thingiverse.com/thing:3483359 

Also, i've designed this to work with KrisHo1's damper mount; just leave the corner screw out. https://www.thingiverse.com/thing:3240449

# Print Settings

Printer Brand: Creality
Printer: Ender 3
Rafts: No
Supports: Yes
Resolution: .12
Infill: 20%
Filament_brand: SUNLU
Filament_color: Green
Filament_material: PLA+