#Developing blocks

If you can use max/msp, making blocks for benny is easy. 

Every block needs, at minimum:

- a .json file describing its inputs, outputs, parameters

- a .maxpat file (that does the processing - note or audio - for one voice of your block)

Have a look in ```docs/block development/example patchers```. The examples tell you everything you **need** to do and cover all the helpful things benny provides. There are handy things like pitch lookup tables and shared memory for things like sequence storage and your patch can easily manipulate absolutely any part of the song or set. 

Optionally blocks can draw their own fullscreen / mini ui views like some of the included ones do. This is a 'block_ui_patcher' - a different patch, loaded separately from the voices. There's a max-only example of this in the note blocks folder, or you can look at the javascript-powered uis of any of the built in sequencers. 

If you need help, please do ask on the [discussion](https://github.com/playbenny/benny/discussions) forum.