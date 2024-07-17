- [Download the latest benny](https://github.com/playbenny/benny/archive/refs/heads/main.zip) and extract the whole folder. 

- Install [Max](http://www.cycling74.com). You don't need to buy Max in order to use benny, but if you want to build your own blocks you will need to buy or subscribe. (Please do not bother cycling74 support with problems with benny! We have a [forum](https://github.com/playbenny/benny/discussions) for that.)

- A few blocks require Airwindows console 7 VSTs. They're included in the download, look in the VST dependencies subfolder and install the ones you need for your system. 

    *Windows users should install VSTs to C:\Program Files\VSTPlugins otherwise max/msp can't see them.*

- Open 'benny.maxproj'. The [benny launcher](launcher.md) window will appear.

- Open the audio settings and choose which audio driver/interface to use. Generally ASIO drivers are best.

The dropdown contains a list of example hardware configurations. Choose the 'no hardware.json' one then press the **start** button to try benny out using just the default stereo io on your computer.

To set benny up for seamless integration with your midi controllers, modular synth, keyboards, drum machines, synths, microphones, pedals, and outboard effects you'll need to make your own hardware configuration file.


## Hardware configuration

To use your **hardware** fluidly within benny you need to build a configuration file. It will tell benny about each piece of hardware that is connected to your computer, and they will appear as blocks. 

If you change your hardware setup benny can help you migrate songs from the old to the new, letting you choose substitutes for missing or replaced items. 

*In my usage I have a configuration file for each iteration of my live touring setup, a different one for a setup I have at home and a setup for the studio with my synths and outboard compressors available as individual blocks.*

The hardware configuration file also includes information about the **midi controllers** you have connected - how many controls, how they're arranged, the midi channels and protocols etc that they use, and which other controllers work as a substitute.

There are example files included that might help - so far i've made configs for:

- [Midi Fighter Twister](https://www.midifighter.com/#Twister) (recommended, the led feedback works well with the automapping features in benny)

- Novation launch control xl

- Akai lpd8 mk2 (not recommended, incomplete midi implementation)

(A library of presets for controller setup are on my to do list.)

## VST configuration

To use a **VST plugin** in benny you need to set it up in the VST manager. First run the VST plugin scanner and wait until the progress bar has finished.

benny comes with a library of config files for VST plugins that we have already encountered. When you run the scan these will be set up automatically, but you are free to make your own edits.

If your plugin is not automatically added to benny you can set it up in the VST manager. You need to tell it which parameters you want to see, and what order they should appear in. At the moment it lets you assign them to 4 groups (1 group = 1 row of sliders in the benny interface).

If you've done a complete and useable configuration for a plugin please do post the .json file (found in benny/audio_blocks) on the [discussions](https://github.com/playbenny/benny/discussions) pages and we'll add it to the library.


## Preferences

All the visual/ui preferences - colour palette, wire curve detail and various behaviours with self explanatory names, are in **config.json**. If you want to change a setting:

- copy the whole line for that setting and paste it into **userconfig.json**

- anything in **userconfig.json** overrides the default value in **config.json**. it is created in the root of the benny folder after you first run benny.

- **config.json** will be overwritten with defaults next time you update benny but **userconfig.json** will not.

## Recommended computer specs

Benny is fairly resource intensive. A lot of graphic work is handled by the GPU but if you have an old laptop with only integrated graphics it may struggle. See below for some settings that can lighten the load on the GPU.

The audio side of benny takes full advantage of multi core CPUs *(afaik this is an advantage over hosting patches in Max for Live, which last time I checked, doesn't).*

We've tested benny on the systems below, and hope it will be useable on any current mid range (integrated graphics only) laptop.

- M1 MacBook Air

- 2023 mid range (i7/intel Xe) Framework laptop

- 2019 PC with integrated graphics (AMD 4700G) 

- 2024 high end (7950X3D) with a 3050 GPU. 

### Resource usage sidebar

Benny shows a CPU meter to the left of the play button. You can press **F12** to show the resource usage sidebar, which shows CPU usage history (yellow, lower better) and framerate history (white dots, higher better).

### Settings that affect GPU usage:

- Wire segment count. Low end GPUs struggle with the number of polygons needed to make smooth wires. Add the following keys to **userconfig.json**:

    ```json
    "MAX_BEZIER_SEGMENTS" : 4,
    "MIN_BEZIER_SEGMENTS" : 4,
    ```

    (the numbers need to be divisible by 4 and MIN must be < MAX - when loading patches it initially draws the min number then upgrades the wires when it is idle to speed up loading. Defaults are 16 / 8)

- You can also make it only show wires to/from the current block, either by pressing **F10** to toggle, or setting this key to set it as the default:

    ```json
    "WIRES_SHOW_ALL" : 1,
    ```

### Settings that affect CPU usage:

- The maximum number of audio blocks & the number of hardware IO have a big effect on the baseline CPU usage. On mid range hardware the default (64) seems fine, and supports fairly complex song patches. On high end hardware much higher values are possible. On very low end computers you could reduce this to lower the baseline CPU load. Add the following key to **userconfig.json**

    ```json
    "MAX_AUDIO_VOICES" : 64,
    ```

- The '**vector size**' of audio processing also has a big effect. This is the size (in samples) of the chunks of audio worked on by each stage of processing in benny. Decreasing it rapidly increases CPU usage. Find this in the **audio settings** dialog (there's a button to open it on the benny launcher window). 

    Because of a limitation of benny's architecture every audio connection adds latency proportional to this value, and while it's possible to offset clocks (and other transport-linked blocks eg wave scan blocks also have time offsets) it obviously pays to keep this as low as your computer can manage. On mid range hardware 256 samples is a good target, 64 is a sensible minimum for high end systems.

- **Upsampling** is a common simple way to mitigate aliasing in harmonics generated by digital processing. Most of benny's non-linear audio blocks default to upsampling x2 as it makes a noticeable difference to the clarity of the sound. However upsampling obviously increases the CPU usage. You can adjust it (from 1x-128x) in the sidebar settings section for the block, or the following key can be used to disable upsampling for all blocks on a particular computer (for example if your main computer is lost or broken and you borrow a less powerful one to run your set):

    ```json
    "UPSAMPLING" : 0,
    ```

## Installation Troubleshooting FAQ

- *The benny window that comes up when I press start is grey*

    Open max, go in options / preferences / jitter preferences and make sure 'graphics engine' is set to glcore. (This issue only happens if you've had this max installation on your pc for a long while)

