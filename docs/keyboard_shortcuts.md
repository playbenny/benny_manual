##GLOBAL KEYS

**ESC** - back out of menus, unselect, recenter blocks view, cancel dragging

**`** - all off (ends all midi notes etc)

**ctrl-`** or **ctrl-=** - resync (resets the phase of all sequencers on the next downbeat)

**space** - play button

**ctrl-space** / **opt-space** - load next song

**ctrl-s** - save

**CAPS LOCK** - when on, the qwerty keyboard is 2.5 octaves of notes, starting at **Z** up to **M** for the first octave, then from **Q** to **]**. To go up and down an octave use **L** and **,**.

**F1** - panels view

**F2** - blocks view

**F3** - waves view

**F4** - recall page.

**F6** - sidebar block settings page

**alt-F6** - open the selected block's voice max patcher for editing.

**F7** - sidebar connections list page

**F8** - files page (save/load/merge/choose song folder)

**F11** - toggle fullscreen

**ctrl-F12** - resource usage page

**F12** - show the core.input.control.auto fullscreen view (so you can see what your midi controller is mapped to)



**ctrl-alt-F12** - hard restart benny




##SIDEBAR

**scroll** / **drag** - to adjust sliders, zoom scopes etc. **+shift** for fine, **+alt+shift** for extra fine.

**ctrl-hover** your mouse over sliders to select an individual voice. **scroll+alt+shift** to tilt individual voice values around that voice.

**alt click** - to return a slider to its default value (or to the value saved in your songfile).

**\\** - while hovering over a sidebar parameter slider, enters midi map mode. move a control to make a mapping to that slider.

**012345679** while hovering over a slider you can enter numbers, hit enter to store
**./** you can also enter lists, eg `1,2,3,,,5,0,2.4` which will create a seq.values wired to make that pattern of automation happen. and if you end the list with a slash and a time division (eg `/4n`) then the seq.values will be connected to a new clock voice at that rate.




##BLOCKS PAGE

**shift-drag** - for a selection rectangle

**shift-click** - to multi-select blocks or wires 

**ctrl-click** - to mute blocks or wires
   
**ctrl-shift-click** - (when unmuting only) holding shift too also 'unmutes the tree' - any muted blocks connected to this one and any muted blocks connected to those, etc.

**alt-click** - to bypass blocks

**drag** - to move blocks, or drag a block over another one to connect them.
        hold **ctrl** when you release to make the new connection muted.

**shift-drag** - to connect a block to itself

**ctrl-shift-drag** - insert a block into a wire

**scroll** / **ctrl-drag** - to zoom

**ctrl-scroll** - over a wire, adjust connection level

**alt-shift-scroll** - make space: push (or pull) all blocks away from (or towards) the mouse cursor, linearly


**home** or **cmd-0** - center view

**-** or **+** - change the polyphony of the selected block

**ctrl-m** - toggle mute for the selected blocks

**ctrl-r** - toggle record arm for the selected blocks

**ctrl-a** - select all

**ctrl-c** - copy

**ctrl-x** - cut

**ctrl-v** - paste. 

    - You can copy and paste single or multiple blocks in the blocks view.

    - To copy parameter values from block to block: copy a single block, select a target block of the same kind and then paste.

**ctrl-alt-V** - paste blocks including their connections. For example, if you copy an oscillator that is connected to a mixer and a midi source, then the pasted duplicate will have the same connections.

**ctrl-d** - duplicate selected blocks

**ctrl-z** - undo

**del** / **backspace** - delete everything selected

**shift-del** / **shift-backspace** - 'delete tree' - deletes the selected blocks, then any blocks that were only connected to/from a deleted block, recursively.

**shift-T** - 'select tree' - selects what delete tree would delete. useful for saving a part of a patch out as a template. by default select tree, delete tree and mute tree all ignore connections to core.input.control.* blocks when counting connections but the config key ```TREE_SELECT_IGNORES_CONTROL_BLOCKS``` can change this.

**alt-left arrow** - back to previous sidebar view

**alt-right arrow** - forward to next sidebar view

**alt-up** / **alt-down** - if you have a wire selected these will take you to the block at the start or end of the wire.

**insert** or **ctrl-i** - if you have a wire selected, insert a block into the connection

**enter** - if you have a wire selected, collapse source / destination input and output menus.

**enter** - open the new block menu

**tab** - toggle between blocks / panels views

**up** / **down** / **left** / **right** - move selected blocks, **+shift** for fine movement.

**PGUP** / **PGDN** - zoom in or out

**ctrl-T** - in fullscreen mode benny shows a clock in the top right corner. This key switches to showing a set timer (that starts the first time you press play). **ctrl-alt-T** resets this timer.

**[** / **]** - for control.auto when there are more parameters than there are knobs/sliders on your controller these keys cycle the mapping offset.

**?** - show the help for the selected block in the sidebar

**/** - to start searching amongst blocks in the current song

**any other keys** - start typing the name of your chosen block to bring up the new block menu.

**shift** - when selecting a block in the block menu automatically makes a connection between the block that was selected before opening the new block menu and the newly added one.



##PANELS PAGE

**ctrl-m** , **tab** ,**-**, **+** work as on the blocks page.






##PERSONALISING

The shortcuts are all stored in keymap.json. If you press a key combination that isn't assigned then benny prints 'keycode 994' or similar to the max console. This number is what you need to swap into the relevent entry in this file if you want to change a keyboard mapping.