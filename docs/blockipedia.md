# Blockipedia

Every block has a help/description text you can view in the sidebar. This automatically generated page collates them all.

## core

### core.clock
- Control tempo, swing, and microtiming settings for multiple free but synchronised clock sources. 1 voice = 1 clock. when you merge in another song that contains a clock, it won't adjust the global tempo until you unmute it. it shares timing sync ids with the first clock - ie voice one of every clock block is the same 'virtual player'. Click offset is measured in multiples of vector size, so it should stay consistent if you change vs in future.

### core.input.control.auto
- Midi controller input with optional automapping.

- The values from your midi controller's knobs and sliders are output by this block so you can use them to modulate parameters etc. 

- If auto assign is turned on then when a block is selected the controller will auto assign to this block's parameters. When you deselect the block the midi controller goes back to it's normal mode - outputting values from this block. 

- You can only have one of these blocks per song, for other midi controllers use the core.input.control.basic block.

### core.input.control.basic
- Midi controller input.

- The values from your midi controller's knobs and sliders are output by this block so you can use them to modulate parameters etc. 

- This kind of input block does not use auto assign, just outputs the controls to wherever you route them.  

### core.input.keyboard
- Midi keyboard input. Outputs notes played and the usual keyboard controllers. 

- If auto assign is turned on then when a block is selected the keyboard notes are sent to that block instead, until the block is deselected.

- The block records the last 64 bars of what you've played, and by switching to loop (or overdub) modes - default shortcut F9 - you can select a section of that history. once you're happy with your selection range pressing the spawn button (default shortcut ctrl-F9) will spawn 1 or more seq.piano.roll objects (depending on what you have connected)

### core.scales.shapes
- Scales and shapes storage. You can make scales (dynamically if you want!) using midi input in two ways: 

- For midi into the 'held' input the currently held notes are stored along with the order they were added. 

- A phrase played into the 'pattern' input is turned into a list of notes and the order they were received. it decides you've finished a couple of hundred ms after the last note off, so you can input repeated notes by either holding another previous note while you enter them, or by leaving a very short gap between them. 

- Scales can also span two octaves, if the scale you input is bigger than an octave then it treats it as being two.

- You can edit scales by clicking the keyboard graphics in the ui, but at the moment you can't edit the order of a pattern that way.

- The seq.shape.player can play back these patterns, various pitch quantisation blocks can use the stored lists of notes too. 

- If you add more voices to this block you can have more stored scales and shapes. 

### core.space
- Lets you blow a wind-like force into the flocked parameters simulation. Also has controls for visual declarification.

### core.states
- recall states via midi message. note number = state number. blend input does a xfade from current state to the selected one, based on the velocity of the incoming note.

### core.tuning
- global tuning controller, affects all blocks that have a midi-pitch function (eg oscillators). the tilt and nonlin controls simulate inaccurate tuning in analogue synths and eg pianos - with tilt stretching the tuning across the whole range, which is common in pianos badly tuned by ear, and nonlin introducing slight brownian deviations as you'd see from slightly nonlinear midi-cv conversion in an analogue synth. offset lets you tune to the nearest churchbells or the hum of the mains in your town or 432Hz if you believe in that sort of thing. the scale and root sliders let you select between the common western 12TET tuning, which only sounds good for certain types of melody and harmony, with 3rds sounding particularly rough, and a few other options - just intonation and a couple of scales used in iranian music, rast and segah. all these non-12TET scales are based around a chosen root key, and they generally share the property of some intervals sounding really good and some sounding extra inharmonious. still TODO: more cultural and technical context for each scale, more scales and import of scale files. 

## seq

### seq.eight.step.rhythm
- Parametric rhythm pattern generator by Luke Abbott

### seq.jumps
- takes the incoming note, if it's above C3 it steps up the scale, if it's below C3 it steps down. the further from C3, the bigger the step. notes in the reset input reset the position in the scale to the one nearest the reset note. 

### seq.note.step
- note step sequencer. add more voices for more polyphony. the editor shows you patterns on other voices as hollow notes. 

