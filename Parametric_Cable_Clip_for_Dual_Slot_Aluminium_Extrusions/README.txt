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


https://www.thingiverse.com/thing:2851629
Parametric Cable Clip for Dual Slot Aluminium Extrusions by MattKi is licensed under the Creative Commons - Attribution - Share Alike license.
http://creativecommons.org/licenses/by-sa/3.0/

# Summary

I was looking at the options for cable management for the AM8 and other dual slotted aluminium extrusion builds and decided to make a customisable model.

This was the result! As you can see from the picture and example models (configured for 2040 extrusions from motedis.co.uk) you can create variations that are taller than the slot itself all the way down to barely wider than the outer slot edges with varying depths.

Currently the file is locked in "Snap in" mode as in practice these proved to be plenty solid enough once fitted. If you want to print the full tabs and slide them into the extrusions from the edge instead then just change the references to "clip2" in the "Assembly" module to "clip".

# Print Settings

Printer: Anet AM8
Rafts: Doesn't Matter
Supports: No
Resolution: 0.24mm first layer and 0.16mm further layers. 0.4mm nozzle and ABS.
Infill: 40% but tweak as required to suit your use case.

Notes: 
Single perimeters work quite well with decent infill. 3mm brim was used on PEI for adhesion.

# How I Designed This

This was designed in OpenSCAD. The implementation of the clips is not particularly elegant. clip2 could just be a variable change in a single module.

I started by getting a boxy version of the part put together and then assigned variables to it's dimensions. Next was working out the clips and dimensions required for those. Next came some testing of different parameters followed by adding some checks to prevent some issues with incorrect dimensions (for example the user specifying that the height of the clip should be less than the distance between the outer edges of the slots plus a small overlap to fit the clip properly). Finally there were some visual changes to add curved corners for the clips and further tweaks to try to ensure that the curving did not interfere with the structure of the finished parts.