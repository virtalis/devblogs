# Cable Router

This folder contains the Cable Router described in Tim's blog here: https://www.virtalis.com/blogs/implementing-an-immersive-cable-routing-system-in-visionary-render

## Usage
Copy the Cable_RouterGUI.VRCollection file to your gallery personal folder.
> C:\Users\\<username\>\Documents\Visionary Render\<version\>\Gallery

When you next start Visonary Render, the collection will appear in your Gallery. You can reload the Gallery with the refresh button if Visionary Render is already running.

The Cable gallery object should be added to the Scenes root node. Select the scenes root then in the Gallery, select Cable_RouterGUI.VRCollection in the gallery and click "Add to Scene".

When enabling HMDs, the code detects the hand controllers and will add the GUI to the left hand.

## Hardware Calibration
The cable router was created and setup using the Oculus Rift S and hasn't be tested with other HMDs.

### Hand alignment
This collection has been aligned for the Oculus Rift S, and will require adjustment to appear correctly when using the HTC Vive or other HMDs. This is just a matter of adjusting the OFFSET node position to be rotated/positioned as desired. 

### Laser Draw Plane
The 'short laser' draw plane that is created to allow drawing in space is positioned to work with the Oculus and is created dynamically. This *may not appear correctly with other HMDs*. If you find that the appearance is incorrect, the draw plane can be moved as required so that the laser will intersect it and create a 'short laser'.

To adjust the laser:
 - Locate the `DrawPlane` node in the scene root.
 - Select the `DrawPlane` Material and change the opacity to 1. As the material is created dynamically you won't see any visual change until you start drawing a new cable.
 - Begin drawing a cable. You should see that a new node is created in the tree called `CabelPlane` and with a child node called `DrawPlane`.
 - Select and re-position the `DrawPlane` node using local Transform property such that it correctly lines up with the laser.
 - Record the Local Transform values used.
 - In script editor search show the find bar (CTRL+F), change the Find setting to "Entire Scene" and search for: "DrawPlane.Transform.Position".
   - The resulting line in the Draw_Cable.Click script allows you to change the dynamically calculated draw plane.
   - Change the transform to the values you recorded when manually adjusting the `DrawPlane` node.
 - In the `DrawPlane` node set the material opacity back to 0.

### Saving Calibration
After adjusting the GUI to your HMD, you can create an update gallery object for future use. Simply select the CableGUI node on the scenes node, right click and select Save to Gallery.