- on the trigger input C=clock B=back D=reset, you can also directly access the first 128 rows through the row select input. 

- The start point can be before, inside or even after the loop points. the loop follow mode determines how it behaves if you move the loop position or length sliders while it's playing - in soft mode if you move the loop later it will just gradually play through into the new loop, in hard mode it will jump into the new loop. 

- You can also choose how it behaves when the pattern slider changes. the default is to keep the playhead where it was and just carry on reading from the new pattern, but you can also have it reset the playhead to the start point in the new pattern, and optionally to quantise that. to make this step sequencer act like a clip in ableton live use the quantise to bar setting.

### seq.note.tracker
- note tracker. each voice is a monophonic channel of midi notes, add more voices for more polyphony.

- on the trigger input C=clock B=back D=reset, you can also directly access the first 128 rows through the row select input. start point can be before, inside or even after the loop points. 

- notes with no length are only cut off by the next note or entering an 'off' with the 1 key. 

- editor keys:
- notes start at z for the bottom octave and q for the top octave and a half
- 1 enters an 'off' in the notes column
- L and , switch octave
- .or backspace clears a cell (or row if you're in the note column)
- del deletes a row, insert inserts one
- hold shift and use arrows or click to select an area
- ctl-c,ctl-x,ctl-v,ctl-a, ctl-l copy cut paste select all select a whole column
- ctl-i interpolates values from one end of a selection to the other.
- '#' toggles 'grouping' for a row. grouped rows (indicated by a small indent) work as a single step, every time the playhead lands on this step it plays the next one of the grouped notes, round-robin-ing. so if you have a sequence CCCDEF and the last 4 are grouped it'll play CCCCCCCDCCCECCCF. 

- the loop follow mode determines how it behaves if you move the loop position or length sliders while it's playing - in soft mode if you move the loop later it will just gradually play through into the new loop, in hard mode it will jump into the new loop

### seq.piano.roll
- Classic piano roll sequencer. 
- Unlike other benny sequencers this one has an internal clock linked to the global clock and doesn't need a clock in. (It does follow timing drift from the kuramoto section of the clock if that's enabled.)

- ctrl-click to create events, ctrl drag to create many events (in a values lane). scroll adjusts velocity or cc levels, drag or arrow keys to move events, ctrl+scroll, drag or arrow keys to adjust lengths. scroll or shift+scroll on the time ruler for zoom/pan. or drag on the ruler, or shift-drag on the background.

- press 3 to put the ruler into triplet divisions of beats when zoomed in.

- press q to time quantise the selected notes or events to the current grid.

- l makes the selected notes legato.

- At the moment only scroll over the loop start / length etc numbers works to adjust those, and longer sequences than 256 beats can't yet be created in the ui here. More soon.

### seq.rene
- a circle on a cartesian plane step sequencer, obviously inspired by the module of the same name

### seq.shape.player
- The core.scales.shapes block stores the 'shape' of a pattern played into it as well as the scale. This block plays back these shapes. In the clocked modes a trigger note starts the whole sequence playing by itself on a regular clock. The ornaments sliders control the chance of various types of ornamentation being applied to the pattern. On the second midi input C = reset, C# on triggers one of the ornament types.

### seq.values
- A step sequencer for values. One voice = one sequencer row. The 'notes out' uses the value as a note, and the velocity from the incoming trigger.

### seq.wonky
- The step time sliders control the length of each step, the block pro-ratas these lengths to make them fit into the time period you've set below. You can use this as a clock or there are also value sliders so you can use it as a stand alone sequencer - it outputs both the raw slider values and quantised pitches (with vel following incoming clocks).

### seq.analogue
- A simple 'analogue-style' step sequencer. Each step has note, vel, and on/off. 

- Unlike many other sequencers in benny, adding more voices adds more playheads traversing the same sequence. 

- You can clock this sequencer from midi or from audio pulses, or you can use an audio signal to set the playhead position, enabling audio-rate scanning of the sequence.

