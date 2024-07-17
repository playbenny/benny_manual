benny was designed not just for making individual songs, but for playing live sets.

Unlike other live music software benny doesn't load all the parts of all the songs at once. I felt that in order to play a song properly it would help both the performer and computer not to be burdened by the knowledge of the other songs.

benny treats the songs folder you've selected as your live set. When it starts it preloads all the songfiles, then looks to see if it can preload any samples too. When you load a new song to the next it recycles as many blocks as it can, so load times are as quick as possible. 

So if you want to play one song then the next (like a band) then benny loads songs faster than people can possibly stop clapping.

If you want to segue between songs there are a few approaches:

- **merge** lets you load the next song in next to the current one. if 'purge_muted_trees' is enabled in config any muted blocks (in the current song) and any blocks that are only connected to those muted blocks, will be deleted as the new song merges in. this means you can mute a load of bits of your previous song and things will tidy up a bit as the new one loads. after merge you'll find two buttons in the top bar: 'select previous' and 'select new' which can help when deleting bits of old song as you move on.

- **output looper** the outputs in benny can have an additional layer of processing - this is defined in the hardware setup, for example you could have a main bus compressor permanently across your stereo outs, if you wanted. these output blocks are part of the hardware setup, not the song, so they don't change when you load a new song. it's not finished, but the 'stretch_looper' output block lets you grab a loop of the playing track and keep that looping while the next one loads (as the output block where the looper lives isn't part of the song it doesn't get interrupted). it uses z-plane timestretch to make it match the tempo of the next song.

- similarly there's a 'big reverb' output block

- hardware loopers (coming soon) i've built an external version of the stretch looper that runs in a bela pepper eurorack module and additionally provides an emergency loop in the extremely unlikely event of your computer crashing.

**live set tips**

tape your usb cables into the ports, at both ends, every time.
