## Configuring the Camera

The Camera is primarily controlled in the **Player Camera Controller** Component on the Player, it handles the following logic:

- Capturing Mouse events through the new Input System
- Orienting the **Pivot** GameObject based on the movement of the Mouse
- Locking and Toggling Visibility of the Cursor
- Tilting the Player based on Horizontal Movement
- Increasing Field of View on Sprinting

## Cinemachine Properties

However, if we just move the **Pivot** then how is the rotation of the Camera determined? This is handled in the **CinemachineVirtualCamera** Component in the **CM VCam 1** GameObject. Let's take a look at that first.