### seq.sample.tracker
- UNFINISHED

- buzz-style sample tracker.

- works but none of the fx commands are implemented yet

## midi

### midi.autodamp
- Implements the korg mono/poly's autodamp feature. Note offs are stored up and not sent, even when all notes are released. Only when a new note starts after a silence are they all sent. Works nicely for paraphonic pads if you play the voices through this and have a separate envelope for a main vca like a mono/poly.

### midi.calculus
- Differentials and integrals of midi value streams.

- This block can output a value representing the speed and direction of movement of a value, or output a value only when it changes, or sum a value over time.

### midi.curve.map.1d
- Maps input values to output values defined by the curve you draw with the sliders. Useful for control mappings. You can choose how many sliders there are if you want a few neat steps.

### midi.delay
- Delays midi events, with optional filtering so that if you patch feedback into this block it won't go on forever.

- The per-note random delays are useful for eg randomly varying the order and spacing of the notes of chords.

### midi.ducker
- Sidechain midi ducker by Luke Abbott

### midi.fidget
- ADHD for a controller. refuses to sit on one value for too long, once it gets bored takes a brownian hop to a nearby value. for example, put it between a midi controller and the parameter you want to control.

### midi.fold
- Transposes, folding notes that lie outside the set range. 

- The last control, 'glissando', determines whether the output notes change when you adjust the controls as opposed to just when new notes come in. You can send midi to the second input to set the transpose value.

### midi.free.clock
- a free-running clock, disconnected from the global one

### midi.holes
- Forgets some midi events, randomly

### midi.lfo
- A midi LFO, if you add more voices they're linked, so you can build eg quadrature lfos from this.

### midi.note.length
- sets the length of midi notes. 

- when set to zero the notes are passed as instantaneous triggers with no length. 

- randomness increases the length of notes, the randomness shape control alters the distribution of random values from evenly spread (at 0) to more like a steep curve skewed towards zero (at 1).

### midi.note.select
- filters notes based on whether they are in the selected scale. 

- also splits to one output per note

### midi.pitch.range
- gate (or split) notes based on pitch

### midi.rhythmes.alpes
- Switches between subdivisions of a clock, inspired by the mechanical proto-drummachine used by the wonderful french group 'Catherine Ribiero & Alpes'.

### midi.scale.quantise
- Quantises notes to the scales defined in the core.scales.shapes module. 

- This block works efficiently for fast note streams (including if you patch an audio signal to the note in) but there is also a utility.audio.scale.quantise which works all the way up to audio rate.

### midi.smooth
- Uses a 2 pole low pass filter modulated by a bandpass out of the same filter to smooth values in a way which responds well to fast changes. Algorithm by Andrew Simper of Cytomic from here: https://cytomic.com/files/dsp/DynamicSmoothing.pdf. The 'sensitivity' control governs how much the bandpass modulates the lowpass.

### midi.stats
- Useful metrics about the incoming midi:
- -notecount
- -lowest
- -highest
- -quietest
- -loudest
- -time interval between notes

### midi.sustain
- hold the last n notes. if n=0 it turns all notes into instantaneous triggers with no duration.

### midi.switch
- Has multiple ins and outs, lets you select an input and route it to an output, (accomplishing the functions of the max gate and switch objects). Also lets you select i/o via midi and cycle through io via midi

### midi.utility.buttons
- 3 buttons on a panel, 3 separate outputs. 

-  Optionally the vertical position of the button click can affect the output velocity. 

- While the button is lit (hold/toggle modes) the 'switched inputs' pass midi messages to their respective outputs.

### midi.utility.delay
- utility delay for midi. has time settings in samples, vectors, ms and beats that are added together.

### midi.utility.values
- 3 sliders 3 values, useful for offsetting params of individual voices, summing modulations, flocking variables from different blocks, etc

### midi.velocity
- gate notes based on velocity
- compress or expand velocity range
- humanise velocity
- control output velocity range

