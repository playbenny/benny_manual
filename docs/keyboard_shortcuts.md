##GLOBAL KEYS

**ESC** - back out of menus, unselect, recenter blocks view, cancel dragging

**`** - all off (ends all midi notes etc)

**space** - play button

**ctrl-space** - load next song

**ctrl-s** - save

**CAPS LOCK** - when on, the qwerty keyboard is 2.5 octaves of notes, starting at **Z** up to **M** for the first octave, then from **Q** to **]**. To go up and down an octave use **L** and **,**.

**F1** - panels view

**F2** - blocks view

**F3** - waves view

**F4** - open the selected block's custom edit page on the main part of the screen. Press again to hide the sidebar and enlarge the edit page.

**F6** - sidebar block settings page

**alt-F6** - open the selected block's voice max patcher for editing.

**F7** - sidebar connections list page

**F8** - files page (save/load/merge/choose song folder)

**F10** - toggle between showing all wires or just those of the selected block (improves performance/reduces GPU load on slow computers)

**F11** - toggle fullscreen

**F12** - show resource usage page



**ctrl-alt-F12** - hard restart benny





##BLOCKS PAGE

**shift-drag** - for a selection rectangle

**shift-click** - to multi-select blocks or wires 

**ctrl-click** - to mute blocks or wires
   
**ctrl-shift-click** - (when unmuting only) holding shift too also 'unmutes the tree' - any muted blocks connected to this one and any muted blocks connected to those, etc.

**alt-click** - to bypass blocks

**drag** - to connect blocks



**home** - center view

**-** or **+** - change the polyphony of the selected block

**ctrl-m** - toggle mute for the selected blocks

**ctrl-r** - toggle record arm for the selected blocks

**ctrl-a** - select all

**ctrl-c** - copy

**ctrl-x** - cut

**ctrl-v** - paste. 

    You can copy and paste single or multiple blocks in the blocks view.

    To copy parameter values from block to block: copy a single block, select a target block of the same kind and then paste.

**ctrl-alt-V** - paste blocks including their connections. For example, if you copy an oscillator that is connected to a mixer and a midi source, then the pasted duplicate will have the same connections.

**ctrl-z** - undo *(currently only undoes delete block, more to come)*

**del** / **backspace** - delete everything selected

**shift-del** - 'delete tree' - deletes the selected blocks, then any blocks that were only connected to/from a deleted block, recursively.

**shift-T** - 'select tree' - selects what delete tree would delete. useful for saving a part of a patch out as a template. by default select tree, delete tree and mute tree all ignore connections to core.input.control.* blocks when counting connections but the config key ```TREE_SELECT_IGNORES_CONTROL_BLOCKS``` can change this.

**alt-left arrow** - back to previous sidebar view

**alt-right arrow** - forward to next sidebar view

**alt-up** / **alt-down** - if you have a wire selected it will take you to the block at the start or end of the wire.

**enter** - open the new block menu

**tab** - toggle between blocks / panels views

**up** / **down** / **left** / **right** - move selected blocks, **+shift** for fine movement.

**PGUP** / **PGDN** - zoom in or out

**ctrl-T** - in fullscreen mode benny shows a clock in the top right corner. This key switches to showing a set timer (that starts the first time you press play). **ctrl-alt-T** resets this timer.

**?** - show help

**/** - to start searching amongst blocks in the current song

**any other keys** - start typing the name of your chosen block to bring up the new block menu.





##PANELS PAGE

**ctrl-m** , **tab** ,**-**, **+** work as on the blocks page.







##SIDEBAR

**scroll** / **drag** - to adjust sliders, zoom scopes etc. **+shift** for fine, **+alt+shift** for extra fine.

**ctrl-hover** your mouse over sliders to select an individual voice. **scroll+alt+shift** to tilt individual voice values around that voice.

**alt click** - to return a slider to its default value (or to the value saved in your songfile).