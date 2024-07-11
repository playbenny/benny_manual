## Arming

To arm a block or blocks for recording, select them (shift+click does multiselect) and press **ctrl-R**.

At the moment (due to a technical limitation I haven't had time to build a workaround for) **hardware blocks cannot be directly recorded**. Instead you can connect a dummy block (eg a vca?) after the hardware one and record that.

![record buttons](assets/screenshots/recording.png)

The 'choose record folder' button will appear in the top bar. Click it and pick a folder, if you haven't already.

The 'record' button will also appear in the top bar. Once you're ready, press record and one stereo wav file will start to be written for every armed block. When you turn off recording, the file recording stops. The files are named with the armed block's name, number, and the time. 

NB unlike many traditional audio softwares, recording is not tied to the global transport - starting recording doesn't start playback, and stopping playback doesn't stop recording.