### midi.wait
- Collects up notes that come in until a trigger is received in the second input, at which point it dumps them all out in the order they were received. The clear input wipes the stored notes.

## source

### source.abb.phase.distortion
- crunked up phase distortion oscillator alligator

### source.abl.chip
- wrapper for the abl.dsp.chip oscillator. only available in max 9.

### source.abl.crackle
- wrapper for the abl.dsp.crackle oscillator. only available in max 9.

### source.basic.osc
- Basic single oscillator. Shape fades from sine through triangle saw rectangle square triangle and back to sine. Accepts MIDI and CV, works in *LFO* and *audio* ranges. The 'initial pitch' slider sets the starting pitch, incoming midi overrides this but doesn't reset the slider. 

- The rectangle portion of this oscillator uses 'EPTR' code from Yofiel.com. 

### source.braids
- A wrapper for Volker Böhm's port of Émilie Gillet's Braids module. 48 different oscillator models! 

- I've adapted it to work with benny's global tuning system. I've also added velocity mod controls, if the vel->vca != 0 it introduces a tiny 3ms delay on notes and triggers to avoid clicks. The scale quantise in the module isn't implemented as it wouldn't work with benny's global tuning, and we have scale quantisers already in benny.

### source.dual.osc
- A pair of basic oscillators with diverse cross modulation possibilities. 

- Shape fades from sine through triangle saw rectangle square triangle and back to sine. Accepts MIDI and CV, works in LFO and audio ranges. 

- The rectangle portion of this oscillator uses code from Yofiel.com. 

### source.harmonic.osc
- 8 drawbar harmonics, uses non-linear summing borrowed from airwindows console which serves to give it a nice glued character that sits in a mix well, less a collection of digital sines than a single voice.

### source.quanti.slide.osc
- Quanti-slide oscillator. Quantises pitch to the selected scale - the quantiser is after the midi note in (with portamento), the detune, the range, the fm input and the unstable pitch are summed. The slide width control controls the size of a linear transition region between pitches - on 0 you get sharply quantised notes, on 1 you get no quantisation at all. 

- Like the basic osc, shape fades from sine through triangle saw rectangle square triangle and back to sine. Accepts MIDI and CV, works in *LFO* and *audio* ranges. The 'initial pitch' slider sets the starting pitch, incoming midi overrides this but doesn't reset the slider. 

- The rectangle portion of this oscillator uses 'EPTR' code from Yofiel.com. 

### source.random.noise.s&h
- inspired by the buchla stepped and continuous random.
- - multiple colours of noise
- - blending shift register
- - sample & hold
- - slew
- - quantise
- - audio input can be used with the s&h / shift register
- - the midi 'both' input feeds the note value into the s&h's audio input (if noise colour slider is on audio input) and also triggers a step, so you can use it to do sublooping type shift register effects on midi patterns.

### source.sheep
- A wrapper for Volker Böhm's port of Émilie Gillet's Tides module running the unofficial 'Sheep' firmware, which is a XY wavetable synth oscillator.

### source.shepherd.osc
- Shepherd oscillator. Mixes multiple octaves of a wave to let you make scales that ascend or descend forever, or parts that fluidly morph between high and low frequencies, using the ideas of Roger Shepherd and his famous barberpole tone (which this block can recreate by connecting a rising sawtooth lfo to the fm input). Shape fades from sine through triangle saw rectangle square triangle and back to sine. Accepts MIDI and CV, works in LFO and audio ranges. The rectangle portion of this oscillator uses code from Yofiel.com. 

### source.tides
- A wrapper for Volker Böhm's port of Émilie Gillet's Tides module. The frequency slider is overridden by note inputs.

### source.wave.scan
- A looping wave player that lets you fluidly move around the longer sample while staying quantised. EG if you have a long wav of a drum performance loaded you can 'play' it by moving the target parameter and this block will keep it in time.

## voice

### voice.basic
- Basic single oscillator through a VCA driven by an ASR envelope. Shape fades from sine through triangle saw rectangle square triangle and back to sine. Accepts MIDI and CV, works in LFO and audio ranges. The rectangle portion of this oscillator uses code from Yofiel.com. 

