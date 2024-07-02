The sidebar shows the details of whatever you're looking at.

## blocks

With a single block selected the sidebar shows you all it's settings. Click the section headers to move through them. If a block has multiple voices there'll a be a section like this where you can choose to select and adjust either the whole block or an individual voice.

### scopes

Audio blocks have a scope for each output. The scrollwheel (or dragging up and down) lets you zoom these scopes. Red shows values that go outside the normal ranges (though there is no clipping on connections between blocks)

### parameters

This section shows the parameters for the block. Drag or use your scroll wheel to adjust these. Shift for fine adjust, Alt+shift for extra fine. Alt-click returns a value to its default (or if you loaded the songfile from disk, to the value it was in the last save).

If a block has multiple voices then while you hold ctrl and mouse over a slider it'll highlight it and let you adjust that one individually. Ctrl+Alt lets you tilt all the values of the individual voices around the one you're hovering over.

### mini-ui

Here's an example of a block with a mini-ui showing what it's doing. Some of these allow mouse interaction. Often they'll have an 'edit' button beneath that brings up a full-featured version of the editor on the rest of the screen.

### block settings

Reload - does a full hard reload of the block's code.
Swap - lets you swap a block out for a different one.
Copy paste del do what you'd expect.
Open patch - opens the max patcher for the first voice of the block.

#### polyphonic note allocation modes

Here you set the number of voices and select the mode for picking what voice a new note goes to. There are separate mode settings for how it allocates a note to a currently inactive voice and for when the new note has to steal a currently active voice.

**Blind cycle** - each note that comes in is allocated to the next voice in turn, without concern for whether that voice is playing or whether the same note is already playing on another voice.
**Blind random** - likewise but the next voice is picked at random
**Cycle free** - the next free voice is picked, working round in order.
**Cycle random** - a voice is picked at random from the currently unused ones.
**Notememory** - it keeps track of which voice last played a particular note and returns to that one. This is how (for example) the prophet 600 allocated midi to voices.

There are two other controls:
**Stack** - plays mutliples of notes, or adds suboctave notes.
**latching** - only implemented on a few blocks so far, this gives the option for parameters to update only one note on and/or note off events (as opposed to continuously, as is the default)

#### panel assign

Press the panel assign button to put the sidebar into a mode where you can select parameters to be shown on the [panels](panels.md) page.

#### flock

Benny lets you attach up to 3 parameters to the position of imaginary creatures in a flocking simulation. Once you've assigned parameters to axes using the flock assign button you can adjust the properties of the simulation. As well as weight, tension of the spring connecting the creature to the parameter value and friction, there are parameters governing the creatures' attraction or repulsion from one another, random movement, and desire to align their motion with the others.

As well as interesting chaotic autovariation and fun parameter-smoothing/overshoot this feature can be useful for making voices try not to occupy exactly the same parameter space as each other.

#### errors

You can introduce per-voice static errors, a gradual (per-voice) drift of parameters, and there's also a 'panel lockup' feature which simulates something my prophet-600 does where randomly, for a few moments, a parameter will stop updating for just one voice.

### states

This section of the sidebar lets you store the current parameter values to a 'state'. States that have something in (either for this block or for others in the song) are highlighted with a border. Alt-click lets you remove this block from a state.

### connections

Here you can see a list of all the connections to and from this block. You can edit them here or click them to bring up the detailed connection edit view.

### help

This shows the help text for the block (also visible when you hover over the block in the new block menu)