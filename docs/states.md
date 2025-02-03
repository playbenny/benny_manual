States hold parameter settings for as many or as few blocks as you want.

## Storing states

![sidebar states section again](assets/screenshots/sidebar_states_edit.png)

With one block selected, in the sidebar click the states section. Click the state you would like to store the current parameters to. You can ctrl-click to remove this block from a state in this section.

With multiple blocks selected the sidebar shows an 'add to state' section to add the current parameter settings of all selected blocks to a state.

### The **init** state

Once you save a songfile the initial state of all blocks is stored to the **init** state, represented by a black square button.

### Naming states

If you ctrl-click one of the global state buttons (bottom left of the benny window) you can edit the state name.

![global state buttons](assets/screenshots/global_states.png)

## Recalling states

![sidebar states](assets/screenshots/sidebar_states_folded.png)

You can recall a state for a single block by clicking the coloured square in the (unexpanded) states section of the sidebar.

The panels page also shows (by default, can be disabled in ui preferences) a button for every stored state on the panel of the relevant block.

To recall a given state for ALL blocks use the global state buttons that are at the bottom left corner of the benny window.

The global states init button returns all blocks to the parameter values stored in the songfile. Alt+click on this button also reloads all blocks' 'data' - everything that isn't a parameter that a block stores, for example patterns in sequencers.

## State crossfading

You can crossfade from current parameter values to the ones stored in a state to make a smooth transition.

![state xfade](assets/screenshots/state_fade.png)

Click and hold on one of the global state buttons in the bottom left corner of the window. After a brief pause a horizontal slider appears. Drag to the right to interpolate from the current settings into the stored state.

## core.states block

The core.states block lets you trigger state transitions and fades from musical events inside benny.