### voice.dual
- A pair of basic oscillators, with 2 envelopes and vcas and a load of diverse cross modulation possibilities. Shape fades from sine through triangle saw rectangle square triangle and back to sine. Accepts MIDI and CV, works in LFO and audio ranges. The rectangle portion of this oscillator uses code from Yofiel.com. 

### voice.elements
- A wrapper for Volker Böhm's port of Émilie Gillet's Elements module.

### voice.harmonic
- 8 drawbar harmonics + env + vca. uses non-linear summing borrowed from airwindows console, and a very gentle sine shaper on the output post env/vca, which all serves to give it a nice glued character that sits in a mix well, less a collection of digital sines than a single voice.

### voice.ks
- Basic KS string model with selfmodulation and a -x^3 saturator in the feedback loop. ##positive values of 'highpass' are a onepole in the loop, negative values are a 2 pole highpass post-filter. in both cases pitch is relative to the string's current note pitch. ##selfmod is self-fm simulating a tanpura's curved bridge. negative values have a half-wave rectifier on this modulation.

### voice.modal
- Simple voice made around a bank of resonators and a selection of model algorithms for setting the frequencies, amplitudes and bandwidths of those resonators. Models come from an article by Nathan Ho.

- -Elements string

- -Piano stiff string

- -Free Beam (eg xylophone)

- -Cantilever Beam (eg mbira)

- -Rectangular Membrane

- -Rectangular clamped plate

- -Tubular bell

- -Free Plate

### voice.multi.sample.player
- multisample player with slices, offset, timestretch, and a set of loose emulations of melotron mechanics - pitch wobble, motor drag (proportional to the number of notes held down*), and a finite limit set on rewind speed. 

- this voice expects you to load a wave with an ascending scale, evenly spaced, with the slices set.

- * motor drag only works when an actual connection has been made - it won't work when auto-assign keyboard is played into the block.

### voice.noise
- noise source + VCA + ENV. midi to the 'damp' input causes the envelope to close quickly.

### voice.organ
- 9 drawbar harmonics with a rough model of how the key contacts of a hammond tonewheel organ worked. the notes input blends between pressed and struck profiles based on velocity, with very quiet notes corresponding to partial keypresses that don't engage the switch for every harmonic. inspired by the paper 'Dynamic temporal behaviour of the keyboard action on the Hammond organ and its perceptual significance' by Giulio Moro, Andrew P. McPherson and Mark B. Sandler in JASA 142/5 2017.

### voice.pitch.env
- like voice.basic - a single oscillator + VCA + ENV but with a 2nd ENV routed to pitch. 

### voice.plaits
- A wrapper for Volker Böhm's port of Émilie Gillet's Plaits module.

- 16 different engines in one. The input destination controllers work with the original module's different behaviour when patched/unpatched - the parameters that aren't selected here are connected to an internal decay envelope.

### voice.rings
- A wrapper for Volker Böhm's port of Émilie Gillet's Rings module.

### voice.sample.player
- sample player with slices, offset, timestretch

### voice.shepherd
- Shepherd oscillator with env and vca. Mixes multiple octaves of a wave to let you make scales that ascend or descend forever, or parts that fluidly morph between high and low frequencies, using the ideas of Roger Shepherd and his famous barberpole tone (which this block can recreate by connecting a rising sawtooth lfo to the fm input). Shape fades from sine through triangle saw rectangle square triangle and back to sine. Accepts MIDI and CV, works in LFO and audio ranges. The rectangle portion of this oscillator uses code from Yofiel.com. 

## fx

### fx.abl.distortion
- wrapper for the abl.dsp.distortion. stereo in stereo out. only available in max 9.

### fx.abl.fuzz
- wrapper for the abl.dsp.fuzz. stereo in stereo out. only available in max 9.

### fx.abl.pitchshift
- wrapper for the abl.dsp.pitchshift. stereo in stereo out. only available in max 9.

