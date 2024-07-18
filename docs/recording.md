## Arming

To arm a block or blocks for recording, select it/them (shift+click to multiselect) and press **ctrl-R**.

![record buttons](assets/screenshots/recording.png)

The 'set record folder' button will appear in the top bar. Click it and pick a folder.

Next to it is the 'record' button. Once you're ready, press record and benny will start to write one stereo wav file for each voice of every armed block. When you turn off recording, the file recording stops. The files are named with the armed block's name, number, and the time. (You can rename blocks by ctrl-clicking)

Note: unlike many traditional audio softwares, **recording is not tied to the global transport** so starting recording does not start playback, and stopping playback does not stop recording.

At the moment (due to a technical limitation I haven't yet had time to build a workaround for) **hardware blocks cannot be directly recorded**. Instead you can connect a dummy block (eg a vca?) after the hardware one and record that.