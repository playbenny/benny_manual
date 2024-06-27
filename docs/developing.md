#developing blocks

if you can use max/msp making blocks for benny is pretty easy. have a look in docs / block development / example patchers

every block needs, at minimum:

- a .json file describing its inputs, outputs, parameters

- a .maxpat file (that does the processing - note or audio - for one voice of your block)

the examples tell you everything you need to do. there are handy things like pitch lookup tables and shared memory for things like sequence storage and your patch can easily manipulate absolutely any part of the song or set. 

optionally blocks can draw their own fullscreen / mini ui views like some of mine do. this is a 'block_ui_patcher' - a different patch, loaded separately from the voices. there's a max-only example in the note blocks folder, or you can look at the javascript-powered uis of any of the built in sequencers.