### fx.abl.waveshaper
- wrapper for the abl.dsp.waveshaper. stereo in stereo out. only available in max 9.

### fx.clouds
- A wrapper for Volker Böhm's port of Émilie Gillet's Clouds module. The module's internal buffer is 4 seconds long, you can save it to a wave slot and you're also able to load waves into it.

### fx.clouds.pvoc
- A wrapper for Volker Böhm's port of just the phase vocoder from Émilie Gillet's Clouds module.

### fx.delay.buckets
- Bucket Brigade Delay emulation. Accurate model of writing into a delay line with variable sample rate, responds to input changes in the same way a real BBD does. Additionally includes pre-filter, compander, soft sat, boundary loss and clock leakage, post-filter, HPF in one of two positions, and bit depth quantise (to simulate an early digi-delay rather than a BBD).

### fx.delay.stretch
- Delay line with phase vocoder read head allowing time change without pitch shift, or pitch shifted delays.

### fx.delay.tape
- Basic delay line with tape-like repitching, mod, timeslips and saturation. The repitch midi input alters the delay time multiplier to shift by the desired interval (so if for example a C is held in the delayline and you play an F the rate is changed in order to repitch the playback and subsequent repeats up to an F)

### fx.elements.verb
- A wrapper for Volker Böhm's port of just the reverb from Émilie Gillet's Elements module.

### fx.filter.2pole.env
- surreal machines' zero delay feedback filter model with an ASR env

### fx.filter.2pole
- surreal machines' zero delay feedback filter model

### fx.filter.abl.filther
- wrapper for the abl.dsp.filther filter. second input is frequence modulation. only available in max 9.

### fx.filter.abl.lowpass
- wrapper for the abl.dsp.dfm filter. second input is frequence modulation. only available in max 9.

### fx.filter.abl.vowel
- wrapper for the abl.dsp.vowel filter. second audio input is switchable between cutoff and formant modulation. only available in max 9.

### fx.filter.fixed.bank
- fixed filter bank based on the moog 914 with an option to split odd and even bands to different outputs. 

- uses airwindows style non-linear summing to recombine the bands, so clips internally if driven too hard. 

- if you want to modulate frequency the fx.filter.reson is a single band, designed for modulation, and you can use it polyphonically to approximate a moveable version of the fixed filter bank.

### fx.filter.reson
- wrapper for max msp's reson~ object, a simple digital biquad resonant bandpass filter with audio-rate modulation of one parameter of your choice. optionally frequencies can be quantised to the notes of a scale defined in core.scales.shapes

### fx.filter.vactrol.lpg
- modelled vactrol lpg, based on the paper and example patches by Julian Parker and Stefano D’Angelo. 

- http://www.acoustics.hut.fi/publications/papers/dafx13-lpg/

### fx.freqshift
- max msp's freqshift object. for both positive and negative shifts mix both outputs. the audio rate input is fm of the freq set by the slider

### fx.mod.abl.chorus
- wrapper for the abl.dsp.chorus. stereo in stereo out. only available in max 9.

### fx.mod.abl.ensemble
- wrapper for the abl.dsp.ensemble. stereo in stereo out. only available in max 9.

### fx.mod.abl.flanger
- wrapper for the abl.dsp.flanger. stereo in stereo out, but there's no crossfeed so you could use one side as an envelope input. only available in max 9.

### fx.mod.abl.phaser
- wrapper for the abl.dsp.phaser. stereo in stereo out, but there's no crossfeed so you could use one side as an envelope input. only available in max 9.

### fx.mod.abl.vibrato
- wrapper for the abl.dsp.vibrato. stereo in stereo out. only available in max 9.

### fx.pitch.divider
- an octave divider / sub oscillator generator inspired by the 4ms atoner

### fx.pitch.gate
- pitch detecting gate, based on an idea Waclaw Zimpel had. the idea is to separate different pitches to different outputs. only works with monophonic input audio, results may vary depending on the source. Waclaw was using the m4l version of this with a mic inside the barrel of his clarinet, which gives a very clean signal that works well.

