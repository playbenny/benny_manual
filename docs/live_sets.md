benny was designed not just for composing individual songs, but also for performing live sets.

Unlike other live music software benny does not fully load up all of the songs at once. 

*I felt that in order to play a song properly it would help both the performer and computer not to be burdened by the knowledge of the other songs.*

When you select a **songs folder** benny treats the contents of this as your whole live set. When you start benny it preloads all the songfiles, then looks to see if it can preload any samples too. When you choose the next song it recycles as many blocks as it can, so that load times are as quick as possible. 

If you want to play one song and then the next (stopping in between like a band), then benny will easily load the next song before people stop clapping.

If you want to segue seamlessly between songs there are a few approaches:

- **Merge** lets you load the next song in with to the current one. All the new song's blocks appear on the blocks page to the right of the blocks for the song that is currently playing. 

    Some blocks - for example hardware blocks and core.control.input.auto - can only ever have one copy present in benny. These blocks are shared between old and new songs but benny moves them over to their position in the new song.
    
    benny automatically helps clean up a little. When you merge, any muted blocks (in the old song) and any blocks that are only connected to those muted blocks, will be deleted as the new song merges in. 
    
    After merge you'll find two buttons in the top bar: 'select previous' and 'select new' which can help when deleting bits of old song as you move on.

- **Output blocks** 

    In the hardware setup, every audio output on your computer has the option to run another layer of audio processing, called 'output blocks'. As standard the transparent anti-aliasing clipper and dither are selected. Because these are part of the hardware setup not the song they're always present. 
    
    - The **stretch_looper** output block lets you grab a loop of the playing track and keep that looping while the next one loads. It uses z-plane timestretch to make it match the tempo of the next song. *This is still a work in progress.*

    - similarly there's a **big reverb** output block prototype.

- **Hardware** loopers, delays or reverbs - anything that can be used to grab a bit and fill 2-10 seconds works here! *In my current live setup i've built an external version of the stretch looper that runs in a bela pepper eurorack module and additionally provides an emergency loop in the extremely unlikely event of my computer crashing.*

**Live set pro-tips**

Tape your usb cables into the ports, at both ends, every time.
