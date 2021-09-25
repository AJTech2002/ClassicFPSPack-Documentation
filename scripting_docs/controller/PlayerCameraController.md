# Player Camera Controller

The Camera is primarily controlled in the **Player Camera Controller** Component on the Player, it handles the following logic:

- Capturing Mouse events through the new Input System
- Orienting the **Pivot** GameObject based on the movement of the Mouse
- Locking and Toggling Visibility of the Cursor
- Tilting the Player based on Horizontal Movement
- Increasing Field of View on Sprinting

## Components

There are two main components that control the Camera, the Cinemachine Controller which has properties that modify the initial camera & follow behaviour; and the Player Camera Controller which handles logic.

### Cinemachine Controller

[Learn more about Cinemachine Controller](cinemachineproperties.md)

### Camera Controller

It's also important to know how the Camera is being modified in the **Player Camera Controller**.

Let's run through the different properties:

1. **Pivot Transform** : A reference to an empty GameObject in the center of the Player.

2. **Virtual Camera** : A reference to the **Cinemachine Virtual Camera** we covered in the last section.

3. **Lock Rotation** : If this is enabled it will just prevent the rotation from changing, this can be useful if we need to override the rotation of the Camera.

4. **Locked** : This is referring to the Cursor Lock State, there are 3 modes that can be selected. Locked is preferred so that the Cursor does not get in the way of testing the game.
   1. Locked : The Cursor cannot move when in the Game Window
   2. Confined : The Cursor cannot leave the Game Window
   3. None : The Cursor is left without change
5. **Visible** : Whether or not the Cursor is visible on the screen.

6. **Pitch Min Max** : The minimum and maximum rotation on the **up** and **down** axis for looking.

7. **Mouse Sensitivity** : How much a movement in the mouse affects the rotation of the Camera.

8. **Rotation Smooth Time** : How quickly the rotation of the Camera reaches its desired value.

9. **Camera Influenced By Player Input** : Whether or not the Player Camera Controller should listen to inputs from the controller to change its behaviour. Also this can be set to `false` if this Player is to be repurposed for a Third Person Controller.

10. **FOV Zoom Amount** : How much to increase the FOV when the Player starts sprinting.

11. **Tilt Amount** : How much to tilt the character when a horizontal movement is detected (inspired by Dusk).

12. **Tilt Speed** and **FOV Zoom Speed** : How quickly the two respective parameters above are influenced.

### Weapon Camera

In FPS Games there is a common problem whereby the Weapon will clip into the walls when the Player walks too close to walls. To combat this issue there are two Cameras rendering in the Player Controller.

The Camera which is controlled by the Cinemachine component and the Weapon Camera. The Weapon Camera is a child of the main Player Camera so it follows the same rotation/position.

The **Weapon Camera** is a property of the PlayerCameraController.

The Weapon Camera renders only items with the Layer: 'Weapon'. While the main Camera renders items without the Layer 'Weapon'.

With this combination the Weapon Camera will be rendererd ontop hence ensuring that the Weapons will always be ontop.

---

### What exactly does the Tilt and FOV Increase do?

By increasing the FOV when sprinting it gives a feel of speed increasing by slightly increasing the amount that you can see in the corners. By tilting the Camera while moving horizontally it provides a natural feel to the Camera and a sense of motion.

![fov_tilt_displace_2.gif](fov_tilt_displace_2.gif)