- in single voice mode output 1 is the 'selected notes' and output 2 is the 'unselected notes'. 

- if multiple voices are instantiated then each voice only selects / unselects one note from the list of available ones.

- as with the fx.pitch.retune block you set the notes you want either using a scale (defined in the core.scales.shapes block) or midi input.

- the midi outputs give you (on 1) the detected pitch and (on 2) the gate status of the voice, which you could use to drive an envelope, for example.

### fx.pitch.retune
- automatic retuner, autotune-like, tries to force incoming (monophonic) audio to fit the scale (or list of allowed notes) it's been given. you can set scales using the core.scales.shapes block or with midi in. 

- also outputs detected pitch (though a limitation of the max object it uses means this is just note, not octave).

### fx.pitch.shift
- pitch shift

### fx.reverb.abl.darkhall
- wrapper for the abl.dsp.darkhall reverb. stereo in stereo out. only available in max 9.

### fx.reverb.abl.plate
- wrapper for the abl.device.reverb. mono in stereo out simple plate reverb. only available in max 9.

### fx.reverb.abl.prism
- wrapper for the abl.dsp.prism reverb. stereo in stereo out. only available in max 9.

### fx.reverb.abl.quartz
- wrapper for the abl.dsp.quartz reverb. stereo in stereo out. only available in max 9.

### fx.reverb.abl.shimmer
- wrapper for the abl.dsp.quartz reverb. stereo in stereo out. only available in max 9.

### fx.reverb.abl.tides
- wrapper for the abl.dsp.tides reverb. stereo in stereo out. only available in max 9.

### fx.varispeed.looper
- Flexible buffer record/playback device inspired by monome norns' softcut: record and play into and out of the buffer can occur at any rate you like. Multiple voices can access the same or different wave buffers. All jumps and loops are crossfaded smoothly. The buffer it uses is tagged with timestamps and metadata and available (as one of the waves on the waves page) for other blocks to play or write into. You can save this wave from there if you fill the buffer with something you like. Does an excellent impression of how BBD delays repitch, but is capable of far more - loopers, buffer-fx, repitchers, complex delays, sample-mangling, live resampling, etc

### fx.warps
- A wrapper for Volker Böhm's port of Émilie Gillet's Warps module, which lets you smoothly fade between several different algorithms for combining two signals.

### fx.wavefold
- wavefolder modelled roughly after the doepfer one

### fx.wizard.saturation
- W I Z A R D S A T U R A T I O N##By Luke Abbott

## utility

### utility.abl.3band.eq
- wrapper for the abl.device.channeleq. stereo. only available in max 9.

### utility.abl.compressor
- wrapper for the abl.device.compressor. only available in max 9. the second output is the compressor gain reduction amount.

### utility.abl.env.follow
- wrapper for the abl.device.envfollower. a simple envelope follower. only available in max 9.

### utility.abl.limiter
- wrapper for the abl.device.limiter. stereo. only available in max 9.

### utility.abl.transient.design
- wrapper for the abl.dsp.transientdesigner. a simple transient design effect with a separate input for the control signal. only available in max 9.

### utility.audio.smooth
- Uses a 2 pole low pass filter modulated by a bandpass out of the same filter to smooth values in a way which responds well to fast changes. Algorithm by Andrew Simper of Cytomic from here: https://cytomic.com/files/dsp/DynamicSmoothing.pdf. The 'sensitivity' control governs how much the bandpass modulates the lowpass.

### utility.basic.file.player
- lets you open a file and play it. autostarts on record. handy for rendering a stem through a benny fx chain, for example.

- for playing waves with more control try wave scan (lets you skip eg stem recordings maintaining phase with the loop in the recording) or the sample player or sample tracker blocks.

- you can drag and drop waves onto the benny logo on the launcher and they'll be loaded into the waves page for you.

