- To set a particular song file as your default startup file, save it as 'autoload.json' in the templates folder in the benny folder


- To assign a mini controller control (e.g. knob) to a parameter, 



- To load a sample to be used in your set, go to the Waves panel, click a box and load it in.



- To record a performance, select the blocks you want to record, click the record arm shortcut CTRL + R, choose the saved file destination from the top bar, and then click record as you perform your recording. Click record again to finish, the file will be in the destination.
- benny records both outputs of every voice to a separate WAV file. at the moment hardware blocks can't be recorded directly, so put a VCA set to unity gain after them and record that.
- if you use the mix channel / stereo channel and mix bus blocks then you have convenient things to record stems / stereo master from



- To shift from one note pattern (e.g. a melody in the Note Step block) to another (a different melody):


The note step block has a patterns slider that lets you switch between predefined patterns. You could sequence that with a seq.values

That block has an output at the end of pattern, designed for if you want to move to the next pattern with it.

- Some blocks (seq.analog) store their pattern as parameters. You could sequence these by storing states for different patterns.

- alternatively, you can modulate the 'start' or 'offset' controls on many sequencers, so you can just write one pattern after the other
