#Developing blocks

If you already know how to use max/msp then it is easy to make blocks for benny. 

Every block needs, at minimum:

- a **.json** file describing its inputs, outputs, parameters

- a **.maxpat** file (which does the processing - note or audio - for one voice of your block)

Have a look in the ```docs/block development/example patchers``` folder. The examples tell you everything you need to do and cover all of the helpful things benny provides, such as precalculated pitch lookup tables and shared memory for things like sequence storage. You can make a patch to manipulate absolutely any part of the song or set. 

Some of the included blocks draw their own custom fullscreen / mini ui views, and you also have the option to add this functionality to your own blocks. This requires a **block_ui_patcher**, a new patch which loads separately from the voices. There is a max-only example of this in the note blocks folder, but for more involved interfaces it makes more sense to use javascript. See the included code for examples.

If you need help, please do ask on the [discussion](https://github.com/playbenny/benny/discussions) forum.