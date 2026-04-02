# Renoise Duplex Script for the Korg NanoKontrol 2

This is a custom Lua script for use with the Duplex tool in Renoise. More information about Duplex can be found here: [Duplex](https://www.renoise.com/tools/duplex-browser)

Since Duplex appears to be abandonware, I recommend using this fork by ylmrx instead: [https://github.com/ylmrx/DeuxPieces](https://github.com/ylmrx/DeuxPieces)

The fork has resolved several bugs present in the original Duplex, which hasn't been updated in years. I've been using it without any issues, so thanks to ylmrx for keeping it alive. The last release was from late 2025, making it quite recent.

I started using Duplex because I wanted to use my Korg NanoKontrol 2 with Renoise, but out of the box it lacks any bank-switching capability. This meant I couldn't control more than 8 tracks at a time. There are workarounds using software like Bome MIDI Translator, but that approach is more complex and costly.

Duplex does include a built-in NanoKontrol 2 preset, but it didn't suit my needs — in particular, I couldn't get bank switching to work with it. So I wrote a new Lua script from scratch.

## What it does

1. The **Track** buttons on the NK2 move one track left or right.
2. The **Marker** buttons move up or down one bank. Pressing the right arrow shifts fader control to tracks 9–16; pressing the left arrow returns to tracks 1–8.
3. The **CYCLE** button toggles the bottom DSP pane on or off.
4. The **double left / double right** arrow buttons (bottom left) switch between the DSP pane and the automation pane.
5. The **Stop**, **Play**, and **Record** buttons control transport in Renoise.
6. The **faders** control track volume. The **S/M** buttons handle solo and mute per track.
7. The **R** buttons jump directly to the corresponding track.
8. The **encoders** required some extra work: I wanted them to control the 8 macro controls on the sampler page, but switch to plugin parameters when working in the pattern or mixer view. Duplex normally handles one or the other — not both. This script adds a toggle using the **SET** button on the NK2. The default mode controls sampler macro controls; the second mode controls parameters of the plugin currently in focus on the pattern or mixer page.

## Installation

There are two steps:

**Step 1:**

Place `MixerTransport.lua` in the Duplex configuration folder for the NanoKontrol 2. On Mac:

```
/Library/Preferences/Renoise/V3.5.4/Scripts/Tools/com.renoise.Duplex.xrnx/Duplex/Controllers/nanoKONTROL2/Configurations/MixerTransport.lua
```

On Windows (looked up via Google, may not be exact):

```
C:\Users\YourUsername\AppData\Roaming\Renoise\V[RenoiseVersion]\Scripts\Tools\com.renoise.Duplex.xrnx
```

> **Note:** Delete all other files in the `Configurations` folder, leaving only `MixerTransport.lua`. Otherwise it will not work.

**Step 2:**

Place `InstrumentMacros.lua` in the following folder (on Mac):

```
/Library/Preferences/Renoise/V3.5.4/Scripts/Tools/com.renoise.Duplex.xrnx/Duplex/Applications/InstrumentMacros.lua
```

Restart Renoise, then go to **Tools > Duplex > Nano Control 2**. If everything is set up correctly, you should see two options:

- Mixer & Macros
- Mixer & FX

These are the two modes that Duplex switches between when you press the **SET** button on the NK2.

Click on **Mixer & Macros** to open the Duplex window for that preset. Then open **Settings** and select your NanoKontrol 2 in the top dropdown (for both input and output). Without this step, nothing will work. From there, configure the remaining settings to your preference.

Two important settings to check:

- Set **Page size** to **8** in both the Mixer and TrackSelector menus.
- Check the **Pre/Post** mode — it defaults to Pre, but I switched it to Post so the NK2 controls the faders as shown in the mixer page.
