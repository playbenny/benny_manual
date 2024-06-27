- [download the latest benny](https://github.com/jamesholdenmusic/benny/archive/refs/heads/main.zip) and extract the whole folder. 

- install [max](http://www.cycling74.com) but no need to buy it, just ignore all those messages, don't start the free trial, don't subscribe, nothing. you'll be able to use all the features of benny. BUT if you decide you want to learn to build your own blocks you'll need to buy max.

- a few blocks require airwindows console 7 vsts. they're included in the download, look in the vst dependencies subfolder and install the ones you need for your system. windows users should install vsts to C:\Program Files\VSTPlugins otherwise max/msp can't see them.

- open max, go in options / preferences / jitter preferences and make sure 'graphics engine' is set to glcore.

- open 'benny.maxproj'. the benny launcher window will appear.

- open the audio settings and choose which audio driver/interface to use

- choose the 'no hardware' configuration to try benny out using just the default io on your computer. 

to set benny up for seamless integration with your midi controllers, modular synth, keyboards, drum machines, synths, microphones, pedals, and outboard effects you'll need to make your own hardware configuration file.


##hardware configuration

to use your **hardware** fluidly within benny you need to build a configuration file. in it you tell benny about each piece of hardware that's connected to your computer, then they appear as blocks. if you change your hardware setup benny can help you migrate songs from the old to the new, letting you choose substitutes for missing or replaced items. in my usage i have a configuration file for each iteration of my live touring setup and a different one for a setup i have at home and a setup for the studio with my synths and outboard compressors available as individual blocks.

the hardware configuration file also includes information about the **midi controllers** you have connected - how many controls, how they're arranged, the midi channels and protocols etc that they use, and which other controllers work as a substitute.

there are example files included that might help - so far i've made configs for:

- midi fighter twister (recommended, the led feedback works well with the automapping features in benny)

- novation launch control xl

- akai lpd8 mk2 (not recommended, shoddy midi implementation)

presets for controller setup are in the to-do list.


##vst configuration

to use a **vst plugin** in benny you need to set it up in the vst manager. pick a plugin from the list the scanner finds (on windows if it doesn't find your vsts, put them in C:\Program Files\VSTPlugins), then pick the parameters you want to see in benny, and the order they should appear - at the moment it lets you assign them to 4 groups (1 group = 1 row of sliders in the benny interface).

##preferences

all the **visual/ui preferences** - colour palette, wire curve detail, various other behaviours with self explanatory names, are in config.json. if you want to change a setting copy the relevant entry you want to change the value of over to userconfig.json and change it there, as config.json will be overwritten with defaults next time you update benny but userconfig will not.

the default numbers of note and audio voice slots can be changed this way, but baseline cpu usage of the system's matrix mixer grows fast with audio voice count.
