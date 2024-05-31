# Node editor updates
## Add node shortcuts
![AddShortcuts.gif](AddShortcuts.gif){style=block}
Holding Ctrl and tapping a key on the Numpad (0-9, /, *, -, +, .) will open a popup of the available nodes and presets. Selecting one of the nodes/presets will assign that Numpad key to that node/preset so that each time the Numpad key is pressed - without Ctrl, since that's for setting the assignment - the chosen node/preset will be added to the active Node Editor.

Holding Ctrl and tapping the same key but clicking off the menu without making a selection will unassign the shortcut. The Alt key can be used for a second set of shortcuts. e.g.

* Ctrl+Num5 and choose Image node
* Hitting Num5 adds an Image node
* Ctrl+Alt+Num5 and choose Bricks node
* Hitting Alt+Num5 adds a Bricks node

## Adding Under Mouse
![Add_under_mouse.gif](Add_under_mouse.gif){style=block}
Newly-added nodes are now placed under the mouse when it is inside the node area, such as when using the shortcuts detailed above. When the mouse is outside the node area, double-clicking on a node in the list on the left, then the previous center placement is used.

## Mouse Wheel Zooming
![node_zoominout.gif](node_zoominout.gif){style=block}
An option has been added which allows the Node Editor's node view to be zoomed in/out via the mouse wheel. The MMB is still used to move the view in any direction.

## Quick Fit All
Double Middle-clicking in the Node Editor will perform the Fit All view adjustment.

## Drag-n-Drop Support
Image files can now be dragged from an OS file manager window into the Node Editor and the files will be imported into the active node graph. If of a supported type, a popup window is presented allowing the user to set what type of image node to load the image into. Node network .nod/.nodes can also be dropped into the window.

## Custom Colors
![Node_editor-customcolours.png](Node_editor-customcolours.png){style=block}
The right-click menu for a node now contains a Change Color entry, clicking that presents the chosen color picker. Allowing the user to change the color of a node.

## Group to Compound Node

The selected nodes can be grouped into a Compound node, preserving all the connections going into and out of the Compound node. This is available on a selected node's right-click menu or via the Ctrl+g shortcut. Ungrouping a Compound node, so that its contents are at the current node depth, is also available on the right-click menu and via the Ctrl+u shortcut.

## Node Presets

Selected nodes can be saved to a Preset in one of the defined Preset Locations. These presets will appear in the Node Tree on the left along with the other available nodes. Renaming and deleting a node preset can be done via the right-click menu in the Node Tree.

## Flat Node Menu
![Node_editor-flatmenu.png](Node_editor-flatmenu.png){style=block}
A Node Editor Option was added which allows the Add Node popup menu to appear "flat" i.e. one long list. This allows the existing menu filtering functionality to be used to quickly find the desired node. This menu includes Node Presets as well.

## VPR Node Editor Shortcut

Shift+Left Clicking a surface in a VPR viewport opens the Surface Editor to the surface that was clicked, this isn't new but now Shift+Right Clicking instead opens the Node Editor for the clicked surface.

## Tidy Selected Nodes

An enhancement to the existing Tidy Nodes. It now supports performing the tidy process on just the selected nodes, following the "Nothing is selected = everything is selected" paradigm.

## Duplicate Nodes
![Node_editor-duplicate.png](Node_editor-duplicate.png){style=block}
This creates a duplicate of the selected node(s) and preserves their incoming connections. These incoming connections are lost when doing a simple copy-and-paste of the node selection, but preserved when duplicating. The feature is present on a selected node's right-click menu as well as the shortcut Ctrl+d

## Node Connection Early Rejection

For the known connection types, when a connection cannot obviously be made the connection line will be drawn red. When the connection might be possible (or not), it's drawn yellow. And when the connection is likely to be compatible it's drawn in the normal highlight color (the same color that's normally used).

## Global Node Graph Tree
![Node_editor-globaltree.png](Node_editor-globaltree.png){style=block}
A searchable tree in the right side of the Node Editor window (visibility toggled via the 'h' key or the square/two column icon at the upper right corner of the window). The tree contains all the other Node Graphs that are present in the running application. Items are organized by their Graph Editor context, providing a natural hierarchy. Clicking an item, switches the active graph to the one that was clicked without having to close/reopen the Node Editor window.

## Expanded the LWShelfFuncs Global
Added four new functions to the public Preset Shelf API. These functions add the ability to poll and query the details of the host's Preset Locations (i.e. the folders that the user has configured as places to read and /or write preset files to). This change was needed as part of the Node Preset feature. This change is also documented in the SDK docs.