### utility.bonk
- wrapper for Volker Böhm's 64bit port of Miller Puckette's bonk~ object for max/msp. detects drum hits and outputs midi. to train it so it can identify which drum is which it needs to hear at least 10 of each with learn mode on, then turn learn off.

- *at the moment learn mode works but the save/recall of learned drum templates isn't implemented.

### utility.cv.scale.quantise
- Quantises notes to the scales defined in the core.scales.shapes module. 

- This version is optimised around supporting CV input for audio-rate quantising of control signals. There is a midi-only scale quantise block that uses slightly less resources.

### utility.delay
- uncoloured digital delay. time settings in samples, vectors, ms and beats are ADDED together. each cable connection step in the patch introduces 1x vector's worth of delay.

### utility.env.asr
- ASR envelope, follower, slew etc

### utility.env.eight.stage
- 8 stage multi-mode envelope. easily chainable, lots of interesting trigger ins and outs.

### utility.env.four.stage
- 4 stage multi-mode envelope. easily chainable, lots of interesting trigger ins and outs.

### utility.eq.peak
- a single band of nonstandard stereo peak/notch eq. partially gain compensated, airwindows style nonlinear internal summing, selfmod. cut is a subtle (undistorted) notch, boost fades from a peak kind of shape into more of a bandpass at the extreme settings. 

- all parameters are smoothed, this block was designed with flocking in mind - eg for eq peaks that move out of each other's way.

- pan goes wider than the stereo field - ie if abs(pan)>1 the opposite effect starts to happen on the other side - a peak on the left gets a cut on the right, etc.

### utility.gate
- very basic gate

### utility.lowpass.highpass
- airwindows capacitor2 - a lowpass / highpass with modelled self-modulation.

### utility.mid.side
- mid-side processor

### utility.pan.mono
- takes a mono input, lets you adjust pan. has audio-rate control input.

### utility.record.endpoint.stereo
- DOES NOTHING. but is a convenient way to record a stereo wav - just route whatever into it and arm it to record. useful for recording multiple blocks. passes through unaltered audio.

### utility.self.tuner
- self-tuning midi to cv converter. 

- connect your osc's output to the listen input. connect the cv output to the osc cv input. optionally if you want to modulate the osc's frequency do it THROUGH this block, via the second input. play notes into the midi input here. 

- if you have more than one oscillator you can add more voices to the tuner for polyphonic midi. the midi through out is useful for lining envelopes up with voices.

- IMPORTANT make sure you've used the hardware config tool to run at least one loopback test so it can store the measured loopback latency for your current system. this helps tuner stability.

### utility.sidechain.compressor
- simple sidechain compressor

### utility.vca.env
- VCA with integrated ASR envelope, follower, slew etc

### utility.vca
- log/lin vca

### utility.xfade
- each voice of this is just a vca controlled by the main xfade slider, so it can xfade between either inputs or outputs.

- to fade one input signal between a number of outputs connect the input to every voice. 

- to xfade between a number of inputs connect every output to a single destination.

## mix

### mix.bus
- every mix.channel/stereo.channel etc block has to be routed, at unity gain, to one of these, to make the magic work.

- IMPORTANT this block will only work if you have the airwindows console 7 vsts (console7channel64, console7cascade64, console7buss64) installed.

### mix.channel
- mixer channel. borrows the mix concept from worrng modules, uses airwindows console7 for nice summing and drive. 

- MUST BE ALL ROUTED FROM THIS BLOCK INTO A mix.bus BLOCK.

- IMPORTANT this block will only work if you have the airwindows console 7 vsts (console7channel64, console7cascade64, console7buss64) installed.

### mix.stereo.channel
- mixer channel. borrows the mix concept from worrng modules, uses airwindows console7cascade for nice summing and drive. MUST BE ALL ROUTED FROM THIS BLOCK, AT UNITY GAIN, INTO A utility.mixer.buss BLOCK.

- IMPORTANT this block will only work if you have the airwindows console 7 vsts (console7channel64, console7cascade64, console7buss64) installed.

## zx

## test

## tg

## fb

