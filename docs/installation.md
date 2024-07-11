- [download the latest benny](https://github.com/jamesholdenmusic/benny/archive/refs/heads/main.zip) and extract the whole folder. 

- install [max](http://www.cycling74.com). you don't need to buy max in order to use benny, but if you want to build your own blocks you'll need to. please do not bother cycling74 support with problems with benny.

- a few blocks require airwindows console 7 vsts. they're included in the download, look in the vst dependencies subfolder and install the ones you need for your system. windows users should install vsts to C:\Program Files\VSTPlugins otherwise max/msp can't see them.

- open max, go in options / preferences / jitter preferences and make sure 'graphics engine' is set to glcore.

- open 'benny.maxproj'. the benny launcher window will appear.

- open the audio settings and choose which audio driver/interface to use

- choose the 'no hardware' configuration to try benny out using just the default io on your computer. 

to set benny up for seamless integration with your midi controllers, modular synth, keyboards, drum machines, synths, microphones, pedals, and outboard effects you'll need to make your own hardware configuration file.


## Hardware configuration

to use your **hardware** fluidly within benny you need to build a configuration file. in it you tell benny about each piece of hardware that's connected to your computer, then they appear as blocks. if you change your hardware setup benny can help you migrate songs from the old to the new, letting you choose substitutes for missing or replaced items. in my usage i have a configuration file for each iteration of my live touring setup and a different one for a setup i have at home and a setup for the studio with my synths and outboard compressors available as individual blocks.

the hardware configuration file also includes information about the **midi controllers** you have connected - how many controls, how they're arranged, the midi channels and protocols etc that they use, and which other controllers work as a substitute.

there are example files included that might help - so far i've made configs for:

- midi fighter twister (recommended, the led feedback works well with the automapping features in benny)

- novation launch control xl

- akai lpd8 mk2 (not recommended, shoddy midi implementation)

presets for controller setup are in the to-do list.


## VST configuration

to use a **vst plugin** in benny you need to set it up in the vst manager. pick a plugin from the list the scanner finds (on windows if it doesn't find your vsts, put them in C:\Program Files\VSTPlugins), then pick the parameters you want to see in benny, and the order they should appear - at the moment it lets you assign them to 4 groups (1 group = 1 row of sliders in the benny interface).

## Preferences

all the **visual/ui preferences** - colour palette, wire curve detail, various other behaviours with self explanatory names, are in config.json. if you want to change a setting copy the relevant entry you want to change the value of over to userconfig.json and change it there, as config.json will be overwritten with defaults next time you update benny but userconfig will not.

the default numbers of note and audio voice slots can be changed this way, but baseline cpu usage of the system's matrix mixer grows fast with audio voice count.

## Recommended computer specs

Benny is fairly resource intensive. A lot of graphic work is handled by the GPU but if you have an old laptop with only integrated graphics it may struggle. See below for some settings that can lighten the load on the GPU.

Currently benny is tested against a 2014 intel i7/nvidia 980 gaming laptop, a 2023 mid-range (i7/intel Xe) framework laptop and a couple of desktop PCs, one with integrated graphics (AMD 4700G) and a high end 7950X3D with a 3080 GPU. The aim is for it to run fine on a current, mid-range integrated graphics only laptop. (Mac users: in the examples I've seen so far the ARM macs all count as mid-range for the purposes of the discussions below)

### Settings that affect GPU usage:

- wire segment count. Low end GPUs struggle with the number of polygons needed to make smooth wires. Add the following keys to **userconfig.json** (which will be created in the root of the benny folder after you first run benny):

    "MAX_BEZIER_SEGMENTS" : 4,
    "MIN_BEZIER_SEGMENTS" : 4,

    (the numbers need to be divisible by 4 and MIN must be < MAX - when loading patches it initially draws the min number then upgrades the wires when it's idle to speed up loading)

- you can also, either by pressing F10 to toggle, or setting this key to set it as the default, make it only show wires to/from the current block.

### Settings that affect CPU usage:

- the maximum number of audio blocks & the number of hardware io. the audio blocks and io are connected to a matrix mixer, cpu usage seems to increase steeply as the size of this increases. On mid range hardware the default (64) seems fine, and supports fairly complex song patches. On high end hardware much higher values are possible. On very low end computers you could reduce this to lower the baseline CPU load.

    "MAX_AUDIO_VOICES" : 64,

- the 'vector size' of audio processing. find this in the audio settings dialog (there's a button to open it on the benny launcher window). This is the number of samples processed at once by each stage of the audio processing in benny. Decreasing it rapidly increases CPU usage. Because of a limitation of how benny's architecture every audio connection adds this much latency, and while it's possible to offset clocks (and other transport-linked blocks eg wave scan blocks also have time offsets) it obviously pays to keep this as low as your computer can manage.

- upsampling. upsampling is a common simple way to mitigate aliasing in harmonics generated by digital processing. most of benny's non-linear audio blocks default to upsampling x2 as it makes a noticeable difference to the clarity of the sound. however upsampling obviously increases the cpu usage. the following key can be used to disable upsampling on a computer. for example if your main computer is lost or broken and you borrow a less powerful one to run your set.

    "UPSAMPLING" : 0,