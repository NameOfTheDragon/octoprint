# Printing the Sliding Legolini

I started by following `jaaanik`'s (the creator's) printing instructions to the letter but they didn't work out too well for me on my Ender-3.
Here are my suggestions based on my own experience, trial and error.

## General Recommendations

There are several big parts that only just fit the bed of an Ender-3.
I've found that the stock build plate tends to be uneven and therefore challenging with parts that cover a large area or when printing multiple parts.
If you haven't already, may I recommend that you treat yourself to a glass bed upgrade.
Trust me, you will be glad you did.
While you're at it, get rid of those bulldog clips as you will likely run into them printing some of the large parts.
Especially nasty if you have a BL-Touch.
I recommend Kapton tape, which is stable at high temperatures, and can be used to tape the bed in place along all 3 sides.
The tape will not be affected even if the hot end touches it.

Jaaanik says to print hot, and to increase the flow rate.
He also says to use 25% to 30% infill.
He doesn't specify a pattern but from the photos it looks like he's used a simple grid pattern.
This combination didn't work well for me and I had problems printing several parts.
Instead, I printed at my normal temperature for PLA (205°C) and at normal 100% flow rate.
I used Gyroid infill at 18%, which I found to be very adequate.
Gyroid fill pattern is one of the strongest infill patterns while still being fairly quick to print, especially as you can get away with lower infill densities for the same strength.

Jaaanik mentions that the extreme curvature of some parts requires special treatment.
I personally found that, even following jaaanik's instructions, some parts (particularly the bow slider and magazine parts) tended to warp away from the bed.
I don't usually have this problem with PLA so these parts are indeed quite demanding.
I found that adding a 10mm brim along with my standard print settings was sufficient to hold the parts flat to the bed.
I used a brim on all 3 of the magazine parts and on the bow slider.
I didn't need a brim on the bow arm and bow grip.
I guess this may be printer-dependent so "Your Mileage May Vary".

The design that I downloaded in late March 2020 had print-in-place string hooks designed into the bow arm and bow grip.
The hooks were supposed to be broken out with the aid of a screwdriver.
Jaaanik casually mentioned cutting them out with a knife if needed.
Bad idea.
I drew blood at least twice getting the hooks out and ended up breaking them in the process.
I asked jaaanik about this and he said there were versions of the parts with the hooks removed.
Jaaanik must have added these just after I downloaded because they weren't present in my copy.
I highly recommend using the versions with the string hooks separated out.
See my comments below under `Bow Grip` and `Bow Arm`.

If you find your parts don't fit the print area when using a skirt, try reducing the skirt distance.
In Cura, this is the `Skirt Distance` setting and I used 4mm.
You could also turn the skirt off, but I like to have it there as a check that my bed is level and things are going to go well.
I don't allow a print to continue if the skirt doesn't pring perfectly.

Pay attention to model orientation.
The parts import in their design orientation which is often not the best orientation for printing.
If necessary, flip them over to the position documented by jaaanik.
The recommendations here are pretty much perfect.

The instructions say that no supports are needed, but I disagree with that as there are clearly some non-bridgable unsupported overhangs.
In particular, some of the parts print with screw holes that start wide at the bottom and get abruptly narrower part-way up.
I think this was the case with the `Bow Grip` and `Bow Arm`.
Bridging doesn't work in this situation and although you might get away with it, the holes will often not be very clean.
I recommend using supports for these parts as I found this gives me a cleaner results that clean up easily.
On my printer, these supports usually pull out as I'm removing the part from the build plate, but they can also just be poked out from the opposite side with an allen key.

# Part-by-Part Recommendations

I use Cura as my slicer and unless otherwise stated, my _Standard Settings_ were as follows:
- Speed: 80 mm/s
- Print temperature (for PLA) 205°
- Flow rate 100%
- Small Hole Max Size: 5mm (this reduces the print speed for small features)
- Infill: Gyroid 18%
- Wall thickness: 1.6mm (4 lines)
- Top thickness: 1.2mm (6 lines)
- Bottom thickness: 1.2mm (6 lines)
- Bed adhesion: skirt, 3 lines, 4mm spacing

I made a custom Cura profile with all these settings in and then just re-used it for all my parts, varying as necessary for parts that need special handling mentioned below.

## Magazine (Parts 1, 2 and 3)

Use a 10mm brim to keep the parts flat while printing.

Part 3 has supports deigned into the barrel, but by default Cura ignores the vertical supports because it considers them too thin to print.
If using Cura, make sure to enable the option `Print Thin Walls`.
It might be possible to print without these supports if your printer is good at bridging, but I decided not to risk it.
The supports are removed with a round file after printing.

## Bow slider

For me, this was the most troublesome part.
My first attempt, I followed jaaanik's instructions to the letter and it warped badly and was unusable.
Second attempt, I used my standard settings and added a 10mm brim.
That was enough to hold it down flat and my second attempt came out perfect.

## Bow Grip

I didn't use a brim for this, just a normal 3-line skirt.
I recommend using the version without the print-in-place string hooks.
I found these impossible to remove cleanly without breaking the parts and injuring myself.
You'll need supports for the slot where the string hook would have been and also for the screw holes.

In Cura, enable `Generate Support` and set `Support Placement` to `Everywhere`.
Thsi should give you supports in the slots and the bottom part of the screw holes.
If you notice unwanted suports anywhere else try setting the `Support Overhang Angle` to something approaching 90°.

## Bow Arm

Another part that has screw holes that get narrower part-way up.
I also recommend using the version without the print-in-place string hook.
For these reasons, I recommend using supports for this part.

In Cura, enable `Generate Support` and set `Support Placement` to `Everywhere`. set the overhang angle to 60°.

This will put supports in the string hook slot as well as in the screw holes.
Perfect.

## Back Grip

I had no problems printing this item with my standard  settings.
This part comes in several sizes to fit different sized hands.
Jorge Sprave mentioned in his video that the large size felt a bit big for him.
The standard version of this part feels OK to me even though I have big-ish hands, so this seems like a good choice if you're not sure what size to go for.
It's easy enough to printer a smaller or larger size and swap it out later.

## Spring Body

Printed fine with standard settings and no supports.
The internal gaps can be quite successfully bridged.

## Spring Body Clip 1 & 2

These popped off the print bed on my first attempt.
I guess they are too small to get good adhesion and are easily knocked off.
I reprined with a brim, problem solved.

## Release

Worked first go with standard settings.

## Magazine Spring

Worked with standard settings.