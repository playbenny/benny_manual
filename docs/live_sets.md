benny was designed not just for composing individual songs, but also for performing live sets.

Unlike other live music software benny does not load up all of the songs in a set at once. 

*I felt that in order to play a song properly it would help both the performer and computer not to be burdened by the knowledge of the other songs.*

When you select a **songs folder** benny treats the contents of this as your whole live set. When you start benny it preloads all the songfiles, then looks to see if it can preload any samples too. When you choose the next song it recycles as many blocks as it can, so that load times are as quick as possible. 

If you want to play one song and then the next (stopping in between like a band), then benny will easily load the next song before people stop clapping.

If you want to segue seamlessly between songs there are a few approaches:

- **Merge** lets you load the next song in with the current one. All of the new song's blocks appear on the blocks page to the right of the blocks for the song that is currently playing. 

    benny only permits one copy of certain blocks - for example hardware blocks and core.control.input.auto. These blocks are therefore shared between the current and next song, but benny will automatically move them over to their position in the new song.
    
    benny also cleans up as you merge: any muted blocks in the old song (and all connected blocks that aren't in use elsewhere) will be deleted as the new song merges in. To disable this behaviour in ui preferences uncheck ```"PURGE_MUTED_TREES"```.
        
    After merge you will see two new buttons in the top bar: **select previous** and **select new**, which can be used to delete bits of old song.

- **Output blocks** 

    In the hardware setup, every audio output on your computer has the option to run another layer of audio processing, called 'output blocks'. By default benny applies a transparent anti-aliasing clipper and dither here. Because these are part of the hardware setup rather than part of the song they are always present, even when benny is loading a new song.

    There are two *(prototype)* output blocks included:
    
    - The **stretch_looper** lets you grab a loop of the playing track and keep it looping while the next one loads. It uses z-plane timestretch to make it match the tempo of the next song. *This is still a work in progress.*

    - The **big reverb** does what you expect it to.

- **Hardware** loopers, delays or reverbs - anything that can be used to fill 2-10 seconds works here! *In my current live setup I've built an external version of the stretch looper that runs in a Bela Pepper Eurorack module and additionally provides an emergency loop in the unlikely event of my computer crashing.*

**Live set pro-tip:** To prevent crashes, tape your usb cables into the ports, at both ends, every time.
