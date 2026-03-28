# Renoise Duplex Script for the Korg Nano Control 2

This is a custom LUA script to use with Duplex Tool in Renoise. The info page for Duplex is here: (Duplex)[https://www.renoise.com/tools/duplex-browser]

Now as Duplex “seems" to be abandonware, you should actually get this fork here by ylmrx (https://github.com/ylmrx/DeuxPieces)h[ttps://github.com/ylmrx/DeuxPieces]

The fork seems to have solved bugs and other things not working in the original Duplex which aunt been updated in years. I am using the fork and have not experienced any issues with it. So thanks to ylmrx for this update. The last version was from the end of 2025, so it us quite recent.

I started using Duplex because I wanted to use my Korg NanoKontrol 2 in Renoise but the originally it does not have any capability to switch banks or anything like this. So i was not able out of the box for example to control more than 8 tracks in Renoise. There are ways to achieve this with software like Bome midi translator but this is much more complicated and also expensive.

Duplex comes with a premade NanoKontrol 2 preset but it was no use to me. I could also not get the bank switching done on the included one so I created a new LUA script.

## Here is what it does:

1. The Track buttons on the NK2 move 1 track left and right.
2. The Marker buttons on the NK2 move up and down one bank. So clicking on the right arrow will switch the fader controls to track 9-16. Click on the left arrow again, it will go back to track 1-8.
3. The CYCLE button on the NK2 toggles the bottom DSP pane display (on or off).
4. The bottom left double left / double right arrow buttons on the NK2 switch between DSP pane and automation pane.
5. The stop, play and record transport controls the transport in Renoise.
6. The faders control obviously the volume of tracks. S/M buttons control solo and mute on each track.
7. The R buttons on each track will jump to that track directly.
8. Finally, the encoders. This one required a bit of fiddling to get that working: I wanted to be able to control the 8 macro controls on the sampler page. But when Im on the pattern or mixer view, I wanted the encoders to control plugin parameters. Usually Duplex does one or the other. But not both together. In this script it will do both using a “switch behavior” button. When you press the SET button on the NK2 it will toggle between the 2 modes. Default mode controls the macro controls on the sampler page. And the 2nd mode will control parameters of the plugin that is in focus on pattern or mixer page.

## Installation:

There are 2 things to do: 

1:

Put the MixerTransport.lua file into the config folder of Duplex. For the NanoKontrol 2, on a Mac, this is at:
   /Library/Preferences/Renoise/V3.5.4/Scripts/Tools/com.renoise.Duplex.xrnx/Duplex/Controllers/nanoKONTROL2/Configurations/MixerTransport.lua

For Windows it should be here (althgough I only liked this up via Google, so it might not be 100% correct):
C:\Users\YourUsername\AppData\Roaming\Renoise\V[RenoiseVersion]\Scripts\Tools\com.renoise.Duplex.xrnx 

Note: You need to delete all other files in there except the MixerTransport.lua. Otherwise it will not work.

2:

Put the file InstrumentMacros.lua into this folder (on Mac):
Library/Preferences/Renoise/V3.5.4/Scripts/Tools/com.renoise.Duplex.xrnx/Duplex/Applications/InstrumentMacros.lua

Restart Renoise. Then go into Tools > Duplex > Nano Control 2
If all went well, you will see 2 options in this folder: 

Mixer & Macros 
Mixer & FX

These are the 2 modes Duplex will switch between when you press the SET button on the NK2.

Finally, you can click on the “Mixer & Macros” menu item to open the Duplex window for that preset. Then click on settings and select your Nano Control 2 in the top drop-down (For both in and out). If you do not do that, nothing will work. Then also click on the menus shown below and pick the settings you want.

It is important that you select “8” for Page size (both in Mixer and in the Mixer and in the TrackSelector menus. 
And one more setting to look at is the “Pre/Post” mode. This defaults to Pre. But I switched this behavior to Post, as I want the NK2 to control the faders in the mixer page.
