States hold parameter settings for as many or as few blocks as you want.

## Storing states

With one block selected, in the sidebar click the states section. Click the state you'd like to store the current parameters to. You can ctrl-click to remove this block from a state in this section.

With multiple blocks selected the sidebar shows an 'add to state' section to add the current parameter settings of all selected blocks to a state.

### The **init** state

Once you save a songfile the initial state of all blocks is stored to the **init** state, represented by a black square button.

### Naming states

If you ctrl-click one of the global state buttons (bottom left of the benny window) you can edit the state name.

## Recalling states

For a single block you can recall a state by clicking the coloured square in the (unexpanded) states section of the sidebar.

The panels page also shows (by default, can be disabled in userconfig) a button for every stored state on the panel of the relevant block.

To recall a given state for ALL blocks use the global state buttons that are at the bottom left corner of the benny window.

![global state buttons](assets/screenshots/global_states.png)

Alt+click on the init state button also reloads all blocks' 'data' - everything that isn't a parameter that a block stores, eg patterns in sequencers, etc.

## State crossfading

You can smoothly and gradually transition into a state.

Click and hold on one of the global state buttons in the bottom left corner of the window. After a brief pause a horizontal slider appears. Drag to the right to interpolate from the current settings into the stored state.

![state xfade](assets/screenshots/state_fade.png)

## core.states block

The core.states block lets you trigger state transitions and fades from musical events inside benny.